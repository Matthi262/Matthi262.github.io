# Matthi262.github.io
<!DOCTYPE html>
<html lang="de" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Global Questing - Entdecke die Welt spielerisch</title>
    <meta name="description" content="Verwandle deine Reise in ein episches Abenteuer mit KI-generierten Quests.">
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700&family=Outfit:wght@300;500;700;900&display=swap" rel="stylesheet">

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        primary: '#0f172a',      // Slate 900 als Basis
                        secondary: '#1e293b',    // Slate 800 für Cards
                        brand: {
                            light: '#34d399',    // Emerald 400 (Minty Green)
                            DEFAULT: '#10b981',  // Emerald 500
                            dark: '#059669',     // Emerald 600
                        },
                        ocean: {
                            light: '#38bdf8',    // Sky 400
                            DEFAULT: '#0ea5e9',  // Sky 500
                            dark: '#0284c7',     // Sky 600
                        },
                    },
                    fontFamily: {
                        sans: ['Plus Jakarta Sans', 'sans-serif'],
                        display: ['Outfit', 'sans-serif'],
                    },
                    backgroundImage: {
                        'hero-gradient': 'linear-gradient(135deg, #0f172a 0%, #00334e 50%, #004d40 100%)',
                        'card-gradient': 'linear-gradient(145deg, rgba(255,255,255,0.05) 0%, rgba(255,255,255,0.01) 100%)',
                        'soft-gradient': 'linear-gradient(180deg, #f0f9ff 0%, #ecfdf5 100%)',
                    },
                    boxShadow: {
                        'soft': '0 20px 40px -15px rgba(16, 185, 129, 0.15)',
                        'glow': '0 0 20px rgba(56, 189, 248, 0.3)',
                    }
                }
            }
        }
    </script>

    <style>
        /* Custom Utilities */
        .glass-nav {
            background: rgba(15, 23, 42, 0.85);
            backdrop-filter: blur(12px);
            border-bottom: 1px solid rgba(255, 255, 255, 0.05);
        }

        .glass-card {
            background: rgba(255, 255, 255, 0.7);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.5);
        }
        
        .dark-glass-card {
            background: rgba(30, 41, 59, 0.6);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.08);
        }

        .text-gradient {
            background: linear-gradient(to right, #34d399, #38bdf8);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .blob {
            position: absolute;
            filter: blur(80px);
            z-index: 0;
            opacity: 0.4;
        }

        .hover-lift {
            transition: transform 0.3s cubic-bezier(0.34, 1.56, 0.64, 1), box-shadow 0.3s ease;
        }
        .hover-lift:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 40px -10px rgba(0,0,0,0.1);
        }

        /* Phone Mockup Animation */
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-15px); }
            100% { transform: translateY(0px); }
        }
        .floating-mockup {
            animation: float 6s ease-in-out infinite;
        }

        /* Modal Transition */
        .modal-enter { opacity: 0; transform: scale(0.95); }
        .modal-enter-active { opacity: 1; transform: scale(1); transition: all 0.3s ease-out; }
        .modal-exit { opacity: 1; transform: scale(1); }
        .modal-exit-active { opacity: 0; transform: scale(0.95); transition: all 0.2s ease-in; }
    </style>
