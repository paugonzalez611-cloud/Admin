import React, { useState, useEffect } from 'react';
import { 
  MessageSquare, 
  Target, 
  BarChart3, 
  Palette, 
  Info, 
  Users, 
  ArrowRight,
  ChevronLeft,
  Search,
  BookOpen,
  ShieldCheck
} from 'lucide-react';

// Mock Data for Chatbots
const CHATBOTS = [
  {
    id: 'community-manager',
    name: 'Elena Social',
    role: 'Community Manager',
    icon: <Users className="w-6 h-6" />,
    color: 'bg-blue-500',
    description: 'Experta en gestión de comunidades y tono de voz en redes sociales.',
    personality: 'Cercana, energética y siempre al día con las tendencias.',
    chat: [
      { role: 'user', content: '¿Cómo podemos mejorar el engagement en nuestra nueva campaña de lanzamiento?' },
      { role: 'bot', content: '¡Hola! Para el lanzamiento, no solo publiquemos anuncios. Necesitamos Storytelling. Sugiero crear una serie de "detrás de escena" en Stories y un concurso interactivo que premie la lealtad. Recuerda: la CIM exige que el tono en Instagram sea el mismo que en tu sitio web, pero adaptado a la calidez de la red.' },
      { role: 'user', content: '¿Qué hacemos si recibimos críticas negativas en los comentarios?' },
      { role: 'bot', content: 'La transparencia es clave en CIM. Responde rápido, con empatía y siempre alineado a los valores de la marca. Una respuesta coherente transforma un problema en una oportunidad de servicio al cliente.' }
    ]
  },
  {
    id: 'estratega',
    name: 'Marcus Plan',
    role: 'Estratega CIM',
    icon: <Target className="w-6 h-6" />,
    color: 'bg-indigo-600',
    description: 'Especialista en alineación estratégica y omnicanalidad.',
    personality: 'Profesional, estructurado y enfocado en la visión global.',
    chat: [
      { role: 'user', content: '¿Cómo aseguramos que el mensaje sea coherente en todos los canales?' },
      { role: 'bot', content: 'La clave es el "Manual de Identidad de Campaña". Antes de ejecutar, definimos un mensaje central único. Si en TV decimos "Innovación para todos", en el mailing no podemos enfocarnos solo en "Precio bajo". La omnicanalidad significa que el cliente siente la misma marca, sin importar dónde nos encuentre.' },
      { role: 'user', content: '¿Cuál es el error más común al intentar integrar canales?' },
      { role: 'bot', content: 'Trabajar en silos. El equipo de redes no habla con el de ventas. La CIM rompe esas barreras para que la experiencia del usuario sea fluida y sin contradicciones.' }
    ]
  },
  {
    id: 'analista',
    name: 'Dr. Data',
    role: 'Analista de Métricas',
    icon: <BarChart3 className="w-6 h-6" />,
    color: 'bg-orange-500',
    description: 'Experto en ROI, conversión y comportamiento del consumidor.',
    personality: 'Preciso, lógico y basado en evidencias numéricas.',
    chat: [
      { role: 'user', content: '¿Qué KPIs son los más importantes para medir el éxito de una estrategia CIM?' },
      { role: 'bot', content: 'No te pierdas en las métricas de vanidad. Para CIM, analizamos el Atribución Multi-Touch. Debemos mirar el CTR, la Tasa de Conversión Cruzada y, sobre todo, el Valor de Vida del Cliente (CLV). El éxito no es una venta aislada, es la sinergia de los puntos de contacto.' },
      { role: 'user', content: '¿Cómo sabemos si la integración de canales está funcionando?' },
      { role: 'bot', content: 'Si el costo de adquisición (CAC) baja mientras la recordación de marca sube, la integración es efectiva. Los datos no mienten: la coherencia genera confianza, y la confianza genera ventas.' }
    ]
  },
  {
    id: 'creativo',
    name: 'Santi Creativo',
    role: 'Creativo Publicitario',
    icon: <Palette className="w-6 h-6" />,
    color: 'bg-purple-500',
    description: 'Especialista en conceptos visuales e impacto emocional.',
    personality: 'Inspirador, visual y disruptivo.',
    chat: [
      { role: 'user', content: '¿Cómo crear una campaña visualmente impactante que respete la CIM?' },
      { role: 'bot', content: '¡La magia está en la consistencia! No se trata de repetir la misma imagen, sino de usar una "constante visual" (colores, tipografía, estilo fotográfico). Si el usuario ve un post y luego un cartel en la calle, debe reconocer la marca en 2 segundos, incluso sin ver el logo.' },
      { role: 'user', content: '¿Es más importante la creatividad o el mensaje?' },
      { role: 'bot', content: 'En CIM son inseparables. Una creatividad brillante sin un mensaje coherente es solo ruido. Diseñamos para emocionar, pero siempre bajo el paraguas de la estrategia de comunicación.' }
    ]
  }
];

