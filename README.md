<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Md Zuber - Engineering Impact Dashboard</title>
<script src="https://cdn.tailwindcss.com"></script>
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">
<style>
body { font-family: 'Plus Jakarta Sans', sans-serif; background-color: #FAF9F6; color: #1C1917; }
.chart-container { position: relative; width: 100%; max-width: 600px; margin-left: auto; margin-right: auto; height: 320px; max-height: 400px; }
@media (min-width: 768px) { .chart-container { height: 360px; } }
.glass-card { background: #FFFFFF; border: 1px solid #E7E5E4; box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.05), 0 2px 4px -1px rgba(0, 0, 0, 0.03); border-radius: 1rem; }
.nav-btn.active { background-color: #D97706; color: #FFFFFF; border-color: #D97706; }
.nav-btn { background-color: transparent; color: #57534E; border: 1px solid #D6D3D1; transition: all 0.2s ease; }
.nav-btn:hover:not(.active) { background-color: #F5F5F4; }
.arch-btn.active { border-left: 4px solid #D97706; background-color: #FFFBEB; font-weight: 700; color: #B45309; }
.arch-btn { border-left: 4px solid transparent; transition: all 0.2s ease; }
.fade-in { animation: fadeIn 0.4s ease-in-out; }
@keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
::-webkit-scrollbar { width: 8px; }
::-webkit-scrollbar-track { background: #F5F5F4; }
::-webkit-scrollbar-thumb { background: #D6D3D1; border-radius: 4px; }
::-webkit-scrollbar-thumb:hover { background: #A8A29E; }
</style>
</head>
<body class="antialiased min-h-screen flex flex-col">

<!-- Chosen Palette: Warm Neutrals (Alabaster, Stone) with Amber (#D97706) and Teal (#0D9488) Accents -->
<!-- Application Structure Plan: A dashboard layout featuring a persistent header and three primary functional views (Performance Metrics, System Architectures, Career Timeline). This structure is chosen to break down complex technical achievements into digestible, interactive segments. The default view focuses heavily on the highlighted 'Latency Reduction' and quantitative impact, directly addressing the core of the provided text. -->
<!-- Visualization & Content Choices: 
1. Latency & Processing Speed -> Goal: Compare -> Method: Bar Charts (Chart.js) -> Interaction: Hover tooltips -> Justification: Clearest way to show before/after optimization metrics.
2. Architecture Details -> Goal: Organize -> Method: Master-Detail Split View (HTML/Tailwind) -> Interaction: Click list to update detail pane -> Justification: Avoids overwhelming text walls, encourages active exploration of the 4 complex systems.
-->
<!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->

<header class="bg-white border-b border-stone-200 sticky top-0 z-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-6 flex flex-col md:flex-row justify-between items-center gap-4">
        <div>
            <h1 class="text-3xl font-extrabold text-stone-900 tracking-tight">Md Zuber</h1>
            <p class="text-sm font-medium text-amber-600 uppercase tracking-widest mt-1">Senior Backend Engineer & Architect</p>
        </div>
        <div class="flex gap-3 overflow-x-auto w-full md:w-auto pb-2 md:pb-0">
            <button onclick="switchTab('metrics')" id="btn-metrics" class="nav-btn active px-5 py-2.5 rounded-full text-sm font-bold whitespace-nowrap">📊 Performance Impact</button>
            <button onclick="switchTab('architecture')" id="btn-architecture" class="nav-btn px-5 py-2.5 rounded-full text-sm font-bold whitespace-nowrap">🏗️ System Architectures</button>
            <button onclick="switchTab('timeline')" id="btn-timeline" class="nav-btn px-5 py-2.5 rounded-full text-sm font-bold whitespace-nowrap">⏱️ Experience Journey</button>
        </div>
    </div>
</header>

<main class="flex-grow max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8 w-full">

    <div id="view-metrics" class="fade-in block">
        <div class="mb-8 max-w-3xl">
            <h2 class="text-2xl font-bold text-stone-800 mb-3">Quantifiable Engineering Impact</h2>
            <p class="text-stone-600 leading-relaxed">
                This section visualizes the direct performance improvements and scale managed across major enterprise systems. It highlights the <strong>25% reduction in inter-service latency</strong> achieved by transitioning to reactive microservices (Spring WebFlux), alongside critical throughput and settlement optimization metrics.
            </p>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 mb-8">
            <div class="glass-card p-6 flex flex-col">
                <h3 class="text-lg font-bold text-stone-800 mb-1">Latency Reduction</h3>
                <p class="text-xs text-stone-500 mb-6 font-mono">J.P. Morgan · Spring WebFlux vs Blocking REST</p>
                <div class="chart-container flex-grow">
                    <canvas id="latencyChart"></canvas>
                </div>
                <p class="text-sm text-stone-600 mt-4 text-center">Achieved a <span class="font-bold text-amber-600">25% drop</span> in p99 inter-service latency.</p>
            </div>

            <div class="glass-card p-6 flex flex-col">
                <h3 class="text-lg font-bold text-stone-800 mb-1">Settlement Batch Processing</h3>
                <p class="text-xs text-stone-500 mb-6 font-mono">VISA RTP · Parallel Stream Processing</p>
                <div class="chart-container flex-grow">
                    <canvas id="processingChart"></canvas>
                </div>
                <p class="text-sm text-stone-600 mt-4 text-center">Execution time reduced by <span class="font-bold text-teal-600">~67%</span>, unblocking SLA commitments.</p>
            </div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
            <div class="glass-card p-6 text-center">
                <div class="text-4xl font-extrabold text-amber-600 mb-2">300k+</div>
                <div class="text-sm font-bold text-stone-800 uppercase tracking-wider">Daily Events</div>
                <div class="text-xs text-stone-500 mt-2">Processed with 99.9% uptime on AWS (ECS, SQS, S3).</div>
            </div>
            <div class="glass-card p-6 text-center">
                <div class="text-4xl font-extrabold text-teal-600 mb-2">50k+</div>
                <div class="text-sm font-bold text-stone-800 uppercase tracking-wider">Daily Settlements</div>
                <div class="text-xs text-stone-500 mt-2">Reconciled with ~99.99% accuracy for VISA RTP.</div>
            </div>
            <div class="glass-card p-6 text-center">
                <div class="text-4xl font-extrabold text-stone-800 mb-2">12 min</div>
                <div class="text-sm font-bold text-stone-800 uppercase tracking-wider">Deployment Cycle</div>
                <div class="text-xs text-stone-500 mt-2">Reduced from 40 mins via Jenkins CI/CD & Terraform.</div>
            </div>
        </div>
    </div>

    <div id="view-architecture" class="fade-in hidden">
        <div class="mb-8 max-w-3xl">
            <h2 class="text-2xl font-bold text-stone-800 mb-3">Architectural System Designs</h2>
            <p class="text-stone-600 leading-relaxed">
                Explore the high-level and low-level design patterns implemented across various domains. Select a project from the menu to dive into its architectural pattern, technology stack, and core engineering solutions.
            </p>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 h-[600px]">
            <div class="lg:col-span-4 glass-card overflow-hidden flex flex-col">
                <div class="p-4 border-b border-stone-200 bg-stone-50">
                    <h3 class="font-bold text-stone-800 text-sm uppercase tracking-wider">Select System</h3>
                </div>
                <div class="overflow-y-auto flex-grow p-2" id="arch-list">
                </div>
            </div>

            <div class="lg:col-span-8 glass-card p-8 overflow-y-auto flex flex-col relative">
                <div id="arch-detail-content" class="fade-in">
                </div>
            </div>
        </div>
    </div>

    <div id="view-timeline" class="fade-in hidden">
         <div class="mb-8 max-w-3xl">
            <h2 class="text-2xl font-bold text-stone-800 mb-3">Professional Experience Journey</h2>
            <p class="text-stone-600 leading-relaxed">
                A chronological overview of roles, responsibilities, and key environments demonstrating a trajectory from high-volume transaction processing to cloud-native architectural design.
            </p>
        </div>

        <div class="glass-card p-8 relative">
            <div class="absolute left-8 md:left-1/2 top-8 bottom-8 w-0.5 bg-stone-200 transform md:-translate-x-1/2"></div>
            
            <div class="relative flex flex-col md:flex-row items-center mb-16">
                <div class="hidden md:flex w-1/2 justify-end pr-8 text-right">
                    <div>
                        <h4 class="text-lg font-bold text-stone-800">Deloitte — Consultant</h4>
                        <p class="text-sm text-amber-600 font-bold mb-2">Client: J.P. Morgan</p>
                        <p class="text-sm text-stone-600">Architected cloud-native event-processing pipelines handling 300k daily events. Reduced latency via Spring WebFlux.</p>
                    </div>
                </div>
                <div class="absolute left-8 md:left-1/2 w-4 h-4 bg-amber-500 border-4 border-white rounded-full transform -translate-x-1/2 mt-1 md:mt-0"></div>
                <div class="md:hidden pl-16 w-full">
                    <h4 class="text-lg font-bold text-stone-800">Deloitte — Consultant</h4>
                    <p class="text-sm text-amber-600 font-bold mb-1">Oct 2024 – Present</p>
                    <p class="text-sm text-stone-600 mb-2">Client: J.P. Morgan</p>
                </div>
                <div class="hidden md:flex w-1/2 pl-8">
                    <div class="bg-stone-50 px-4 py-2 rounded-lg border border-stone-200 text-sm font-bold text-stone-500 font-mono">
                        Oct 2024 – Present
                    </div>
                </div>
            </div>

            <div class="relative flex flex-col md:flex-row items-center">
                <div class="hidden md:flex w-1/2 justify-end pr-8">
                    <div class="bg-stone-50 px-4 py-2 rounded-lg border border-stone-200 text-sm font-bold text-stone-500 font-mono">
                        Mar 2022 – Sep 2024
                    </div>
                </div>
                <div class="absolute left-8 md:left-1/2 w-4 h-4 bg-teal-500 border-4 border-white rounded-full transform -translate-x-1/2 mt-1 md:mt-0"></div>
                <div class="md:hidden pl-16 w-full">
                    <h4 class="text-lg font-bold text-stone-800">Infosys — Senior Systems Engineer</h4>
                    <p class="text-sm text-teal-600 font-bold mb-1">Mar 2022 – Sep 2024</p>
                    <p class="text-sm text-stone-600 mb-2">Client: VISA</p>
                </div>
                <div class="hidden md:flex w-1/2 pl-8">
                    <div>
                        <h4 class="text-lg font-bold text-stone-800">Infosys — Senior Systems Engineer</h4>
                        <p class="text-sm text-teal-600 font-bold mb-2">Client: VISA</p>
                        <p class="text-sm text-stone-600">Owned core reconciliation modules for RTP system. Scaled Kafka event pipelines. Reduced execution time by 67%.</p>
                    </div>
                </div>
            </div>
        </div>
    </div>

</main>

<script>
    const state = {
        currentView: 'metrics',
        chartsInitialized: false,
        latencyChartInstance: null,
        processingChartInstance: null,
        activeProject: 'jpmorgan'
    };

    const projectsData = {
        jpmorgan: {
            icon: '🏦',
            title: 'J.P. Morgan UPI Payment System v2',
            pattern: 'Lean Modular Monolith (9 Modules)',
            tech: ['Java 21', 'Spring Boot 3.2', 'PostgreSQL', 'Redis', 'PhonePe UPI 2.0'],
            highlights: [
                'Implemented <code class="bg-stone-100 px-1 rounded text-amber-700 text-xs font-mono">@Transactional(SERIALIZABLE)</code> settlement engine for ACID-compliant ledger debits/credits.',
                'Replaced Kafka with 5 named <code class="bg-stone-100 px-1 rounded text-amber-700 text-xs font-mono">Spring ApplicationEvents</code> for atomic internal communication.',
                'Built an Idempotency layer (Redis 24h TTL) & SHA256 webhook checksum verification to prevent double-charges and spoofing.',
                'Automated EOD reconciliation via <code class="bg-stone-100 px-1 rounded text-amber-700 text-xs font-mono">@Scheduled</code> cron jobs matching against PSP reports.'
            ]
        },
        getwork: {
            icon: '👷',
            title: 'GetWork - Gig Economy Platform',
            pattern: 'Two-sided Marketplace & Wallet System',
            tech: ['Spring Boot 3.2', 'Firebase Cloud Functions', 'React Native 0.81', 'Google Maps API'],
            highlights: [
                'Designed a multi-tier wallet economics system utilizing atomic transactions for 10% platform commission auto-deductions.',
                'Implemented Haversine formula-based geospatial matching and geohash route caching.',
                'Built dynamic pricing algorithms accounting for base pay, travel allowance, and worker count per Tier 1/2 cities.',
                'Engineered a 6-stage interactive state machine for worker lifecycles (Open ➔ In-Progress ➔ Completed).'
            ]
        },
        visa: {
            icon: '💳',
            title: 'VISA Real-Time Settlement Engine',
            pattern: 'Event-Driven High-Throughput Pipeline',
            tech: ['Java', 'Spring Boot', 'Apache Kafka'],
            highlights: [
                'Owned reconciliation modules for RTP systems processing 50K+ daily transactions.',
                'Engineered Kafka consumer groups with exactly-once delivery semantics for customer notifications.',
                'Implemented parallel stream processing and connection pooling to crush SLA resolution times from 2 hours to 15 mins.'
            ]
        },
        trackr: {
            icon: '🤖',
            title: 'TrackR v2 - AI Finance App',
            pattern: 'Offline-first Mobile Application',
            tech: ['Expo', 'Zustand', 'MMKV', 'Claude Vision API', 'Firebase'],
            highlights: [
                'Integrated Claude 3.5 Sonnet Vision API via secure Cloud Functions for instant AI receipt scanning and NLP categorization.',
                'Built an offline-first sync queue using MMKV for immediate UI updates with background Firestore sync.',
                'Developed high-performance UI using FlashList (60fps) and Reanimated gesture interactions.'
            ]
        }
    };

    function switchTab(viewId) {
        document.getElementById('view-' + state.currentView).classList.add('hidden');
        document.getElementById('btn-' + state.currentView).classList.remove('active');
        
        state.currentView = viewId;
        
        document.getElementById('view-' + viewId).classList.remove('hidden');
        document.getElementById('btn-' + viewId).classList.add('active');

        if (viewId === 'metrics' && !state.chartsInitialized) {
            initCharts();
            state.chartsInitialized = true;
        }
    }

    function initCharts() {
        Chart.defaults.font.family = "'Plus Jakarta Sans', sans-serif";
        Chart.defaults.color = '#78716C';

        const ctxLatency = document.getElementById('latencyChart').getContext('2d');
        state.latencyChartInstance = new Chart(ctxLatency, {
            type: 'bar',
            data: {
                labels: ['Blocking REST API', 'Reactive WebFlux'],
                datasets: [{
                    label: 'p99 Latency (Relative %)',
                    data: [100, 75],
                    backgroundColor: ['#E7E5E4', '#D97706'],
                    borderRadius: 6,
                    barThickness: 60
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: { display: false },
                    tooltip: {
                        callbacks: {
                            label: function(context) { return context.raw + '% relative time'; }
                        }
                    }
                },
                scales: {
                    y: { beginAtZero: true, max: 110, grid: { color: '#F5F5F4' }, ticks: { stepSize: 25 } },
                    x: { grid: { display: false } }
                }
            }
        });

        const ctxProcessing = document.getElementById('processingChart').getContext('2d');
        state.processingChartInstance = new Chart(ctxProcessing, {
            type: 'bar',
            data: {
                labels: ['Legacy Sequential', 'Parallel Streams'],
                datasets: [{
                    label: 'Execution Time (Minutes)',
                    data: [6, 2],
                    backgroundColor: ['#E7E5E4', '#0D9488'],
                    borderRadius: 6,
                    barThickness: 60
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: { display: false },
                    tooltip: {
                        callbacks: {
                            label: function(context) { return context.raw + ' Minutes'; }
                        }
                    }
                },
                scales: {
                    y: { beginAtZero: true, max: 7, grid: { color: '#F5F5F4' }, title: { display: true, text: 'Minutes' } },
                    x: { grid: { display: false } }
                }
            }
        });
    }

    function renderProjectList() {
        const listContainer = document.getElementById('arch-list');
        listContainer.innerHTML = '';
        
        for (const [key, project] of Object.entries(projectsData)) {
            const btn = document.createElement('button');
            btn.className = `w-full text-left px-4 py-4 rounded-lg mb-1 arch-btn ${key === state.activeProject ? 'active' : ''}`;
            btn.innerHTML = `<div class="flex items-center gap-3"><span class="text-2xl">${project.icon}</span><span class="truncate">${project.title}</span></div>`;
            btn.onclick = () => selectProject(key);
            listContainer.appendChild(btn);
        }
    }

    function selectProject(key) {
        state.activeProject = key;
        renderProjectList();
        renderProjectDetail();
    }

    function renderProjectDetail() {
        const detailContainer = document.getElementById('arch-detail-content');
        const project = projectsData[state.activeProject];
        
        detailContainer.innerHTML = '';
        detailContainer.classList.remove('fade-in');
        void detailContainer.offsetWidth; 
        detailContainer.classList.add('fade-in');

        const techTags = project.tech.map(t => `<span class="bg-stone-100 text-stone-600 border border-stone-200 px-3 py-1 rounded-full text-xs font-bold font-mono shadow-sm">${t}</span>`).join('');
        
        const highlightsHtml = project.highlights.map(h => `<li class="flex items-start gap-3 text-stone-700 leading-relaxed mb-4"><span class="text-amber-500 mt-1">▹</span><span>${h}</span></li>`).join('');

        detailContainer.innerHTML = `
            <div class="flex items-center gap-4 mb-6">
                <div class="w-16 h-16 rounded-2xl bg-gradient-to-br from-stone-100 to-stone-200 flex items-center justify-center text-3xl shadow-inner border border-stone-300">
                    ${project.icon}
                </div>
                <div>
                    <h2 class="text-2xl font-extrabold text-stone-900 leading-tight">${project.title}</h2>
                    <p class="text-sm font-bold text-amber-600 uppercase tracking-widest mt-1">${project.pattern}</p>
                </div>
            </div>
            
            <div class="mb-8">
                <h4 class="text-xs font-bold text-stone-400 uppercase tracking-widest mb-3">Technology Stack</h4>
                <div class="flex flex-wrap gap-2">
                    ${techTags}
                </div>
            </div>

            <div>
                <h4 class="text-xs font-bold text-stone-400 uppercase tracking-widest mb-4">Architectural Highlights</h4>
                <ul class="pl-1">
                    ${highlightsHtml}
                </ul>
            </div>
        `;
    }

    window.onload = () => {
        initCharts();
        state.chartsInitialized = true;
        renderProjectList();
        renderProjectDetail();
    };

</script>
</body>
</html>