</head>
<body class="font-sans text-slate-800 antialiased overflow-x-hidden bg-slate-50">

    <!-- Navigation -->
    <nav class="fixed w-full z-50 glass-nav transition-all duration-300" id="navbar">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-20">
                <!-- Logo -->
                <div class="flex-shrink-0 flex items-center gap-2 cursor-pointer group" onclick="window.scrollTo(0,0)">
                    <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-brand-light to-ocean flex items-center justify-center shadow-glow group-hover:scale-105 transition-transform">
                        <i class="fa-solid fa-compass text-white text-xl"></i>
                    </div>
                    <span class="font-display text-xl font-bold text-white tracking-wide">Global<span class="text-brand-light">Questing</span></span>
                </div>
                
                <!-- Desktop Menu -->
                <div class="hidden md:flex space-x-8 items-center">
                    <a href="#quests" class="text-slate-300 hover:text-brand-light transition text-sm font-medium">Top Quests</a>
                    <a href="#features" class="text-slate-300 hover:text-brand-light transition text-sm font-medium">Features</a>
                    <a href="#creators" class="text-slate-300 hover:text-brand-light transition text-sm font-medium">Creator Hub</a>
                    <a href="#download" class="bg-white/10 hover:bg-white/20 border border-white/10 text-white px-6 py-2.5 rounded-full font-semibold transition backdrop-blur-sm flex items-center gap-2 group">
                        App laden
                        <i class="fa-solid fa-arrow-right text-xs opacity-0 group-hover:opacity-100 -translate-x-2 group-hover:translate-x-0 transition-all"></i>
                    </a>
                </div>

                <!-- Mobile Menu Button -->
                <div class="md:hidden flex items-center">
                    <button id="mobile-menu-btn" class="text-slate-300 hover:text-white focus:outline-none p-2">
                        <i class="fa-solid fa-bars text-2xl"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Mobile Menu Panel -->
        <div id="mobile-menu" class="hidden md:hidden bg-primary border-t border-slate-800 absolute w-full">
            <div class="px-4 pt-4 pb-6 space-y-2">
                <a href="#quests" class="block px-4 py-3 rounded-xl text-base font-medium text-slate-300 hover:text-white hover:bg-white/10">Top Quests</a>
                <a href="#features" class="block px-4 py-3 rounded-xl text-base font-medium text-slate-300 hover:text-white hover:bg-white/10">Features</a>
                <a href="#creators" class="block px-4 py-3 rounded-xl text-base font-medium text-slate-300 hover:text-white hover:bg-white/10">Creator Hub</a>
                <a href="#download" class="block px-4 py-3 rounded-xl text-base font-bold text-brand-light bg-white/5 mt-4 text-center">App laden</a>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="relative min-h-screen flex items-center pt-24 overflow-hidden bg-hero-gradient">
        <!-- Background Blobs -->
        <div class="blob bg-brand w-96 h-96 rounded-full top-0 left-0 -translate-x-1/2 -translate-y-1/2"></div>
        <div class="blob bg-ocean w-[500px] h-[500px] rounded-full bottom-0 right-0 translate-x-1/3 translate-y-1/3"></div>

        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 w-full grid grid-cols-1 lg:grid-cols-2 gap-16 items-center relative z-10">
            
            <!-- Text Content -->
            <div class="text-white space-y-8 order-2 lg:order-1">
                <div class="inline-flex items-center gap-2 px-4 py-1.5 rounded-full bg-white/10 border border-white/20 backdrop-blur-md text-sm font-medium text-brand-light animate-fade-in">
                    <span class="relative flex h-2 w-2">
                      <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-brand-light opacity-75"></span>
                      <span class="relative inline-flex rounded-full h-2 w-2 bg-brand-light"></span>
                    </span>
                    AI Storytelling V2.0 ist live
                </div>
                
                <h1 class="text-5xl lg:text-7xl font-display font-extrabold leading-tight tracking-tight">
                    Entdecke die Welt <br>
                    <span class="text-gradient">wie ein Spiel.</span>
                </h1>
                
                <p class="text-lg text-slate-300 max-w-lg font-light leading-relaxed">
                    Deine Reise, dein Abenteuer. Unsere KI verwandelt Städte in Spielfelder. Löse Rätsel in Rom, finde Geheimnisse in Paris und sammle XP, wo immer du bist.
                </p>
                
                <div class="flex flex-col sm:flex-row gap-4 pt-4">
                    <button class="bg-gradient-to-r from-brand to-ocean-dark hover:shadow-lg hover:shadow-brand/25 text-white px-8 py-4 rounded-2xl font-bold text-lg transition transform hover:-translate-y-1 flex items-center justify-center gap-3">
                        <span>Kostenlos Starten</span>
                        <i class="fa-solid fa-play text-sm"></i>
                    </button>
                    <a href="#quests" class="bg-white/5 hover:bg-white/10 backdrop-blur-md text-white border border-white/10 px-8 py-4 rounded-2xl font-bold text-lg transition flex items-center justify-center gap-2 group">
                        <span>Quests ansehen</span>
                        <i class="fa-solid fa-location-dot group-hover:text-brand-light transition-colors"></i>
                    </a>
                </div>

                <div class="pt-8 flex items-center gap-4 text-sm text-slate-400">
                    <div class="flex -space-x-3">
                        <img class="w-10 h-10 rounded-full border-2 border-primary" src="https://randomuser.me/api/portraits/women/44.jpg" alt="User">
                        <img class="w-10 h-10 rounded-full border-2 border-primary" src="https://randomuser.me/api/portraits/men/32.jpg" alt="User">
                        <img class="w-10 h-10 rounded-full border-2 border-primary" src="https://randomuser.me/api/portraits/women/68.jpg" alt="User">
                    </div>
                    <p>100k+ Explorer weltweit</p>
                </div>
            </div>

            <!-- App Mockup Visual -->
            <div class="relative order-1 lg:order-2 flex justify-center lg:justify-end floating-mockup pointer-events-none lg:pointer-events-auto">
                <div class="relative w-[320px] h-[650px] bg-primary rounded-[3.5rem] border-[8px] border-slate-800 shadow-2xl overflow-hidden ring-1 ring-white/20">
                    <!-- Screen Content -->
                    <div class="w-full h-full bg-slate-900 relative">
                        <!-- Map Img -->
                        <img src="https://images.unsplash.com/photo-1499856871940-a09627c6d7db?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" class="absolute inset-0 w-full h-full object-cover opacity-70" alt="Map Paris">
                        
                        <!-- Gradient Overlay -->
                        <div class="absolute inset-0 bg-gradient-to-b from-slate-900/80 via-transparent to-slate-900/90"></div>

                        <!-- Top Bar -->
                        <div class="absolute top-6 left-0 w-full px-6 flex justify-between items-center text-white z-20">
                            <div class="flex items-center gap-2 bg-black/30 backdrop-blur-md px-3 py-1 rounded-full border border-white/10">
                                <i class="fa-solid fa-gem text-brand-light text-xs"></i>
                                <span class="text-xs font-bold">2,450 XP</span>
                            </div>
                            <div class="w-8 h-8 rounded-full bg-white/10 flex items-center justify-center">
                                <i class="fa-solid fa-gear text-xs"></i>
                            </div>
                        </div>
                        
                        <!-- Quest Card in App -->
                        <div class="absolute bottom-24 left-4 right-4">
                            <div class="dark-glass-card p-5 rounded-3xl text-white shadow-xl border-l-4 border-l-brand">
                                <div class="flex justify-between items-start mb-3">
                                    <span class="px-2 py-1 rounded-md bg-brand/20 text-brand-light text-[10px] font-bold uppercase tracking-wider">Aktuell</span>
                                    <span class="text-ocean-light text-xs font-bold"><i class="fa-solid fa-location-arrow mr-1"></i> 150m</span>
                                </div>
                                <h3 class="font-display font-bold text-xl mb-1">Phantom der Oper</h3>
                                <p class="text-xs text-slate-300 mb-4 leading-relaxed">Der Geist verlangt nach Musik. Finde das versteckte Notenblatt am Seiteneingang.</p>
                                
                                <div class="flex gap-2">
                                    <button class="flex-1 bg-brand hover:bg-brand-dark py-2.5 rounded-xl text-xs font-bold transition shadow-lg shadow-brand/20">
                                        Kamera öffnen
                                    </button>
                                    <button class="px-3 py-2.5 bg-white/10 rounded-xl hover:bg-white/20 transition">
                                        <i class="fa-solid fa-circle-question"></i>
                                    </button>
                                </div>
                            </div>
                        </div>

                        <!-- Bottom Nav -->
                        <div class="absolute bottom-0 w-full h-24 bg-slate-900/90 backdrop-blur-lg flex justify-around items-center px-2 pb-2">
                            <div class="text-brand-light flex flex-col items-center p-2"><i class="fa-solid fa-map text-xl"></i></div>
                            <div class="text-slate-500 flex flex-col items-center p-2"><i class="fa-solid fa-scroll text-xl"></i></div>
                            <div class="bg-gradient-to-r from-brand to-ocean -mt-10 w-16 h-16 rounded-full flex items-center justify-center text-white shadow-lg shadow-brand/30 border-4 border-slate-900"><i class="fa-solid fa-cube text-2xl"></i></div>
                            <div class="text-slate-500 flex flex-col items-center p-2"><i class="fa-solid fa-bag-shopping text-xl"></i></div>
                            <div class="text-slate-500 flex flex-col items-center p-2"><i class="fa-solid fa-user text-xl"></i></div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Trending Quests -->
    <section id="quests" class="py-24 bg-soft-gradient">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16">
                <span class="text-ocean font-bold tracking-wider uppercase text-xs mb-2 block">Beliebte Destinationen</span>
                <h2 class="text-4xl font-display font-bold text-primary mb-4">Starte dein Abenteuer hier</h2>
                <p class="text-slate-500 max-w-2xl mx-auto">Wähle eine Stadt und lass dich von unserer KI durch geheime Gassen und vergessene Epochen führen.</p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <!-- Paris Card -->
                <div class="group bg-white rounded-[2rem] overflow-hidden shadow-soft hover-lift border border-slate-100 flex flex-col h-full">
                    <div class="h-64 relative overflow-hidden shrink-0">
                        <img src="https://images.unsplash.com/photo-1502602898657-3e91760cbb34?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Paris" class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-110">
                        <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent"></div>
                        <div class="absolute bottom-4 left-6 text-white">
                            <h3 class="font-display font-bold text-2xl">Paris</h3>
                            <div class="flex items-center gap-2 text-xs font-medium opacity-90">
                                <i class="fa-solid fa-flag"></i> Frankreich
                            </div>
                        </div>
                        <div class="absolute top-4 right-4 bg-white/20 backdrop-blur-md border border-white/30 text-white text-xs font-bold px-3 py-1 rounded-full">
                            Hard
                        </div>
                    </div>
                    <div class="p-6 flex-1 flex flex-col">
                        <div class="flex justify-between items-center mb-4">
                            <h4 class="font-bold text-lg text-slate-800">Das Phantom der Oper</h4>
                            <span class="text-brand font-bold text-sm">+500 XP</span>
                        </div>
                        <p class="text-slate-500 text-sm mb-6 line-clamp-2 flex-1">
                            Ein musikalisches Mysterium rund um das Opéra Garnier. Entschlüssele die Noten, bevor der Vorhang fällt.
                        </p>
                        <button onclick="openQuestModal('paris')" class="w-full py-3 rounded-xl border border-slate-200 text-slate-600 font-bold hover:bg-slate-50 hover:border-ocean hover:text-ocean transition flex justify-center items-center gap-2">
                            Quest ansehen <i class="fa-solid fa-chevron-right text-xs"></i>
                        </button>
                    </div>
                </div>

                <!-- Rom Card -->
                <div class="group bg-white rounded-[2rem] overflow-hidden shadow-soft hover-lift border border-slate-100 flex flex-col h-full">
                    <div class="h-64 relative overflow-hidden shrink-0">
                        <img src="https://images.unsplash.com/photo-1552832230-c0197dd311b5?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Rom" class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-110">
                        <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent"></div>
                        <div class="absolute bottom-4 left-6 text-white">
                            <h3 class="font-display font-bold text-2xl">Rom</h3>
                            <div class="flex items-center gap-2 text-xs font-medium opacity-90">
                                <i class="fa-solid fa-flag"></i> Italien
                            </div>
                        </div>
                        <div class="absolute top-4 right-4 bg-white/20 backdrop-blur-md border border-white/30 text-white text-xs font-bold px-3 py-1 rounded-full">
                            Medium
                        </div>
                    </div>
                    <div class="p-6 flex-1 flex flex-col">
                        <div class="flex justify-between items-center mb-4">
                            <h4 class="font-bold text-lg text-slate-800">Gladiator's Legacy</h4>
                            <span class="text-brand font-bold text-sm">+750 XP</span>
                        </div>
                        <p class="text-slate-500 text-sm mb-6 line-clamp-2 flex-1">
                            Steige hinab in die Katakomben des Kolosseums. Finde das verlorene Schwert des Imperators.
                        </p>
                        <button onclick="openQuestModal('rom')" class="w-full py-3 rounded-xl border border-slate-200 text-slate-600 font-bold hover:bg-slate-50 hover:border-ocean hover:text-ocean transition flex justify-center items-center gap-2">
                            Quest ansehen <i class="fa-solid fa-chevron-right text-xs"></i>
                        </button>
                    </div>
                </div>

                <!-- Wien Card -->
                <div class="group bg-white rounded-[2rem] overflow-hidden shadow-soft hover-lift border border-slate-100 flex flex-col h-full">
                    <div class="h-64 relative overflow-hidden shrink-0">
                        <img src="https://images.unsplash.com/photo-1516550893923-42d28e5677af?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Wien" class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-110">
                        <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent"></div>
                        <div class="absolute bottom-4 left-6 text-white">
                            <h3 class="font-display font-bold text-2xl">Wien</h3>
                            <div class="flex items-center gap-2 text-xs font-medium opacity-90">
                                <i class="fa-solid fa-flag"></i> Österreich
                            </div>
                        </div>
                        <div class="absolute top-4 right-4 bg-white/20 backdrop-blur-md border border-white/30 text-white text-xs font-bold px-3 py-1 rounded-full">
                            Easy
                        </div>
                    </div>
                    <div class="p-6 flex-1 flex flex-col">
                        <div class="flex justify-between items-center mb-4">
                            <h4 class="font-bold text-lg text-slate-800">Sisis Geheimnis</h4>
                            <span class="text-brand font-bold text-sm">+400 XP</span>
                        </div>
                        <p class="text-slate-500 text-sm mb-6 line-clamp-2 flex-1">
                            Ein entspannter Spaziergang durch Schönbrunn. Finde die versteckten Juwelen im Garten.
                        </p>
                        <button onclick="openQuestModal('wien')" class="w-full py-3 rounded-xl border border-slate-200 text-slate-600 font-bold hover:bg-slate-50 hover:border-ocean hover:text-ocean transition flex justify-center items-center gap-2">
                            Quest ansehen <i class="fa-solid fa-chevron-right text-xs"></i>
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Features / How it Works -->
    <section id="features" class="py-24 bg-white">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
            <h2 class="text-ocean font-bold tracking-wider uppercase text-xs mb-2">Features</h2>
            <h3 class="text-4xl font-display font-bold text-primary mb-16">Die Zukunft des Reisens</h3>
            
            <div class="grid grid-cols-1 md:grid-cols-3 gap-12">
                <!-- Feature 1 -->
                <div class="p-8 rounded-[2.5rem] bg-slate-50 border border-slate-100 hover:shadow-soft transition duration-500 group">
                    <div class="w-20 h-20 bg-white rounded-3xl shadow-sm flex items-center justify-center mx-auto mb-8 group-hover:scale-110 transition-transform duration-300">
                        <i class="fa-solid fa-brain text-3xl text-ocean group-hover:text-brand transition-colors"></i>
                    </div>
                    <h4 class="text-xl font-bold mb-4 text-primary">AI Dungeon Master</h4>
                    <p class="text-slate-500 leading-relaxed">
                        Kein starrer Reiseführer. Unsere KI generiert dynamische Geschichten basierend auf Wetter, Uhrzeit und deinen Interessen.
                    </p>
                </div>

                <!-- Feature 2 -->
                <div class="p-8 rounded-[2.5rem] bg-slate-50 border border-slate-100 hover:shadow-soft transition duration-500 group">
                    <div class="w-20 h-20 bg-white rounded-3xl shadow-sm flex items-center justify-center mx-auto mb-8 group-hover:scale-110 transition-transform duration-300">
                        <i class="fa-solid fa-trophy text-3xl text-brand group-hover:text-ocean transition-colors"></i>
                    </div>
                    <h4 class="text-xl font-bold mb-4 text-primary">Gamified Travel</h4>
                    <p class="text-slate-500 leading-relaxed">
                        Sammle XP, steige Level auf und schalte exklusive Rabatte bei lokalen Partnern frei. Dein Urlaub wird zum Highscore.
                    </p>
                </div>

                <!-- Feature 3 -->
                <div class="p-8 rounded-[2.5rem] bg-slate-50 border border-slate-100 hover:shadow-soft transition duration-500 group">
                    <div class="w-20 h-20 bg-white rounded-3xl shadow-sm flex items-center justify-center mx-auto mb-8 group-hover:scale-110 transition-transform duration-300">
                        <i class="fa-solid fa-users text-3xl text-indigo-500 group-hover:text-indigo-400 transition-colors"></i>
                    </div>
                    <h4 class="text-xl font-bold mb-4 text-primary">Community Built</h4>
                    <p class="text-slate-500 leading-relaxed">
                        Erstellt von Locals, verfeinert durch KI. Erlebe authentische Geschichten abseits der Touristenpfade.
                    </p>
                </div>
            </div>
        </div>
    </section>

    <!-- AI Tech Section -->
    <section id="ai-tech" class="py-24 bg-primary relative overflow-hidden">
        <div class="absolute top-0 right-0 w-1/2 h-full bg-gradient-to-l from-ocean-dark/20 to-transparent"></div>
        <div class="absolute bottom-0 left-0 w-1/3 h-2/3 bg-brand-dark/10 rounded-full blur-3xl"></div>

        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 items-center">
                <!-- Left Content -->
                <div>
                    <div class="inline-block px-4 py-1.5 rounded-full bg-ocean/10 text-ocean-light border border-ocean/20 text-sm font-bold mb-6">
                        <i class="fa-solid fa-microchip mr-2"></i>Powered by Gemini & GPT-4
                    </div>
                    <h2 class="text-4xl lg:text-5xl font-display font-bold text-white mb-6 leading-tight">
                        Intelligenz, die <br><span class="text-transparent bg-clip-text bg-gradient-to-r from-brand-light to-ocean-light">mit dir reist.</span>
                    </h2>
                    <p class="text-slate-400 text-lg mb-8 leading-relaxed">
                        Wir nutzen multimodale LLMs, um deine Umgebung in Echtzeit zu analysieren. Richte deine Kamera auf eine Statue, und die App erzählt dir nicht nur wer das ist, sondern gibt dir ein Rätsel dazu auf.
                    </p>
                    
                    <div class="space-y-6">
                        <div class="flex items-center gap-4 p-4 rounded-2xl bg-white/5 border border-white/5 hover:bg-white/10 transition">
                            <div class="w-12 h-12 rounded-full bg-brand/20 text-brand-light flex items-center justify-center flex-shrink-0">
                                <i class="fa-solid fa-camera"></i>
                            </div>
                            <div>
                                <h4 class="text-white font-bold">Visuelle Erkennung</h4>
                                <p class="text-slate-400 text-sm">Erkennt Gebäude und Objekte sofort.</p>
                            </div>
                        </div>
                        <div class="flex items-center gap-4 p-4 rounded-2xl bg-white/5 border border-white/5 hover:bg-white/10 transition">
                            <div class="w-12 h-12 rounded-full bg-ocean/20 text-ocean-light flex items-center justify-center flex-shrink-0">
                                <i class="fa-solid fa-comment-dots"></i>
                            </div>
                            <div>
                                <h4 class="text-white font-bold">Interaktive NPCs</h4>
                                <p class="text-slate-400 text-sm">Chatte mit historischen Figuren.</p>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Right Chat UI -->
                <div class="relative">
                    <div class="absolute -inset-1 bg-gradient-to-r from-brand to-ocean rounded-[2rem] blur opacity-30"></div>
                    <div class="relative bg-slate-900 border border-slate-700 rounded-[2rem] p-6 shadow-2xl">
                        <div class="flex items-center gap-3 border-b border-slate-800 pb-4 mb-4">
                            <div class="w-10 h-10 rounded-full bg-gradient-to-br from-brand to-ocean flex items-center justify-center">
                                <i class="fa-solid fa-robot text-white"></i>
                            </div>
                            <div>
                                <p class="text-white font-bold text-sm">Quest Guide AI</p>
                                <p class="text-brand-light text-xs flex items-center gap-1"><span class="w-1.5 h-1.5 bg-brand-light rounded-full animate-pulse"></span> Online</p>
                            </div>
                        </div>
                        
                        <div class="space-y-4 font-mono text-sm">
                            <!-- User -->
                            <div class="flex justify-end">
                                <div class="bg-ocean/10 text-ocean-light border border-ocean/20 px-4 py-3 rounded-2xl rounded-tr-sm max-w-[85%]">
                                    Ich bin am Kolosseum. Was ist meine Aufgabe?
                                </div>
                            </div>
                            <!-- AI -->
                            <div class="flex justify-start">
                                <div class="bg-slate-800 text-slate-300 border border-slate-700 px-4 py-3 rounded-2xl rounded-tl-sm max-w-[90%]">
                                    <span class="text-xs font-bold text-brand mb-1 block">Standort verifiziert <i class="fa-solid fa-check ml-1"></i></span>
                                    Salve, Gladiator! ⚔️ Suche nach dem Stein mit der Inschrift "XVIII". Er markiert den Eingang für die Kämpfer. Mach ein Foto davon für 200 XP.
                                </div>
                            </div>
                        </div>

                        <div class="mt-6 relative">
                            <input type="text" disabled placeholder="Antwort eingeben..." class="w-full bg-slate-950 border border-slate-800 rounded-xl py-3 px-4 text-sm text-slate-500 focus:outline-none">
                            <button class="absolute right-2 top-2 w-8 h-8 bg-ocean rounded-lg text-white flex items-center justify-center text-xs hover:bg-ocean-light">
                                <i class="fa-solid fa-paper-plane"></i>
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Creators Section -->
    <section id="creators" class="py-24 bg-slate-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="bg-white rounded-[3rem] p-12 shadow-soft border border-slate-100 text-center relative overflow-hidden">
                <div class="absolute top-0 left-0 w-full h-2 bg-gradient-to-r from-brand to-ocean"></div>
                
                <h2 class="text-3xl md:text-4xl font-display font-bold text-primary mb-6">Werde Quest Designer</h2>
                <p class="text-slate-500 max-w-2xl mx-auto mb-10 text-lg">
                    Nutze unsere No-Code Tools, um deine Stadt in ein Spiel zu verwandeln. Perfekt für Tourismusverbände, Hotels und kreative Minds.
                </p>

                <div class="grid grid-cols-1 md:grid-cols-3 gap-8 mb-12 text-left">
                    <div class="flex gap-4 items-start">
                        <div class="w-10 h-10 rounded-full bg-slate-100 flex items-center justify-center flex-shrink-0 text-primary"><i class="fa-solid fa-wand-magic-sparkles"></i></div>
                        <div>
                            <h4 class="font-bold text-primary">AI Builder</h4>
                            <p class="text-sm text-slate-500">Lass die KI Storys und Rätsel schreiben.</p>
                        </div>
                    </div>
                    <div class="flex gap-4 items-start">
                        <div class="w-10 h-10 rounded-full bg-slate-100 flex items-center justify-center flex-shrink-0 text-primary"><i class="fa-solid fa-chart-pie"></i></div>
                        <div>
                            <h4 class="font-bold text-primary">Analytics</h4>
                            <p class="text-sm text-slate-500">Sehe genau, wo Spieler sich aufhalten.</p>
                        </div>
                    </div>
                    <div class="flex gap-4 items-start">
                        <div class="w-10 h-10 rounded-full bg-slate-100 flex items-center justify-center flex-shrink-0 text-primary"><i class="fa-solid fa-sack-dollar"></i></div>
                        <div>
                            <h4 class="font-bold text-primary">Verdiene Geld</h4>
                            <p class="text-sm text-slate-500">Monetarisiere Premium-Quests.</p>
                        </div>
                    </div>
                </div>

                <button class="bg-primary text-white px-8 py-4 rounded-2xl font-bold hover:bg-slate-800 transition shadow-lg inline-flex items-center gap-2">
                    Zum Creator Portal <i class="fa-solid fa-arrow-right"></i>
                </button>
            </div>
        </div>
    </section>

    <!-- CTA / Download Section -->
    <section id="download" class="bg-gradient-to-br from-brand to-ocean py-24 relative overflow-hidden">
        <!-- Circles background -->
        <div class="absolute top-0 left-0 w-64 h-64 bg-white/10 rounded-full -translate-x-1/2 -translate-y-1/2"></div>
        <div class="absolute bottom-0 right-0 w-96 h-96 bg-white/10 rounded-full translate-x-1/3 translate-y-1/3"></div>

        <div class="max-w-4xl mx-auto px-4 text-center text-white relative z-10">
            <h2 class="text-4xl md:text-5xl font-display font-bold mb-6">Die Welt wartet auf dich.</h2>
            <p class="text-lg text-white/90 mb-12 max-w-2xl mx-auto">
                Lade Global Questing jetzt herunter. Kostenlos für iOS und Android.
            </p>
            
            <div class="flex flex-col sm:flex-row justify-center gap-4">
                <button class="bg-white text-slate-900 px-8 py-4 rounded-2xl font-bold text-lg hover:scale-105 transition shadow-xl flex items-center justify-center gap-3">
                    <i class="fa-brands fa-apple text-2xl"></i>
                    <div class="text-left leading-tight">
                        <span class="text-[10px] block font-bold text-slate-400 uppercase">Download on</span>
                        App Store
                    </div>
                </button>
                <button class="bg-white/20 backdrop-blur-md border border-white/30 text-white px-8 py-4 rounded-2xl font-bold text-lg hover:bg-white/30 transition shadow-xl flex items-center justify-center gap-3">
                    <i class="fa-brands fa-google-play text-2xl"></i>
                    <div class="text-left leading-tight">
                        <span class="text-[10px] block font-bold text-white/70 uppercase">Get it on</span>
                        Google Play
                    </div>
                </button>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="bg-primary text-slate-400 py-16 border-t border-slate-800">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 grid grid-cols-1 md:grid-cols-4 gap-12">
            <div class="col-span-1 md:col-span-1">
                <div class="flex items-center gap-2 mb-6 text-white">
                    <div class="w-8 h-8 rounded-lg bg-gradient-to-br from-brand to-ocean flex items-center justify-center">
                        <i class="fa-solid fa-compass text-white text-sm"></i>
                    </div>
                    <span class="font-display font-bold text-lg">Global<span class="text-brand-light">Questing</span></span>
                </div>
                <p class="text-sm mb-6 leading-relaxed">Wir verbinden Technologie mit der realen Welt, um Reisen unvergesslich zu machen.</p>
                <div class="flex space-x-4">
                    <a href="#" class="w-10 h-10 rounded-full bg-slate-800 flex items-center justify-center hover:bg-brand hover:text-white transition"><i class="fa-brands fa-instagram"></i></a>
                    <a href="#" class="w-10 h-10 rounded-full bg-slate-800 flex items-center justify-center hover:bg-brand hover:text-white transition"><i class="fa-brands fa-tiktok"></i></a>
                    <a href="#" class="w-10 h-10 rounded-full bg-slate-800 flex items-center justify-center hover:bg-brand hover:text-white transition"><i class="fa-brands fa-twitter"></i></a>
                </div>
            </div>
            
            <div>
                <h4 class="text-white font-bold mb-6">Entdecken</h4>
                <ul class="space-y-3 text-sm">
                    <li><a href="#" class="hover:text-brand-light transition">Städte</a></li>
                    <li><a href="#" class="hover:text-brand-light transition">Top Quests</a></li>
                    <li><a href="#" class="hover:text-brand-light transition">Events</a></li>
                    <li><a href="#" class="hover:text-brand-light transition">Leaderboard</a></li>
                </ul>
            </div>

            <div>
                <h4 class="text-white font-bold mb-6">Community</h4>
                <ul class="space-y-3 text-sm">
                    <li><a href="#" class="hover:text-brand-light transition">Creator Portal</a></li>
                    <li><a href="#" class="hover:text-brand-light transition">Partner Programm</a></li>
                    <li><a href="#" class="hover:text-brand-light transition">Discord</a></li>
                    <li><a href="#" class="hover:text-brand-light transition">Hilfe Center</a></li>
                </ul>
            </div>

            <div>
                <h4 class="text-white font-bold mb-6">Legal</h4>
                <ul class="space-y-3 text-sm">
                    <li><a href="#" class="hover:text-brand-light transition">Impressum</a></li>
                    <li><a href="#" class="hover:text-brand-light transition">Datenschutz</a></li>
                    <li><a href="#" class="hover:text-brand-light transition">AGB</a></li>
                </ul>
            </div>
        </div>
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 mt-16 pt-8 border-t border-slate-800 text-center text-xs text-slate-500">
            &copy; 2025 Global Questing Inc. Alle Rechte vorbehalten.
        </div>
    </footer>

    <!-- Quest Modal Overlay -->
    <div id="quest-modal" class="fixed inset-0 z-[100] hidden flex items-center justify-center px-4">
        <!-- Backdrop -->
        <div class="absolute inset-0 bg-slate-900/80 backdrop-blur-sm transition-opacity" onclick="closeQuestModal()"></div>
        
        <!-- Modal Content -->
        <div class="relative bg-white rounded-[2.5rem] w-full max-w-2xl shadow-2xl overflow-hidden transform transition-all scale-95 opacity-0" id="modal-content">
            
            <!-- Modal Header with Image -->
            <div class="relative h-56">
                <img id="modal-image" src="" alt="Quest Cover" class="w-full h-full object-cover">
                <div class="absolute inset-0 bg-gradient-to-t from-black/80 to-transparent"></div>
                
                <!-- Close Button (Top Right) - Kept as secondary option -->
                <button onclick="closeQuestModal()" class="absolute top-4 right-4 w-10 h-10 bg-black/30 backdrop-blur text-white rounded-full flex items-center justify-center hover:bg-white hover:text-slate-900 transition z-10">
                    <i class="fa-solid fa-xmark"></i>
                </button>

                <div class="absolute bottom-6 left-6 right-6 text-white">
                    <div class="flex gap-2 mb-3 ml-14"> <!-- Added margin to align with text -->
                        <span id="modal-difficulty" class="px-3 py-1 rounded-full bg-white/20 backdrop-blur text-xs font-bold uppercase">Hard</span>
                        <span class="px-3 py-1 rounded-full bg-brand text-white text-xs font-bold flex items-center gap-1"><i class="fa-solid fa-bolt"></i> <span id="modal-xp">500 XP</span></span>
                    </div>
                    
                    <div class="flex items-center gap-4">
                        <button onclick="closeQuestModal()" class="w-10 h-10 bg-white/20 backdrop-blur border border-white/30 rounded-full flex items-center justify-center hover:bg-white hover:text-slate-900 transition flex-shrink-0 group">
                            <i class="fa-solid fa-arrow-left group-hover:-translate-x-1 transition-transform"></i>
                        </button>
                        <h2 id="modal-title" class="text-3xl font-display font-bold leading-none drop-shadow-lg">Quest Title</h2>
                    </div>
                </div>
            </div>

            <!-- Modal Body -->
            <div class="p-8 max-h-[60vh] overflow-y-auto">
                <!-- Intro -->
                <div class="flex items-start gap-4 mb-8">
                    <div class="w-12 h-12 rounded-full bg-ocean/10 text-ocean flex items-center justify-center shrink-0">
                        <i class="fa-solid fa-robot text-xl"></i>
                    </div>
                    <div class="bg-slate-50 p-4 rounded-2xl rounded-tl-none text-sm text-slate-600 italic leading-relaxed border border-slate-100">
                        <span class="block text-xs font-bold text-ocean mb-1 not-italic">AI Intro</span>
                        "<span id="modal-story">Loading Story...</span>"
                    </div>
                </div>

                <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mb-8">
                    <div class="text-center p-3 bg-slate-50 rounded-2xl border border-slate-100">
                        <i class="fa-regular fa-clock text-slate-400 mb-1"></i>
                        <p class="text-xs text-slate-500">Dauer</p>
                        <p id="modal-duration" class="font-bold text-slate-800">2h 30m</p>
                    </div>
                    <div class="text-center p-3 bg-slate-50 rounded-2xl border border-slate-100">
                        <i class="fa-solid fa-shoe-prints text-slate-400 mb-1"></i>
                        <p class="text-xs text-slate-500">Distanz</p>
                        <p id="modal-distance" class="font-bold text-slate-800">4.5 km</p>
                    </div>
                    <div class="text-center p-3 bg-slate-50 rounded-2xl border border-slate-100">
                        <i class="fa-solid fa-user-group text-slate-400 mb-1"></i>
                        <p class="text-xs text-slate-500">Spieler</p>
                        <p class="font-bold text-slate-800">1-4</p>
                    </div>
                    <div class="text-center p-3 bg-slate-50 rounded-2xl border border-slate-100">
                        <i class="fa-solid fa-star text-slate-400 mb-1"></i>
                        <p class="text-xs text-slate-500">Rating</p>
                        <p class="font-bold text-slate-800">4.8/5</p>
                    </div>
                </div>

                <div class="space-y-6">
                    <div>
                        <h3 class="font-bold text-primary mb-3 flex items-center gap-2">
                            <i class="fa-solid fa-crosshairs text-brand"></i> Mission
                        </h3>
                        <ul class="space-y-2 text-sm text-slate-600">
                            <li class="flex gap-3 items-start">
                                <i class="fa-solid fa-check text-brand mt-1 text-xs"></i>
                                <span id="modal-mission-1">Finde den Startpunkt am Opernplatz</span>
                            </li>
                            <li class="flex gap-3 items-start">
                                <i class="fa-solid fa-check text-brand mt-1 text-xs"></i>
                                <span id="modal-mission-2">Löse 5 Krypto-Rätsel zur Geschichte</span>
                            </li>
                            <li class="flex gap-3 items-start">
                                <i class="fa-solid fa-check text-brand mt-1 text-xs"></i>
                                <span id="modal-mission-3">Mache ein AR-Foto mit dem Phantom</span>
                            </li>
                        </ul>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                        <div>
                            <h3 class="font-bold text-primary mb-3 flex items-center gap-2">
                                <i class="fa-solid fa-gift text-yellow-500"></i> Loot (Belohnungen)
                            </h3>
                            <div class="flex gap-2">
                                <div class="w-10 h-10 bg-yellow-50 rounded-lg border border-yellow-100 flex items-center justify-center text-yellow-600" title="Gold Badge">
                                    <i class="fa-solid fa-medal"></i>
                                </div>
                                <div class="w-10 h-10 bg-blue-50 rounded-lg border border-blue-100 flex items-center justify-center text-blue-600" title="Ticket Voucher">
                                    <i class="fa-solid fa-ticket"></i>
                                </div>
                                <div class="w-10 h-10 bg-purple-50 rounded-lg border border-purple-100 flex items-center justify-center text-purple-600" title="Avatar Item">
                                    <i class="fa-solid fa-hat-wizard"></i>
                                </div>
                            </div>
                        </div>
                         <div>
                            <h3 class="font-bold text-primary mb-3 flex items-center gap-2">
                                <i class="fa-solid fa-suitcase text-slate-500"></i> Ausrüstung
                            </h3>
                            <div class="flex flex-wrap gap-2">
                                <span class="px-2 py-1 bg-slate-100 rounded text-xs text-slate-600">Kopfhörer</span>
                                <span class="px-2 py-1 bg-slate-100 rounded text-xs text-slate-600">Powerbank</span>
                                <span class="px-2 py-1 bg-slate-100 rounded text-xs text-slate-600">Bequeme Schuhe</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Footer -->
            <div class="p-6 border-t border-slate-100 bg-slate-50 flex gap-4">
                <button onclick="closeQuestModal()" class="px-6 py-3 rounded-xl font-bold text-slate-500 hover:bg-slate-200 transition">Zurück</button>
                <button class="flex-1 bg-gradient-to-r from-brand to-ocean text-white py-3 rounded-xl font-bold shadow-lg shadow-brand/20 hover:shadow-brand/40 hover:-translate-y-0.5 transition transform flex items-center justify-center gap-2">
                    Quest Starten <i class="fa-solid fa-play text-xs"></i>
                </button>
            </div>
        </div>
    </div>

    <script>
        // Quest Data
        const quests = {
            'paris': {
                title: 'Das Phantom der Oper',
                difficulty: 'Hard',
                xp: '500 XP',
                image: 'https://images.unsplash.com/photo-1502602898657-3e91760cbb34?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
                story: 'Ein Schatten huscht durch die Gänge der Opéra Garnier. Die Primadonna wird vermisst und nur eine alte Partitur enthält Hinweise auf ihren Verbleib. Bist du bereit, die Musik des Todes zu hören?',
                duration: '2h 30m',
                distance: '4.5 km',
                missions: [
                    'Finde den geheimen Eingang am Opernplatz',
                    'Entschlüssele die Noten auf der Statue',
                    'Finde den unterirdischen See (Virtuell)'
                ]
            },
            'rom': {
                title: "Gladiator's Legacy",
                difficulty: 'Medium',
                xp: '750 XP',
                image: 'https://images.unsplash.com/photo-1552832230-c0197dd311b5?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
                story: 'Der letzte Imperator hat sein Schwert versteckt, bevor Rom fiel. Es heißt, nur wer den Mut eines Löwen besitzt, kann die Prüfungen des Kolosseums bestehen und das Erbe antreten.',
                duration: '3h 00m',
                distance: '5.2 km',
                missions: [
                    'Betrete das Kolosseum durch das Tor des Lebens',
                    'Finde die Inschrift des Marcus Aurelius',
                    'Besiege den virtuellen Wächter im Forum'
                ]
            },
            'wien': {
                title: 'Sisis Geheimnis',
                difficulty: 'Easy',
                xp: '400 XP',
                image: 'https://images.unsplash.com/photo-1516550893923-42d28e5677af?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80',
                story: 'Kaiserin Elisabeth hat ihr Tagebuch im Schlosspark verloren. Die Seiten sind im Wind verweht. Folge den goldenen Blättern und entdecke die private Seite der Monarchin.',
                duration: '1h 45m',
                distance: '3.0 km',
                missions: [
                    'Startpunkt: Gloriette Aussichtsplattform',
                    'Finde Sisis Lieblingsbank im Rosengarten',
                    'Sammle 5 digitale Goldblätter'
                ]
            }
        };

        // Modal Logic
        const modal = document.getElementById('quest-modal');
        const modalContent = document.getElementById('modal-content');

        function openQuestModal(questId) {
            const data = quests[questId];
            if(!data) return;

            // Populate Data
            document.getElementById('modal-title').innerText = data.title;
            document.getElementById('modal-difficulty').innerText = data.difficulty;
            document.getElementById('modal-xp').innerText = data.xp;
            document.getElementById('modal-image').src = data.image;
            document.getElementById('modal-story').innerText = data.story;
            document.getElementById('modal-duration').innerText = data.duration;
            document.getElementById('modal-distance').innerText = data.distance;
            
            // Populate Missions List
            document.getElementById('modal-mission-1').innerText = data.missions[0];
            document.getElementById('modal-mission-2').innerText = data.missions[1];
            document.getElementById('modal-mission-3').innerText = data.missions[2];

            // Show Modal
            modal.classList.remove('hidden');
            setTimeout(() => {
                modalContent.classList.remove('scale-95', 'opacity-0');
                modalContent.classList.add('scale-100', 'opacity-100');
            }, 10);
        }

        function closeQuestModal() {
            modalContent.classList.remove('scale-100', 'opacity-100');
            modalContent.classList.add('scale-95', 'opacity-0');
            setTimeout(() => {
                modal.classList.add('hidden');
            }, 200); // Match transition duration
        }

        // Mobile Menu Toggle
        const btn = document.getElementById('mobile-menu-btn');
        const menu = document.getElementById('mobile-menu');

        btn.addEventListener('click', () => {
            menu.classList.toggle('hidden');
        });

        // Smooth Scroll for Anchor Links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                if(!menu.classList.contains('hidden')) menu.classList.add('hidden');
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });

        // Navbar scroll effect
        const navbar = document.getElementById('navbar');
        window.addEventListener('scroll', () => {
            if (window.scrollY > 20) {
                navbar.classList.add('shadow-lg');
            } else {
                navbar.classList.remove('shadow-lg');
            }
        });
    </script>
</body>
</html>