const App = () => {
  const [view, setView] = useState('landing'); // landing, dashboard, chat, education
  const [selectedBot, setSelectedBot] = useState(null);
  const [searchQuery, setSearchQuery] = useState('');

  const filteredBots = CHATBOTS.filter(bot => 
    bot.name.toLowerCase().includes(searchQuery.toLowerCase()) || 
    bot.role.toLowerCase().includes(searchQuery.toLowerCase())
  );

  const renderLanding = () => (
    <div className="flex flex-col items-center justify-center min-h-[80vh] text-center px-4">
      <div className="mb-6 p-4 bg-blue-100 rounded-full animate-bounce">
        <ShieldCheck className="w-12 h-12 text-blue-600" />
      </div>
      <h1 className="text-4xl md:text-6xl font-bold text-slate-900 mb-6">
        <span className="text-blue-600">Admin</span> Master
      </h1>
      <p className="text-xl text-slate-600 max-w-2xl mb-10 leading-relaxed">
        El centro de mando definitivo para las <strong>Comunicaciones Integradas de Marketing</strong>. Aprende de expertos y domina la coherencia estratégica.
      </p>
      <div className="flex flex-col sm:flex-row gap-4">
        <button 
          onClick={() => setView('dashboard')}
          className="px-8 py-4 bg-blue-600 text-white rounded-xl font-semibold hover:bg-blue-700 transition-all flex items-center justify-center gap-2 shadow-lg hover:shadow-blue-200"
        >
          Acceder al Panel <ArrowRight className="w-5 h-5" />
        </button>
        <button 
          onClick={() => setView('education')}
          className="px-8 py-4 bg-white text-slate-700 border border-slate-200 rounded-xl font-semibold hover:bg-slate-50 transition-all flex items-center justify-center gap-2"
        >
          Manual de CIM <BookOpen className="w-5 h-5" />
        </button>
      </div>
    </div>
  );

  const renderDashboard = () => (
    <div className="max-w-6xl mx-auto px-4 py-10">
      <div className="flex flex-col md:flex-row md:items-center justify-between mb-10 gap-6">
        <div>
          <h2 className="text-3xl font-bold text-slate-900">Admin Master Expertos</h2>
          <p className="text-slate-500">Gestione y aprenda de los líderes en cada área del marketing.</p>
        </div>
        <div className="relative">
          <Search className="absolute left-3 top-1/2 transform -translate-y-1/2 text-slate-400 w-5 h-5" />
          <input 
            type="text" 
            placeholder="Buscar experto o rol..." 
            className="pl-10 pr-4 py-2 border border-slate-200 rounded-lg w-full md:w-64 focus:outline-none focus:ring-2 focus:ring-blue-500 transition-all"
            value={searchQuery}
            onChange={(e) => setSearchQuery(e.target.value)}
          />
        </div>
      </div>

      <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
        {filteredBots.map((bot) => (
          <div 
            key={bot.id}
            className="bg-white border border-slate-100 rounded-2xl p-6 shadow-sm hover:shadow-xl transition-all group cursor-pointer"
            onClick={() => {
              setSelectedBot(bot);
              setView('chat');
            }}
          >
            <div className={`${bot.color} text-white w-12 h-12 rounded-xl flex items-center justify-center mb-4 group-hover:scale-110 transition-transform shadow-lg`}>
              {bot.icon}
            </div>
            <h3 className="text-xl font-bold text-slate-900 mb-1">{bot.name}</h3>
            <p className="text-sm font-semibold text-blue-600 mb-3">{bot.role}</p>
            <p className="text-slate-600 text-sm mb-6 line-clamp-2">{bot.description}</p>
            <button className="w-full py-2 bg-slate-50 text-slate-700 rounded-lg text-sm font-bold group-hover:bg-blue-600 group-hover:text-white transition-colors border border-slate-100">
              Consultar Experto
            </button>
          </div>
        ))}
      </div>
    </div>
  );

  const renderChat = () => (
    <div className="max-w-4xl mx-auto px-4 py-6">
      <button 
        onClick={() => setView('dashboard')}
        className="flex items-center gap-2 text-slate-500 hover:text-blue-600 mb-6 transition-colors font-medium"
      >
        <ChevronLeft className="w-5 h-5" /> Volver al Panel Maestro
      </button>

      <div className="bg-white rounded-3xl shadow-2xl overflow-hidden border border-slate-100 flex flex-col h-[70vh]">
        {/* Chat Header */}
        <div className={`${selectedBot.color} p-6 text-white flex items-center justify-between`}>
          <div className="flex items-center gap-4">
            <div className="bg-white/20 p-3 rounded-full">
              {selectedBot.icon}
            </div>
            <div>
              <h3 className="text-xl font-bold">{selectedBot.name}</h3>
              <p className="text-white/80 text-sm italic">{selectedBot.role}</p>
            </div>
          </div>
          <div className="hidden sm:block">
            <span className="bg-black/20 px-3 py-1 rounded-full text-xs font-mono">ID: {selectedBot.id.toUpperCase()}</span>
          </div>
        </div>

        {/* Personality Badge */}
        <div className="bg-slate-50 px-6 py-2 border-b border-slate-100 italic text-xs text-slate-500 flex justify-between">
          <span>Personalidad: {selectedBot.personality}</span>
          <span>Status: Sesión Grabada</span>
        </div>

        {/* Chat Body */}
        <div className="flex-1 overflow-y-auto p-6 space-y-6 bg-slate-50/30">
          {selectedBot.chat.map((msg, index) => (
            <div key={index} className={`flex ${msg.role === 'user' ? 'justify-end' : 'justify-start'}`}>
              <div className={`max-w-[85%] p-4 rounded-2xl ${
                msg.role === 'user' 
                  ? 'bg-blue-600 text-white rounded-br-none shadow-md' 
                  : 'bg-white border border-slate-200 text-slate-800 rounded-bl-none shadow-sm'
              }`}>
                <p className="text-sm md:text-base leading-relaxed">
                  {msg.content}
                </p>
              </div>
            </div>
          ))}
        </div>

        {/* Chat Input Placeholder */}
        <div className="p-4 bg-white border-t border-slate-100">
          <div className="flex gap-2 items-center text-slate-400 bg-slate-50 px-4 py-2 rounded-full text-sm italic border border-slate-100">
            <ShieldCheck className="w-4 h-4 text-blue-500" /> Registro de conversación autenticado por Admin Master
          </div>
        </div>
      </div>
    </div>
  );

  const renderEducation = () => (
    <div className="max-w-4xl mx-auto px-4 py-10">
      <button 
        onClick={() => setView('landing')}
        className="flex items-center gap-2 text-slate-500 hover:text-blue-600 mb-8 transition-colors font-medium"
      >
        <ChevronLeft className="w-5 h-5" /> Regresar
      </button>

      <div className="space-y-12">
        <header className="border-b border-slate-200 pb-8">
          <h2 className="text-4xl font-bold text-slate-900 mb-4">Manual Estratégico CIM</h2>
          <p className="text-lg text-slate-600">
            La Comunicación Integrada de Marketing (CIM) es el estándar de oro para las marcas modernas gestionadas en <span className="font-bold text-blue-600">Admin Master</span>.
          </p>
        </header>

        <div className="grid grid-cols-1 md:grid-cols-2 gap-8">
          <div className="bg-white p-8 rounded-2xl border-l-4 border-l-blue-600 shadow-sm border border-slate-100">
            <h3 className="text-xl font-bold text-blue-600 mb-4">Los 4 Pilares Fundamentales</h3>
            <ul className="space-y-4 text-slate-600">
              <li className="flex gap-3">
                <div className="w-6 h-6 rounded-full bg-blue-100 text-blue-600 flex items-center justify-center text-xs font-bold shrink-0">1</div>
                <div><strong>Coherencia:</strong> Alineación absoluta de todos los mensajes.</div>
              </li>
              <li className="flex gap-3">
                <div className="w-6 h-6 rounded-full bg-blue-100 text-blue-600 flex items-center justify-center text-xs font-bold shrink-0">2</div>
                <div><strong>Consistencia:</strong> Ausencia total de contradicciones en el discurso.</div>
              </li>
              <li className="flex gap-3">
                <div className="w-6 h-6 rounded-full bg-blue-100 text-blue-600 flex items-center justify-center text-xs font-bold shrink-0">3</div>
                <div><strong>Continuidad:</strong> Mantenimiento estratégico a largo plazo.</div>
              </li>
              <li className="flex gap-3">
                <div className="w-6 h-6 rounded-full bg-blue-100 text-blue-600 flex items-center justify-center text-xs font-bold shrink-0">4</div>
                <div><strong>Complementariedad:</strong> Sinergia entre canales para potenciar el ROI.</div>
              </li>
            </ul>
          </div>

          <div className="bg-slate-900 text-white p-8 rounded-2xl shadow-xl">
            <h3 className="text-xl font-bold text-blue-400 mb-4">Visión Admin Master</h3>
            <p className="text-slate-300 mb-4 italic">
              "Una marca no es lo que decimos, es lo que el consumidor percibe en cada punto de contacto."
            </p>
            <ul className="space-y-3 text-slate-400 text-sm">
              <li>• Integración de Ventas y Marketing.</li>
              <li>• Análisis de Big Data para decisiones.</li>
              <li>• Creatividad basada en estrategia.</li>
              <li>• Tono de voz omnicanal.</li>
            </ul>
          </div>
        </div>

        <div className="bg-blue-600 text-white p-10 rounded-3xl text-center shadow-blue-200 shadow-2xl">
          <h3 className="text-2xl font-bold mb-4">Comience su Entrenamiento</h3>
          <p className="text-blue-100 mb-6 max-w-md mx-auto">Acceda a las conversaciones grabadas para ver la teoría aplicada por nuestros expertos.</p>
          <button 
            onClick={() => setView('dashboard')}
            className="px-8 py-3 bg-white text-blue-600 rounded-xl font-bold hover:bg-slate-50 transition-all transform hover:-translate-y-1"
          >
            Abrir Consola de Expertos
          </button>
        </div>
      </div>
    </div>
  );

  return (
    <div className="min-h-screen bg-slate-50 font-sans text-slate-900 selection:bg-blue-100 selection:text-blue-900">
      {/* Navigation Bar */}
      <nav className="sticky top-0 z-50 bg-white/90 backdrop-blur-md border-b border-slate-200 px-6 py-4 shadow-sm">
        <div className="max-w-6xl mx-auto flex items-center justify-between">
          <div 
            className="flex items-center gap-2 cursor-pointer group"
            onClick={() => setView('landing')}
          >
            <div className="w-10 h-10 bg-blue-600 rounded-xl flex items-center justify-center group-hover:rotate-12 transition-transform shadow-blue-200 shadow-lg">
              <ShieldCheck className="w-6 h-6 text-white" />
            </div>
            <div className="flex flex-col -space-y-1">
              <span className="font-black text-xl tracking-tighter text-slate-900 italic">ADMIN</span>
              <span className="font-medium text-xs tracking-widest text-blue-600 uppercase">MASTER</span>
            </div>
          </div>
          
          <div className="hidden md:flex items-center gap-8 text-sm font-bold text-slate-500">
            <button onClick={() => setView('landing')} className={`hover:text-blue-600 transition-colors uppercase tracking-wider ${view === 'landing' ? 'text-blue-600' : ''}`}>Inicio</button>
            <button onClick={() => setView('dashboard')} className={`hover:text-blue-600 transition-colors uppercase tracking-wider ${view === 'dashboard' || view === 'chat' ? 'text-blue-600' : ''}`}>Consola</button>
            <button onClick={() => setView('education')} className={`hover:text-blue-600 transition-colors uppercase tracking-wider ${view === 'education' ? 'text-blue-600' : ''}`}>Manual</button>
          </div>

          <button 
            onClick={() => setView('dashboard')}
            className="bg-slate-900 text-white px-6 py-2 rounded-lg text-xs font-black uppercase tracking-widest hover:bg-blue-600 transition-all shadow-md active:scale-95 border border-white/10"
          >
            Acceso Master
          </button>
        </div>
      </nav>

      {/* Main Content */}
      <main className="animate-in fade-in slide-in-from-bottom-4 duration-700">
        {view === 'landing' && renderLanding()}
        {view === 'dashboard' && renderDashboard()}
        {view === 'chat' && renderChat()}
        {view === 'education' && renderEducation()}
      </main>

      {/* Footer */}
      <footer className="mt-20 border-t border-slate-200 py-10 text-center">
        <div className="flex items-center justify-center gap-2 mb-2 text-slate-400 font-bold uppercase text-[10px] tracking-[0.3em]">
          <ShieldCheck className="w-4 h-4" /> Autenticado por Admin Master
        </div>
        <p className="text-slate-400 text-xs">© 2024 Admin Master System - Inteligencia Estratégica en CIM</p>
      </footer>
    </div>
  );
};

export default App;
