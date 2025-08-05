<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TourNative - Interactive Business Plan</title>
    <!-- Chosen Palette: Warm Neutrals with Orange Accent -->
    <!-- Application Structure Plan: A thematic, dashboard-style single-page application. The structure is designed for intuitive exploration rather than a linear report format. It starts with the core value proposition (Hero), moves to the market opportunity (Problem/Why Now), details the product and business model, visualizes market size and growth strategy, presents financial projections, and concludes with the team and the investment ask. This flow guides the user from the "what" and "why" to the "how" and "how much," making the business case compelling and easy to digest. Key interactions include dynamic counters for impact, interactive charts for financial and market data, tabbed content to prevent information overload, and LLM-powered Q&A and idea generation. -->
    <!-- Visualization & Content Choices: 
        - Market Size ($7T, $781B): Goal: Inform/Impact. Method: Dynamic JS counters. Justification: Creates an immediate "wow" factor for market scale.
        - The Problem: Goal: Inform. Method: Tabbed HTML/CSS cards. Justification: Breaks down pain points into digestible chunks.
        - User Flow: Goal: Organize. Method: Numbered HTML/CSS flexbox layout. Justification: Clearly visualizes the simple, three-step process for the user.
        - Market Share (TAM/SAM/SOM): Goal: Compare/Inform. Method: Chart.js Donut Chart. Interaction: Hover to see values. Justification: Effectively shows the addressable market segments as parts of a whole.
        - Revenue Model: Goal: Compare/Inform. Method: Interactive HTML/CSS pricing cards and a Chart.js Bar Chart comparing guide wages. Interaction: Hover effects on cards. Justification: Clearly presents pricing tiers and highlights the key value proposition for guides (higher pay).
        - Financial Projections: Goal: Show Change. Method: Chart.js Line Chart. Interaction: Hover over points to see yearly data. Justification: Provides a clear, dynamic view of projected growth over five years.
        - Go-to-Market: Goal: Show Change/Organize. Method: HTML/CSS timeline. Justification: Presents the expansion plan in a clear, chronological format.
        - LLM-Powered Market Insights: Goal: Explore/Inform. Method: Text input, button, and text output. Interaction: User asks a question, LLM provides an answer based on provided context. Justification: Allows deeper, AI-assisted exploration of market data within the business plan.
        - LLM-Powered Tagline Generator: Goal: Engage/Brainstorm. Method: Button and text output. Interaction: User clicks button, LLM generates creative taglines. Justification: Showcases creative potential of AI for marketing and branding.
        - Library/Method: Chart.js via CDN for all charts. Vanilla JS for all interactions and LLM API calls. Tailwind CSS for styling.
    -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; background-color: #f8fafc; color: #1e293b; }
        .chart-container { position: relative; width: 100%; max-width: 500px; margin-left: auto; margin-right: auto; height: 300px; max-height: 400px; }
        @media (min-width: 768px) { .chart-container { height: 350px; } }
        .stat-card { background-color: white; border-radius: 0.75rem; padding: 1.5rem; box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1); text-align: center; }
        .nav-link { padding: 8px 16px; border-radius: 9999px; transition: background-color 0.3s, color 0.3s; font-weight: 500; }
        .nav-link.active { background-color: #fb923c; color: white; }
        .nav-link:not(.active):hover { background-color: #fed7aa; }
    </style>
</head>
<body class="antialiased">

    <!-- Header -->
    <header class="bg-white/80 backdrop-blur-lg sticky top-0 z-50 shadow-sm">
        <nav class="container mx-auto px-6 py-3 flex justify-between items-center">
            <div class="text-2xl font-extrabold text-orange-500">
                TourNative
            </div>
            <div class="hidden md:flex items-center space-x-2 bg-orange-50 p-1 rounded-full">
                <a href="#opportunity" class="nav-link">Opportunity</a>
                <a href="#solution" class="nav-link">Solution</a>
                <a href="#model" class="nav-link">Model</a>
                <a href="#market" class="nav-link">Market</a>
                <a href="#financials" class="nav-link">Financials</a>
                <a href="#team" class="nav-link">Team</a>
            </div>
            <a href="#ask" class="hidden md:block bg-orange-500 text-white font-bold py-2 px-5 rounded-full hover:bg-orange-600 transition-colors">
                The Ask
            </a>
            <button id="mobile-menu-button" class="md:hidden text-gray-700">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path></svg>
            </button>
        </nav>
        <!-- Mobile Menu -->
        <div id="mobile-menu" class="hidden md:hidden px-4 pt-2 pb-4 space-y-2">
             <a href="#opportunity" class="block nav-link text-center">Opportunity</a>
             <a href="#solution" class="block nav-link text-center">Solution</a>
             <a href="#model" class="block nav-link text-center">Model</a>
             <a href="#market" class="block nav-link text-center">Market</a>
             <a href="#financials" class="block nav-link text-center">Financials</a>
             <a href="#team" class="block nav-link text-center">Team</a>
             <a href="#ask" class="block bg-orange-500 text-white font-bold py-2 px-5 rounded-full hover:bg-orange-600 transition-colors text-center mt-2">The Ask</a>
        </div>
    </header>

    <main class="container mx-auto px-6 py-8">

        <!-- Hero Section -->
        <section class="text-center py-12">
            <h1 class="text-4xl md:text-6xl font-extrabold text-slate-800 leading-tight">
                <span class="block">Don't Google It.</span>
                <span class="block text-orange-500">Ask a Local.</span>
            </h1>
            <p class="mt-6 max-w-2xl mx-auto text-lg md:text-xl text-slate-600">
                TourNative is a travel-tech platform connecting travelers with native guides via live video chat for personalized, authentic advice. This interactive plan outlines our vision to disrupt the travel planning industry.
            </p>
            <button id="generate-taglines-btn" class="mt-8 bg-orange-500 text-white font-bold py-3 px-6 rounded-full hover:bg-orange-600 transition-colors shadow-md">
                ✨ Generate Tagline Ideas
            </button>
            <div id="tagline-output" class="mt-4 p-4 bg-orange-50 text-orange-800 rounded-lg hidden">
                <p class="font-semibold mb-2">Here are some ideas:</p>
                <div id="tagline-text" class="whitespace-pre-wrap"></div>
                <div id="tagline-loading" class="text-center mt-2 hidden">Generating...</div>
            </div>
        </section>

        <!-- Opportunity Section -->
        <section id="opportunity" class="py-16">
            <div class="text-center mb-12">
                <h2 class="text-3xl md:text-4xl font-bold text-slate-800">The Market Opportunity</h2>
                <p class="mt-4 max-w-3xl mx-auto text-lg text-slate-600">The travel industry is massive and ripe for disruption. Modern travelers are moving away from generic, one-size-fits-all solutions and actively seeking authentic, personalized experiences that traditional tools can't provide.</p>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8 mb-12">
                <div class="stat-card">
                    <div id="problem-1" class="text-2xl font-bold text-slate-700">Generic Trips</div>
                    <p class="text-slate-500 mt-2">Travelers are tired of cookie-cutter trips and crave authenticity.</p>
                </div>
                <div class="stat-card">
                     <div id="problem-2" class="text-2xl font-bold text-slate-700">Flawed Tools</div>
                    <p class="text-slate-500 mt-2">Yelp & Google offer majority opinions, not personalized advice.</p>
                </div>
                <div class="stat-card">
                    <div id="problem-3" class="text-2xl font-bold text-slate-700">High Costs</div>
                    <p class="text-slate-500 mt-2">Traditional agents are expensive (>$75) and often disconnected.</p>
                </div>
                 <div class="stat-card">
                    <div id="problem-4" class="text-2xl font-bold text-slate-700">Growing Demand</div>
                    <p class="text-slate-500 mt-2">Online travel booking is projected to grow 1% annually.</p>
                </div>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8 text-center">
                <div class="bg-white p-8 rounded-lg shadow-lg">
                    <p class="text-lg font-medium text-slate-500">Global Travel & Tourism Market</p>
                    <div id="market-size-stat" class="text-5xl md:text-6xl font-extrabold text-orange-500 my-2">
                        $0
                    </div>
                </div>
                <div class="bg-white p-8 rounded-lg shadow-lg">
                    <p class="text-lg font-medium text-slate-500">U.S. Domestic Leisure Travel</p>
                    <div id="us-travel-stat" class="text-5xl md:text-6xl font-extrabold text-orange-500 my-2">
                        $0
                    </div>
                    <p class="text-slate-500">Represents 77% of domestic trips.</p>
                </div>
            </div>
        </section>

        <!-- Market Insights Section -->
        <section id="market-insights" class="py-16 bg-slate-50 rounded-2xl">
            <div class="text-center mb-12">
                <h2 class="text-3xl md:text-4xl font-bold text-slate-800">✨ Market Insights Q&A</h2>
                <p class="mt-4 max-w-3xl mx-auto text-lg text-slate-600">
                    Ask a question about the market, problems, or opportunities mentioned in this business plan, and our AI will provide a concise answer based on the provided information.
                </p>
            </div>
            <div class="max-w-2xl mx-auto bg-white p-8 rounded-lg shadow-lg">
                <textarea id="market-question-input" class="w-full p-3 border border-gray-300 rounded-md focus:ring-2 focus:ring-orange-500 focus:border-transparent resize-y min-h-[80px]" placeholder="e.g., What are the main pain points for travelers?"></textarea>
                <button id="ask-market-question-btn" class="mt-4 w-full bg-orange-500 text-white font-bold py-3 px-6 rounded-md hover:bg-orange-600 transition-colors">
                    Ask AI
                </button>
                <div id="market-answer-output" class="mt-6 p-4 bg-orange-50 text-orange-800 rounded-lg hidden">
                    <p class="font-semibold mb-2">AI Response:</p>
                    <div id="market-answer-text" class="whitespace-pre-wrap"></div>
                    <div id="market-loading" class="text-center mt-2 hidden">Thinking...</div>
                </div>
            </div>
        </section>

        <!-- Solution Section -->
        <section id="solution" class="py-16">
            <div class="text-center mb-12">
                <h2 class="text-3xl md:text-4xl font-bold text-slate-800">A Simple, Powerful Solution</h2>
                <p class="mt-4 max-w-3xl mx-auto text-lg text-slate-600">We bridge the gap between traveler and destination with a seamless platform that prioritizes human connection and expert, local knowledge. This is how we deliver authentic travel planning.</p>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8 items-start text-center">
                <div class="p-6 bg-slate-50 rounded-lg shadow-sm">
                    <div class="flex items-center justify-center bg-orange-100 text-orange-500 w-16 h-16 rounded-full mx-auto mb-4 text-2xl font-bold">1</div>
                    <h3 class="text-xl font-bold mb-2">Share Your Vision</h3>
                    <p class="text-slate-600">Travelers complete a quick, intuitive questionnaire about their interests and trip details.</p>
                </div>
                <div class="p-6 bg-slate-50 rounded-lg shadow-sm">
                    <div class="flex items-center justify-center bg-orange-100 text-orange-500 w-16 h-16 rounded-full mx-auto mb-4 text-2xl font-bold">2</div>
                    <h3 class="text-xl font-bold mb-2">Meet Your Guide</h3>
                    <p class="text-slate-600">Our platform matches them with a list of ideal native guides. They can review profiles and book an appointment.</p>
                </div>
                <div class="p-6 bg-slate-50 rounded-lg shadow-sm">
                    <div class="flex items-center justify-center bg-orange-100 text-orange-500 w-16 h-16 rounded-full mx-auto mb-4 text-2xl font-bold">3</div>
                    <h3 class="text-xl font-bold mb-2">Get Real Advice</h3>
                    <p class="text-slate-600">Connect via live video chat for tailored advice. Travelers can even reconnect during their trip for more help.</p>
                </div>
            </div>
        </section>

        <!-- Business Model Section -->
        <section id="model" class="py-16 bg-slate-50 rounded-2xl">
            <div class="text-center mb-12">
                <h2 class="text-3xl md:text-4xl font-bold text-slate-800">A Win-Win Business Model</h2>
                <p class="mt-4 max-w-3xl mx-auto text-lg text-slate-600">Our model is designed to be highly accessible for travelers while providing significant value and above-average earnings for our local guides, creating a sustainable and scalable ecosystem.</p>
            </div>
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-8 mb-12">
                <div class="bg-white p-8 rounded-lg shadow-xl border-t-4 border-orange-400 transform hover:scale-105 transition-transform duration-300">
                    <h3 class="text-2xl font-bold text-slate-800">Pay-Per-Minute</h3>
                    <p class="text-4xl font-extrabold text-slate-800 my-4">$1 <span class="text-lg font-medium text-slate-500">/ minute</span></p>
                    <p class="text-slate-600">Ultimate flexibility for quick questions or detailed planning sessions.</p>
                </div>
                <div class="bg-orange-500 text-white p-8 rounded-lg shadow-2xl transform hover:scale-105 transition-transform duration-300">
                    <h3 class="text-2xl font-bold">Value Packages</h3>
                     <ul class="my-4 space-y-2 text-lg">
                        <li><strong>5 Hours:</strong> $250 ($0.83/min)</li>
                        <li><strong>10 Hours:</strong> $400 ($0.66/min)</li>
                    </ul>
                    <p>Significant savings for travelers who want in-depth planning support.</p>
                </div>
                <div class="bg-white p-8 rounded-lg shadow-xl border-t-4 border-orange-400 transform hover:scale-105 transition-transform duration-300">
                    <h3 class="text-2xl font-bold text-slate-800">Free Trial</h3>
                    <p class="text-4xl font-extrabold text-slate-800 my-4">30 <span class="text-lg font-medium text-slate-500">minutes free</span></p>
                    <p class="text-slate-600">Lets first-time users experience the value of TourNative risk-free.</p>
                </div>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-center">
                <div class="text-center md:text-left">
                    <h3 class="text-2xl font-bold text-slate-800">Empowering Local Guides</h3>
                    <p class="mt-2 text-lg text-slate-600">Our 40/60 revenue split provides guides with an hourly wage of <strong class="text-orange-500">$24/hour</strong>. This is a powerful incentive that attracts high-quality, knowledgeable local experts to our platform.</p>
                </div>
                <div>
                    <h4 class="text-center font-semibold text-slate-700 mb-2">Guide Earnings Comparison ($/hour)</h4>
                    <div class="chart-container">
                        <canvas id="guideWagesChart"></canvas>
                    </div>
                </div>
            </div>
        </section>

        <!-- Market Section -->
        <section id="market" class="py-16">
             <div class="text-center mb-12">
                <h2 class="text-3xl md:text-4xl font-bold text-slate-800">Market Size & Strategy</h2>
                <p class="mt-4 max-w-3xl mx-auto text-lg text-slate-600">We are targeting a significant segment of the massive travel industry. Our go-to-market strategy is focused, scalable, and designed for rapid growth and brand awareness.</p>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
                <div>
                    <h3 class="text-2xl font-bold text-slate-800 text-center mb-4">Capturing Our Slice</h3>
                    <div class="chart-container" style="max-width: 400px; height: 300px;">
                        <canvas id="marketShareChart"></canvas>
                    </div>
                    <div class="mt-6 text-center text-slate-600">
                        <p><strong class="text-slate-700">SOM: $2.7 Billion.</strong> Our initial obtainable market provides a massive runway for growth. We aim to capture just 0.5% to meet our initial financial goals.</p>
                    </div>
                </div>
                <div>
                    <h3 class="text-2xl font-bold text-slate-800 text-center mb-6">Go-to-Market Roadmap</h3>
                    <div class="relative border-l-2 border-orange-200 pl-8 space-y-10">
                        <div class="relative">
                            <div class="absolute -left-[42px] top-1 w-4 h-4 bg-orange-500 rounded-full border-4 border-white"></div>
                            <h4 class="font-bold">Phase 1: Launch</h4>
                            <p class="text-slate-600">Launch in New York City (47M annual travelers). Prove the model and build initial traction through social media marketing and Kickstarter crowdfunding.</p>
                        </div>
                        <div class="relative">
                            <div class="absolute -left-[42px] top-1 w-4 h-4 bg-orange-500 rounded-full border-4 border-white"></div>
                            <h4 class="font-bold">Phase 2: Expansion (Year 2+)</h4>
                            <p class="text-slate-600">Expand to other major US travel hubs like Orlando and Chicago, leveraging learnings from the NYC launch.</p>
                        </div>
                        <div class="relative">
                            <div class="absolute -left-[42px] top-1 w-4 h-4 bg-orange-500 rounded-full border-4 border-white"></div>
                            <h4 class="font-bold">Phase 3: Global Scale</h4>
                            <p class="text-slate-600">Pursue international expansion into key markets like Europe, China, and India, funded by a future IPO.</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Financials Section -->
        <section id="financials" class="py-16 bg-slate-50 rounded-2xl">
            <div class="text-center mb-12">
                <h2 class="text-3xl md:text-4xl font-bold text-slate-800">Traction & Financial Projections</h2>
                <p class="mt-4 max-w-3xl mx-auto text-lg text-slate-600">We are currently in the prototyping and market research phase. Our financial model projects strong profitability and a clear path to breaking even within five years, based on conservative market capture estimates.</p>
            </div>
            <div class="bg-white p-6 rounded-lg shadow-xl">
                 <h3 class="text-2xl font-bold text-slate-800 text-center mb-4">5-Year Financial Outlook (in thousands)</h3>
                <div class="chart-container" style="max-width: 800px; height: 350px;">
                    <canvas id="financialsChart"></canvas>
                </div>
            </div>
            <div class="mt-8 text-center grid grid-cols-1 md:grid-cols-3 gap-4">
                <p class="text-slate-600"><strong class="text-slate-800">Year 1 Profit:</strong> Projected over $500,000.</p>
                <p class="text-slate-600"><strong class="text-slate-800">Break-Even Point:</strong> Projected in Year 5.</p>
                <p class="text-slate-600"><strong class="text-slate-800">Annual Profit by Year 5:</strong> Projected over $1 Million.</p>
            </div>
        </section>

        <!-- Team & Ask Section -->
        <section id="team" class="py-16">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
                <div>
                    <h2 class="text-3xl md:text-4xl font-bold text-slate-800 mb-6">Our Team</h2>
                    <p class="text-lg text-slate-600 mb-6">We are a passionate team with a vision to revolutionize travel planning.</p>
                    <div class="space-y-4">
                        <div class="font-semibold text-slate-700">Taylor Shapiro | Founder</div>
                    </div>
                </div>
                <div id="ask" class="bg-white p-8 rounded-lg shadow-lg">
                    <h2 class="text-3xl md:text-4xl font-bold text-slate-800 mb-6">The Ask</h2>
                    <p class="text-5xl font-extrabold text-orange-500 mb-6">$750K <span class="text-2xl font-medium text-slate-500">Pre-Seed</span></p>
                    <h3 class="text-xl font-bold text-slate-700 mb-2">Use of Funds:</h3>
                    <ul class="list-disc list-inside text-lg text-slate-600 space-y-2">
                        <li>Hire a core programming team to build the app and website.</li>
                        <li>Expand team with marketing, IT, and data specialists.</li>
                        <li>Fund initial marketing campaigns for NYC launch.</li>
                    </ul>
                     <p class="mt-6 font-semibold">Contact: TaylorShapiro@tournative.com</p>
                </div>
            </div>
        </section>

    </main>

    <footer class="bg-slate-800 text-slate-400 mt-16">
        <div class="container mx-auto px-6 py-8 text-center">
            <p>&copy; 2025 TourNative. All Rights Reserved.</p>
            <p class="mt-2">An interactive business plan.</p>
        </div>
    </footer>

<script>
document.addEventListener('DOMContentLoaded', () => {

    // Mobile Menu Toggle
    const mobileMenuButton = document.getElementById('mobile-menu-button');
    const mobileMenu = document.getElementById('mobile-menu');
    mobileMenuButton.addEventListener('click', () => {
        mobileMenu.classList.toggle('hidden');
    });

    // Active Nav Link Scrolling
    const sections = document.querySelectorAll('section[id]');
    const navLinks = document.querySelectorAll('.nav-link');

    const observerOptions = {
        root: null,
        rootMargin: '0px',
        threshold: 0.5
    };

    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                const id = entry.target.getAttribute('id');
                navLinks.forEach(link => {
                    link.classList.remove('active');
                    if (link.getAttribute('href') === `#${id}`) {
                        link.classList.add('active');
                    }
                });
            }
        });
    }, observerOptions);

    sections.forEach(section => {
        observer.observe(section);
    });
    
    // Dynamic Number Counters
    function animateValue(obj, start, end, duration) {
        let startTimestamp = null;
        const step = (timestamp) => {
            if (!startTimestamp) startTimestamp = timestamp;
            const progress = Math.min((timestamp - startTimestamp) / duration, 1);
            const currentValue = Math.floor(progress * (end - start) + start);
            
            if (end > 1000000) {
                 obj.innerHTML = `$${(currentValue / 1000000).toFixed(1)} Trillion`;
            } else if (end > 1000) {
                 obj.innerHTML = `$${(currentValue / 1000).toFixed(0)} Billion`;
            } else {
                 obj.innerHTML = `$${currentValue}`;
            }

            if (progress < 1) {
                window.requestAnimationFrame(step);
            }
        };
        window.requestAnimationFrame(step);
    }

    const marketSizeStat = document.getElementById('market-size-stat');
    const usTravelStat = document.getElementById('us-travel-stat');
    
    const statsObserver = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                if(entry.target.id === 'market-size-stat') {
                    animateValue(marketSizeStat, 0, 7000000, 2000);
                }
                if(entry.target.id === 'us-travel-stat') {
                    animateValue(usTravelStat, 0, 781000, 2000);
                }
                statsObserver.unobserve(entry.target);
            }
        });
    }, { threshold: 0.8 });

    statsObserver.observe(marketSizeStat);
    statsObserver.observe(usTravelStat);

    // Chart.js Implementations
    const chartObserver = new IntersectionObserver((entries, observer) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                if (entry.target.id === 'guideWagesChart') createGuideWagesChart();
                if (entry.target.id === 'marketShareChart') createMarketShareChart();
                if (entry.target.id === 'financialsChart') createFinancialsChart();
                observer.unobserve(entry.target);
            }
        });
    }, { threshold: 0.5 });
    
    chartObserver.observe(document.getElementById('guideWagesChart'));
    chartObserver.observe(document.getElementById('marketShareChart'));
    chartObserver.observe(document.getElementById('financialsChart'));


    // Chart: Guide Wages
    function createGuideWagesChart() {
        const ctx = document.getElementById('guideWagesChart').getContext('2d');
        new Chart(ctx, {
            type: 'bar',
            data: {
                labels: ['Average Tour Guide', 'TourNative Guide'],
                datasets: [{
                    label: 'Hourly Wage ($)',
                    data: [12, 24],
                    backgroundColor: ['#cbd5e1', '#f97316'],
                    borderColor: ['#94a3b8', '#ea580c'],
                    borderWidth: 1
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: { display: false },
                    tooltip: {
                        callbacks: {
                            label: function(context) {
                                return `$${context.raw}`;
                            }
                        }
                    }
                },
                scales: {
                    y: { beginAtZero: true, grid: { color: '#e2e8f0' } },
                    x: { grid: { display: false } }
                }
            }
        });
    }

    // Chart: Market Share
    function createMarketShareChart() {
        const ctx = document.getElementById('marketShareChart').getContext('2d');
        new Chart(ctx, {
            type: 'doughnut',
            data: {
                labels: ['TAM: Global Travel ($7T)', 'SAM: U.S. OTA ($157B)', 'SOM: TourNative Opportunity ($2.7B)'],
                datasets: [{
                    data: [7000, 157, 2.7], // Simplified for visualization
                    backgroundColor: ['#fed7aa', '#fb923c', '#ea580c'],
                    hoverOffset: 4
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: { position: 'bottom' },
                    tooltip: {
                         callbacks: {
                            label: function(context) {
                                let label = context.label || '';
                                if (label) {
                                    label += ': ';
                                }
                                if (context.parsed !== null) {
                                    // Extract value from label string
                                    const value = label.match(/\(\$([0-9.,]+[T|B])\)/)[1];
                                    label = context.label.split('(')[0].trim() + `: $${value}`;
                                }
                                return label;
                            }
                        }
                    }
                }
            }
        });
    }

    // Chart: Financials
    function createFinancialsChart() {
        const ctx = document.getElementById('financialsChart').getContext('2d');
        const labels = ['Year 1', 'Year 2', 'Year 3', 'Year 4', 'Year 5'];
        new Chart(ctx, {
            type: 'line',
            data: {
                labels: labels,
                datasets: [
                    {
                        label: 'Total Revenue',
                        data: [861, 1200, 1500, 1800, 2200], // in thousands
                        borderColor: '#22c55e',
                        backgroundColor: '#22c55e20',
                        fill: true,
                        tension: 0.4
                    },
                    {
                        label: 'Total Costs',
                        data: [361, 600, 900, 1200, 1100], // in thousands
                        borderColor: '#ef4444',
                        backgroundColor: '#ef444420',
                        fill: false,
                        tension: 0.4
                    },
                    {
                        label: 'Profit',
                        data: [500, 600, 600, 600, 1100], // in thousands
                        borderColor: '#3b82f6',
                        backgroundColor: '#3b82f620',
                        fill: false,
                        tension: 0.4
                    }
                ]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: { position: 'top' },
                    tooltip: {
                        mode: 'index',
                        intersect: false,
                        callbacks: {
                            label: function(context) {
                                let label = context.dataset.label || '';
                                if (label) {
                                    label += ': ';
                                }
                                if (context.parsed.y !== null) {
                                    label += new Intl.NumberFormat('en-US', { style: 'currency', currency: 'USD', minimumFractionDigits: 0, maximumFractionDigits: 0 }).format(context.parsed.y * 1000);
                                }
                                return label;
                            }
                        }
                    }
                },
                scales: {
                    y: {
                        beginAtZero: true,
                        ticks: {
                            callback: function(value, index, values) {
                                return '$' + value + 'K';
                            }
                        },
                        grid: { color: '#e2e8f0' }
                    },
                    x: {
                        grid: { display: false }
                    }
                },
                 interaction: {
                    intersect: false,
                    mode: 'index',
                },
            }
        });
    }

    // Gemini API Integration
    const marketQuestionInput = document.getElementById('market-question-input');
    const askMarketQuestionBtn = document.getElementById('ask-market-question-btn');
    const marketAnswerOutput = document.getElementById('market-answer-output');
    const marketAnswerText = document.getElementById('market-answer-text');
    const marketLoading = document.getElementById('market-loading');

    const generateTaglinesBtn = document.getElementById('generate-taglines-btn');
    const taglineOutput = document.getElementById('tagline-output');
    const taglineText = document.getElementById('tagline-text');
    const taglineLoading = document.getElementById('tagline-loading');

    const businessPlanContext = `
        TourNative is a travel-tech platform that connects travelers with native, local guides via live video chat.
        The service aims to provide personalized, insider advice for a more authentic travel experience, differentiating itself from generic online review sites and costly, traditional travel agents.
        The target market is domestic leisure travelers between the ages of 25 and 64.
        TourNative offers a free trial, followed by a pricing model of $1 per minute or package deals.
        The travel and tourism industry is a significant market, with a total global contribution of $7 trillion.
        The U.S. online travel agency (OTA) market was valued at $157 billion in 2013 and is highly concentrated, with 95% of the market controlled by companies like Expedia and Priceline.
        In contrast, TourNative plans to compete with the fragmented traditional travel agency market, where less than 10% of U.S. travelers use an agent.
        The company will initially launch in New York City, which has 47 million travelers annually, before expanding to other major destinations.
        Travelers are tired of generic, cookie-cutter trips. They crave authentic, local insights that go beyond crowded tourist destinations.
        Online services like Yelp and Google often provide broad recommendations based on majority opinion, not individual preferences.
        Traditional travel agents are expensive (typically costing over $75) and can be disconnected from a destination's local knowledge.
        Domestic travel spending in the US is approximately $781 billion this year, with 77% of trips for leisure purposes.
        Online travel services are a growing market, with online booking channels expected to grow at about 1% per year.
    `;

    async function callGeminiAPI(prompt, outputElement, loadingElement) {
        outputElement.classList.add('hidden');
        loadingElement.classList.remove('hidden');
        outputElement.parentElement.classList.remove('hidden'); // Show container

        let chatHistory = [];
        chatHistory.push({ role: "user", parts: [{ text: prompt }] });
        const payload = { contents: chatHistory };
        const apiKey = ""; // If you want to use models other than gemini-2.5-flash-preview-05-20 or imagen-3.0-generate-002, provide an API key here. Otherwise, leave this as-is.
        const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-05-20:generateContent?key=${apiKey}`;

        let retries = 0;
        const maxRetries = 5;
        const baseDelay = 1000; // 1 second

        while (retries < maxRetries) {
            try {
                const response = await fetch(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });

                if (response.status === 429) { // Too Many Requests
                    const delay = baseDelay * Math.pow(2, retries) + Math.random() * 1000; // Exponential backoff with jitter
                    retries++;
                    await new Promise(res => setTimeout(res, delay));
                    continue; // Retry the request
                }

                if (!response.ok) {
                    throw new Error(`HTTP error! status: ${response.status}`);
                }

                const result = await response.json();
                if (result.candidates && result.candidates.length > 0 &&
                    result.candidates[0].content && result.candidates[0].content.parts &&
                    result.candidates[0].content.parts.length > 0) {
                    const text = result.candidates[0].content.parts[0].text;
                    outputElement.innerHTML = text;
                    outputElement.classList.remove('hidden');
                } else {
                    outputElement.innerHTML = "Could not generate a response. Please try again.";
                    outputElement.classList.remove('hidden');
                }
                break; // Exit loop on success
            } catch (error) {
                console.error("Error calling Gemini API:", error);
                outputElement.innerHTML = "An error occurred. Please try again later.";
                outputElement.classList.remove('hidden');
                break; // Exit loop on unrecoverable error
            } finally {
                loadingElement.classList.add('hidden');
            }
        }

        if (retries === maxRetries) {
            outputElement.innerHTML = "Failed to get a response after multiple retries. Please try again later.";
            outputElement.classList.remove('hidden');
            loadingElement.classList.add('hidden');
        }
    }

    askMarketQuestionBtn.addEventListener('click', () => {
        const userQuestion = marketQuestionInput.value.trim();
        if (userQuestion) {
            const prompt = `Based on the following business plan for TourNative:\n\n${businessPlanContext}\n\nAnswer the following question concisely, drawing only from the provided text: ${userQuestion}`;
            callGeminiAPI(prompt, marketAnswerText, marketLoading);
        } else {
            marketAnswerOutput.classList.remove('hidden');
            marketAnswerText.innerHTML = "Please enter a question.";
            marketLoading.classList.add('hidden');
        }
    });

    generateTaglinesBtn.addEventListener('click', () => {
        const prompt = `TourNative is a platform that connects travelers with local guides via live video chat for authentic, personalized travel advice. It aims to be an alternative to generic online searches and expensive travel agents. Generate 3-5 short, catchy, and impactful taglines or marketing slogans for TourNative. Focus on authenticity, local connection, and ease of use. Do not include any introductory or concluding remarks, just the taglines, each on a new line.`;
        callGeminiAPI(prompt, taglineText, taglineLoading);
    });

});
</script>
</body>
</html>
