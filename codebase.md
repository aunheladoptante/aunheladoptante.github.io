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
        .sidebar-border { border-left: 1px solid #e2e8f0; }
        @media (max-width: 1024px) { .sidebar-border { border-left: none; border-top: 1px solid #e2e8f0; } }
        .fade-in { animation: fadeIn 0.8s ease-out forwards; opacity: 0; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
    </style>
</head>
<body class="antialiased p-2 md:p-8 lg:p-12">
    <main class="max-w-7xl mx-auto rounded-3xl wide-container overflow-hidden">
        <div id="section-header" class="fade-in"></div>
        
        <div class="grid grid-cols-1 lg:grid-cols-12">
            <div class="lg:col-span-9 p-8 md:p-12 lg:p-16">
                <div id="section-research" class="fade-in"></div>
                <div id="section-projects" class="mt-24 fade-in" style="animation-delay: 0.1s;"></div>
                <div id="section-publications" class="mt-24 fade-in" style="animation-delay: 0.2s;"></div>
            </div>

            <aside class="lg:col-span-3 p-8 lg:p-12 sidebar-border bg-slate-50/20">
                <div id="section-sidebar" class="fade-in" style="animation-delay: 0.3s;"></div>
            </aside>
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
                document.getElementById(id).innerHTML = content;
            } catch (err) { console.error(`Error loading ${file}`, err); }
        }
        window.addEventListener('DOMContentLoaded', () => {
            loadSection('section-header', 'header.html');
            loadSection('section-research', 'research.html');
            loadSection('section-projects', 'projects.html');
            loadSection('section-publications', 'publications.html');
            loadSection('section-sidebar', 'sidebar.html');
        });

        // Toggle Visibility
        function toggleBib(id) {
            const el = document.getElementById(id);
            if (!el) return;
            el.classList.toggle('hidden');
            if (!el.classList.contains('hidden')) el.classList.add('fade-in');
        }

        // Copy to Clipboard with Feedback
        async function copyBib(event, id) {
            const text = document.getElementById(id).innerText;
            const btn = event.currentTarget;
            const originalHTML = btn.innerHTML;

            try {
                await navigator.clipboard.writeText(text);
                // Visual Feedback
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

        async function loadSection(id, file) {
            try {
                const response = await fetch(`sections/${file}`);
                const content = await response.text();
                document.getElementById(id).innerHTML = content;
            } catch (err) { console.error(`Error loading ${file}`, err); }
        }

        window.addEventListener('DOMContentLoaded', () => {
            ['header', 'research', 'projects', 'publications', 'sidebar'].forEach(s => 
                loadSection(`section-${s}`, `${s}.html`)
            );
        });
    </script>
</body>
</html>
```

# sections\header.html

```html
<header class="p-8 lg:p-12 bg-sky-50/60 flex flex-col lg:flex-row items-center gap-10 border-b border-sky-100">
    <div class="w-32 h-32 md:w-44 md:h-44 rounded-full border-4 border-white shadow-2xl overflow-hidden ring-4 ring-sky-200">
        <img src="images\photo.jpeg" alt="Aunhel John Adoptante" class="w-full h-full object-cover">
    </div>
    <div class="flex-1 text-center lg:text-left">
        <div class="inline-flex items-center gap-2 px-3 py-1.5 rounded-lg bg-sky-100 text-sky-900 text-[10px] font-black uppercase tracking-widest mb-4">
            DOST-ASTI COMPUTER SOFTWARE DIVISION
        </div>
        <h1 class="text-4xl md:text-6xl font-black tracking-tighter text-slate-900 mb-2">Aunhel John Adoptante</h1>
        <div class="flex flex-wrap justify-center lg:justify-start items-center gap-3 text-slate-700 font-bold text-xl">
            <span>AI Researcher</span><span class="text-slate-300">|</span><span class="text-sky-800">NLP & LLM Specialist</span>
        </div>
        <p class="text-[10px] font-black text-slate-500 mt-6 uppercase tracking-[0.4em]">FOCUS: RAG • CODE-SWITCHING • LANGUAGE MODELS</p>
    </div>
    <div class="bg-white border border-sky-100 rounded-3xl p-8 space-y-5 shadow-sm min-w-[340px]">
        <a href="mailto:engr.ajadoptante@gmail.com" class="flex items-center gap-4 group">
            <div class="w-10 h-10 rounded-xl bg-sky-100 flex items-center justify-center text-sky-800"><i class="fa-solid fa-location-dot"></i></div>
            <span class="text-sm font-black text-slate-800">Quezon City, Philippines</span>
        </a>
        <div class="flex items-center gap-4">
            <div class="w-10 h-10 rounded-xl bg-sky-100 flex items-center justify-center text-sky-800"><i class="fa-solid fa-user-tag"></i></div>
            <span class="text-sm font-black text-slate-800">Au / AJ <span class="text-slate-400 font-medium ml-2">(He/Him)</span></span>
        </div>
        <div class="pt-4 border-t border-slate-100 space-y-3">
            <a href="https://github.com/aunheladoptante" class="flex items-center gap-3 text-xs font-bold text-slate-700"><i class="fa-brands fa-github text-sky-700"></i> aunheladoptante</a>
            <a href="mailto:engr.ajadoptante@gmail.com" class="flex items-center gap-3 text-xs font-bold text-slate-700"><i class="fa-solid fa-envelope"></i>engr.ajadoptante@gmail.com</a>
            <!-- <div class="w-10 h-10 rounded-xl bg-sky-700 flex items-center justify-center text-white shadow-lg"><i class="fa-solid fa-envelope"></i>engr.ajadoptante@gmail.com</div></a> -->
            <!-- <div class="flex items-center gap-3 text-xs font-bold text-slate-700"><i class="fa-solid fa-location-dot text-sky-500"></i> Manila, PH</div> -->
        </div>
    </div>
</header>
```

# sections\projects.html

```html
<section>
    <div class="flex items-center gap-4 mb-12"><h3 class="text-[11px] font-black text-slate-400 uppercase tracking-[0.3em] whitespace-nowrap">Selected Initiatives</h3><div class="w-full h-[1px] bg-slate-100"></div></div>
    <div class="grid md:grid-cols-2 gap-8">
        <div class="p-8 bg-slate-50/50 border border-slate-100 rounded-3xl">
            <h4 class="text-xl font-black text-slate-900 mb-2">Project: Polaris</h4>
            <p class="text-[13px] text-slate-700 font-medium">Orchestrated a community-driven fundraiser managing design, logistics, and medical support initiatives.</p>
        </div>
        <div class="p-8 bg-slate-50/50 border border-slate-100 rounded-3xl">
            <h4 class="text-xl font-black text-slate-900 mb-2">Heart & Sole Run</h4>
            <p class="text-[13px] text-slate-700 font-medium">Led branding and registration strategy for a virtual charity run supporting cancer treatment.</p>
        </div>
    </div>
</section>
```

# sections\publications.html

```html
<section>
    <div class="flex items-center gap-4 mb-12">
        <h3 class="text-[11px] font-black text-slate-400 uppercase tracking-[0.3em] whitespace-nowrap">Academic Publications</h3>
        <div class="w-full h-[1px] bg-slate-100"></div>
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
    <div class="flex items-center gap-4 mb-12">
        <h3 class="text-[11px] font-black text-slate-400 uppercase tracking-[0.3em] whitespace-nowrap">Research Narrative</h3>
        <div class="w-full h-[1px] bg-slate-100"></div>
    </div>
    
    <div class="space-y-16">

        <div class="group">
            <div class="mb-4">
                <h4 class="text-2xl font-black text-slate-900 leading-tight">AI Technical Lead and Consultant</h4>
                <p class="text-[11px] font-black text-sky-800 uppercase tracking-widest mt-1">
                    2025 - Present • DOST-ASTI AI Initiatives
                </p>
            </div>
            
            <p class="text-[15px] text-slate-700 font-medium leading-relaxed mb-6">
                Currently serving as a <strong>Technical Lead and Consultant</strong> for multiple AI projects, providing strategic oversight on the implementation of <strong>Retrieval-Augmented Generation (RAG)</strong> systems. I focus on ensuring that <strong>NLP research</strong> translates into scalable, production-ready systems that address local linguistic nuances like <strong>Taglish code-switching</strong>.
            </p><div class="flex flex-wrap gap-2 mt-6">
                <span class="text-[10px] font-black text-slate-600 border border-slate-200 px-3 py-1 rounded uppercase">Technical Strategy</span>
                <span class="text-[10px] font-black text-slate-600 border border-slate-200 px-3 py-1 rounded uppercase">Consultancy</span>
            </div>
        </div>

        <div class="group">
            <div class="mb-4">
                <h4 class="text-2xl font-black text-slate-900 leading-tight">Project Technical Co-lead</h4>
                <p class="text-[11px] font-black text-sky-700 uppercase tracking-widest mt-1">
                    2024 • iTANONG Project
                </p>
            </div>
            
            <p class="text-[15px] text-slate-700 font-medium leading-relaxed mb-6">
                In my role as <strong>Project Technical Co-lead</strong>, I directed the research and development of <strong>RAG systems</strong> and led the <strong>benchmarking of Large Language Models (LLMs)</strong> for Philippine contexts. I supervised research teams to ensure the integration of advanced <strong>semantic parsing models</strong> aligned with organizational data accessibility goals, moving the project toward production-level technical stability.
            </p>

            <div class="flex flex-wrap gap-2 mt-6">
                <span class="text-[10px] font-black text-slate-600 border border-slate-200 px-3 py-1 rounded uppercase">Team Supervision</span>
                <span class="text-[10px] font-black text-slate-600 border border-slate-200 px-3 py-1 rounded uppercase">LLM Benchmarking</span>
                <span class="text-[10px] font-black text-slate-600 border border-slate-200 px-3 py-1 rounded uppercase">RAG Systems Research</span>
            </div>
        </div>

        <div class="group">
            <div class="mb-4">
                <h4 class="text-2xl font-black text-slate-900 leading-tight">iTANONG Project Staff</h4>
                <p class="text-[11px] font-black text-slate-500 uppercase tracking-widest mt-1">
                    2022 — 2023 • Engineering & Dataset Curation
                </p>
            </div>
            
            <p class="text-[15px] text-slate-700 font-medium leading-relaxed mb-6">
                Executed the technical groundwork for <strong>iTANONG</strong>, focusing on <strong>Semantic Parsing</strong> and <strong>Natural Language Interfaces to Databases (NLIDB)</strong>. My work centered on <strong>Parallel Corpus Curation</strong> and building the <strong>iTANONG-DS</strong> benchmark dataset, which serves as the foundation for downstream NLP tasks in Philippine languages.
            </p><div class="flex flex-wrap gap-2 mt-6">
                <span class="text-[10px] font-black text-slate-500 border border-slate-200 px-3 py-1 rounded uppercase">Dataset Engineering</span>
                <span class="text-[10px] font-black text-slate-500 border border-slate-200 px-3 py-1 rounded uppercase">Text-to-SQL</span>
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

