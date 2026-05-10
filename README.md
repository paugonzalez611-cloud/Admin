import React, { useState, useEffect, useRef } from 'react';
import {
  MessageSquare, Target, BarChart3, Palette, Users,
  ArrowRight, ChevronLeft, Search, BookOpen, Zap, TrendingUp, Award, Sparkles
} from 'lucide-react';

const FONTS = `@import url('https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,700;0,9..144,900;1,9..144,400&family=Syne:wght@400;600;700;800&display=swap');`;

const CHATBOTS = [
  {
    id: 'community-manager',
    name: 'Elena Social',
    role: 'Community Manager',
    icon: <Users className="w-5 h-5" />,
    accent: '#3B82F6',
    accentLight: '#EFF6FF',
    accentDark: '#1D4ED8',
    tag: 'Redes & Comunidad',
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
    icon: <Target className="w-5 h-5" />,
    accent: '#6366F1',
    accentLight: '#EEF2FF',
    accentDark: '#4338CA',
    tag: 'Estrategia Global',
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
    icon: <BarChart3 className="w-5 h-5" />,
    accent: '#F97316',
    accentLight: '#FFF7ED',
    accentDark: '#C2410C',
    tag: 'ROI & Analytics',
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
    icon: <Palette className="w-5 h-5" />,
    accent: '#A855F7',
    accentLight: '#FAF5FF',
    accentDark: '#7E22CE',
    tag: 'Creatividad Visual',
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

const PILLARS = [
  { num: '01', title: 'Coherencia', desc: 'Los mensajes deben relacionarse entre sí y reforzar un mensaje central único a través de todos los puntos de contacto.', color: '#3B82F6' },
  { num: '02', title: 'Consistencia', desc: 'El mensaje no puede ser contradictorio. La marca debe hablar con una sola voz sin importar el canal.', color: '#6366F1' },
  { num: '03', title: 'Continuidad', desc: 'Comunicación sostenida en el tiempo que construye reconocimiento y confianza de forma progresiva.', color: '#F97316' },
  { num: '04', title: 'Complementariedad', desc: 'La suma de las partes es mayor al todo. Cada canal amplifica el impacto de los demás.', color: '#A855F7' },
];

const globalStyles = `
  ${FONTS}
  .cim-display { font-family: 'Fraunces', serif; }
  .cim-ui { font-family: 'Syne', sans-serif; }
  .cim-body { font-family: 'Syne', sans-serif; }
  
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }
  
  @keyframes shimmer {
    0% { background-position: -200% center; }
    100% { background-position: 200% center; }
  }

  @keyframes float {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-10px); }
  }

  .fade-up { animation: fadeUp 0.6s cubic-bezier(0.16,1,0.3,1) both; }
  .fade-up-1 { animation-delay: 0.05s; }
  .fade-up-2 { animation-delay: 0.12s; }
  .fade-up-3 { animation-delay: 0.2s; }
  .fade-up-4 { animation-delay: 0.28s; }
  
  .shimmer-text {
    background: linear-gradient(90deg, #1e3a8a 0%, #3b82f6 30%, #818cf8 50%, #3b82f6 70%, #1e3a8a 100%);
    background-size: 200% auto;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    animation: shimmer 4s linear infinite;
  }

  .floating-icon {
    animation: float 4s ease-in-out infinite;
  }

  .bot-card-inner { transition: transform 0.4s cubic-bezier(0.16,1,0.3,1), box-shadow 0.4s ease; }
  .bot-card:hover .bot-card-inner { transform: translateY(-8px); box-shadow: 0 30px 60px -12px rgba(0,0,0,0.15); }
  
  .nav-link { position: relative; }
  .nav-link::after { content: ''; position: absolute; bottom: -2px; left: 0; width: 0; height: 2px; background: #3b82f6; transition: width 0.3s ease; }
  .nav-link.active::after, .nav-link:hover::after { width: 100%; }
  
  .custom-scrollbar::-webkit-scrollbar { width: 6px; }
  .custom-scrollbar::-webkit-scrollbar-track { background: transparent; }
  .custom-scrollbar::-webkit-scrollbar-thumb { background: #E2E8F0; border-radius: 10px; }
  .custom-scrollbar::-webkit-scrollbar-thumb:hover { background: #CBD5E1; }
  
  .hero-bg {
    background: radial-gradient(circle at top right, rgba(59,130,246,0.1) 0%, transparent 40%),
                radial-gradient(circle at bottom left, rgba(99,102,241,0.08) 0%, transparent 40%),
                #FAFAFA;
  }
`;

export default function App() {
  const [view, setView] = useState('landing');
  const [selectedBot, setSelectedBot] = useState(null);
  const [searchQuery, setSearchQuery] = useState('');
  const chatEndRef = useRef(null);

  useEffect(() => {
    if (view === 'chat' && chatEndRef.current) {
      chatEndRef.current.scrollIntoView({ behavior: 'smooth' });
    }
  }, [view, selectedBot]);

  const filteredBots = CHATBOTS.filter(bot =>
    bot.name.toLowerCase().includes(searchQuery.toLowerCase()) ||
    bot.role.toLowerCase().includes(searchQuery.toLowerCase()) ||
    bot.tag.toLowerCase().includes(searchQuery.toLowerCase())
  );

  const navigate = (dest) => {
    window.scrollTo({ top: 0, behavior: 'smooth' });
    setView(dest);
  };

  const renderLanding = () => (
    <div className="hero-bg min-h-screen">
      <div className="max-w-6xl mx-auto px-6 pt-24 pb-20">
        <div className="text-center mb-16">
          <div className="fade-up fade-up-1 mb-6 inline-flex items-center gap-2 px-4 py-2 bg-white rounded-full border border-slate-200 shadow-sm text-xs font-bold text-slate-600 tracking-wider uppercase">
            <Sparkles size={14} className="text-blue-500" />
            Simulador de Estrategia Publicitaria
          </div>

          <h1 className="cim-display fade-up fade-up-2 mb-8"
            style={{ fontSize: 'clamp(48px, 9vw, 96px)', fontWeight: 900, lineHeight: 0.9, letterSpacing: '-3px', color: '#0F172A' }}>
            Marketing <br />
            <span className="shimmer-text">Integrado</span><br />
            <span style={{ fontStyle: 'italic', fontWeight: 300 }}>con Propósito</span>
          </h1>

          <p className="cim-body fade-up fade-up-3 mx-auto mb-12 text-lg text-slate-500 max-w-xl leading-relaxed">
            Explora la sinergia de canales a través de diálogos con mentores virtuales. Domina la coherencia, consistencia y el impacto de marca.
          </p>

          <div className="fade-up fade-up-4 flex flex-col sm:flex-row gap-4 justify-center items-center">
            <button onClick={() => navigate('dashboard')}
              className="cim-ui bg-slate-900 text-white px-10 py-5 rounded-2xl font-bold text-base transition-all hover:bg-slate-800 hover:scale-105 active:scale-95 shadow-xl shadow-slate-200 flex items-center gap-3">
              Comenzar Simulación <ArrowRight size={20} />
            </button>
            <button onClick={() => navigate('education')}
              className="cim-ui bg-white text-slate-700 border-2 border-slate-100 px-10 py-5 rounded-2xl font-bold text-base transition-all hover:border-blue-400 hover:text-blue-600 flex items-center gap-3">
              <BookOpen size={20} /> Guía Académica
            </button>
          </div>
        </div>

        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 fade-up" style={{ animationDelay: '0.4s' }}>
          {CHATBOTS.map((bot, i) => (
            <div key={bot.id} 
              onClick={() => { setSelectedBot(bot); navigate('chat'); }}
              className="group cursor-pointer bg-white p-8 rounded-3xl border border-slate-100 shadow-sm transition-all hover:border-blue-200 hover:shadow-xl hover:-translate-y-2">
              <div className="mb-6 flex items-center justify-between">
                <div style={{ background: bot.accentLight, color: bot.accent }} className="w-14 h-14 rounded-2xl flex items-center justify-center transition-transform group-hover:scale-110">
                  {React.cloneElement(bot.icon, { size: 28 })}
                </div>
                <div className="opacity-0 group-hover:opacity-100 transition-opacity text-slate-300">
                  <ArrowRight size={20} />
                </div>
              </div>
              <h3 className="cim-ui text-xl font-extrabold text-slate-900 mb-1">{bot.name}</h3>
              <p className="cim-ui text-xs font-bold uppercase tracking-widest mb-4" style={{ color: bot.accent }}>{bot.tag}</p>
              <p className="cim-body text-sm text-slate-500 leading-relaxed line-clamp-2">{bot.description}</p>
            </div>
          ))}
        </div>
      </div>
    </div>
  );

  const renderDashboard = () => (
    <div className="max-w-6xl mx-auto px-6 py-16">
      <div className="flex flex-col md:flex-row md:items-center justify-between mb-12 gap-8">
        <div className="fade-up">
          <span className="cim-ui text-blue-500 font-black text-xs tracking-widest uppercase mb-3 block">Mentoría Especializada</span>
          <h2 className="cim-display text-5xl font-black text-slate-900 tracking-tight leading-none">
            Panel de <br /><span className="italic font-light">Expertos CIM</span>
          </h2>
        </div>
        <div className="fade-up fade-up-2 relative">
          <Search className="absolute left-4 top-1/2 -translate-y-1/2 text-slate-400" size={18} />
          <input
            type="text"
            placeholder="Filtrar por rol o nombre..."
            className="cim-ui w-full md:w-80 pl-12 pr-6 py-4 bg-white border border-slate-200 rounded-2xl focus:outline-none focus:ring-4 focus:ring-blue-50 focus:border-blue-400 transition-all text-slate-600"
            value={searchQuery}
            onChange={e => setSearchQuery(e.target.value)}
          />
        </div>
      </div>

      <div className="grid grid-cols-1 md:grid-cols-2 gap-8">
        {filteredBots.map((bot, i) => (
          <div key={bot.id} 
            className="bot-card fade-up"
            style={{ animationDelay: `${i * 0.1}s` }}
            onClick={() => { setSelectedBot(bot); navigate('chat'); }}>
            <div className="bot-card-inner bg-white rounded-[32px] border border-slate-100 overflow-hidden group cursor-pointer h-full">
              <div className="h-2 w-full" style={{ background: `linear-gradient(90deg, ${bot.accent}, ${bot.accentDark})` }} />
              <div className="p-10">
                <div className="flex items-start justify-between mb-8">
                  <div className="flex gap-6 items-center">
                    <div style={{ background: bot.accentLight, color: bot.accent }} className="w-16 h-16 rounded-2xl flex items-center justify-center flex-shrink-0">
                      {React.cloneElement(bot.icon, { size: 32 })}
                    </div>
                    <div>
                      <h3 className="cim-ui text-2xl font-black text-slate-900 mb-1">{bot.name}</h3>
                      <span className="cim-ui text-xs font-extrabold px-3 py-1 rounded-full uppercase tracking-wider" 
                            style={{ background: bot.accentLight, color: bot.accent }}>
                        {bot.role}
                      </span>
                    </div>
                  </div>
                </div>
                <p className="cim-body text-slate-500 text-base leading-relaxed mb-8">{bot.description}</p>
                <div className="flex items-center justify-between pt-8 border-t border-slate-50">
                  <span className="cim-ui text-sm font-bold italic text-slate-400">"{bot.personality}"</span>
                  <div className="flex gap-1.5">
                    {[1,2,3].map(dot => (
                      <div key={dot} className="w-1.5 h-1.5 rounded-full" style={{ background: bot.accent, opacity: 0.3 }} />
                    ))}
                  </div>
                </div>
              </div>
            </div>
          </div>
        ))}
        {filteredBots.length === 0 && (
          <div className="col-span-full py-20 text-center bg-slate-50 rounded-[32px] border-2 border-dashed border-slate-200">
            <p className="cim-ui text-slate-400 font-bold">No se encontraron expertos para tu búsqueda.</p>
          </div>
        )}
      </div>
    </div>
  );

  const renderChat = () => (
    <div className="max-w-4xl mx-auto px-4 py-12">
      <div className="flex items-center justify-between mb-8 fade-up">
        <button onClick={() => navigate('dashboard')}
          className="cim-ui flex items-center gap-2 text-slate-500 font-bold hover:text-blue-600 transition-colors">
          <ChevronLeft size={20} /> Panel de Expertos
        </button>
        <div className="px-4 py-2 bg-white rounded-full border border-slate-100 text-[11px] font-black text-slate-400 uppercase tracking-widest">
          Caso Práctico: Lanzamiento 2025
        </div>
      </div>

      <div className="fade-up fade-up-1 bg-white rounded-[40px] border border-slate-100 shadow-2xl overflow-hidden flex flex-col h-[75vh]">
        {/* Chat Header */}
        <div className="p-8 flex items-center justify-between" style={{ background: `linear-gradient(135deg, ${selectedBot.accentDark} 0%, ${selectedBot.accent} 100%)` }}>
          <div className="flex items-center gap-5">
            <div className="w-16 h-16 rounded-2xl bg-white/20 backdrop-blur-md flex items-center justify-center text-white border border-white/20">
              {React.cloneElement(selectedBot.icon, { size: 32 })}
            </div>
            <div>
              <h3 className="cim-ui text-2xl font-black text-white leading-tight">{selectedBot.name}</h3>
              <p className="cim-ui text-sm text-white/70 font-bold tracking-wide uppercase">{selectedBot.role}</p>
            </div>
          </div>
          <div className="hidden sm:flex items-center gap-3 bg-black/10 px-4 py-2 rounded-xl border border-white/10">
            <div className="w-2 h-2 rounded-full bg-green-400 animate-pulse" />
            <span className="cim-ui text-[11px] font-black text-white uppercase">Activo para consulta</span>
          </div>
        </div>

        {/* Chat Content */}
        <div className="flex-1 overflow-y-auto p-8 space-y-8 custom-scrollbar bg-slate-50/30">
          <div className="text-center py-4">
             <span className="cim-ui text-[10px] font-black text-slate-300 uppercase tracking-[0.2em]">Inicio de la sesión de mentoría</span>
          </div>
          
          {selectedBot.chat.map((msg, idx) => (
            <div key={idx} className={`flex ${msg.role === 'user' ? 'justify-end' : 'justify-start'}`}>
              <div className={`max-w-[85%] sm:max-w-[70%] rounded-3xl p-6 shadow-sm flex flex-col gap-2 ${
                msg.role === 'user' 
                  ? 'bg-slate-900 text-white rounded-tr-none' 
                  : 'bg-white border border-slate-100 text-slate-700 rounded-tl-none'
              }`}>
                <p className="cim-body text-sm leading-relaxed">{msg.content}</p>
                <span className={`text-[10px] font-bold uppercase tracking-wider opacity-40 text-right`}>
                  {msg.role === 'user' ? 'Tú' : selectedBot.name}
                </span>
              </div>
            </div>
          ))}
          <div ref={chatEndRef} />
        </div>

        {/* Chat Input Placeholder */}
        <div className="p-6 bg-white border-t border-slate-50">
          <div className="bg-slate-50 rounded-2xl p-4 flex items-center justify-between border border-slate-100">
            <div className="flex items-center gap-3 text-slate-400">
              <MessageSquare size={18} />
              <span className="cim-ui text-sm font-bold">Simulación de lectura: Analiza la respuesta del experto</span>
            </div>
            <div className="flex gap-2">
              <button className="px-4 py-2 bg-blue-100 text-blue-600 rounded-lg text-xs font-black uppercase tracking-wider">Siguiente</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  );

  const renderEducation = () => (
    <div className="max-w-4xl mx-auto px-6 py-16">
      <button onClick={() => navigate('landing')}
        className="cim-ui flex items-center gap-2 text-slate-500 font-bold hover:text-blue-600 transition-colors mb-12">
        <ChevronLeft size={20} /> Regresar
      </button>

      <div className="fade-up mb-16">
        <span className="cim-ui text-blue-500 font-black text-xs tracking-widest uppercase mb-3 block">Fundamentos</span>
        <h2 className="cim-display text-6xl font-black text-slate-900 leading-none mb-8 tracking-tighter">
          Dominando la <br /><span className="italic font-light">Estrategia CIM</span>
        </h2>
        <div className="p-8 bg-blue-50 rounded-[32px] border-l-8 border-blue-500">
           <p className="cim-body text-lg text-blue-900 font-medium leading-relaxed">
            "La CIM no es solo marketing multicanal; es la orquestación perfecta de la voz de una marca para que el consumidor siempre reciba la misma promesa, sin importar el punto de contacto."
           </p>
        </div>
      </div>

      <div className="grid grid-cols-1 md:grid-cols-2 gap-6 mb-20">
        {PILLARS.map((p, i) => (
          <div key={i} className="fade-up bg-white p-10 rounded-[32px] border border-slate-100 hover:border-blue-200 transition-all group"
               style={{ animationDelay: `${i * 0.1}s` }}>
            <span className="cim-display text-5xl font-black text-slate-100 group-hover:text-blue-50 transition-colors mb-4 block leading-none">{p.num}</span>
            <h4 className="cim-ui text-xl font-black text-slate-900 mb-3" style={{ color: p.color }}>{p.title}</h4>
            <p className="cim-body text-slate-500 text-sm leading-relaxed">{p.desc}</p>
          </div>
        ))}
      </div>

      <div className="fade-up bg-slate-900 rounded-[48px] p-12 text-center relative overflow-hidden">
        <div className="absolute top-0 left-0 w-full h-full opacity-10 pointer-events-none">
          <div className="absolute top-10 left-10 w-40 h-40 bg-blue-500 rounded-full blur-[80px]" />
          <div className="absolute bottom-10 right-10 w-60 h-60 bg-purple-500 rounded-full blur-[100px]" />
        </div>
        <h3 className="cim-display text-4xl font-black text-white mb-6 relative z-10">¿Listo para aplicar <br /><span className="italic font-light">lo aprendido?</span></h3>
        <p className="cim-body text-slate-400 text-base mb-10 max-w-md mx-auto relative z-10">Pon a prueba tu conocimiento interactuando con los mentores en el panel de expertos.</p>
        <button onClick={() => navigate('dashboard')}
          className="cim-ui relative z-10 bg-white text-slate-900 px-10 py-5 rounded-2xl font-extrabold transition-transform hover:scale-105 active:scale-95 shadow-2xl">
          Ir al Panel de Expertos
        </button>
      </div>
    </div>
  );

  return (
    <div className="min-h-screen bg-slate-50/50 selection:bg-blue-100 selection:text-blue-900 overflow-x-hidden">
      <style>{globalStyles}</style>

      {/* Modern Navigation */}
      <nav className="sticky top-0 z-50 bg-white/80 backdrop-blur-xl border-b border-slate-100 px-6 h-20 flex items-center">
        <div className="max-w-6xl mx-auto w-full flex justify-between items-center">
          <div className="flex items-center gap-3 cursor-pointer group" onClick={() => navigate('landing')}>
            <div className="w-12 h-12 bg-slate-900 rounded-2xl flex items-center justify-center transition-transform group-hover:rotate-12 group-active:scale-90">
              <Target size={24} className="text-blue-400" />
            </div>
            <div className="flex flex-col">
              <span className="cim-ui text-lg font-black text-slate-900 leading-none tracking-tight">AdminMaster</span>
              <span className="cim-ui text-[10px] font-bold text-slate-400 uppercase tracking-widest mt-1">Simulador CIM</span>
            </div>
          </div>

          <div className="hidden md:flex items-center gap-10">
            {[
              { label: 'Inicio', dest: 'landing' },
              { label: 'Mentores', dest: 'dashboard' },
              { label: 'Conceptos', dest: 'education' },
            ].map(item => (
              <button key={item.dest} 
                onClick={() => navigate(item.dest)}
                className={`nav-link cim-ui text-sm font-bold transition-colors ${
                  view === item.dest || (item.dest === 'dashboard' && view === 'chat') 
                    ? 'text-slate-900 active' 
                    : 'text-slate-400 hover:text-slate-600'
                }`}>
                {item.label}
              </button>
            ))}
          </div>

          <button onClick={() => navigate('dashboard')}
            className="cim-ui bg-blue-600 text-white px-6 py-3 rounded-xl font-bold text-sm hover:bg-blue-700 transition-all hover:shadow-lg hover:shadow-blue-200 active:scale-95">
            Iniciar Mentoría
          </button>
        </div>
      </nav>

      {/* Page Content */}
      <main>
        {view === 'landing' && renderLanding()}
        {view === 'dashboard' && renderDashboard()}
        {view === 'chat' && selectedBot && renderChat()}
        {view === 'education' && renderEducation()}
      </main>

      {/* Minimal Footer */}
      <footer className="py-12 border-t border-slate-100 text-center">
        <div className="flex items-center justify-center gap-3 mb-4 opacity-30">
          <Target size={16} />
          <div className="w-1 h-1 rounded-full bg-slate-400" />
          <BarChart3 size={16} />
          <div className="w-1 h-1 rounded-full bg-slate-400" />
          <Palette size={16} />
        </div>
        <p className="cim-ui text-slate-400 font-bold text-[10px] uppercase tracking-[0.2em]">
          Simulador Educativo de Comunicación Integrada de Marketing · 2025
        </p>
      </footer>
    </div>
  );
}
