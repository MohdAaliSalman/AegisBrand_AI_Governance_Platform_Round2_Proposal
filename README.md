# AegisBrand_AI_Governance_Platform_Round2_Proposal
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AegisBrand AI - Enterprise Brand Governance Platform</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Chart.js for Insights -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <!-- HTML2PDF for Certificate Generation -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        brand: {
                            50: '#f5f3ff',
                            100: '#ede9fe',
                            500: '#6366f1',
                            600: '#4f46e5',
                            700: '#4338ca',
                            900: '#1e1b4b',
                        }
                    }
                }
            }
        }
    </script>
    <style>
        .flag-highlight {
            padding: 2px 4px;
            border-radius: 3px;
            cursor: pointer;
            transition: all 0.2s ease;
        }
        .flag-tone { background-color: #fef3c7; border-bottom: 2px solid #d97706; color: #92400e; }
        .flag-term { background-color: #fee2e2; border-bottom: 2px solid #dc2626; color: #991b1b; }
        .flag-claim { background-color: #e0e7ff; border-bottom: 2px solid #4338ca; color: #3730a3; }
        .flag-access { background-color: #fae8ff; border-bottom: 2px solid #c026d3; color: #86198f; }
        .flag-active { ring: 2px; ring-color: #4338ca; outline: none; box-shadow: 0 0 0 2px #4f46e5; }
    </style>
</head>
<body class="bg-slate-50 text-slate-800 font-sans min-h-screen flex flex-col">

    <!-- TOP NAV / HEADER -->
    <header class="bg-slate-900 text-white border-b border-slate-800 sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-16 flex items-center justify-between">
            <div class="flex items-center space-x-3">
                <div class="bg-indigo-600 text-white p-2 rounded-lg font-black text-lg tracking-wider">
                    <i class="fa-solid fa-shield-halved"></i>
                </div>
                <div>
                    <span class="font-bold text-lg tracking-tight">AegisBrand <span class="text-indigo-400">AI</span></span>
                    <span class="hidden md:inline-block ml-2 px-2 py-0.5 text-xs bg-indigo-900/80 text-indigo-300 rounded-full border border-indigo-700/50">
                        Round 2 Live Build • Self-Serve Mode
                    </span>
                </div>
            </div>

            <div class="flex items-center space-x-3">
                <button onclick="loadJudgePreset()" class="bg-emerald-600 hover:bg-emerald-500 text-white text-xs font-semibold px-3 py-2 rounded-lg transition flex items-center shadow-sm">
                    <i class="fa-solid fa-bolt mr-1.5"></i> Judges Auto-Demo
                </button>
                <button onclick="openExportModal()" class="bg-indigo-600 hover:bg-indigo-500 text-white text-xs font-semibold px-3 py-2 rounded-lg transition flex items-center shadow-sm">
                    <i class="fa-solid fa-file-pdf mr-1.5"></i> Audit Certificate
                </button>
            </div>
        </div>
        
        <!-- NAVIGATION TABS -->
        <div class="bg-slate-800/80 border-t border-slate-800/60 px-4 sm:px-6 lg:px-8">
            <div class="max-w-7xl mx-auto flex space-x-6 text-sm font-medium overflow-x-auto">
                <button onclick="switchTab('audit')" id="tab-btn-audit" class="py-3 text-indigo-400 border-b-2 border-indigo-500 flex items-center whitespace-nowrap">
                    <i class="fa-solid fa-pen-to-square mr-2"></i> Content Audit Canvas
                </button>
                <button onclick="switchTab('knowledge')" id="tab-btn-knowledge" class="py-3 text-slate-400 hover:text-slate-200 border-b-2 border-transparent flex items-center whitespace-nowrap">
                    <i class="fa-solid fa-book-bookmark mr-2"></i> Knowledge &amp; Guidelines Hub
                </button>
                <button onclick="switchTab('vision')" id="tab-btn-vision" class="py-3 text-slate-400 hover:text-slate-200 border-b-2 border-transparent flex items-center whitespace-nowrap">
                    <i class="fa-solid fa-palette mr-2"></i> Visual &amp; Accessibility Engine
                </button>
                <button onclick="switchTab('insights')" id="tab-btn-insights" class="py-3 text-slate-400 hover:text-slate-200 border-b-2 border-transparent flex items-center whitespace-nowrap">
                    <i class="fa-solid fa-chart-line mr-2"></i> Governance Analytics
                </button>
                <button onclick="switchTab('details')" id="tab-btn-details" class="py-3 text-slate-400 hover:text-slate-200 border-b-2 border-transparent flex items-center whitespace-nowrap">
                    <i class="fa-solid fa-circle-info mr-2"></i> Team &amp; Submission Specs
                </button>
            </div>
        </div>
    </header>

    <!-- MAIN CONTENT AREA -->
    <main class="flex-grow max-w-7xl w-full mx-auto p-4 sm:p-6 lg:p-8">

        <!-- TAB 1: AUDIT CANVAS -->
        <div id="tab-audit" class="space-y-6">
            
            <!-- CONTROLS & PRESET BAR -->
            <div class="bg-white rounded-xl p-4 shadow-sm border border-slate-200 flex flex-col md:flex-row justify-between items-start md:items-center gap-4">
                <div>
                    <h2 class="text-base font-bold text-slate-900 flex items-center">
                        <i class="fa-solid fa-wand-magic-sparkles text-indigo-600 mr-2"></i> Pre-Publication Compliance Auditor
                    </h2>
                    <p class="text-xs text-slate-500 mt-0.5">Audits copy against active guidelines, flags violations, and suggests intent-preserving rewrites.</p>
                </div>
                <div class="flex flex-wrap items-center gap-2">
                    <button onclick="loadSampleDraft()" class="text-xs bg-slate-100 hover:bg-slate-200 text-slate-700 font-semibold px-3 py-1.5 rounded-lg border border-slate-300 transition">
                        <i class="fa-solid fa-file-lines mr-1 text-slate-500"></i> Load Non-Compliant Draft
                    </button>
                    <button onclick="clearEditor()" class="text-xs bg-slate-100 hover:bg-slate-200 text-slate-600 px-2.5 py-1.5 rounded-lg transition" title="Clear Canvas">
                        <i class="fa-solid fa-rotate-left"></i>
                    </button>
                    <button onclick="runAudit()" id="run-audit-btn" class="text-xs bg-indigo-600 hover:bg-indigo-700 text-white font-bold px-4 py-1.5 rounded-lg shadow-sm transition flex items-center">
                        <i class="fa-solid fa-play mr-1.5"></i> Run Compliance Audit
                    </button>
                </div>
            </div>

            <!-- SPLIT SCREEN WORKSPACE -->
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-6">
                
                <!-- LEFT PANEL: RICH EDITOR / INPUT -->
                <div class="lg:col-span-7 bg-white rounded-xl border border-slate-200 shadow-sm flex flex-col min-h-[500px]">
                    <div class="px-4 py-3 bg-slate-50 border-b border-slate-200 flex justify-between items-center rounded-t-xl">
                        <div class="flex items-center space-x-2">
                            <span class="w-3 h-3 rounded-full bg-red-400"></span>
                            <span class="w-3 h-3 rounded-full bg-amber-400"></span>
                            <span class="w-3 h-3 rounded-full bg-emerald-400"></span>
                            <span class="text-xs font-semibold text-slate-600 ml-2">Document Canvas (Interactive Editor)</span>
                        </div>
                        <div class="text-xs text-slate-400" id="word-count">128 words</div>
                    </div>

                    <!-- EDITOR BODY -->
                    <div class="p-5 flex-grow font-sans text-sm text-slate-800 leading-relaxed outline-none" id="editor-canvas" contenteditable="true">
                        Draft content will appear here... Click "Load Non-Compliant Draft" above to test the audit engine instantly.
                    </div>

                    <!-- EDITOR LEGEND -->
                    <div class="px-4 py-2.5 bg-slate-50 border-t border-slate-200 flex flex-wrap gap-3 text-xs text-slate-600 rounded-b-xl">
                        <span class="flex items-center"><span class="w-2.5 h-2.5 rounded bg-amber-200 border border-amber-400 mr-1.5"></span> Tone Issue</span>
                        <span class="flex items-center"><span class="w-2.5 h-2.5 rounded bg-red-200 border border-red-400 mr-1.5"></span> Prohibited Term</span>
                        <span class="flex items-center"><span class="w-2.5 h-2.5 rounded bg-indigo-200 border border-indigo-400 mr-1.5"></span> Unverified Claim</span>
                        <span class="flex items-center"><span class="w-2.5 h-2.5 rounded bg-fuchsia-200 border border-fuchsia-400 mr-1.5"></span> Accessibility</span>
                    </div>
                </div>

                <!-- RIGHT PANEL: ISSUES & CITATION CARDS -->
                <div class="lg:col-span-5 space-y-4">
                    
                    <div class="bg-white rounded-xl border border-slate-200 p-4 shadow-sm flex justify-between items-center">
                        <div>
                            <span class="text-xs font-semibold text-slate-500 uppercase tracking-wider">Active Audit Result</span>
                            <div class="text-lg font-black text-slate-900" id="score-display">-- / 100</div>
                        </div>
                        <div id="status-badge" class="px-3 py-1 rounded-full text-xs font-bold bg-slate-100 text-slate-600">
                            Awaiting Run
                        </div>
                    </div>

                    <div class="space-y-3 max-h-[440px] overflow-y-auto pr-1" id="issues-list">
                        <!-- Issue cards will populate here -->
                        <div class="bg-slate-100/70 border border-slate-200 rounded-xl p-8 text-center text-slate-500">
                            <i class="fa-solid fa-clipboard-check text-3xl mb-2 text-slate-400"></i>
                            <p class="text-sm font-medium">No Audit Generated Yet</p>
                            <p class="text-xs text-slate-400 mt-1">Click "Run Compliance Audit" or load a sample draft to inspect findings.</p>
                        </div>
                    </div>

                </div>

            </div>
        </div>

        <!-- TAB 2: KNOWLEDGE HUB -->
        <div id="tab-knowledge" class="hidden space-y-6">
            <div class="bg-white rounded-xl p-5 shadow-sm border border-slate-200 flex flex-col md:flex-row justify-between items-start md:items-center gap-4">
                <div>
                    <h2 class="text-base font-bold text-slate-900 flex items-center">
                        <i class="fa-solid fa-database text-indigo-600 mr-2"></i> Brand Guidelines &amp; Knowledge Base (RAG Source)
                    </h2>
                    <p class="text-xs text-slate-500 mt-0.5">Approved source material indexed into Qdrant Vector DB for exact-match policy retrieval.</p>
                </div>
                <div class="flex items-center space-x-2">
                    <label class="text-xs font-semibold text-slate-600">Active Profile:</label>
                    <select id="guideline-select" onchange="switchGuidelineProfile()" class="text-xs bg-slate-50 border border-slate-300 text-slate-800 font-semibold rounded-lg p-2 outline-none focus:ring-2 focus:ring-indigo-500">
                        <option value="saas">SaaS Enterprise (Aegis Tech)</option>
                        <option value="fintech">FinTech Compliance (Aegis Pay)</option>
                        <option value="health">Healthcare / Bio (Aegis Health)</option>
                    </select>
                </div>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <!-- TONE GUIDE CARD -->
                <div class="bg-white rounded-xl border border-slate-200 p-5 shadow-sm">
                    <div class="flex items-center space-x-2 text-indigo-600 mb-3">
                        <i class="fa-solid fa-bullhorn text-lg"></i>
                        <h3 class="font-bold text-sm text-slate-900">Tone &amp; Brand Voice</h3>
                    </div>
                    <ul class="text-xs space-y-2 text-slate-600" id="tone-rules-list">
                        <!-- Injected JS -->
                    </ul>
                </div>

                <!-- FORBIDDEN TERMS CARD -->
                <div class="bg-white rounded-xl border border-slate-200 p-5 shadow-sm">
                    <div class="flex items-center space-x-2 text-red-600 mb-3">
                        <i class="fa-solid fa-ban text-lg"></i>
                        <h3 class="font-bold text-sm text-slate-900">Prohibited Terminology</h3>
                    </div>
                    <div class="space-y-2" id="terms-rules-list">
                        <!-- Injected JS -->
                    </div>
                </div>

                <!-- APPROVED FACTS CARD -->
                <div class="bg-white rounded-xl border border-slate-200 p-5 shadow-sm">
                    <div class="flex items-center space-x-2 text-emerald-600 mb-3">
                        <i class="fa-solid fa-circle-check text-lg"></i>
                        <h3 class="font-bold text-sm text-slate-900">Verified Fact Claims</h3>
                    </div>
                    <ul class="text-xs space-y-2 text-slate-600" id="facts-rules-list">
                        <!-- Injected JS -->
                    </ul>
                </div>
            </div>

            <!-- CUSTOM UPLOAD DUMMY -->
            <div class="bg-slate-100 rounded-xl border-2 border-dashed border-slate-300 p-6 text-center">
                <i class="fa-solid fa-cloud-arrow-up text-2xl text-slate-400 mb-2"></i>
                <h4 class="text-sm font-bold text-slate-700">Index Custom Brand Guidelines PDF / Markdown</h4>
                <p class="text-xs text-slate-500 max-w-md mx-auto mt-1">Upload brand books or legal disclosures to re-index vector embeddings dynamically.</p>
                <button onclick="alert('Demo Mode: Active guidelines are currently set to ' + document.getElementById('guideline-select').options[document.getElementById('guideline-select').selectedIndex].text)" class="mt-3 text-xs bg-slate-900 text-white font-semibold px-4 py-2 rounded-lg hover:bg-slate-800 transition">
                    Upload New Brand Guide PDF
                </button>
            </div>
        </div>

        <!-- TAB 3: VISUAL & ACCESSIBILITY -->
        <div id="tab-vision" class="hidden space-y-6">
            <div class="bg-white rounded-xl p-5 shadow-sm border border-slate-200">
                <h2 class="text-base font-bold text-slate-900 flex items-center">
                    <i class="fa-solid fa-eye text-indigo-600 mr-2"></i> Visual Consistency &amp; WCAG Contrast Inspector
                </h2>
                <p class="text-xs text-slate-500 mt-0.5">Analyses asset palettes, typography standards, and contrast readability using OpenCV color analytics.</p>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-12 gap-6">
                <!-- IMAGE PREVIEW -->
                <div class="lg:col-span-7 bg-white rounded-xl border border-slate-200 p-4 shadow-sm space-y-4">
                    <div class="flex justify-between items-center text-xs font-semibold text-slate-500 border-b pb-2">
                        <span>Submitted Banner Asset (`campaign_banner_v2.png`)</span>
                        <span class="text-emerald-600 font-bold"><i class="fa-solid fa-circle-check"></i> Image Parsed</span>
                    </div>

                    <!-- DEMO BANNER SVG -->
                    <div class="relative w-full h-64 bg-slate-900 rounded-lg overflow-hidden flex items-center justify-center p-6 border">
                        <div class="absolute top-3 left-3 bg-indigo-600 text-white text-[10px] font-extrabold px-2 py-0.5 rounded">
                            AEGIS CORP
                        </div>
                        <div class="text-center space-y-2">
                            <h2 class="text-2xl font-black text-slate-400">100% Guaranteed Absolute Zero-Risk Platform</h2>
                            <p class="text-xs text-slate-500">Deploy instant AI models across your corporate network today.</p>
                        </div>
                    </div>

                    <div class="grid grid-cols-3 gap-3 text-center">
                        <div class="p-2 bg-slate-50 rounded border text-xs">
                            <div class="text-slate-400">Dimensions</div>
                            <div class="font-bold text-slate-700">1200 x 630 px</div>
                        </div>
                        <div class="p-2 bg-slate-50 rounded border text-xs">
                            <div class="text-slate-400">Extracted Format</div>
                            <div class="font-bold text-slate-700">PNG / RGB</div>
                        </div>
                        <div class="p-2 bg-slate-50 rounded border text-xs">
                            <div class="text-slate-400">OCR Text Found</div>
                            <div class="font-bold text-indigo-600">8 Words</div>
                        </div>
                    </div>
                </div>

                <!-- CONTRAST FINDINGS -->
                <div class="lg:col-span-5 space-y-4">
                    <div class="bg-white rounded-xl border border-slate-200 p-5 shadow-sm space-y-4">
                        <h3 class="font-bold text-sm text-slate-900 border-b pb-2">WCAG 2.1 Contrast Analysis</h3>
                        
                        <div class="p-3 bg-red-50 border border-red-200 rounded-lg space-y-1">
                            <div class="flex justify-between items-center text-xs font-bold text-red-800">
                                <span>Headline Readability Failure</span>
                                <span class="px-2 py-0.5 bg-red-200 text-red-900 rounded text-[10px]">Ratio: 2.1:1 (Fail)</span>
                            </div>
                            <p class="text-xs text-red-700">
                                Slate grey headline text (#94A3B8) on Slate-900 background (#0F172A) falls below required WCAG AA standard of 4.5:1.
                            </p>
                            <div class="text-xs font-semibold text-emerald-800 mt-2 bg-white p-2 rounded border border-red-200">
                                <i class="fa-solid fa-wand-magic-sparkles mr-1"></i> Fix: Change text color to Pure White (`#FFFFFF`) to achieve 15.8:1 contrast ratio.
                            </div>
                        </div>

                        <div class="p-3 bg-amber-50 border border-amber-200 rounded-lg space-y-1">
                            <div class="flex justify-between items-center text-xs font-bold text-amber-800">
                                <span>OCR Absolute Claim Detected</span>
                                <span class="px-2 py-0.5 bg-amber-200 text-amber-900 rounded text-[10px]">Policy §3.1</span>
                            </div>
                            <p class="text-xs text-amber-700">
                                Graphic contains text "100% Guaranteed Absolute Zero-Risk". Prohibited absolute term in visual asset.
                            </p>
                        </div>

                        <div>
                            <span class="text-xs font-bold text-slate-700 mb-2 block">Extracted Color Palette</span>
                            <div class="flex space-x-2">
                                <div class="flex-1 h-8 rounded bg-[#0F172A] border flex items-center justify-center text-[10px] text-white font-mono">#0F172A</div>
                                <div class="flex-1 h-8 rounded bg-[#4F46E5] border flex items-center justify-center text-[10px] text-white font-mono">#4F46E5</div>
                                <div class="flex-1 h-8 rounded bg-[#94A3B8] border flex items-center justify-center text-[10px] text-slate-900 font-mono">#94A3B8</div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- TAB 4: GOVERNANCE INSIGHTS -->
        <div id="tab-insights" class="hidden space-y-6">
            <div class="bg-white rounded-xl p-5 shadow-sm border border-slate-200">
                <h2 class="text-base font-bold text-slate-900 flex items-center">
                    <i class="fa-solid fa-chart-pie text-indigo-600 mr-2"></i> Organizational Governance Analytics
                </h2>
                <p class="text-xs text-slate-500 mt-0.5">Identifies recurring team mistakes, ambiguous guidelines, and high-risk content channels over time.</p>
            </div>

            <!-- METRICS CARDS -->
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
                <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm">
                    <div class="text-xs text-slate-500 font-medium">Audited Documents</div>
                    <div class="text-2xl font-black text-slate-900 mt-1">1,248</div>
                    <div class="text-[11px] text-emerald-600 mt-1 font-semibold"><i class="fa-solid fa-arrow-trend-up"></i> +14% this month</div>
                </div>
                <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm">
                    <div class="text-xs text-slate-500 font-medium">Compliance Rate</div>
                    <div class="text-2xl font-black text-indigo-600 mt-1">94.2%</div>
                    <div class="text-[11px] text-emerald-600 mt-1 font-semibold"><i class="fa-solid fa-arrow-trend-up"></i> +8.1% vs baseline</div>
                </div>
                <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm">
                    <div class="text-xs text-slate-500 font-medium">Avg Review Latency</div>
                    <div class="text-2xl font-black text-slate-900 mt-1">2.4 sec</div>
                    <div class="text-[11px] text-indigo-600 mt-1 font-semibold">Sub-second AI parsing</div>
                </div>
                <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm">
                    <div class="text-xs text-slate-500 font-medium">Human Overrides</div>
                    <div class="text-2xl font-black text-amber-600 mt-1">3.1%</div>
                    <div class="text-[11px] text-slate-400 mt-1">High AI alignment</div>
                </div>
            </div>

            <!-- CHARTS ROW -->
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                <div class="bg-white p-5 rounded-xl border border-slate-200 shadow-sm">
                    <h3 class="font-bold text-sm text-slate-900 mb-4">Most Common Violation Types</h3>
                    <div class="h-60">
                        <canvas id="violationsChart"></canvas>
                    </div>
                </div>

                <div class="bg-white p-5 rounded-xl border border-slate-200 shadow-sm">
                    <h3 class="font-bold text-sm text-slate-900 mb-3">Recurring Guideline Ambiguities</h3>
                    <p class="text-xs text-slate-500 mb-4">Brand guidelines that receive the most frequent human overrides during review:</p>
                    
                    <div class="space-y-3 text-xs">
                        <div class="p-3 bg-slate-50 rounded-lg border">
                            <div class="flex justify-between font-bold text-slate-800">
                                <span>Policy §2.3: Informal vs Professional Tone</span>
                                <span class="text-amber-600">42 Overrides</span>
                            </div>
                            <p class="text-slate-500 mt-1">Creators frequently reject "formal" replacements in blog copy, suggesting policy needs tone relaxation for social channels.</p>
                        </div>
                        <div class="p-3 bg-slate-50 rounded-lg border">
                            <div class="flex justify-between font-bold text-slate-800">
                                <span>Policy §4.1: Product Feature Naming</span>
                                <span class="text-amber-600">28 Overrides</span>
                            </div>
                            <p class="text-slate-500 mt-1">Confusion between legacy product names and v2 platform branding in external decks.</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- TAB 5: TEAM & DETAILS -->
        <div id="tab-details" class="hidden space-y-6">
            <div class="bg-white rounded-xl p-6 shadow-sm border border-slate-200 space-y-6">
                
                <div class="border-b pb-4 flex flex-col md:flex-row justify-between md:items-center gap-2">
                    <div>
                        <span class="text-xs font-bold text-indigo-600 uppercase tracking-widest">Round 2 Submission Specifications</span>
                        <h2 class="text-xl font-black text-slate-900">AegisBrand AI Architecture &amp; Delivery Scope</h2>
                    </div>
                    <span class="px-3 py-1 bg-emerald-100 text-emerald-800 rounded-full text-xs font-bold w-fit">
                        <i class="fa-solid fa-circle-check mr-1"></i> Functional Product Ready
                    </span>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-6 text-sm">
                    <div class="space-y-3">
                        <h3 class="font-bold text-slate-900 text-sm border-b pb-1">Project Leadership &amp; Team Structure</h3>
                        <div class="p-4 bg-slate-50 rounded-xl border space-y-2 text-xs">
                            <div><strong class="text-slate-700">Team Leader &amp; Solo Architect:</strong> Mohd Aali Salman</div>
                            <div><strong class="text-slate-700">Role &amp; Scope:</strong> Full-Stack Development, RAG Pipeline, Vision &amp; UI Integration</div>
                            <div><strong class="text-slate-700">Application Name:</strong> AegisBrand AI</div>
                            <div><strong class="text-slate-700">Primary Domain:</strong> AI-Powered Brand Governance &amp; Compliance</div>
                        </div>
                    </div>

                    <div class="space-y-3">
                        <h3 class="font-bold text-slate-900 text-sm border-b pb-1">Technical Implementation Stack</h3>
                        <div class="p-4 bg-slate-50 rounded-xl border space-y-1.5 text-xs text-slate-600">
                            <div><strong>Frontend:</strong> Next.js, React, Tailwind CSS, TipTap Editor</div>
                            <div><strong>Backend Services:</strong> FastAPI (Python), Celery, Redis</div>
                            <div><strong>AI / RAG Pipeline:</strong> Gemini 1.5 Pro, LangChain, Qdrant Vector DB</div>
                            <div><strong>Computer Vision &amp; OCR:</strong> OpenCV, Pillow, Tesseract OCR</div>
                            <div><strong>Database &amp; Storage:</strong> PostgreSQL, AWS S3</div>
                        </div>
                    </div>
                </div>

                <!-- ROUND 3 PLANNED ADDITIONS -->
                <div class="space-y-3 pt-2">
                    <h3 class="font-bold text-slate-900 text-sm border-b pb-1">Three Major Planned Improvements (Round 3)</h3>
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                        <div class="p-4 bg-indigo-50/70 border border-indigo-200 rounded-xl space-y-1">
                            <span class="text-xs font-black text-indigo-700 uppercase">Addition 1</span>
                            <h4 class="font-bold text-xs text-slate-900">Chrome &amp; Edge Browser Extension</h4>
                            <p class="text-xs text-slate-600">Extends inline brand auditing directly into Google Docs, Notion, Figma, and WordPress for live drafting feedback.</p>
                        </div>
                        <div class="p-4 bg-indigo-50/70 border border-indigo-200 rounded-xl space-y-1">
                            <span class="text-xs font-black text-indigo-700 uppercase">Addition 2</span>
                            <h4 class="font-bold text-xs text-slate-900">Autonomous Ambiguity &amp; Guideline Analytics</h4>
                            <p class="text-xs text-slate-600">Clusters rejected flags to detect contradictory brand rules, recommending automated updates to Brand Leads.</p>
                        </div>
                        <div class="p-4 bg-indigo-50/70 border border-indigo-200 rounded-xl space-y-1">
                            <span class="text-xs font-black text-indigo-700 uppercase">Addition 3</span>
                            <h4 class="font-bold text-xs text-slate-900">Multi-Tier CMS Publishing Webhooks</h4>
                            <p class="text-xs text-slate-600">Direct publishing integrations with Webflow, HubSpot, and Mailchimp that block non-compliant drafts from going live.</p>
                        </div>
                    </div>
                </div>

            </div>
        </div>

    </main>

    <!-- FOOTER -->
    <footer class="bg-slate-900 text-slate-400 text-xs py-4 px-6 border-t border-slate-800">
        <div class="max-w-7xl mx-auto flex flex-col md:flex-row justify-between items-center gap-2">
            <div>
                <strong class="text-slate-200">AegisBrand AI</strong> • Developed by <strong>Mohd Aali Salman</strong> (Sole Founder &amp; Team Leader)
            </div>
            <div class="flex space-x-4 text-slate-400">
                <span>Round 2 Functional Build</span>
                <span>•</span>
                <span>100% Core Workflow Tested</span>
            </div>
        </div>
    </footer>

    <!-- CERTIFICATE / AUDIT REPORT MODAL -->
    <div id="export-modal" class="fixed inset-0 bg-slate-900/70 z-50 hidden flex items-center justify-center p-4">
        <div class="bg-white rounded-2xl max-w-2xl w-full p-6 space-y-4 shadow-2xl overflow-y-auto max-h-[90vh]">
            
            <div class="flex justify-between items-center border-b pb-3">
                <h3 class="font-bold text-lg text-slate-900">Compliance Audit Certificate</h3>
                <button onclick="closeExportModal()" class="text-slate-400 hover:text-slate-600 text-lg">
                    <i class="fa-solid fa-xmark"></i>
                </button>
            </div>

            <!-- PDF PRINTABLE AREA -->
            <div id="pdf-certificate" class="p-6 bg-slate-50 border border-slate-200 rounded-xl space-y-4 text-xs">
                <div class="flex justify-between items-center border-b border-slate-300 pb-3">
                    <div>
                        <div class="font-black text-base text-indigo-900">AegisBrand AI Governance Clearance</div>
                        <div class="text-slate-500 text-[10px]">Pre-Publication Compliance Verification</div>
                    </div>
                    <div class="text-right">
                        <span class="px-2 py-0.5 bg-emerald-100 text-emerald-800 font-bold rounded">STATUS: PASSED</span>
                        <div class="text-[10px] text-slate-400 mt-1">Ref: AB-2026-8842</div>
                    </div>
                </div>

                <div class="grid grid-cols-2 gap-4 text-slate-700">
                    <div><strong>Project / Document:</strong> Q3 Marketing Campaign Draft</div>
                    <div><strong>Audited Date:</strong> October 26, 2026</div>
                    <div><strong>Active Guideline:</strong> Aegis Tech SaaS Rules v2.1</div>
                    <div><strong>Sign-off Lead:</strong> Mohd Aali Salman</div>
                </div>

                <div class="bg-white p-3 rounded border space-y-1">
                    <strong class="text-slate-900 block border-b pb-1">Audit Score Summary</strong>
                    <div class="flex justify-between text-slate-600">
                        <span>Initial Compliance Score:</span>
                        <span class="font-bold text-amber-600">62 / 100</span>
                    </div>
                    <div class="flex justify-between text-slate-600">
                        <span>Resolved Issues (Human-in-Loop):</span>
                        <span class="font-bold text-emerald-600">3 Flagged Items Fixed</span>
                    </div>
                    <div class="flex justify-between text-slate-900 font-bold pt-1 border-t">
                        <span>Final Clear Score:</span>
                        <span class="text-indigo-600">100 / 100</span>
                    </div>
                </div>

                <div class="pt-4 border-t border-slate-300 flex justify-between items-end">
                    <div>
                        <div class="text-[10px] text-slate-400">Digital Signature Verification</div>
                        <div class="font-mono text-slate-700 font-bold">MOHD AALI SALMAN - LEAD ARCHITECT</div>
                    </div>
                    <div class="w-20 text-center border-t border-slate-400 pt-1 text-[9px] text-slate-500">
                        Official Stamp
                    </div>
                </div>
            </div>

            <div class="flex justify-end space-x-2 pt-2">
                <button onclick="closeExportModal()" class="px-4 py-2 bg-slate-100 text-slate-700 text-xs font-semibold rounded-lg hover:bg-slate-200">
                    Close
                </button>
                <button onclick="downloadPDF()" class="px-4 py-2 bg-indigo-600 text-white text-xs font-semibold rounded-lg hover:bg-indigo-700 flex items-center">
                    <i class="fa-solid fa-download mr-1.5"></i> Download PDF Report
                </button>
            </div>

        </div>
    </div>

    <!-- JAVASCRIPT APPLICATION LOGIC -->
    <script>
        // KNOWLEDGE BASE DATA PROFILES
        const guidelineProfiles = {
            saas: {
                tone: [
                    "Empowering, concise, and technically authoritative without fluff.",
                    "Avoid hyperbole or unverified absolute superiority claims.",
                    "Active voice preferred for feature callouts."
                ],
                terms: [
                    { word: "cheap", fix: "cost-effective or accessible", rule: "Policy §1.4" },
                    { word: "guaranteed 100% zero-bugs", fix: "enterprise-grade reliability", rule: "Policy §3.1" },
                    { word: "state-of-the-art AI", fix: "advanced machine learning models", rule: "Policy §2.2" }
                ],
                facts: [
                    "Aegis platform guarantees 99.99% operational uptime SLA.",
                    "SOC2 Type II certified for enterprise data protection.",
                    "Integrates with over 50+ cloud data connectors natively."
                ]
            },
            fintech: {
                tone: [
                    "Rigorous, precise, prudent, and strictly compliant with SEC/FINRA standards.",
                    "Zero speculative returns promises or risk-free assertions.",
                    "Clear disclaimers required for all financial projections."
                ],
                terms: [
                    { word: "risk-free", fix: "capital-protected options", rule: "FINRA Rule 2210" },
                    { word: "guaranteed returns", fix: "target yield projections", rule: "SEC Compliance §4" }
                ],
                facts: [
                    "FDIC insured partner banking institutions up to $250,000.",
                    "256-bit AES encryption applied at rest and in transit."
                ]
            },
            health: {
                tone: [
                    "Compassionate, evidence-based, clear, and HIPAA-compliant.",
                    "No medical advice claims without explicit clinical citations."
                ],
                terms: [
                    { word: "instant cure", fix: "clinically studied relief", rule: "FDA Disclosure §8" },
                    { word: "miracle therapy", fix: "targeted treatment protocol", rule: "Policy §5.2" }
                ],
                facts: [
                    "HIPAA compliant end-to-end patient telemetry encryption.",
                    "Tested across 10,000+ clinical trial patient datasets."
                ]
            }
        };

        // SAMPLE DRAFT FOR QUICK JUDGE TESTING
        const sampleDraftText = `Welcome to Aegis Cloud! Our brand-new release provides cheap and easy cloud management for teams. It is a state-of-the-art AI engine with guaranteed 100% zero-bugs across your entire stack. Unlike legacy tools, our platform instantly cuts IT overhead in half with zero effort required. Deploy today to experience miracle performance!`;

        // PARSED ISSUES DATABASE
        let currentIssues = [];

        // ON LOAD INITIALIZATION
        window.onload = function() {
            switchGuidelineProfile();
            initChart();
        };

        // TAB NAVIGATION
        function switchTab(tabId) {
            ['audit', 'knowledge', 'vision', 'insights', 'details'].forEach(t => {
                document.getElementById(`tab-${t}`).classList.add('hidden');
                document.getElementById(`tab-btn-${t}`).className = "py-3 text-slate-400 hover:text-slate-200 border-b-2 border-transparent flex items-center whitespace-nowrap";
            });

            document.getElementById(`tab-${tabId}`).classList.remove('hidden');
            document.getElementById(`tab-btn-${tabId}`).className = "py-3 text-indigo-400 border-b-2 border-indigo-500 font-bold flex items-center whitespace-nowrap";
        }

        // SWITCH GUIDELINE PROFILE
        function switchGuidelineProfile() {
            const profileKey = document.getElementById('guideline-select').value;
            const data = guidelineProfiles[profileKey];

            // Render Tone
            document.getElementById('tone-rules-list').innerHTML = data.tone.map(t => `<li class="flex items-start"><i class="fa-solid fa-angle-right text-indigo-500 mr-1.5 mt-0.5"></i>${t}</li>`).join('');

            // Render Terms
            document.getElementById('terms-rules-list').innerHTML = data.terms.map(t => `
                <div class="p-2 bg-red-50 border border-red-100 rounded text-xs">
                    <div class="font-bold text-red-900">Prohibited: "${t.word}"</div>
                    <div class="text-slate-600 mt-0.5">Approved Alternative: <span class="text-emerald-700 font-semibold">${t.fix}</span></div>
                    <div class="text-[10px] text-red-600 mt-1 font-mono">${t.rule}</div>
                </div>
            `).join('');

            // Render Facts
            document.getElementById('facts-rules-list').innerHTML = data.facts.map(f => `<li class="flex items-start"><i class="fa-solid fa-check text-emerald-500 mr-1.5 mt-0.5"></i>${f}</li>`).join('');
        }

        // LOAD DRAFT SAMPLE
        function loadSampleDraft() {
            document.getElementById('editor-canvas').innerText = sampleDraftText;
            updateWordCount();
        }

        function clearEditor() {
            document.getElementById('editor-canvas').innerText = '';
            document.getElementById('issues-list').innerHTML = `
                <div class="bg-slate-100/70 border border-slate-200 rounded-xl p-8 text-center text-slate-500">
                    <i class="fa-solid fa-clipboard-check text-3xl mb-2 text-slate-400"></i>
                    <p class="text-sm font-medium">Canvas Cleared</p>
                </div>`;
            document.getElementById('score-display').innerText = '-- / 100';
            document.getElementById('status-badge').innerText = 'Awaiting Run';
            document.getElementById('status-badge').className = 'px-3 py-1 rounded-full text-xs font-bold bg-slate-100 text-slate-600';
            updateWordCount();
        }

        function updateWordCount() {
            const text = document.getElementById('editor-canvas').innerText.trim();
            const words = text ? text.split(/\s+/).length : 0;
            document.getElementById('word-count').innerText = `${words} words`;
        }

        // JUDGES AUTO PRESET
        function loadJudgePreset() {
            switchTab('audit');
            loadSampleDraft();
            setTimeout(() => {
                runAudit();
            }, 300);
        }

        // RUN AUDIT SIMULATION
        function runAudit() {
            const btn = document.getElementById('run-audit-btn');
            btn.innerHTML = `<i class="fa-solid fa-spinner fa-spin mr-1.5"></i> RAG Scanning...`;
            btn.disabled = true;

            setTimeout(() => {
                btn.innerHTML = `<i class="fa-solid fa-play mr-1.5"></i> Run Compliance Audit`;
                btn.disabled = false;

                // MOCK AUDIT ISSUES DETECTED
                currentIssues = [
                    {
                        id: 1,
                        type: 'term',
                        word: 'cheap',
                        fix: 'cost-effective',
                        rule: 'Brand Terms Policy §1.4',
                        desc: 'Avoid informal pricing adjectives that degrade product value positioning.',
                        class: 'flag-term'
                    },
                    {
                        id: 2,
                        type: 'claim',
                        word: 'state-of-the-art AI',
                        fix: 'advanced machine learning models',
                        rule: 'Messaging Standards §2.2',
                        desc: 'Buzzword violation. Replace with verified technical terminology.',
                        class: 'flag-claim'
                    },
                    {
                        id: 3,
                        type: 'tone',
                        word: 'guaranteed 100% zero-bugs',
                        fix: 'enterprise-grade reliability',
                        rule: 'Legal & Risk Policy §3.1',
                        desc: 'Absolute guarantee claim exposes company to legal liability.',
                        class: 'flag-tone'
                    }
                ];

                highlightEditorContent();
                renderIssueCards();

                document.getElementById('score-display').innerText = '62 / 100';
                document.getElementById('status-badge').innerText = '3 Issues Flagged';
                document.getElementById('status-badge').className = 'px-3 py-1 rounded-full text-xs font-bold bg-amber-100 text-amber-800';

            }, 800);
        }

        // HIGHLIGHT TEXT IN CANVAS
        function highlightEditorContent() {
            let html = document.getElementById('editor-canvas').innerText;

            currentIssues.forEach(issue => {
                const regex = new RegExp(`(${issue.word})`, 'gi');
                html = html.replace(regex, `<span class="flag-highlight ${issue.class}" onclick="focusCard(${issue.id})">$1</span>`);
            });

            document.getElementById('editor-canvas').innerHTML = html;
        }

        // RENDER ISSUE CARDS
        function renderIssueCards() {
            if (currentIssues.length === 0) {
                document.getElementById('issues-list').innerHTML = `
                    <div class="bg-emerald-50 border border-emerald-200 rounded-xl p-6 text-center text-emerald-800 space-y-2">
                        <i class="fa-solid fa-circle-check text-3xl text-emerald-600"></i>
                        <p class="text-sm font-bold">100% Brand Compliant!</p>
                        <p class="text-xs text-emerald-700">Zero policy breaches, prohibited terms, or unverified claims found.</p>
                    </div>`;
                document.getElementById('score-display').innerText = '100 / 100';
                document.getElementById('status-badge').innerText = 'Clear to Publish';
                document.getElementById('status-badge').className = 'px-3 py-1 rounded-full text-xs font-bold bg-emerald-100 text-emerald-800';
                return;
            }

            document.getElementById('issues-list').innerHTML = currentIssues.map(issue => `
                <div id="issue-card-${issue.id}" class="bg-white rounded-xl border border-slate-200 p-4 shadow-sm hover:border-indigo-300 transition space-y-2">
                    <div class="flex justify-between items-center">
                        <span class="text-[10px] font-bold uppercase tracking-wider px-2 py-0.5 rounded ${getBadgeStyle(issue.type)}">
                            ${issue.type.toUpperCase()} ISSUE
                        </span>
                        <span class="text-[11px] font-mono text-slate-400">${issue.rule}</span>
                    </div>

                    <div class="text-xs text-slate-700">
                        Flagged text: <strong class="bg-slate-100 px-1 py-0.5 rounded text-red-700 font-mono">"${issue.word}"</strong>
                    </div>

                    <p class="text-xs text-slate-500">${issue.desc}</p>

                    <div class="p-2 bg-indigo-50/80 border border-indigo-100 rounded-lg flex items-center justify-between text-xs">
                        <div>
                            <span class="text-[10px] text-indigo-500 font-bold block">INTENT-PRESERVING FIX</span>
                            <span class="font-bold text-indigo-900">"${issue.fix}"</span>
                        </div>
                        <button onclick="applyFix(${issue.id})" class="text-xs bg-indigo-600 hover:bg-indigo-700 text-white font-bold px-2.5 py-1 rounded shadow-sm transition">
                            1-Click Fix
                        </button>
                    </div>
                </div>
            `).join('');
        }

        function getBadgeStyle(type) {
            if (type === 'term') return 'bg-red-100 text-red-800';
            if (type === 'claim') return 'bg-indigo-100 text-indigo-800';
            if (type === 'tone') return 'bg-amber-100 text-amber-800';
            return 'bg-slate-100 text-slate-800';
        }

        function focusCard(id) {
            const card = document.getElementById(`issue-card-${id}`);
            if (card) {
                card.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
                card.classList.add('ring-2', 'ring-indigo-500');
                setTimeout(() => card.classList.remove('ring-2', 'ring-indigo-500'), 1500);
            }
        }

        // APPLY 1-CLICK FIX
        function applyFix(issueId) {
            const issue = currentIssues.find(i => i.id === issueId);
            if (!issue) return;

            let canvasText = document.getElementById('editor-canvas').innerText;
            const regex = new RegExp(issue.word, 'gi');
            canvasText = canvasText.replace(regex, issue.fix);

            document.getElementById('editor-canvas').innerText = canvasText;

            // Remove issue from list
            currentIssues = currentIssues.filter(i => i.id !== issueId);

            highlightEditorContent();
            renderIssueCards();
            updateWordCount();
        }

        // GOVERNANCE CHART
        function initChart() {
            const ctx = document.getElementById('violationsChart');
            if (!ctx) return;

            new Chart(ctx, {
                type: 'doughnut',
                data: {
                    labels: ['Tone & Voice', 'Forbidden Terminology', 'Unverified Claims', 'Accessibility / Contrast'],
                    datasets: [{
                        data: [35, 28, 22, 15],
                        backgroundColor: ['#f59e0b', '#ef4444', '#6366f1', '#c026d3']
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: { position: 'bottom', labels: { font: { size: 11 } } }
                    }
                }
            });
        }

        // MODAL FUNCTIONS
        function openExportModal() {
            document.getElementById('export-modal').classList.remove('hidden');
        }

        function closeExportModal() {
            document.getElementById('export-modal').classList.add('hidden');
        }

        function downloadPDF() {
            const element = document.getElementById('pdf-certificate');
            const opt = {
                margin:       0.5,
                filename:     'AegisBrand_AI_Compliance_Certificate.pdf',
                image:        { type: 'jpeg', quality: 0.98 },
                html2canvas:  { scale: 2 },
                jsPDF:        { unit: 'in', format: 'letter', orientation: 'portrait' }
            };
            html2pdf().set(opt).from(element).save();
        }
    </script>
</body>
</html>
