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
            background-repeat: no-repeat;
            color: #1e293b; 
        }
        .wide-container {
            background-color: rgba(255, 255, 255, 0.5); 
            backdrop-filter: blur(12px);
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.2);
            border: 1px solid rgba(255, 255, 255, 0.4);
        }
        .fade-in { animation: fadeIn 0.8s ease-out forwards; opacity: 0; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
    </style>
</head>
<body class="antialiased p-2 md:p-8 lg:p-12">
    <main class="max-w-7xl mx-auto rounded-3xl wide-container overflow-hidden">
        <div id="section-header" class="fade-in"></div>
        
        <div class="p-8 md:p-12 lg:p-16 max-w-5xl mx-auto">
            <div id="section-research" class="fade-in" style="animation-delay: 0.1s;"></div>
            
            <div id="section-projects" class="mt-16 fade-in" style="animation-delay: 0.2s;"></div>
            
            <div id="section-publications" class="mt-16 fade-in" style="animation-delay: 0.3s;"></div>
        </div>
    </main>

    <footer class="max-w-7xl mx-auto py-12 flex justify-between items-center px-6 text-slate-700 font-bold text-[10px] uppercase tracking-[0.4em]">
        <span>Aunhel John Adoptante • 2026</span>
        <div class="flex gap-8">
            <a href="https://github.com/aunheladoptante" target="_blank">Github</a>
            <a href="https://scholar.google.com/citations?user=s8GNZhEAAAAJ" target="_blank">Scholar</a>
        </div>
    </footer>

    <script>
        async function loadSection(id, file) {
            try {
                const response = await fetch(`sections/${file}`);
                const content = await response.text();
                const container = document.getElementById(id);
                container.innerHTML = content;

                // Manually execute scripts found in the injected HTML
                const scripts = container.querySelectorAll('script');
                scripts.forEach(oldScript => {
                    const newScript = document.createElement('script');
                    Array.from(oldScript.attributes).forEach(attr => newScript.setAttribute(attr.name, attr.value));
                    newScript.appendChild(document.createTextNode(oldScript.innerHTML));
                    oldScript.parentNode.replaceChild(newScript, oldScript);
                });
            } catch (err) { console.error(`Error loading ${file}`, err); }
        }

        window.addEventListener('DOMContentLoaded', () => {
            // Loading header, research, projects, and publications
            ['header', 'research', 'projects', 'publications'].forEach(s => 
                loadSection(`section-${s}`, `${s}.html`)
            );
        });

        // Toggle Visibility for BibTeX
        function toggleBib(id) {
            const el = document.getElementById(id);
            if (!el) return;
            el.classList.toggle('hidden');
            if (!el.classList.contains('hidden')) el.classList.add('fade-in');
        }

        // Copy Citation to Clipboard
        async function copyBib(event, id) {
            const text = document.getElementById(id).innerText;
            const btn = event.currentTarget;
            const originalHTML = btn.innerHTML;

            try {
                await navigator.clipboard.writeText(text);
                btn.innerHTML = '<i class="fa-solid fa-check text-emerald-500"></i> <span class="text-emerald-600">Copied!</span>';
                btn.classList.add('scale-105');
                
                setTimeout(() => {
                    btn.innerHTML = originalHTML;
                    btn.classList.remove('scale-105');
                }, 2000);
            } catch (err) {
                console.error('Failed to copy:', err);
            }
        }
    </script>
</body>
</html>
```

# sections\header.html

```html
<header class="p-10 md:p-14 lg:p-16 bg-sky-50/60 border-b border-sky-100 flex flex-col items-center text-center">
    <div class="max-w-5xl mx-auto">
        <div class="w-32 h-32 md:w-40 md:h-40 rounded-full border-4 border-white shadow-xl overflow-hidden ring-4 ring-sky-200 mx-auto mb-8">
            <img src="images/photo.jpeg" alt="Aunhel John Adoptante" class="w-full h-full object-cover">
        </div>

        <div class="inline-flex items-center gap-2 px-3 py-1 rounded-lg bg-sky-100 text-sky-900 text-[10px] font-black uppercase tracking-widest mb-4">
            DOST-ASTI Computer Software Division
        </div>
        <h1 class="text-4xl md:text-6xl font-black tracking-tighter text-slate-900 mb-3">
            Aunhel John Adoptante
        </h1>
        <div class="flex flex-wrap justify-center items-center gap-3 text-slate-700 font-bold text-xl md:text-2xl mb-4">
            <span>AI Researcher</span>
            <span class="text-slate-300">|</span>
            <span class="text-sky-800">NLP & LLM Specialist</span>
        </div>
        <p class="text-[10px] font-black text-slate-400 uppercase tracking-[0.5em] mb-10">
            FOCUS: RAG • CODE-SWITCHING • LANGUAGE MODELS
        </p>

        <div class="flex flex-wrap justify-center items-center gap-x-8 gap-y-4 pt-8 border-t border-sky-200/50">
            <div class="flex items-center gap-2 text-[13px] font-bold text-slate-700">
                <i class="fa-solid fa-location-dot text-sky-500"></i>
                <span>Quezon City, Philippines</span>
            </div>
            <a href="https://github.com/aunheladoptante" class="flex items-center gap-2 text-[13px] font-bold text-slate-700 hover:text-sky-600 transition">
                <i class="fa-brands fa-github text-sky-500"></i>
                <span>aunheladoptante</span>
            </a>
            <a href="mailto:engr.ajadoptante@gmail.com" class="flex items-center gap-2 text-[13px] font-bold text-slate-700 hover:text-sky-600 transition">
                <i class="fa-solid fa-envelope text-sky-500"></i>
                <span>engr.ajadoptante@gmail.com</span>
            </a>
            <a href="mailto:aunheljohn.adoptante@asti.dost.gov.ph" class="flex items-center gap-2 text-[13px] font-bold text-slate-700 hover:text-sky-600 transition">
                <i class="fa-solid fa-building text-sky-500"></i>
                <span>aunheljohn.adoptante@asti.dost.gov.ph</span>
            </a>
        </div>
    </div>
</header>
```

# sections\projects.html

```html
<section class="py-12">
    <div class="flex items-center gap-6 mb-16 px-2">
        <h3 class="text-[14px] font-black text-slate-400 uppercase tracking-[0.6em] whitespace-nowrap">
            Passion <span class="text-sky-600">&</span> Purpose
        </h3>
        <div class="w-full h-[1px] bg-slate-200/60"></div>
    </div>

    <style>
        .carousel-viewport {
            overflow: hidden;
            position: relative;
        }
        .carousel-track {
            display: flex;
            gap: 20px;
            transition: transform 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            will-change: transform;
        }
        .project-card {
            flex-shrink: 0;
            border-radius: 2rem;
            padding: 2rem;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .project-card:hover {
            transform: translateY(-4px);
            box-shadow: 0 20px 40px -12px rgba(0,0,0,0.12);
        }
        .carousel-btn {
            width: 44px;
            height: 44px;
            border-radius: 50%;
            border: 1.5px solid #e2e8f0;
            background: rgba(255,255,255,0.8);
            backdrop-filter: blur(8px);
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.2s ease;
            color: #475569;
            font-size: 18px;
            line-height: 1;
        }
        .carousel-btn:hover {
            background: #0ea5e9;
            border-color: #0ea5e9;
            color: white;
            box-shadow: 0 8px 20px -4px rgba(14,165,233,0.4);
        }
        .carousel-btn:disabled {
            opacity: 0.3;
            cursor: default;
            pointer-events: none;
        }
    </style>

    <div class="relative">
        <div class="carousel-viewport" id="carouselViewport">
            <div class="carousel-track" id="carouselTrack">

                <!-- GUNITA & UNAWA -->
                <div class="project-card bg-slate-900 border border-slate-800 shadow-2xl w-80 h-56 flex flex-col justify-between relative overflow-hidden">
                    <div class="absolute -top-16 -right-16 w-48 h-48 bg-sky-500/10 rounded-full blur-[60px]"></div>
                    <div class="relative z-10">
                        <span class="px-3 py-1 bg-sky-500/20 text-sky-400 text-[9px] font-black uppercase tracking-widest rounded-lg border border-sky-500/30">Active R&D</span>
                        <h4 class="text-2xl font-black text-white mt-4 tracking-tighter">GUNITA & UNAWA</h4>
                        <p class="text-slate-400 text-xs font-medium leading-relaxed mt-2">
                            Non-invasive BCI converting neural signals into text/speech for individuals with speech impairments.
                        </p>
                    </div>
                    <div class="flex items-center gap-3 text-[9px] font-black text-slate-600 uppercase tracking-widest relative z-10">
                        <span>Phase I: Signal</span>
                        <div class="w-6 h-px bg-slate-700"></div>
                        <span>Phase II: Intent</span>
                    </div>
                </div>

                <!-- Project Polaris -->
                <div class="project-card bg-white/60 backdrop-blur-md border border-amber-100 shadow-xl w-64 h-56 flex flex-col justify-between">
                    <div class="flex justify-between items-start">
                        <div class="w-10 h-10 bg-amber-50 rounded-2xl flex items-center justify-center">
                            <i class="fa-solid fa-star text-amber-500 text-sm"></i>
                        </div>
                        <span class="text-[9px] font-black text-slate-400 uppercase tracking-widest">Fundraiser</span>
                    </div>
                    <div>
                        <h4 class="text-xl font-black text-slate-900">Project: Polaris</h4>
                        <p class="text-slate-500 text-xs font-medium leading-relaxed mt-2">
                            Mantra-based merchandise for cervical cancer treatment advocacy.
                        </p>
                    </div>
                </div>

                <!-- Heart & Sole Run -->
                <div class="project-card bg-rose-50/60 border border-rose-100 w-52 h-56 flex flex-col justify-between">
                    <i class="fa-solid fa-heart-pulse text-rose-500 text-xl"></i>
                    <div>
                        <h4 class="text-lg font-black text-slate-900 leading-tight">Heart &<br>Sole Run</h4>
                        <p class="text-[10px] font-bold text-slate-400 uppercase tracking-wider mt-2">Charity Event Strategy</p>
                    </div>
                </div>

                <!-- iTANONG -->
                <div class="project-card bg-sky-50/60 border border-sky-100 w-64 h-56 flex flex-col justify-between">
                    <div class="w-10 h-10 bg-sky-100 rounded-2xl flex items-center justify-center">
                        <i class="fa-solid fa-database text-sky-600 text-sm"></i>
                    </div>
                    <div>
                        <span class="text-[9px] font-black text-sky-600 uppercase tracking-widest">NLP Research</span>
                        <h4 class="text-xl font-black text-slate-900 mt-1">iTANONG</h4>
                        <p class="text-slate-500 text-xs font-medium leading-relaxed mt-2">
                            Natural language interface to databases — Text-to-SQL for Philippine languages.
                        </p>
                    </div>
                </div>

                <!-- Strategy & Play -->
                <div class="project-card bg-white/60 backdrop-blur-md border border-slate-200 w-52 h-56 flex flex-col justify-between">
                    <div class="flex -space-x-2">
                        <div class="w-9 h-9 rounded-full bg-sky-500 flex items-center justify-center text-white text-[10px] font-black border-2 border-white shadow-sm">P</div>
                        <div class="w-9 h-9 rounded-full bg-amber-500 flex items-center justify-center text-white text-[10px] font-black border-2 border-white shadow-sm">T</div>
                    </div>
                    <div>
                        <h4 class="text-sm font-black text-slate-900 uppercase tracking-tight">Strategy & Play</h4>
                        <p class="text-[10px] text-slate-400 font-bold leading-tight mt-1">Pickleballer · Pokémon TCG</p>
                    </div>
                </div>

                <!-- RAG Systems -->
                <div class="project-card bg-slate-800 border border-slate-700 w-64 h-56 flex flex-col justify-between">
                    <div class="w-10 h-10 bg-slate-700 rounded-2xl flex items-center justify-center">
                        <i class="fa-solid fa-robot text-sky-400 text-sm"></i>
                    </div>
                    <div>
                        <span class="text-[9px] font-black text-sky-500 uppercase tracking-widest">Production</span>
                        <h4 class="text-xl font-black text-white mt-1">RAG Systems</h4>
                        <p class="text-slate-400 text-xs font-medium leading-relaxed mt-2">
                            Scalable retrieval-augmented generation for Taglish code-switched queries.
                        </p>
                    </div>
                </div>

            </div>
        </div>

        <div class="flex gap-2 mt-6">
            <button class="carousel-btn" id="btnPrev" onclick="carouselScroll(-1)" disabled>&#8592;</button>
            <button class="carousel-btn" id="btnNext" onclick="carouselScroll(1)">&#8594;</button>
        </div>
    </div>

    <script>
        (function () {
            const track = document.getElementById('carouselTrack');
            const viewport = document.getElementById('carouselViewport');
            const btnPrev = document.getElementById('btnPrev');
            const btnNext = document.getElementById('btnNext');
            const GAP = 20;
            let position = 0;

            function getStepSize() {
                const card = track.children[0];
                return card ? card.offsetWidth + GAP : 300;
            }

            function maxScroll() {
                return track.scrollWidth - viewport.offsetWidth;
            }

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

