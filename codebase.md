# images\bg.png

This is a binary file of the type: Image

# images\photo.jpeg

This is a binary file of the type: Image

# index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CV | Aunhel John Adoptante</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        body { 
            font-family: 'Inter', sans-serif; 
            background-image: url('images/bg.png');
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
            color: #0f172a;
        }

        /* Sidebar: WALO-Style Clear Glass */
        .sidebar-clear {
            background: rgba(255, 255, 255, 0.12);
            backdrop-filter: blur(20px) saturate(160%);
            border-right: 0.5px solid rgba(255, 255, 255, 0.2);
        }

        /* Content Card: High-Saturation Clear Glass */
        .content-card-clear {
            background: rgba(255, 255, 255, 0.22);
            backdrop-filter: blur(30px) saturate(150%);
            border: 1px solid rgba(255, 255, 255, 0.3);
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.03);
        }

        .sticky-sidebar {
            position: -webkit-sticky;
            position: sticky;
            top: 0;
            align-self: flex-start;
        }

        /* Enhanced Navigation Pill */
        .nav-pill-container {
            background: rgba(255, 255, 255, 0.2); 
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.4);
            padding: 8px; /* Increased padding */
            border-radius: 9999px;
            display: inline-flex;
            gap: 12px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.08);
        }

        .nav-link {
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            color: #1e293b; 
            letter-spacing: 0.35em; /* Wider spacing for readability */
            padding: 12px 28px; /* Bigger button area */
            border-radius: 9999px;
            font-size: 11px; /* Increased from 8px */
            font-weight: 900;
            text-transform: uppercase;
        }

        .nav-link:hover {
            color: #0369a1;
            background: rgba(255, 255, 255, 0.3);
            transform: scale(1.05); /* Added scale effect */
        }

        .nav-link.active {
            color: #ffffff;
            background: #0369a1; 
            box-shadow: 0 4px 15px rgba(3, 105, 161, 0.4);
            transform: scale(1.1); /* Active tab stays slightly larger */
        }

        .fade-in { animation: fadeIn 0.6s ease-out forwards; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
    </style>
</head>
<body class="antialiased">
    <div class="flex flex-col lg:flex-row min-h-screen items-start">
        
        <aside id="section-header" class="w-full lg:w-[500px] sticky-sidebar sidebar-clear px-8 py-12 min-h-screen flex flex-col items-center"></aside>

        <main class="flex-1 flex flex-col min-h-screen w-full">
            <div class="sticky top-0 z-30 p-10 flex justify-center">
                <nav class="nav-pill-container">
                    <button onclick="switchTab('professional')" id="btn-professional" class="nav-link active">Professional</button>
                    <button onclick="switchTab('passion')" id="btn-passion" class="nav-link">Passion</button>
                    <button onclick="switchTab('lifestyle')" id="btn-lifestyle" class="nav-link">Lifestyle</button>
                </nav>
            </div>

            <div class="p-6 lg:p-14 lg:pt-0">
                <div id="tab-content" class="content-card-clear rounded-[3rem] p-10 md:p-16 max-w-5xl mx-auto fade-in"></div>
            </div>

            <footer class="mt-auto p-12 text-center text-slate-500 font-bold text-[9px] uppercase tracking-[0.5em]">
                Aunhel John Adoptante • 2026
            </footer>
        </main>
    </div>

    <script>
        async function loadSection(file, containerId = 'tab-content') {
            try {
                const response = await fetch(`sections/${file}`);
                const content = await response.text();
                const container = document.getElementById(containerId);
                if (containerId === 'tab-content') {
                    container.classList.remove('fade-in');
                    void container.offsetWidth;
                    container.classList.add('fade-in');
                }
                container.innerHTML = content;
                // Script re-execution
                container.querySelectorAll('script').forEach(oldScript => {
                    const newScript = document.createElement('script');
                    Array.from(oldScript.attributes).forEach(attr => newScript.setAttribute(attr.name, attr.value));
                    newScript.appendChild(document.createTextNode(oldScript.innerHTML));
                    oldScript.parentNode.replaceChild(newScript, oldScript);
                });
            } catch (err) { console.error(err); }
        }

        function switchTab(tabName) {
            document.querySelectorAll('.nav-link').forEach(btn => btn.classList.remove('active'));
            document.getElementById(`btn-${tabName}`).classList.add('active');
            loadSection(`${tabName}.html`);
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        window.addEventListener('DOMContentLoaded', () => {
            loadSection('header.html', 'section-header');
            switchTab('professional');
        });
    </script>
</body>
</html>
```

# sections\header.html

```html
<div class="flex flex-col h-full items-center text-center space-y-8 w-full">
    <div class="space-y-4 flex flex-col items-center w-full">
        <div class="relative">
            <div class="relative w-32 h-32 md:w-36 md:h-36 rounded-3xl overflow-hidden border-4 border-white shadow-xl rotate-1">
                <img src="images/photo.jpeg" alt="Aunhel John Adoptante" class="w-full h-full object-cover">
            </div>
        </div>
        
        <div class="px-2">
            <h1 class="text-2xl font-black tracking-tighter text-slate-900 mb-1">Aunhel John Adoptante</h1>
            <div class="inline-flex items-center gap-2 px-3 py-1 rounded-lg bg-white/30 text-sky-950 text-[9px] font-black uppercase tracking-widest mb-2 border border-white/20">
                AI Researcher and Consultant
            </div>
            <p class="text-[12px] text-slate-800 font-medium max-w-xs leading-relaxed">
                Currently leading AI R&D initiatives at the DOST-ASTI Computer Software Division.
            </p>
        </div>
    </div>

    <div class="space-y-3 w-full px-2">
        <h3 class="text-[9px] font-black text-slate-500 uppercase tracking-[0.4em] border-b border-white/20 pb-1">Education</h3>
        <ul class="space-y-3">
            <li>
                <p class="text-[15px] font-black text-slate-900 leading-tight">MS Artificial Intelligence</p>
                <p class="text-[8px] font-black text-sky-700 uppercase tracking-tighter mb-1">Ongoing</p>
                <p class="text-[10px] font-bold text-slate-600 uppercase tracking-tight">Batangas State University</p>
                <p class="text-[9px] text-slate-500 font-medium italic">The National Engineering University</p>
            </li>
            <li>
                <p class="text-[15px] font-black text-slate-900 leading-tight">BS Electronics Engineering</p>
                <p class="text-[10px] font-bold text-slate-600 uppercase tracking-tight mt-1">Batangas State University</p>
            </li>
        </ul>
    </div>

    <div class="space-y-3 w-full px-2">
        <h3 class="text-[9px] font-black text-slate-500 uppercase tracking-[0.4em] border-b border-white/20 pb-1">Expertise</h3>
        <div class="grid grid-cols-3 gap-2">
            <div class="py-2 bg-white/20 rounded-lg border border-white/30 text-[10px] font-black text-slate-800 uppercase shadow-sm">AI and NLP</div>
            <div class="py-2 bg-white/20 rounded-lg border border-white/30 text-[10px] font-black text-slate-800 uppercase shadow-sm">LLMs & RAG</div>
            <div class="py-2 bg-white/20 rounded-lg border border-white/30 text-[10px] font-black text-slate-800 uppercase shadow-sm">Machine Learning</div>
            <div class="py-2 bg-white/20 rounded-lg border border-white/30 text-[10px] font-black text-slate-800 uppercase shadow-sm">Semantic Parsing</div>
            <div class="py-2 bg-white/20 rounded-lg border border-white/30 text-[10px] font-black text-slate-800 uppercase shadow-sm">Vibe Coding</div>
            <div class="py-2 bg-white/20 rounded-lg border border-white/30 text-[10px] font-black text-slate-800 uppercase shadow-sm">Prompt Engineering</div>
        </div>
    </div>

    <div class="pt-1 flex justify-center gap-8 text-slate-600 text-xl w-full">
        <a href="mailto:engr.ajadoptante@gmail.com" class="hover:text-sky-700 transition duration-300"><i class="fa-solid fa-envelope"></i></a>
        <a href="https://github.com/aunheladoptante" target="_blank" class="hover:text-sky-700 transition duration-300"><i class="fa-brands fa-github"></i></a>
        <a href="https://scholar.google.com/citations?user=s8GNZhEAAAAJ" target="_blank" class="hover:text-sky-700 transition duration-300"><i class="fa-solid fa-graduation-cap"></i></a>
    </div>
</div>
```

# sections\lifestyle.html

```html
<section class="space-y-32">
    <div class="grid lg:grid-cols-12 gap-12 items-start">
        <div class="lg:col-span-4 sticky top-24">
            <h3 class="text-[10px] font-black text-rose-600 uppercase tracking-[0.5em] mb-4">01 / Passion</h3>
            <h4 class="text-3xl font-black italic tracking-tighter text-slate-900 leading-none">Fandom & Collections</h4>
            <p class="mt-6 text-[13px] text-slate-500 font-medium leading-relaxed">
                Just a dedicated Bloom and Once documenting the journey through digital archives, photocard hunting, and live shows.
            </p>
        </div>
        
        <div class="lg:col-span-8 space-y-24">
            <div class="group">
                <div class="relative aspect-[16/9] rounded-[2.5rem] overflow-hidden border-[0.5px] border-white/40 shadow-2xl transition-all duration-700">
                    <img src="images/bg.png" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-1000">
                    <div class="absolute inset-0 bg-gradient-to-t from-slate-950/40 to-transparent"></div>
                    <p class="absolute bottom-6 left-8 text-white text-[10px] font-black uppercase tracking-[0.3em]">Project: WALO Archives</p>
                </div>
                <div class="mt-8 px-2">
                    <h5 class="text-xl font-black text-slate-900 italic">The BINI Archive</h5>
                    <p class="text-[14px] text-slate-600 mt-2 leading-relaxed">I built WALO to be the ultimate digital library for BINI. It's all about keeping their history and media safe and organized for the fandom.</p>
                </div>
            </div>

            <div class="grid grid-cols-2 gap-8">
                <div class="group">
                    <div class="relative aspect-[3/4] rounded-[2rem] overflow-hidden border-[0.5px] border-white/40 shadow-xl">
                        <img src="images/bg.png" class="w-full h-full object-cover">
                    </div>
                    <div class="mt-4 px-2">
                        <p class="text-[11px] font-black text-slate-900 uppercase tracking-widest">Collecting PCs</p>
                        <p class="text-[12px] text-slate-500 mt-1 italic">Hunting for TWICE & BINI sets.</p>
                    </div>
                </div>
                <div class="group">
                    <div class="relative aspect-[3/4] rounded-[2rem] overflow-hidden border-[0.5px] border-white/40 shadow-xl">
                        <img src="images/bg.png" class="w-full h-full object-cover">
                    </div>
                    <div class="mt-4 px-2">
                        <p class="text-[11px] font-black text-slate-900 uppercase tracking-widest">Concert Life</p>
                        <p class="text-[12px] text-slate-500 mt-1 italic">Nothing beats seeing them live.</p>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <div class="grid lg:grid-cols-12 gap-12 items-start">
        <div class="lg:col-span-4 sticky top-24">
            <h3 class="text-[10px] font-black text-amber-600 uppercase tracking-[0.5em] mb-4">02 / Hobby</h3>
            <h4 class="text-3xl font-black italic tracking-tighter text-slate-900 leading-none">Pokémon TCG</h4>
            <p class="mt-6 text-[13px] text-slate-500 font-medium leading-relaxed">
                I’m not just chasing the meta—I’m in it for the fun. I love trying out new mechanics and building decks that are actually interesting to play.
            </p>
        </div>
        
        <div class="lg:col-span-8">
            <div class="group relative">
                <div class="relative aspect-video rounded-[2.5rem] overflow-hidden border-[0.5px] border-white/40 shadow-2xl transition-all duration-700">
                    <img src="images/bg.png" class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700">
                </div>
                <div class="mt-8 px-2">
                    <h5 class="text-xl font-black text-slate-900 italic">Exploring the Game</h5>
                    <p class="text-[14px] text-slate-600 mt-2 leading-relaxed">
                        I'm currently just exploring and playing. Whether it's testing a new archetype or having casual matches with the local community, it's all about the experience and having a good time with the cards.
                    </p>
                </div>
            </div>
        </div>
    </div>

    <div class="grid lg:grid-cols-12 gap-12 items-start pb-20">
        <div class="lg:col-span-4 sticky top-24">
            <h3 class="text-[10px] font-black text-emerald-600 uppercase tracking-[0.5em] mb-4">03 / Active</h3>
            <h4 class="text-3xl font-black italic tracking-tighter text-slate-900 leading-none">Pickleball & Badminton</h4>
            <p class="mt-6 text-[13px] text-slate-500 font-medium leading-relaxed">
                How I stay active. I love the tactical side of these sports—it's like chess, but you actually have to run.
            </p>
        </div>
        
        <div class="lg:col-span-8 grid grid-cols-2 gap-8">
            <div class="group">
                <div class="relative aspect-square rounded-[2rem] overflow-hidden border-[0.5px] border-white/40 shadow-xl transition-all duration-700">
                    <img src="images/bg.png" class="w-full h-full object-cover">
                </div>
                <div class="mt-4 flex justify-between items-center px-2">
                    <p class="text-[10px] font-black text-slate-900 uppercase tracking-widest">Pickleball</p>
                    <span class="h-1.5 w-1.5 bg-emerald-500 rounded-full"></span>
                </div>
            </div>
            <div class="group">
                <div class="relative aspect-square rounded-[2rem] overflow-hidden border-[0.5px] border-white/40 shadow-xl transition-all duration-700">
                    <img src="images/bg.png" class="w-full h-full object-cover">
                </div>
                <div class="mt-4 flex justify-between items-center px-2">
                    <p class="text-[10px] font-black text-slate-900 uppercase tracking-widest">Badminton</p>
                    <span class="h-1.5 w-1.5 bg-emerald-500 rounded-full"></span>
                </div>
            </div>
        </div>
    </div>
</section>
```

# sections\passion.html

```html
<section class="space-y-20">
    <div>
        <div class="flex items-center gap-4 mb-12">
            <h3 class="text-[10px] font-black text-slate-900 uppercase tracking-[0.4em] whitespace-nowrap">
                <span class="text-sky-600 mr-2">From the Heart</span>
            </h3>
            <div class="w-full h-[0.5px] bg-slate-300/50"></div>
        </div>
        
        <div class="space-y-16">
            <div class="grid md:grid-cols-12 gap-10 items-center group">
                <div class="md:col-span-5">
                    <div class="relative rounded-[2rem] overflow-hidden border-[0.5px] border-white/40 shadow-2xl transition-transform duration-700 group-hover:scale-[1.02] rotate-1">
                        <img src="images/bg.png" alt="Project Polaris" class="w-full h-64 object-cover">
                    </div>
                </div>
                <div class="md:col-span-7">
                    <h4 class="text-2xl font-black text-slate-900 leading-tight mb-2 italic tracking-tight">Project: Polaris</h4>
                    <p class="text-[9px] font-black text-amber-600 uppercase tracking-[0.3em] mb-4">A Personal North Star</p>
                    <p class="text-[14px] text-slate-700 font-medium leading-relaxed mb-6 opacity-90">
                        This is more than just a fundraiser; it’s my way of fighting back. I started Project: Polaris to help fund my mother’s cervical cancer treatment. By blending my love for graphic design with apparel, I'm working to turn a difficult season into a community of support and hope.
                    </p>
                    <div class="flex flex-wrap gap-2">
                        <span class="text-[8px] font-black text-slate-600 bg-white/10 border border-white/30 px-4 py-1.5 rounded-full uppercase tracking-widest shadow-sm">Love & Support</span>
                        <span class="text-[8px] font-black text-slate-600 bg-white/10 border border-white/30 px-4 py-1.5 rounded-full uppercase tracking-widest shadow-sm">Design with Purpose</span>
                    </div>
                </div>
            </div>

            <div class="grid md:grid-cols-12 gap-10 items-center group">
                <div class="md:col-span-5 md:order-2">
                    <div class="relative rounded-[2rem] overflow-hidden border-[0.5px] border-white/40 shadow-2xl transition-transform duration-700 group-hover:scale-[1.02] -rotate-1">
                        <img src="images/bg.png" alt="Heart and Sole" class="w-full h-64 object-cover">
                    </div>
                </div>
                <div class="md:col-span-7 md:order-1">
                    <h4 class="text-2xl font-black text-slate-900 leading-tight mb-2 italic tracking-tight">Heart and Sole</h4>
                    <p class="text-[9px] font-black text-rose-600 uppercase tracking-[0.3em] mb-4">A Virtual Tribute</p>
                    <p class="text-[14px] text-slate-700 font-medium leading-relaxed mb-6 opacity-90">
                        I wanted to create something that honors the strength of mothers everywhere. Heart and Sole is a virtual run dedicated to those battling cancer. It’s my passion project where I handle everything from the branding to the medals, all to make sure these incredible women feel seen and celebrated.
                    </p>
                    <div class="flex flex-wrap gap-2">
                        <span class="text-[8px] font-black text-slate-600 bg-white/10 border border-white/30 px-4 py-1.5 rounded-full uppercase tracking-widest shadow-sm">Mother's Day Run</span>
                        <span class="text-[8px] font-black text-slate-600 bg-white/10 border border-white/30 px-4 py-1.5 rounded-full uppercase tracking-widest shadow-sm">Community Strength</span>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <div>
        <div class="flex items-center gap-4 mb-12">
            <h3 class="text-[10px] font-black text-slate-900 uppercase tracking-[0.4em] whitespace-nowrap">
                <span class="text-sky-600 mr-2">Sharing the Spark</span>
            </h3>
            <div class="w-full h-[0.5px] bg-slate-300/50"></div>
        </div>

        <div class="space-y-16">
            <div class="grid md:grid-cols-12 gap-10 items-center group">
                <div class="md:col-span-5">
                    <div class="relative rounded-[2rem] overflow-hidden border-[0.5px] border-white/40 shadow-2xl transition-transform duration-700 group-hover:scale-[1.02] rotate-1">
                        <img src="images/bg.png" alt="Team Gwen" class="w-full h-64 object-cover">
                    </div>
                </div>
                <div class="md:col-span-7">
                    <h4 class="text-2xl font-black text-slate-900 leading-tight mb-2 italic tracking-tight">Team Gwen Outreach</h4>
                    <p class="text-[9px] font-black text-sky-700 uppercase tracking-[0.3em] mb-4">Giving Back</p>
                    <p class="text-[14px] text-slate-700 font-medium leading-relaxed mb-6 opacity-90">
                        I love being part of Team Gwen. There’s something so rewarding about stepping out of the lab and into the community to help with outreach programs. It keeps me grounded and reminds me why we do what we do—to make life better for others.
                    </p>
                    <div class="flex flex-wrap gap-2">
                        <span class="text-[8px] font-black text-slate-600 bg-white/10 border border-white/30 px-4 py-1.5 rounded-full uppercase tracking-widest shadow-sm">Helping Hands</span>
                        <span class="text-[8px] font-black text-slate-600 bg-white/10 border border-white/30 px-4 py-1.5 rounded-full uppercase tracking-widest shadow-sm">Outreach Life</span>
                    </div>
                </div>
            </div>

            <div class="grid md:grid-cols-12 gap-10 items-center group">
                <div class="md:col-span-5 md:order-2">
                    <div class="relative rounded-[2rem] overflow-hidden border-[0.5px] border-white/40 shadow-2xl transition-transform duration-700 group-hover:scale-[1.02] -rotate-1">
                        <img src="images/bg.png" alt="AI Advocacy" class="w-full h-64 object-cover">
                    </div>
                </div>
                <div class="md:col-span-7 md:order-1">
                    <h4 class="text-2xl font-black text-slate-900 leading-tight mb-2 italic tracking-tight">AI Advocacy & Speaking</h4>
                    <p class="text-[9px] font-black text-emerald-600 uppercase tracking-[0.3em] mb-4">Passing the Torch</p>
                    <p class="text-[14px] text-slate-700 font-medium leading-relaxed mb-6 opacity-90">
                        I’m genuinely excited about where AI is going, and I love sharing that spark with others. Whether I’m talking to the public sector or private companies, my goal is always to demystify the tech. It's about empowering people to understand the "Good, the Bad, and everything in between" of this AI revolution.
                    </p>
                    <div class="flex flex-wrap gap-2">
                        <span class="text-[8px] font-black text-slate-600 bg-white/10 border border-white/30 px-4 py-1.5 rounded-full uppercase tracking-widest shadow-sm">Empowering Others</span>
                        <span class="text-[8px] font-black text-slate-600 bg-white/10 border border-white/30 px-4 py-1.5 rounded-full uppercase tracking-widest shadow-sm">AI Storytelling</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>
```

# sections\professional.html

```html
<section class="space-y-10">
    <div>
        <div class="flex items-center gap-4 mb-6">
            <h3 class="text-[25px] font-black text-slate-900 uppercase tracking-[0.4em] whitespace-nowrap">
                <span class="text-sky-600 mr-2">Research Narrative</span>
            </h3>
            <div class="w-full h-[1px] bg-slate-200"></div>
        </div>
        
        <div class="space-y-8">
            <div class="group grid md:grid-cols-12 gap-4">
                <div class="md:col-span-4">
                    <h4 class="text-lg font-black text-slate-900 leading-tight">AI Technical Lead & Consultant</h4>
                    <p class="text-[9px] font-black text-sky-900 uppercase tracking-widest mt-1">DOST-ASTI AI Initiatives</p>
                    <p class="text-[9px] font-bold text-slate-400 uppercase tracking-widest">2025 — Present</p>
                </div>
                <div class="md:col-span-8">
                    <p class="text-[14px] text-slate-600 font-medium leading-relaxed mb-3">
                        Providing strategic oversight for the implementation of Retrieval-Augmented Generation (RAG) systems. Focus remains on bridging the gap between NLP research and scalable, production-ready systems that address local linguistic nuances, specifically Taglish code-switching.
                    </p>
                    <div class="flex flex-wrap gap-2">
                        <span class="text-[8px] font-black text-slate-500 bg-white/50 border border-slate-200 px-2 py-1 rounded-md uppercase tracking-wider">Technical Strategy</span>
                        <span class="text-[8px] font-black text-slate-500 bg-white/50 border border-slate-200 px-2 py-1 rounded-md uppercase tracking-wider">Consultancy</span>
                        <span class="text-[8px] font-black text-slate-500 bg-white/50 border border-slate-200 px-2 py-1 rounded-md uppercase tracking-wider">RAG Deployment</span>
                    </div>
                </div>
            </div>

            <div class="group grid md:grid-cols-12 gap-4">
                <div class="md:col-span-4">
                    <h4 class="text-lg font-black text-slate-900 leading-tight">Project Technical Co-lead</h4>
                    <p class="text-[9px] font-black text-sky-800 uppercase tracking-widest mt-1">iTANONG Project</p>
                    <p class="text-[9px] font-bold text-slate-400 uppercase tracking-widest">2024</p>
                </div>
                <div class="md:col-span-8">
                    <p class="text-[14px] text-slate-600 font-medium leading-relaxed mb-3">
                        Directed the R&D of RAG systems and led the benchmarking of Large Language Models (LLMs) for Philippine contexts. Supervised research teams to ensure the integration of advanced semantic parsing models aligned with organizational data accessibility goals.
                    </p>
                    <div class="flex flex-wrap gap-2">
                        <span class="text-[8px] font-black text-slate-500 bg-white/50 border border-slate-200 px-2 py-1 rounded-md uppercase tracking-wider">Team Supervision</span>
                        <span class="text-[8px] font-black text-slate-500 bg-white/50 border border-slate-200 px-2 py-1 rounded-md uppercase tracking-wider">LLM Benchmarking</span>
                        <span class="text-[8px] font-black text-slate-500 bg-white/50 border border-slate-200 px-2 py-1 rounded-md uppercase tracking-wider">R&D Direction</span>
                    </div>
                </div>
            </div>

            <div class="group grid md:grid-cols-12 gap-4">
                <div class="md:col-span-4">
                    <h4 class="text-lg font-black text-slate-900 leading-tight">iTANONG Project Staff</h4>
                    <p class="text-[9px] font-black text-slate-500 uppercase tracking-widest mt-1">Engineering & Dataset Curation</p>
                    <p class="text-[9px] font-bold text-slate-300 uppercase tracking-widest">2022 — 2023</p>
                </div>
                <div class="md:col-span-8">
                    <p class="text-[14px] text-slate-600 font-medium leading-relaxed mb-3">
                        Executed the technical groundwork for iTANONG, focusing on Semantic Parsing and Natural Language Interfaces to Databases (NLIDB). Contributed to Parallel Corpus Curation and building the iTANONG-DS benchmark dataset for Philippine languages.
                    </p>
                    <div class="flex flex-wrap gap-2">
                        <span class="text-[8px] font-black text-slate-400 bg-white/50 border border-slate-200 px-2 py-1 rounded-md uppercase tracking-wider">Dataset Engineering</span>
                        <span class="text-[8px] font-black text-slate-400 bg-white/50 border border-slate-200 px-2 py-1 rounded-md uppercase tracking-wider">Text-to-SQL</span>
                        <span class="text-[8px] font-black text-slate-400 bg-white/50 border border-slate-200 px-2 py-1 rounded-md uppercase tracking-wider">Semantic Parsing</span>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <div class="pt-6">
        <div class="flex items-center gap-4 mb-6">
            <h3 class="text-[25px] font-black text-slate-900 uppercase tracking-[0.4em] whitespace-nowrap">
                <span class="text-sky-600 mr-2">Publications</span>
            </h3>
            <div class="w-full h-[1px] bg-slate-200"></div>
        </div>

        <div class="space-y-8">
            <div class="group">
                <h4 class="text-md font-black text-slate-900 group-hover:text-sky-800 transition leading-snug">
                    Benchmarking Open-Source Large Language Models on Code-Switched Tagalog-English Retrieval Augmented Generation
                </h4>
                <p class="text-[11px] text-slate-700 font-bold mt-1">
                    <span class="underline decoration-sky-400 font-black italic">Aunhel John M. Adoptante</span>, J. A. D. V. Castro, M. L. B. Medrano, A. P. B. Ocampo, E. C. Peramo, M. R. M. Miranda
                </p>
                <p class="text-[10px] font-bold italic text-slate-400 mt-1">Journal of Advances in Information Technology, Vol. 16, No. 2 (2025)</p>
                <div class="flex items-center gap-4 mt-2">
                    <button onclick="toggleBib('bib-bench')" class="text-[8px] font-black text-slate-400 hover:text-sky-700 uppercase tracking-widest flex items-center gap-1">
                        <i class="fa-solid fa-eye text-[10px]"></i> View BibTeX
                    </button>
                    <button onclick="copyBib(event, 'bib-bench')" class="text-[8px] font-black text-slate-400 hover:text-emerald-600 uppercase tracking-widest flex items-center gap-1">
                        <i class="fa-solid fa-copy text-[10px]"></i> Copy
                    </button>
                </div>
                <pre id="bib-bench" class="hidden mt-3 p-3 bg-slate-900 text-slate-300 rounded-lg text-[9px] overflow-x-auto">@article{adoptante2025benchmarking,
  title={Benchmarking Open-Source Large Language Models on Code-Switched Tagalog-English Retrieval Augmented Generation},
  author={Adoptante, Aunhel John M. and Castro, Jasper Adrian Dwight V. and Medrano, Micholo Lanz B. and Ocampo, Alyssa Patricia B. and Peramo, Elmer C. and Miranda, Melissa Ruth M.},
  journal={Journal of Advances in Information Technology},
  volume={16},
  number={2},
  pages={233--242},
  year={2025}
}</pre>
            </div>

            <div class="group">
                <h4 class="text-md font-black text-slate-900 group-hover:text-sky-800 transition leading-snug">
                    iTANONG-DS: A Collection of Benchmark Datasets for Downstream Natural Language Processing Tasks on Select Philippine Languages
                </h4>
                <p class="text-[11px] text-slate-700 font-bold mt-1">M. L. Visperas, C. J. Borjal, <span class="underline decoration-sky-400 font-black italic">Aunhel John M. Adoptante</span>, D. S. R. Abacial, M. M. Decano, E. C. Peramo</p>
                <p class="text-[10px] font-bold italic text-slate-400 mt-1">Proceedings of the 6th International Conference on Natural Language and Speech Processing (ICNLSP 2023)</p>
                <div class="flex items-center gap-4 mt-2">
                    <button onclick="toggleBib('bib-itanong')" class="text-[8px] font-black text-slate-400 hover:text-sky-700 uppercase tracking-widest flex items-center gap-1">
                        <i class="fa-solid fa-eye text-[10px]"></i> View BibTeX
                    </button>
                </div>
            </div>

            <div class="group">
                <h4 class="text-md font-black text-slate-900 group-hover:text-sky-800 transition leading-snug">
                    Parallel Corpus Curation for Filipino Text-to-SQL Semantic Parsing
                </h4>
                <p class="text-[11px] text-slate-700 font-bold mt-1">C. J. Borjal, M. Visperas, <span class="underline decoration-sky-400 font-black italic">Aunhel John Adoptante</span>, M. T. Abia, J. K. Catapang, E. Peramo</p>
                <p class="text-[10px] font-bold italic text-slate-400 mt-1">2023 International Conference on Artificial Intelligence in Information and Communication (ICAIIC)</p>
                <div class="flex items-center gap-4 mt-2">
                    <button onclick="toggleBib('bib-sql-parallel')" class="text-[8px] font-black text-slate-400 hover:text-sky-700 uppercase tracking-widest flex items-center gap-1">
                        <i class="fa-solid fa-eye text-[10px]"></i> View BibTeX
                    </button>
                </div>
            </div>

            <div class="group">
                <h4 class="text-md font-black text-slate-900 group-hover:text-sky-800 transition leading-snug">
                    On modern text-to-sql semantic parsing methodologies for natural language interface to databases: A comparative study
                </h4>
                <p class="text-[11px] text-slate-700 font-bold mt-1">M. Visperas, <span class="underline decoration-sky-400 font-black italic">Aunhel John Adoptante</span>, C. J. Borjal, M. T. Abia, J. K. Catapang, E. Peramo</p>
                <p class="text-[10px] font-bold italic text-slate-400 mt-1">2023 International Conference on Artificial Intelligence in Information and Communication (ICAIIC)</p>
                <div class="flex items-center gap-4 mt-2">
                    <button onclick="toggleBib('bib-sql-study')" class="text-[8px] font-black text-slate-400 hover:text-sky-700 uppercase tracking-widest flex items-center gap-1">
                        <i class="fa-solid fa-eye text-[10px]"></i> View BibTeX
                    </button>
                </div>
            </div>

            <div class="group">
                <h4 class="text-md font-black text-slate-900 group-hover:text-sky-800 transition leading-snug">
                    Spoken-digit classification using artificial neural network
                </h4>
                <p class="text-[11px] text-slate-700 font-bold mt-1"><span class="underline decoration-sky-400 font-black italic">Aunhel John M. Adoptante</span>, A. M. Baes, J. C. A. Catilo, P. K. L. Lucero, A. L. P. De Ocampo, A. S. Alon, R. M. Dellosa</p>
                <p class="text-[10px] font-bold italic text-slate-400 mt-1">ASEAN Engineering Journal, Vol. 13, No. 1 (2023)</p>
                <div class="flex items-center gap-4 mt-2">
                    <button onclick="toggleBib('bib-spoken')" class="text-[8px] font-black text-slate-400 hover:text-sky-700 uppercase tracking-widest flex items-center gap-1">
                        <i class="fa-solid fa-eye text-[10px]"></i> View BibTeX
                    </button>
                </div>
            </div>

            <div class="group">
                <h4 class="text-md font-black text-slate-900 group-hover:text-sky-800 transition leading-snug">
                    Deep autoencoders for denoising computerized tomography (CT) images
                </h4>
                <p class="text-[11px] text-slate-700 font-bold mt-1"><span class="underline decoration-sky-400 font-black italic">Aunhel John M. Adoptante</span>, A. S. Alon, S. Avasthi</p>
                <p class="text-[10px] font-bold italic text-slate-400 mt-1">International Research Journal on Innovations in Engineering, Science and Technology, Vol. 8 (2022)</p>
                <div class="flex items-center gap-4 mt-2">
                    <button onclick="toggleBib('bib-denoise')" class="text-[8px] font-black text-slate-400 hover:text-sky-700 uppercase tracking-widest flex items-center gap-1">
                        <i class="fa-solid fa-eye text-[10px]"></i> View BibTeX
                    </button>
                </div>
            </div>

            <div class="group">
                <h4 class="text-md font-black text-slate-900 group-hover:text-sky-800 transition leading-snug">
                    A novel screening tool system for depressive disorders using social media and artificial neural network
                </h4>
                <p class="text-[11px] text-slate-700 font-bold mt-1">A. M. M. Baes, <span class="underline decoration-sky-400 font-black italic">Aunhel John M. Adoptante</span>, J. C. A. Catilo, P. K. L. Lucero, J. F. P. Peralta, A. L. P. De Ocampo</p>
                <p class="text-[10px] font-bold italic text-slate-400 mt-1">International Journal of Intelligent Systems and Applications in Engineering, Vol. 10, No. 1 (2022)</p>
                <div class="flex items-center gap-4 mt-2">
                    <button onclick="toggleBib('bib-depress')" class="text-[8px] font-black text-slate-400 hover:text-sky-700 uppercase tracking-widest flex items-center gap-1">
                        <i class="fa-solid fa-eye text-[10px]"></i> View BibTeX
                    </button>
                </div>
            </div>

            <div class="group border-b border-slate-50 pb-12">
                <h4 class="text-md font-black text-slate-900 group-hover:text-sky-800 transition leading-snug">
                    INTELLIGENT SYSTEMS AND APPLICATIONS IN ENGINEERING
                </h4>
                <p class="text-[11px] text-slate-700 font-bold mt-1">A. M. M. Baes, <span class="underline decoration-sky-400 font-black italic">Aunhel John M. Adoptante</span>, J. C. A. Catilo, P. K. L. Lucero, J. F. Peralta, A. L. P. de Ocampo</p>
                <div class="flex items-center gap-4 mt-2">
                    <button onclick="toggleBib('bib-ann')" class="text-[8px] font-black text-slate-400 hover:text-sky-700 uppercase tracking-widest flex items-center gap-1">
                        <i class="fa-solid fa-eye text-[10px]"></i> View BibTeX
                    </button>
                </div>
            </div>
        </div>
    </div>
</section>
```

# sections\projects.html

```html
<section class="py-12">
    <div class="flex items-center gap-6 mb-16 px-2">
        <h3 class="text-[16px] md:text-[20px] font-black text-slate-900 uppercase tracking-[0.5em] whitespace-nowrap">
            <span class="text-sky-600 mr-2">Passion and Purpose
        </h3>
        <div class="w-full h-[2px] bg-slate-100"></div>
    </div>

    <style>
        .carousel-viewport { overflow: hidden; position: relative; padding: 40px 0; margin: -40px 0; }
        .carousel-track { display: flex; gap: 32px; transition: transform 0.8s cubic-bezier(0.16, 1, 0.3, 1); will-change: transform; }
        
        /* Card Style */
        .project-card {
            flex-shrink: 0; border-radius: 48px; padding: 2.5rem; height: 380px; width: 340px;
            display: flex; flex-direction: column; background: rgba(255, 255, 255, 0.6);
            backdrop-filter: blur(20px); border: 2px solid #ffffff;
            box-shadow: 0 20px 40px -15px rgba(0, 0, 0, 0.03);
            transition: all 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
            position: relative; overflow: hidden; cursor: pointer;
        }
        .project-card:hover { transform: translateY(-12px); box-shadow: 0 30px 60px -12px rgba(0, 0, 0, 0.08); }
        
        .aura { position: absolute; width: 180px; height: 180px; border-radius: 50%; filter: blur(60px); z-index: 0; opacity: 0.3; top: -30px; right: -30px; }
        .icon-pod { width: 60px; height: 60px; border-radius: 24px; display: flex; align-items: center; justify-content: center; background: white; box-shadow: 0 8px 16px rgba(0,0,0,0.05); margin-bottom: 2rem; position: relative; z-index: 10; }

        /* Modal Styles */
        #projectModal { 
            position: fixed; inset: 0; z-index: 9999; display: none; 
            align-items: center; justify-content: center; padding: 20px;
            background: rgba(255, 255, 255, 0.4); backdrop-filter: blur(12px);
        }
        .modal-container { 
            background: white; width: 100%; max-width: 850px; border-radius: 40px; 
            overflow: hidden; box-shadow: 0 50px 100px -20px rgba(0,0,0,0.2);
            animation: modalPop 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }
        @keyframes modalPop { from { opacity: 0; transform: scale(0.9) translateY(20px); } to { opacity: 1; transform: scale(1) translateY(0); } }
        
        .carousel-btn {
            width: 60px; height: 60px; border-radius: 50%; background: white;
            display: flex; align-items: center; justify-content: center; cursor: pointer;
            transition: all 0.4s ease; color: #1e293b; border: 2px solid #f8fafc;
        }
        .carousel-btn:hover:not(:disabled) { border-color: #38bdf8; color: #38bdf8; box-shadow: 0 10px 20px rgba(56, 189, 248, 0.1); }
    </style>

    <div class="relative">
        <div class="carousel-viewport" id="carouselViewport">
            <div class="carousel-track" id="carouselTrack">

                <div class="project-card" onclick="openModal('volunteer')">
                    <div class="aura bg-emerald-300"></div>
                    <div class="icon-pod"><i class="fa-solid fa-hands-holding-circle text-emerald-400 text-2xl"></i></div>
                    <h4 class="text-2xl font-black text-slate-900 tracking-tighter">Volunteerism</h4>
                    <p class="text-slate-500 text-[14px] leading-relaxed mt-4 font-medium">Community initiatives focusing on tech representation and local social impact.</p>
                    <span class="mt-auto inline-block text-[10px] font-black text-emerald-600 uppercase tracking-widest">Community Impact</span>
                </div>

                <div class="project-card" onclick="openModal('mentorship')">
                    <div class="aura bg-indigo-300"></div>
                    <div class="icon-pod"><i class="fa-solid fa-user-graduate text-indigo-400 text-2xl"></i></div>
                    <h4 class="text-2xl font-black text-slate-900 tracking-tighter">Mentorship</h4>
                    <p class="text-slate-500 text-[14px] leading-relaxed mt-4 font-medium">Guiding the next generation of Filipino researchers in AI and NLP.</p>
                    <span class="mt-auto inline-block text-[10px] font-black text-indigo-600 uppercase tracking-widest">Technical Guidance</span>
                </div>

                <div class="project-card" onclick="openModal('walo')">
                    <div class="aura bg-sky-400"></div>
                    <div class="icon-pod"><i class="fa-solid fa-sparkles text-sky-400 text-2xl"></i></div>
                    <h4 class="text-2xl font-black text-slate-900 tracking-tighter">WALO</h4>
                    <p class="text-slate-500 text-[14px] leading-relaxed mt-4 font-medium">A creative visual archive for BINI, featuring "Eras Tour" style poster concepts.</p>
                    <span class="mt-auto inline-block text-[10px] font-black text-sky-500 uppercase tracking-widest">View Designs</span>
                </div>

                <div class="project-card" onclick="openModal('polaris')">
                    <div class="aura bg-amber-300"></div>
                    <div class="icon-pod"><i class="fa-solid fa-star text-amber-400 text-2xl"></i></div>
                    <h4 class="text-2xl font-black text-slate-900 tracking-tighter">Project: Polaris</h4>
                    <p class="text-slate-500 text-[14px] leading-relaxed mt-4 font-medium">Advocacy through apparel to support medical funding and cancer treatment.</p>
                    <span class="mt-auto inline-block text-[10px] font-black text-amber-500 uppercase tracking-widest">Mission & Fundraiser</span>
                </div>

                <div class="project-card" onclick="openModal('heart')">
                    <div class="aura bg-rose-300"></div>
                    <div class="icon-pod"><i class="fa-solid fa-heart text-rose-400 text-2xl"></i></div>
                    <h4 class="text-2xl font-black text-slate-900 tracking-tighter">Heart and Sole</h4>
                    <p class="text-slate-500 text-[14px] leading-relaxed mt-4 font-medium">A virtual run event promoting health awareness and collective social action.</p>
                    <span class="mt-auto inline-block text-[10px] font-black text-rose-500 uppercase tracking-widest">Event Strategy</span>
                </div>

            </div>
        </div>

        <div class="flex gap-4 mt-10 justify-center">
            <button class="carousel-btn" id="btnPrev" onclick="carouselScroll(-1)" disabled><i class="fa-solid fa-chevron-left"></i></button>
            <button class="carousel-btn" id="btnNext" onclick="carouselScroll(1)"><i class="fa-solid fa-chevron-right"></i></button>
        </div>
    </div>

    <div id="projectModal" onclick="closeModal()">
        <div class="modal-container" onclick="event.stopPropagation()">
            <div class="flex flex-col md:flex-row h-full max-h-[85vh] overflow-y-auto">
                <div class="w-full md:w-1/2 bg-slate-50 flex items-center justify-center p-6">
                    <img id="modalImg" src="images/bg.png" class="w-full h-auto rounded-3xl shadow-xl">
                </div>
                <div class="w-full md:w-1/2 p-10 flex flex-col">
                    <div class="flex justify-between items-start mb-6">
                        <div id="modalBadge" class="px-3 py-1 rounded-full text-[9px] font-black uppercase tracking-widest"></div>
                        <button onclick="closeModal()" class="text-slate-300 hover:text-slate-900"><i class="fa-solid fa-xmark text-2xl"></i></button>
                    </div>
                    <h2 id="modalTitle" class="text-4xl font-black text-slate-900 tracking-tighter mb-4"></h2>
                    <p id="modalDesc" class="text-slate-500 text-[15px] leading-relaxed mb-8 font-medium"></p>
                    <div class="mt-auto pt-8 border-t border-slate-100">
                        <span class="text-[10px] font-black text-slate-400 uppercase tracking-[0.2em] block mb-2">Impact Highlight</span>
                        <p id="modalImpact" class="text-[14px] font-bold text-slate-800"></p>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        const projectData = {
            volunteer: {
                title: "Volunteerism",
                badge: "Community Impact",
                badgeColor: "bg-emerald-50 text-emerald-600",
                desc: "Focused on community-led initiatives and leveraging scientific research skills for social impact. My advocacy involves ensuring strong Filipino representation in global tech spaces while supporting local grassroots movements.",
                impact: "Advocacy for Filipino Tech Representation",
                img: "images/photo.jpeg"
            },
            mentorship: {
                title: "Mentorship",
                badge: "Technical Leadership",
                badgeColor: "bg-indigo-50 text-indigo-600",
                desc: "In my capacity as an AI Technical Co-lead at DOST-ASTI, I supervise research teams and direct the technical strategy for advanced NLP systems. I prioritize guiding emerging talent in mastering RAG and semantic parsing methodologies.",
                impact: "Building Research Capacity in the Philippines",
                img: "images/photo.jpeg"
            },
            walo: {
                title: "WALO",
                badge: "Creative Concept",
                badgeColor: "bg-sky-50 text-sky-500",
                desc: "A creative project exploring the discography of the Filipino girl group BINI. This archive features high-fidelity visual concepts, including a custom 'Eras Tour' style poster design for each of the eight members.",
                impact: "Pop Culture Visual Branding",
                img: "images/bg.png"
            },
            polaris: {
                title: "Project: Polaris",
                badge: "Fundraising & Advocacy",
                badgeColor: "bg-amber-50 text-amber-500",
                desc: "A dedicated fundraiser to help cover medical costs for cervical cancer treatment. This initiative involves selling t-shirts featuring unique designs based on my mother's life mantras.",
                impact: "Medical Support for Cervical Cancer Advocacy",
                img: "images/bg.png"
            },
            heart: {
                title: "Heart and Sole",
                badge: "Virtual Event",
                badgeColor: "bg-rose-50 text-rose-500",
                desc: "A Mother's Day virtual run event titled 'Heart and Sole'. A portion of the proceeds from the run is donated to help families undergoing cervical cancer treatment.",
                impact: "Health Awareness & Financial Support",
                img: "images/bg.png"
            }
        };

        function openModal(id) {
            const data = projectData[id];
            document.getElementById('modalTitle').innerText = data.title;
            document.getElementById('modalBadge').innerText = data.badge;
            document.getElementById('modalBadge').className = `px-3 py-1 rounded-full text-[9px] font-black uppercase tracking-widest ${data.badgeColor}`;
            document.getElementById('modalDesc').innerText = data.desc;
            document.getElementById('modalImpact').innerText = data.impact;
            document.getElementById('modalImg').src = data.img;
            document.getElementById('projectModal').style.display = 'flex';
            document.body.style.overflow = 'hidden';
        }

        function closeModal() {
            document.getElementById('projectModal').style.display = 'none';
            document.body.style.overflow = 'auto';
        }

        (function () {
            const track = document.getElementById('carouselTrack');
            const viewport = document.getElementById('carouselViewport');
            const btnPrev = document.getElementById('btnPrev');
            const btnNext = document.getElementById('btnNext');
            const GAP = 32;
            let position = 0;
            function getStepSize() { const card = track.children[0]; return card ? card.offsetWidth + GAP : 372; }
            function maxScroll() { return track.scrollWidth - viewport.offsetWidth; }
            window.carouselScroll = function (dir) {
                const step = getStepSize();
                position = Math.max(0, Math.min(position + dir * step, maxScroll()));
                track.style.transform = `translateX(-${position}px)`;
                btnPrev.disabled = position <= 0;
                btnNext.disabled = position >= maxScroll();
            };
        })();
    </script>
</section>
```

# sections\publications.html

```html
<section>
    <div class="flex items-center gap-6 mb-16">
        <h3 class="text-[16px] md:text-[20px] font-black text-slate-900 uppercase tracking-[0.5em] whitespace-nowrap">
            <span class="text-sky-600 mr-2">Publications
        </h3>
        <div class="w-full h-[2px] bg-slate-100"></div>
    </div>

    <div class="space-y-16">

        <div class="group">
            <h4 class="text-xl font-black text-slate-900 group-hover:text-sky-800 transition leading-snug">
                Benchmarking Open-Source Large Language Models on Code-Switched Tagalog-English Retrieval Augmented Generation
            </h4>
            <p class="text-sm text-slate-700 font-bold mt-2">
                <span class="underline decoration-sky-400 font-black italic">Aunhel John M. Adoptante</span>, J. A. D. V. Castro, M. L. B. Medrano, A. P. B. Ocampo, E. C. Peramo, M. R. M. Miranda
            </p>
            <p class="text-[13px] font-bold italic text-slate-500 mt-1">Journal of Advances in Information Technology, Vol. 16, No. 2 (2025)</p>
            
            <div class="flex items-center gap-6 mt-4">
                <button onclick="toggleBib('bib-bench')" class="text-[9px] font-black text-slate-400 hover:text-sky-700 uppercase tracking-widest flex items-center gap-2 transition-all">
                    <i class="fa-solid fa-eye text-xs"></i> View BibTeX
                </button>
                <button onclick="copyBib(event, 'bib-bench')" class="text-[9px] font-black text-slate-400 hover:text-emerald-600 uppercase tracking-widest flex items-center gap-2 transition-all">
                    <i class="fa-solid fa-copy text-xs"></i> Copy Citation
                </button>
            </div>

            <pre id="bib-bench" class="hidden mt-4 p-4 bg-slate-900 text-slate-300 rounded-xl text-[10px] overflow-x-auto border border-slate-800">@article{adoptante2025benchmarking,
  title={Benchmarking Open-Source Large Language Models on Code-Switched Tagalog-English Retrieval Augmented Generation},
  author={Adoptante, Aunhel John M. and Castro, Jasper Adrian Dwight V. and Medrano, Micholo Lanz B. and Ocampo, Alyssa Patricia B. and Peramo, Elmer C. and Miranda, Melissa Ruth M.},
  journal={Journal of Advances in Information Technology},
  volume={16},
  number={2},
  pages={233--242},
  year={2025}
}</pre>
        </div>

        <div class="group">
            <h4 class="text-xl font-black text-slate-900 group-hover:text-sky-800 transition leading-snug">
                iTANONG-DS: A Collection of Benchmark Datasets for Downstream Natural Language Processing Tasks on Select Philippine Languages
            </h4>
            <p class="text-sm text-slate-700 font-bold mt-2">
                M. L. Visperas, C. J. Borjal, <span class="underline decoration-sky-400 font-black italic">Aunhel John M. Adoptante</span>, D. S. R. Abacial, M. M. Decano, E. C. Peramo
            </p>
            <p class="text-[13px] font-bold italic text-slate-500 mt-1">Proceedings of the 6th International Conference on Natural Language and Speech Processing (ICNLSP 2023)</p>
            
            <div class="flex items-center gap-6 mt-4">
                <button onclick="toggleBib('bib-itanong')" class="text-[9px] font-black text-slate-400 hover:text-sky-700 uppercase tracking-widest flex items-center gap-2">
                    <i class="fa-solid fa-eye text-xs"></i> View BibTeX
                </button>
                <button onclick="copyBib(event, 'bib-itanong')" class="text-[9px] font-black text-slate-400 hover:text-emerald-600 uppercase tracking-widest flex items-center gap-2">
                    <i class="fa-solid fa-copy text-xs"></i> Copy Citation
                </button>
            </div>

            <pre id="bib-itanong" class="hidden mt-4 p-4 bg-slate-900 text-slate-300 rounded-xl text-[10px] overflow-x-auto border border-slate-800">@inproceedings{visperas2023itanong,
  title={iTANONG-DS: A Collection of Benchmark Datasets for Downstream Natural Language Processing Tasks on Select Philippine Languages},
  author={Visperas, Moses L and Borjal, Christalline Joie and Adoptante, Aunhel John M and Abacial, Danielle Shine R and Decano, Ma Miciella and Peramo, Elmer C},
  booktitle={Proceedings of the 6th International Conference on Natural Language and Speech Processing (ICNLSP 2023)},
  pages={316--323},
  year={2023}
}</pre>
        </div>

        <div class="group">
            <h4 class="text-xl font-black text-slate-900 group-hover:text-sky-800 transition leading-snug">
                Parallel Corpus Curation for Filipino Text-to-SQL Semantic Parsing
            </h4>
            <p class="text-sm text-slate-700 font-bold mt-2">
                C. J. Borjal, M. Visperas, <span class="underline decoration-sky-400 font-black italic">Aunhel John Adoptante</span>, M. T. Abia, J. K. Catapang, E. Peramo
            </p>
            <p class="text-[13px] font-bold italic text-slate-500 mt-1">2023 International Conference on Artificial Intelligence in Information and Communication (ICAIIC)</p>
            
            
            
            <div class="flex items-center gap-6 mt-4">
                <button onclick="toggleBib('bib-sql-parallel')" class="text-[9px] font-black text-slate-400 hover:text-sky-700 uppercase tracking-widest flex items-center gap-2">
                    <i class="fa-solid fa-eye text-xs"></i> View BibTeX
                </button>
                <button onclick="copyBib(event, 'bib-sql-parallel')" class="text-[9px] font-black text-slate-400 hover:text-emerald-600 uppercase tracking-widest flex items-center gap-2">
                    <i class="fa-solid fa-copy text-xs"></i> Copy Citation
                </button>
            </div>

            <pre id="bib-sql-parallel" class="hidden mt-4 p-4 bg-slate-900 text-slate-300 rounded-xl text-[10px] overflow-x-auto border border-slate-800">@inproceedings{borjal2023parallel,
  title={Parallel Corpus Curation for Filipino Text-to-SQL Semantic Parsing},
  author={Borjal, Christalline Joie and Visperas, Moses and Adoptante, Aunhel John and Abia, Ma Teresita and Catapang, Jasper Kyle and Peramo, Elmer},
  booktitle={2023 International Conference on Artificial Intelligence in Information and Communication (ICAIIC)},
  pages={163--169},
  year={2023},
  organization={IEEE}
}</pre>
        </div>

        <div class="group">
            <h4 class="text-xl font-black text-slate-900 group-hover:text-sky-800 transition leading-snug">
                On modern text-to-sql semantic parsing methodologies for natural language interface to databases: A comparative study
            </h4>
            <p class="text-sm text-slate-700 font-bold mt-2">
                M. Visperas, <span class="underline decoration-sky-400 font-black italic">Aunhel John Adoptante</span>, C. J. Borjal, M. T. Abia, J. K. Catapang, E. Peramo
            </p>
            <p class="text-[13px] font-bold italic text-slate-500 mt-1">2023 International Conference on Artificial Intelligence in Information and Communication (ICAIIC)</p>
            
            <div class="flex items-center gap-6 mt-4">
                <button onclick="toggleBib('bib-sql-study')" class="text-[9px] font-black text-slate-400 hover:text-sky-700 uppercase tracking-widest flex items-center gap-2">
                    <i class="fa-solid fa-eye text-xs"></i> View BibTeX
                </button>
                <button onclick="copyBib(event, 'bib-sql-study')" class="text-[9px] font-black text-slate-400 hover:text-emerald-600 uppercase tracking-widest flex items-center gap-2">
                    <i class="fa-solid fa-copy text-xs"></i> Copy Citation
                </button>
            </div>

            <pre id="bib-sql-study" class="hidden mt-4 p-4 bg-slate-900 text-slate-300 rounded-xl text-[10px] overflow-x-auto border border-slate-800">@inproceedings{visperas2023modern,
  title={On modern text-to-sql semantic parsing methodologies for natural language interface to databases: A comparative study},
  author={Visperas, Moses and Adoptante, Aunhel John and Borjal, Christalline Joie and Abia, Ma Teresita and Catapang, Jasper Kyle and Peramo, Elmer},
  booktitle={2023 International Conference on Artificial Intelligence in Information and Communication (ICAIIC)},
  pages={390--396},
  year={2023},
  organization={IEEE}
}</pre>
        </div>

        <div class="group">
            <h4 class="text-xl font-black text-slate-900 group-hover:text-sky-800 transition leading-snug">
                Spoken-digit classification using artificial neural network
            </h4>
            <p class="text-sm text-slate-700 font-bold mt-2">
                <span class="underline decoration-sky-400 font-black italic">Aunhel John M. Adoptante</span>, A. M. Baes, J. C. A. Catilo, P. K. L. Lucero, A. L. P. De Ocampo, A. S. Alon, R. M. Dellosa
            </p>
            <p class="text-[13px] font-bold italic text-slate-500 mt-1">ASEAN Engineering Journal, Vol. 13, No. 1 (2023)</p>
            
            <div class="flex items-center gap-6 mt-4">
                <button onclick="toggleBib('bib-spoken')" class="text-[9px] font-black text-slate-400 hover:text-sky-700 uppercase tracking-widest flex items-center gap-2">
                    <i class="fa-solid fa-eye text-xs"></i> View BibTeX
                </button>
                <button onclick="copyBib(event, 'bib-spoken')" class="text-[9px] font-black text-slate-400 hover:text-emerald-600 uppercase tracking-widest flex items-center gap-2">
                    <i class="fa-solid fa-copy text-xs"></i> Copy Citation
                </button>
            </div>

            <pre id="bib-spoken" class="hidden mt-4 p-4 bg-slate-900 text-slate-300 rounded-xl text-[10px] overflow-x-auto border border-slate-800">@article{adoptante2023spoken,
  title={Spoken-digit classification using artificial neural network},
  author={Adoptante, Aunhel John M and Baes, Arnie M and Catilo, John Carlo A and Lucero, Patrick Kendrex L and De Ocampo, Anton Louise P and Alon, Alvin S and Dellosa, Rhowel M},
  journal={ASEAN Engineering Journal},
  volume={13},
  number={1},
  pages={93--99},
  year={2023}
}</pre>
        </div>

        <div class="group">
            <h4 class="text-xl font-black text-slate-900 group-hover:text-sky-800 transition leading-snug">
                Deep autoencoders for denoising computerized tomography (CT) images
            </h4>
            <p class="text-sm text-slate-700 font-bold mt-2">
                <span class="underline decoration-sky-400 font-black italic">Aunhel John M. Adoptante</span>, A. S. Alon, S. Avasthi
            </p>
            <p class="text-[13px] font-bold italic text-slate-500 mt-1">International Research Journal on Innovations in Engineering, Science and Technology, Vol. 8 (2022)</p>
            
            
            
            <div class="flex items-center gap-6 mt-4">
                <button onclick="toggleBib('bib-denoise')" class="text-[9px] font-black text-slate-400 hover:text-sky-700 uppercase tracking-widest flex items-center gap-2">
                    <i class="fa-solid fa-eye text-xs"></i> View BibTeX
                </button>
                <button onclick="copyBib(event, 'bib-denoise')" class="text-[9px] font-black text-slate-400 hover:text-emerald-600 uppercase tracking-widest flex items-center gap-2">
                    <i class="fa-solid fa-copy text-xs"></i> Copy Citation
                </button>
            </div>

            <pre id="bib-denoise" class="hidden mt-4 p-4 bg-slate-900 text-slate-300 rounded-xl text-[10px] overflow-x-auto border border-slate-800">@article{adoptante2022deep,
  title={Deep autoencoders for denoising computerized tomography (CT) images},
  author={Adoptante, Aunhel John M and Alon, Alvin S and Avasthi, Sandhya},
  journal={International Research Journal on Innovations in Engineering, Science and Technology},
  volume={8},
  pages={26--31},
  year={2022}
}</pre>
        </div>

        <div class="group">
            <h4 class="text-xl font-black text-slate-900 group-hover:text-sky-800 transition leading-snug">
                A novel screening tool system for depressive disorders using social media and artificial neural network
            </h4>
            <p class="text-sm text-slate-700 font-bold mt-2">
                A. M. M. Baes, <span class="underline decoration-sky-400 font-black italic">Aunhel John M. Adoptante</span>, J. C. A. Catilo, P. K. L. Lucero, J. F. P. Peralta, A. L. P. De Ocampo
            </p>
            <p class="text-[13px] font-bold italic text-slate-500 mt-1">International Journal of Intelligent Systems and Applications in Engineering, Vol. 10, No. 1 (2022)</p>
            
            <div class="flex items-center gap-6 mt-4">
                <button onclick="toggleBib('bib-depress')" class="text-[9px] font-black text-slate-400 hover:text-sky-700 uppercase tracking-widest flex items-center gap-2">
                    <i class="fa-solid fa-eye text-xs"></i> View BibTeX
                </button>
                <button onclick="copyBib(event, 'bib-depress')" class="text-[9px] font-black text-slate-400 hover:text-emerald-600 uppercase tracking-widest flex items-center gap-2">
                    <i class="fa-solid fa-copy text-xs"></i> Copy Citation
                </button>
            </div>

            <pre id="bib-depress" class="hidden mt-4 p-4 bg-slate-900 text-slate-300 rounded-xl text-[10px] overflow-x-auto border border-slate-800">@article{baes2022novel,
  title={A novel screening tool system for depressive disorders using social media and artificial neural network},
  author={Baes, AMM and Adoptante, AJM and Catilo, JCA and Lucero, PKL and Peralta, JFP and De Ocampo, ALP},
  journal={Int. J. Intell. Syst. Appl. Eng},
  volume={10},
  number={1},
  pages={116--121},
  year={2022}
}</pre>
        </div>

        <div class="group border-b border-slate-50 pb-12">
            <h4 class="text-xl font-black text-slate-900 group-hover:text-sky-800 transition leading-snug">
                INTELLIGENT SYSTEMS AND APPLICATIONS IN ENGINEERING
            </h4>
            <p class="text-sm text-slate-700 font-bold mt-2">
                A. M. M. Baes, <span class="underline decoration-sky-400 font-black italic">Aunhel John M. Adoptante</span>, J. C. A. Catilo, P. K. L. Lucero, J. F. Peralta, A. L. P. de Ocampo
            </p>
            
            <div class="flex items-center gap-6 mt-4">
                <button onclick="toggleBib('bib-ann')" class="text-[9px] font-black text-slate-400 hover:text-sky-700 uppercase tracking-widest flex items-center gap-2">
                    <i class="fa-solid fa-eye text-xs"></i> View BibTeX
                </button>
                <button onclick="copyBib(event, 'bib-ann')" class="text-[9px] font-black text-slate-400 hover:text-emerald-600 uppercase tracking-widest flex items-center gap-2">
                    <i class="fa-solid fa-copy text-xs"></i> Copy Citation
                </button>
            </div>

            <pre id="bib-ann" class="hidden mt-4 p-4 bg-slate-900 text-slate-300 rounded-xl text-[10px] overflow-x-auto border border-slate-800">@article{baesintelligent,
  title={INTELLIGENT SYSTEMS AND APPLICATIONS IN ENGINEERING},
  author={Baes, Arnie Mae M and Adoptante, Aunhel John M and Catilo, John Carlo A and Lucero, Patrick Kendrex L and Peralta, Janice F and de Ocampo, Anton Louise P}
}</pre>
        </div>

    </div>
</section>
```

# sections\research.html

```html
<section>
    <div class="flex items-center gap-6 mb-16">
        <h3 class="text-[16px] md:text-[20px] font-black text-slate-900 uppercase tracking-[0.5em] whitespace-nowrap">
            <span class="text-sky-600 mr-2">Research Narrative
        </h3>
        <div class="w-full h-[2px] bg-slate-100"></div>
    </div>
    
    <div class="space-y-24">

        <div class="group grid md:grid-cols-12 gap-8">
            <div class="md:col-span-4">
                <h4 class="text-2xl font-black text-slate-900 leading-tight mb-1">AI Technical Lead & Consultant</h4>
                <p class="text-[12px] font-black text-sky-900 uppercase tracking-widest mb-1">DOST-ASTI AI Initiatives</p>
                <p class="text-[11px] font-bold text-slate-400 uppercase tracking-widest">2025 — Present</p>
            </div>
            
            <div class="md:col-span-8">
                <p class="text-[16px] text-slate-700 font-medium leading-relaxed mb-6">
                    Providing strategic oversight for the implementation of <strong>Retrieval-Augmented Generation (RAG)</strong> systems. My focus remains on bridging the gap between <strong>NLP research</strong> and scalable, production-ready systems that address local linguistic nuances, specifically <strong>Taglish code-switching</strong>.
                </p>
                <div class="flex flex-wrap gap-2">
                    <span class="text-[9px] font-black text-slate-500 bg-white border border-slate-200 px-3 py-1.5 rounded-lg uppercase tracking-wider">Technical Strategy</span>
                    <span class="text-[9px] font-black text-slate-500 bg-white border border-slate-200 px-3 py-1.5 rounded-lg uppercase tracking-wider">Consultancy</span>
                    <span class="text-[9px] font-black text-slate-500 bg-white border border-slate-200 px-3 py-1.5 rounded-lg uppercase tracking-wider">RAG Deployment</span>
                </div>
            </div>
        </div>

        <div class="group grid md:grid-cols-12 gap-8">
            <div class="md:col-span-4">
                <h4 class="text-2xl font-black text-slate-900 leading-tight mb-1">Project Technical Co-lead</h4>
                <p class="text-[12px] font-black text-sky-800 uppercase tracking-widest mb-1">iTANONG Project</p>
                <p class="text-[11px] font-bold text-slate-400 uppercase tracking-widest">2024</p>
            </div>
            
            <div class="md:col-span-8">
                <p class="text-[16px] text-slate-700 font-medium leading-relaxed mb-6">
                    Directed the R&D of <strong>RAG systems</strong> and led the <strong>benchmarking of Large Language Models (LLMs)</strong> for Philippine contexts. Supervised research teams to ensure the integration of advanced <strong>semantic parsing models</strong> aligned with organizational data accessibility goals.
                </p>
                <div class="flex flex-wrap gap-2">
                    <span class="text-[9px] font-black text-slate-500 bg-white border border-slate-200 px-3 py-1.5 rounded-lg uppercase tracking-wider">Team Supervision</span>
                    <span class="text-[9px] font-black text-slate-500 bg-white border border-slate-200 px-3 py-1.5 rounded-lg uppercase tracking-wider">LLM Benchmarking</span>
                    <span class="text-[9px] font-black text-slate-500 bg-white border border-slate-200 px-3 py-1.5 rounded-lg uppercase tracking-wider">R&D Direction</span>
                </div>
            </div>
        </div>

        <div class="group grid md:grid-cols-12 gap-8">
            <div class="md:col-span-4">
                <h4 class="text-2xl font-black text-slate-900 leading-tight mb-1">iTANONG Project Staff</h4>
                <p class="text-[12px] font-black text-slate-500 uppercase tracking-widest mb-1">Engineering & Dataset Curation</p>
                <p class="text-[11px] font-bold text-slate-300 uppercase tracking-widest">2022 — 2023</p>
            </div>
            
            <div class="md:col-span-8">
                <p class="text-[16px] text-slate-700 font-medium leading-relaxed mb-6">
                    Executed the technical groundwork for <strong>iTANONG</strong>, focusing on <strong>Semantic Parsing</strong> and <strong>Natural Language Interfaces to Databases (NLIDB)</strong>. Contributed to <strong>Parallel Corpus Curation</strong> and building the <strong>iTANONG-DS</strong> benchmark dataset for Philippine languages.
                </p>
                <div class="flex flex-wrap gap-2">
                    <span class="text-[9px] font-black text-slate-400 bg-white border border-slate-200 px-3 py-1.5 rounded-lg uppercase tracking-wider">Dataset Engineering</span>
                    <span class="text-[9px] font-black text-slate-400 bg-white border border-slate-200 px-3 py-1.5 rounded-lg uppercase tracking-wider">Text-to-SQL</span>
                    <span class="text-[9px] font-black text-slate-400 bg-white border border-slate-200 px-3 py-1.5 rounded-lg uppercase tracking-wider">Semantic Parsing</span>
                </div>
            </div>
        </div>

    </div>
</section>
```

# sections\sidebar.html

```html
<div class="space-y-12">
    <div>
        <h3 class="text-[10px] font-black text-slate-400 uppercase tracking-[0.3em] mb-6">Impact Metrics</h3>
        <div class="grid grid-cols-2 gap-4">
            <div class="p-5 bg-sky-700 rounded-2xl text-center shadow-lg shadow-sky-100">
                <span class="block text-2xl font-black text-white">15</span>
                <span class="text-[9px] font-black text-sky-200 uppercase">Citations</span>
            </div>
            <div class="p-5 bg-white border border-sky-100 rounded-2xl text-center shadow-sm">
                <span class="block text-2xl font-black text-sky-800">2</span>
                <span class="text-[9px] font-black text-slate-400 uppercase">h-index</span>
            </div>
        </div>
    </div>
    <div>
        <h3 class="text-[10px] font-black text-slate-400 uppercase tracking-[0.3em] mb-6">Persona</h3>
        <div class="flex flex-wrap gap-2 text-[11px] font-black">
            <span class="px-3 py-2 bg-white border border-slate-200 rounded-xl"><i class="fa-solid fa-badger-honey text-yellow-500"></i> Hufflepuff</span>
            <span class="px-3 py-2 bg-white border border-slate-200 rounded-xl"><i class="fa-solid fa-star text-pink-500"></i> Bloom</span>
            <span class="px-3 py-2 bg-white border border-slate-200 rounded-xl"><i class="fa-solid fa-bolt text-purple-500"></i> Swiftie</span>
            <span class="px-3 py-2 bg-white border border-slate-200 rounded-xl"><i class="fa-solid fa-table-tennis-paddle-ball text-sky-500"></i> Pickleballer</span>
        </div>
    </div>
    <div class="p-8 bg-slate-900 rounded-3xl text-white">
        <p class="text-[9px] font-black text-slate-500 uppercase tracking-[0.3em] mb-4">Academic Goal</p>
        <p class="text-sm font-bold italic leading-relaxed">"To wear the Sablay at UP"</p>
    </div>
</div>
```

