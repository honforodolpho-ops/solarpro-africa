<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>SolarPro Africa AI — Commercial SaaS Module</title>
    <!-- Tailwind + Font Awesome -->
    <script src="https://cdn.tailwindcss.com">
    </script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" />
    <style>
        /* premium custom overrides */
        body {
            background: #f8fafc;
            font-family: 'Inter', system-ui, -apple-system, sans-serif;
        }
        .card-premium {
            background: #ffffff;
            border-radius: 1.25rem;
            box-shadow: 0 4px 24px rgba(0, 20, 40, 0.06);
            transition: box-shadow 0.2s ease;
        }
        .card-premium:hover {
            box-shadow: 0 8px 40px rgba(0, 20, 40, 0.10);
        }
        .badge-gold {
            background: #f5b342;
            color: #0b1a2e;
            font-weight: 600;
        }
        .btn-primary {
            background: #0b1a2e;
            color: #fff;
            padding: 0.65rem 1.5rem;
            border-radius: 9999px;
            font-weight: 600;
            transition: all 0.15s ease;
        }
        .btn-primary:hover {
            background: #1a2f4a;
            transform: scale(1.01);
        }
        .btn-gold {
            background: #f5b342;
            color: #0b1a2e;
            padding: 0.65rem 1.5rem;
            border-radius: 9999px;
            font-weight: 600;
            transition: all 0.15s ease;
        }
        .btn-gold:hover {
            background: #e6a230;
            transform: scale(1.01);
        }
        .text-gold {
            color: #f5b342;
        }
        .border-gold {
            border-color: #f5b342;
        }
        .bg-deep {
            background: #0b1a2e;
        }
        .text-deep {
            color: #0b1a2e;
        }
        .pipeline-card {
            background: #ffffff;
            border-radius: 1rem;
            border: 1px solid #eef2f6;
            padding: 0.75rem 1rem;
            transition: all 0.15s ease;
            cursor: default;
        }
        .pipeline-card:hover {
            border-color: #f5b342;
            box-shadow: 0 4px 16px rgba(245, 179, 66, 0.12);
        }
        .status-dot {
            width: 0.6rem;
            height: 0.6rem;
            border-radius: 9999px;
            display: inline-block;
        }
        .status-dot.won {
            background: #22c55e;
        }
        .status-dot.lost {
            background: #ef4444;
        }
        .status-dot.contacted {
            background: #3b82f6;
        }
        .status-dot.qualified {
            background: #8b5cf6;
        }
        .status-dot.proposal {
            background: #f59e0b;
        }
        .status-dot.negotiation {
            background: #ec4899;
        }
        .status-dot.new {
            background: #64748b;
        }
        .status-dot.site-survey {
            background: #06b6d4;
        }
        .plan-card {
            border-radius: 1.5rem;
            padding: 2rem 1.75rem;
            border: 1px solid #eef2f6;
            transition: all 0.2s ease;
        }
        .plan-card.popular {
            border-color: #f5b342;
            background: #fefcf5;
            position: relative;
        }
        .plan-card.popular::before {
            content: 'Most Popular';
            position: absolute;
            top: -0.65rem;
            left: 50%;
            transform: translateX(-50%);
            background: #f5b342;
            color: #0b1a2e;
            font-size: 0.7rem;
            font-weight: 700;
            padding: 0.2rem 1.2rem;
            border-radius: 9999px;
            letter-spacing: 0.5px;
        }
        .plan-card:hover {
            transform: translateY(-4px);
            box-shadow: 0 16px 48px rgba(0, 20, 40, 0.08);
        }
        .feature-check {
            color: #22c55e;
            margin-right: 0.5rem;
        }
        .feature-muted {
            color: #94a3b8;
        }
        /* mobile-first touch targets */
        @media (max-width: 640px) {
            .btn-primary,
            .btn-gold {
                padding: 0.75rem 1.25rem;
                font-size: 0.9rem;
                width: 100%;
                justify-content: center;
            }
            .plan-card {
                padding: 1.5rem 1rem;
            }
            .card-premium {
                border-radius: 1rem;
            }
        }
        /* scrollable pipeline */
        .pipeline-scroll {
            overflow-x: auto;
            padding-bottom: 0.75rem;
            display: flex;
            gap: 1rem;
        }
        .pipeline-column {
            min-width: 200px;
            flex: 0 0 auto;
        }
        /* sidebar simulation */
        .sidebar-icon {
            width: 2.25rem;
            height: 2.25rem;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 0.75rem;
            color: #64748b;
            transition: all 0.15s ease;
        }
        .sidebar-icon.active {
            background: #f5b342;
            color: #0b1a2e;
        }
        .sidebar-icon:hover {
            background: #f1f5f9;
        }
        .sidebar-icon.active:hover {
            background: #e6a230;
        }
        /* PDF preview mock */
        .pdf-preview {
            background: #ffffff;
            border-radius: 0.75rem;
            border: 1px solid #eef2f6;
            padding: 1.5rem;
            box-shadow: 0 2px 12px rgba(0, 0, 0, 0.02);
        }
        .pdf-preview .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 2px solid #0b1a2e;
            padding-bottom: 0.75rem;
            margin-bottom: 1rem;
        }
        .pdf-preview .logo-placeholder {
            background: #0b1a2e;
            color: #f5b342;
            font-weight: 700;
            padding: 0.3rem 0.8rem;
            border-radius: 0.4rem;
            font-size: 0.85rem;
        }
        .pdf-preview .title {
            font-weight: 700;
            font-size: 1.1rem;
            color: #0b1a2e;
        }
        .pdf-preview .table-preview {
            width: 100%;
            border-collapse: collapse;
            font-size: 0.75rem;
        }
        .pdf-preview .table-preview th {
            text-align: left;
            border-bottom: 1px solid #eef2f6;
            padding: 0.4rem 0.2rem;
            color: #475569;
            font-weight: 600;
        }
        .pdf-preview .table-preview td {
            padding: 0.4rem 0.2rem;
            border-bottom: 1px solid #f1f5f9;
        }
        .pdf-preview .total-row {
            font-weight: 700;
            border-top: 2px solid #0b1a2e;
            padding-top: 0.5rem;
            margin-top: 0.5rem;
        }
        /* AI assistant chat mock */
        .ai-chat-bubble {
            background: #f1f5f9;
            border-radius: 1rem 1rem 1rem 0.25rem;
            padding: 0.75rem 1rem;
            max-width: 80%;
        }
        .ai-chat-bubble.user {
            background: #0b1a2e;
            color: #ffffff;
            border-radius: 1rem 1rem 0.25rem 1rem;
            margin-left: auto;
        }
        /* quick stats */
        .stat-number {
            font-size: 1.6rem;
            font-weight: 700;
            color: #0b1a2e;
            line-height: 1.2;
        }
        .stat-label {
            font-size: 0.8rem;
            color: #64748b;
            font-weight: 500;
            letter-spacing: 0.3px;
        }
        @media (max-width: 640px) {
            .stat-number {
                font-size: 1.3rem;
            }
        }
        /* Toggle switch */
        .toggle-track {
            width: 3rem;
            height: 1.6rem;
            background: #cbd5e1;
            border-radius: 9999px;
            position: relative;
            cursor: pointer;
            transition: background 0.2s ease;
        }
        .toggle-track.active {
            background: #f5b342;
        }
        .toggle-thumb {
            width: 1.2rem;
            height: 1.2rem;
            background: #fff;
            border-radius: 9999px;
            position: absolute;
            top: 0.2rem;
            left: 0.2rem;
            transition: transform 0.2s ease;
            box-shadow: 0 1px 4px rgba(0, 0, 0, 0.15);
        }
        .toggle-track.active .toggle-thumb {
            transform: translateX(1.4rem);
        }
        /* layout helper */
        .grid-sales {
            display: grid;
            grid-template-columns: 1fr;
            gap: 1.5rem;
        }
        @media (min-width: 768px) {
            .grid-sales {
                grid-template-columns: 2fr 1fr;
            }
        }
        @media (min-width: 1024px) {
            .grid-sales {
                grid-template-columns: 2.5fr 1.5fr;
            }
        }
        .grid-three {
            display: grid;
            grid-template-columns: 1fr;
            gap: 1.25rem;
        }
        @media (min-width: 640px) {
            .grid-three {
                grid-template-columns: repeat(2, 1fr);
            }
        }
        @media (min-width: 1024px) {
            .grid-three {
                grid-template-columns: repeat(3, 1fr);
            }
        }
        .grid-pricing {
            display: grid;
            grid-template-columns: 1fr;
            gap: 1.5rem;
        }
        @media (min-width: 768px) {
            .grid-pricing {
                grid-template-columns: repeat(3, 1fr);
            }
        }
        @media (min-width: 1024px) {
            .grid-pricing {
                grid-template-columns: repeat(4, 1fr);
            }
        }
        /* animation */
        .fade-in {
            animation: fadeIn 0.4s ease;
        }
        @keyframes fadeIn {
            0% {
                opacity: 0;
                transform: translateY(8px);
            }
            100% {
                opacity: 1;
                transform: translateY(0);
            }
        }
        .delay-1 {
            animation-delay: 0.05s;
        }
        .delay-2 {
            animation-delay: 0.10s;
        }
        .delay-3 {
            animation-delay: 0.15s;
        }
        .delay-4 {
            animation-delay: 0.20s;
        }
    </style>
</head>
<body>

    <!-- ============================================================ -->
    <!-- SIDEBAR + MAIN LAYOUT (simulated SaaS shell)                  -->
    <!-- ============================================================ -->
    <div class="flex min-h-screen">

        <!-- SIDEBAR (collapsible on mobile) -->
        <aside class="hidden md:flex md:flex-col md:w-[72px] lg:w-[220px] bg-white border-r border-[#eef2f6] p-3 fixed h-full z-30">
            <div class="flex items-center gap-2 px-2 py-4 mb-2">
                <span class="text-lg font-black text-deep tracking-tight">☀️<span class="hidden lg:inline">SolarPro</span></span>
                <span class="hidden lg:inline text-xs font-semibold text-gold bg-[#fef6e6] px-2 py-0.5 rounded-full">Africa</span>
            </div>
            <nav class="flex-1 space-y-1">
                <!-- Dashboard -->
                <a href="#" class="flex items-center gap-3 px-3 py-2.5 rounded-xl text-sm font-medium text-deep bg-[#f8fafc]">
                    <span class="sidebar-icon active"><i class="fas fa-chart-pie"></i></span>
                    <span class="hidden lg:inline">Dashboard</span>
                </a>
                <!-- Sales -->
                <a href="#" class="flex items-center gap-3 px-3 py-2.5 rounded-xl text-sm font-medium text-slate-500 hover:bg-[#f8fafc] transition">
                    <span class="sidebar-icon"><i class="fas fa-bullhorn"></i></span>
                    <span class="hidden lg:inline">Sales</span>
                </a>
                <!-- Leads -->
                <a href="#" class="flex items-center gap-3 px-3 py-2.5 rounded-xl text-sm font-medium text-slate-500 hover:bg-[#f8fafc] transition">
                    <span class="sidebar-icon"><i class="fas fa-users"></i></span>
                    <span class="hidden lg:inline">Leads</span>
                </a>
                <!-- Customers -->
                <a href="#" class="flex items-center gap-3 px-3 py-2.5 rounded-xl text-sm font-medium text-slate-500 hover:bg-[#f8fafc] transition">
                    <span class="sidebar-icon"><i class="fas fa-user-friends"></i></span>
                    <span class="hidden lg:inline">Customers</span>
                </a>
                <!-- Quotations -->
                <a href="#" class="flex items-center gap-3 px-3 py-2.5 rounded-xl text-sm font-medium text-slate-500 hover:bg-[#f8fafc] transition">
                    <span class="sidebar-icon"><i class="fas fa-file-invoice"></i></span>
                    <span class="hidden lg:inline">Quotations</span>
                </a>
                <!-- Solar Designer -->
                <a href="#" class="flex items-center gap-3 px-3 py-2.5 rounded-xl text-sm font-medium text-slate-500 hover:bg-[#f8fafc] transition">
                    <span class="sidebar-icon"><i class="fas fa-solar-panel"></i></span>
                    <span class="hidden lg:inline">Solar Designer</span>
                </a>
                <!-- Projects -->
                <a href="#" class="flex items-center gap-3 px-3 py-2.5 rounded-xl text-sm font-medium text-slate-500 hover:bg-[#f8fafc] transition">
                    <span class="sidebar-icon"><i class="fas fa-tasks"></i></span>
                    <span class="hidden lg:inline">Projects</span>
                </a>
                <!-- AI Center -->
                <a href="#" class="flex items-center gap-3 px-3 py-2.5 rounded-xl text-sm font-medium text-gold bg-[#fef6e6]">
                    <span class="sidebar-icon" style="background:#f5b34220;color:#f5b342;"><i class="fas fa-robot"></i></span>
                    <span class="hidden lg:inline">AI Sales Center</span>
                </a>
                <!-- Settings -->
                <a href="#" class="flex items-center gap-3 px-3 py-2.5 rounded-xl text-sm font-medium text-slate-500 hover:bg-[#f8fafc] transition">
                    <span class="sidebar-icon"><i class="fas fa-cog"></i></span>
                    <span class="hidden lg:inline">Settings</span>
                </a>
            </nav>
            <div class="border-t border-[#eef2f6] pt-4 mt-2">
                <div class="flex items-center gap-3 px-3 py-2">
                    <div class="w-8 h-8 rounded-full bg-deep flex items-center justify-center text-white text-xs font-bold">JD</div>
                    <div class="hidden lg:block">
                        <div class="text-sm font-semibold text-deep">John Doe</div>
                        <div class="text-xs text-slate-400">Company Admin</div>
                    </div>
                </div>
            </div>
        </aside>

        <!-- MAIN CONTENT -->
        <main class="flex-1 md:ml-[72px] lg:ml-[220px] p-4 md:p-6 w-full">

            <!-- Top bar -->
            <div class="flex items-center justify-between mb-6">
                <div>
                    <h1 class="text-2xl md:text-3xl font-bold text-deep tracking-tight">AI Sales Center</h1>
                    <p class="text-sm text-slate-500 mt-0.5">Run your solar business smarter with AI.</p>
                </div>
                <div class="flex items-center gap-3">
                    <span class="text-xs font-medium text-slate-400 bg-white px-3 py-1.5 rounded-full border border-[#eef2f6] hidden sm:inline-flex">
                        <i class="fas fa-calendar-alt mr-1.5 text-gold"></i> Aug 14, 2026
                    </span>
                    <button class="btn-gold text-sm flex items-center gap-2">
                        <i class="fas fa-plus-circle"></i> New Quotation
                    </button>
                </div>
            </div>

            <!-- ========================================================== -->
            <!-- 1.  QUICK STATS                                             -->
            <!-- ========================================================== -->
            <div class="grid grid-cols-2 md:grid-cols-4 gap-3 md:gap-4 mb-6 fade-in">
                <div class="card-premium p-4">
                    <div class="stat-label"><i class="fas fa-bolt text-gold mr-1"></i> Hot Leads</div>
                    <div class="stat-number">14</div>
                    <div class="text-xs text-emerald-600 font-medium mt-0.5">↑ 3 vs last week</div>
                </div>
                <div class="card-premium p-4">
                    <div class="stat-label"><i class="fas fa-file-invoice text-gold mr-1"></i> Quotations</div>
                    <div class="stat-number">27</div>
                    <div class="text-xs text-amber-600 font-medium mt-0.5">7 need follow-up</div>
                </div>
                <div class="card-premium p-4">
                    <div class="stat-label"><i class="fas fa-handshake text-gold mr-1"></i> Conversion</div>
                    <div class="stat-number">28%</div>
                    <div class="text-xs text-slate-400 font-medium mt-0.5">↑ 2% this month</div>
                </div>
                <div class="card-premium p-4">
                    <div class="stat-label"><i class="fas fa-coin text-gold mr-1"></i> Pipeline Value</div>
                    <div class="stat-number">GHS 1.2M</div>
                    <div class="text-xs text-slate-400 font-medium mt-0.5">12 active opportunities</div>
                </div>
            </div>

            <!-- ========================================================== -->
            <!-- 2.  SALES PIPELINE (Kanban)                                 -->
            <!-- ========================================================== -->
            <div class="card-premium p-4 md:p-5 mb-6 fade-in delay-1">
                <div class="flex items-center justify-between mb-4">
                    <h2 class="text-lg font-bold text-deep flex items-center gap-2">
                        <i class="fas fa-arrows-alt-h text-gold"></i> Sales Pipeline
                    </h2>
                    <div class="flex items-center gap-2 text-xs">
                        <span class="flex items-center gap-1"><span class="status-dot new"></span> New</span>
                        <span class="flex items-center gap-1"><span class="status-dot contacted"></span> Contacted</span>
                        <span class="flex items-center gap-1"><span class="status-dot qualified"></span> Qualified</span>
                        <span class="flex items-center gap-1"><span class="status-dot site-survey"></span> Survey</span>
                        <span class="flex items-center gap-1"><span class="status-dot proposal"></span> Proposal</span>
                        <span class="flex items-center gap-1"><span class="status-dot negotiation"></span> Negotiation</span>
                        <span class="flex items-center gap-1"><span class="status-dot won"></span> Won</span>
                    </div>
                </div>

                <!-- Scrollable pipeline -->
                <div class="pipeline-scroll">
                    <!-- New -->
                    <div class="pipeline-column">
                        <div class="text-xs font-semibold text-slate-400 uppercase tracking-wider mb-2">New (3)</div>
                        <div class="space-y-2">
                            <div class="pipeline-card"><div class="flex items-center justify-between"><span class="font-medium text-sm">Abidjan Hotel</span><span class="text-xs font-semibold text-slate-400">GHS 85k</span></div><div class="text-xs text-slate-400 mt-0.5"><span class="status-dot new mr-1"></span> New · 2h ago</div></div>
                            <div class="pipeline-card"><div class="flex items-center justify-between"><span class="font-medium text-sm">Lomé Clinic</span><span class="text-xs font-semibold text-slate-400">GHS 42k</span></div><div class="text-xs text-slate-400 mt-0.5"><span class="status-dot new mr-1"></span> New · 1d ago</div></div>
                        </div>
                    </div>
                    <!-- Contacted -->
                    <div class="pipeline-column">
                        <div class="text-xs font-semibold text-slate-400 uppercase tracking-wider mb-2">Contacted (4)</div>
                        <div class="space-y-2">
                            <div class="pipeline-card"><div class="flex items-center justify-between"><span class="font-medium text-sm">Accra Mall</span><span class="text-xs font-semibold text-slate-400">GHS 220k</span></div><div class="text-xs text-slate-400 mt-0.5"><span class="status-dot contacted mr-1"></span> Contacted · 3d ago</div></div>
                            <div class="pipeline-card"><div class="flex items-center justify-between"><span class="font-medium text-sm">Tema Factory</span><span class="text-xs font-semibold text-slate-400">GHS 180k</span></div><div class="text-xs text-slate-400 mt-0.5"><span class="status-dot contacted mr-1"></span> Contacted · 5d ago</div></div>
                        </div>
                    </div>
                    <!-- Qualified -->
                    <div class="pipeline-column">
                        <div class="text-xs font-semibold text-slate-400 uppercase tracking-wider mb-2">Qualified (2)</div>
                        <div class="space-y-2">
                            <div class="pipeline-card"><div class="flex items-center justify-between"><span class="font-medium text-sm">Cotonou School</span><span class="text-xs font-semibold text-slate-400">GHS 95k</span></div><div class="text-xs text-slate-400 mt-0.5"><span class="status-dot qualified mr-1"></span> Qualified · 1w ago</div></div>
                        </div>
                    </div>
                    <!-- Site Survey -->
                    <div class="pipeline-column">
                        <div class="text-xs font-semibold text-slate-400 uppercase tracking-wider mb-2">Site Survey (2)</div>
                        <div class="space-y-2">
                            <div class="pipeline-card"><div class="flex items-center justify-between"><span class="font-medium text-sm">Kumasi Guest</span><span class="text-xs font-semibold text-slate-400">GHS 64k</span></div><div class="text-xs text-slate-400 mt-0.5"><span class="status-dot site-survey mr-1"></span> Survey · 2d ago</div></div>
                        </div>
                    </div>
                    <!-- Proposal Sent -->
                    <div class="pipeline-column">
                        <div class="text-xs font-semibold text-slate-400 uppercase tracking-wider mb-2">Proposal (3)</div>
                        <div class="space-y-2">
                            <div class="pipeline-card"><div class="flex items-center justify-between"><span class="font-medium text-sm">Abidjan Res.</span><span class="text-xs font-semibold text-slate-400">GHS 38k</span></div><div class="text-xs text-slate-400 mt-0.5"><span class="status-dot proposal mr-1"></span> Sent · 1d ago</div></div>
                            <div class="pipeline-card"><div class="flex items-center justify-between"><span class="font-medium text-sm">Lomé Office</span><span class="text-xs font-semibold text-slate-400">GHS 52k</span></div><div class="text-xs text-slate-400 mt-0.5"><span class="status-dot proposal mr-1"></span> Sent · 4d ago</div></div>
                        </div>
                    </div>
                    <!-- Negotiation -->
                    <div class="pipeline-column">
                        <div class="text-xs font-semibold text-slate-400 uppercase tracking-wider mb-2">Negotiation (1)</div>
                        <div class="space-y-2">
                            <div class="pipeline-card"><div class="flex items-center justify-between"><span class="font-medium text-sm">Tema Port</span><span class="text-xs font-semibold text-slate-400">GHS 340k</span></div><div class="text-xs text-slate-400 mt-0.5"><span class="status-dot negotiation mr-1"></span> Negotiation · 2w ago</div></div>
                        </div>
                    </div>
                    <!-- Won -->
                    <div class="pipeline-column">
                        <div class="text-xs font-semibold text-slate-400 uppercase tracking-wider mb-2">Won (2)</div>
                        <div class="space-y-2">
                            <div class="pipeline-card border-green-200 bg-green-50/40"><div class="flex items-center justify-between"><span class="font-medium text-sm">Accra Hotel</span><span class="text-xs font-semibold text-emerald-600">GHS 125k</span></div><div class="text-xs text-slate-400 mt-0.5"><span class="status-dot won mr-1"></span> Won · 3w ago</div></div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- ========================================================== -->
            <!-- 3.  AI SALES CENTER + QUOTATION BUILDER (two columns)      -->
            <!-- ========================================================== -->
            <div class="grid-sales mb-6 fade-in delay-2">

                <!-- LEFT: Quotation Builder + AI Proposal -->
                <div class="space-y-4">

                    <!-- Quotation Builder -->
                    <div class="card-premium p-4 md:p-5">
                        <div class="flex items-center justify-between mb-3">
                            <h2 class="text-lg font-bold text-deep flex items-center gap-2">
                                <i class="fas fa-file-invoice text-gold"></i> Quotation Builder
                            </h2>
                            <span class="text-xs bg-[#f1f5f9] px-3 py-1 rounded-full font-medium text-slate-500">Draft #Q-00128</span>
                        </div>

                        <!-- Customer & Project -->
                        <div class="grid grid-cols-2 gap-3 mb-3">
                            <div>
                                <label class="text-xs font-semibold text-slate-400 uppercase tracking-wider">Customer</label>
                                <select class="w-full mt-1 px-3 py-2 border border-[#eef2f6] rounded-xl text-sm bg-white focus:outline-none focus:ring-2 focus:ring-gold/40">
                                    <option>Accra Hotel Ltd</option>
                                    <option>Lomé Clinic</option>
                                    <option>Abidjan Res.</option>
                                </select>
                            </div>
                            <div>
                                <label class="text-xs font-semibold text-slate-400 uppercase tracking-wider">Project</label>
                                <select class="w-full mt-1 px-3 py-2 border border-[#eef2f6] rounded-xl text-sm bg-white focus:outline-none focus:ring-2 focus:ring-gold/40">
                                    <option>10kW Hybrid — Accra Hotel</option>
                                    <option>5kW Off-grid — Lomé Clinic</option>
                                </select>
                            </div>
                        </div>

                        <!-- Items table -->
                        <div class="overflow-x-auto">
                            <table class="w-full text-sm">
                                <thead>
                                    <tr class="text-left text-xs text-slate-400 border-b border-[#eef2f6]">
                                        <th class="pb-1.5 font-semibold">Item</th>
                                        <th class="pb-1.5 font-semibold">Qty</th>
                                        <th class="pb-1.5 font-semibold text-right">Unit Price</th>
                                        <th class="pb-1.5 font-semibold text-right">Total</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr><td class="py-1.5">Deye 5kW Hybrid</td><td>2</td><td class="text-right">GHS 18,500</td><td class="text-right font-medium">GHS 37,000</td></tr>
                                    <tr><td class="py-1.5">JA Solar 550W (x12)</td><td>12</td><td class="text-right">GHS 1,850</td><td class="text-right font-medium">GHS 22,200</td></tr>
                                    <tr><td class="py-1.5">Felicity 5.12kWh LiFePO₄</td><td>4</td><td class="text-right">GHS 12,400</td><td class="text-right font-medium">GHS 49,600</td></tr>
                                    <tr><td class="py-1.5">Mounting + Accessories</td><td>1</td><td class="text-right">GHS 8,200</td><td class="text-right font-medium">GHS 8,200</td></tr>
                                    <tr><td class="py-1.5">Installation & Commissioning</td><td>1</td><td class="text-right">GHS 14,500</td><td class="text-right font-medium">GHS 14,500</td></tr>
                                </tbody>
                                <tfoot>
                                    <tr class="border-t border-[#eef2f6]"><td colspan="3" class="pt-2 text-right font-semibold">Subtotal</td><td class="pt-2 text-right font-semibold">GHS 131,500</td></tr>
                                    <tr><td colspan="3" class="text-right text-sm text-slate-500">Discount (5%)</td><td class="text-right text-sm text-slate-500">- GHS 6,575</td></tr>
                                    <tr><td colspan="3" class="text-right text-sm text-slate-500">Tax (12.5%)</td><td class="text-right text-sm text-slate-500">+ GHS 15,616</td></tr>
                                    <tr class="border-t-2 border-deep"><td colspan="3" class="pt-2 text-right font-bold text-deep text-lg">Grand Total</td><td class="pt-2 text-right font-bold text-deep text-lg">GHS 140,541</td></tr>
                                </tfoot>
                            </table>
                        </div>

                        <!-- Actions -->
                        <div class="flex flex-wrap items-center gap-2 mt-4 pt-3 border-t border-[#eef2f6]">
                            <button class="btn-primary text-xs flex items-center gap-1.5"><i class="fas fa-file-pdf"></i> PDF Quotation</button>
                            <button class="btn-gold text-xs flex items-center gap-1.5"><i class="fas fa-robot"></i> AI Proposal</button>
                            <button class="text-xs text-slate-400 hover:text-deep transition px-3 py-1.5 rounded-full border border-[#eef2f6]"><i class="fas fa-save"></i> Save Draft</button>
                            <span class="text-xs text-slate-400 ml-auto"><i class="fas fa-check-circle text-emerald-500 mr-1"></i> All items verified</span>
                        </div>
                    </div>

                    <!-- AI Proposal Writer -->
                    <div class="card-premium p-4 md:p-5 bg-gradient-to-br from-[#fefcf5] to-white border border-gold/20">
                        <div class="flex items-center gap-2 mb-2">
                            <span class="bg-gold/20 p-1.5 rounded-full"><i class="fas fa-robot text-gold"></i></span>
                            <h3 class="font-bold text-deep">AI Proposal Writer</h3>
                            <span class="text-[0.6rem] font-semibold bg-emerald-100 text-emerald-700 px-2 py-0.5 rounded-full">v2.1</span>
                        </div>
                        <div class="text-sm text-slate-600 bg-white rounded-xl p-3 border border-[#eef2f6]">
                            <p class="italic text-slate-400 text-xs mb-1">AI-generated executive summary</p>
                            <p class="mb-1.5">Accra Hotel Ltd requires a <strong>10 kW hybrid solar system</strong> with <strong>20.48 kWh battery backup</strong> to reduce grid dependency and ensure reliable power for critical loads. Based on your load profile, the proposed system will generate approximately <strong>14,400 kWh/year</strong>, saving GHS 28,800 annually in electricity costs.</p>
                            <div class="flex items-center gap-2 text-xs mt-2">
                                <span class="bg-[#f1f5f9] px-2 py-0.5 rounded-full"><i class="far fa-file-alt mr-1"></i> Full proposal ready</span>
                                <button class="text-gold font-semibold hover:underline flex items-center gap-1"><i class="fas fa-download"></i> Download PDF</button>
                            </div>
                        </div>
                        <div class="flex gap-2 mt-2 text-xs">
                            <button class="bg-deep text-white px-3 py-1.5 rounded-full flex items-center gap-1.5"><i class="fas fa-pen-fancy"></i> Regenerate</button>
                            <button class="border border-[#eef2f6] px-3 py-1.5 rounded-full flex items-center gap-1.5 hover:bg-white transition"><i class="fas fa-copy"></i> Copy</button>
                            <button class="border border-[#eef2f6] px-3 py-1.5 rounded-full flex items-center gap-1.5 hover:bg-white transition"><i class="fas fa-whatsapp text-emerald-500"></i> WhatsApp</button>
                        </div>
                    </div>
                </div>

                <!-- RIGHT: AI Sales Assistant + Lead Scoring -->
                <div class="space-y-4">

                    <!-- AI Sales Assistant -->
                    <div class="card-premium p-4 md:p-5">
                        <div class="flex items-center justify-between mb-3">
                            <h3 class="font-bold text-deep flex items-center gap-2">
                                <i class="fas fa-robot text-gold"></i> AI Sales Assistant
                            </h3>
                            <span class="text-[0.6rem] bg-emerald-100 text-emerald-700 px-2 py-0.5 rounded-full">Online</span>
                        </div>
                        <div class="space-y-2 max-h-[200px] overflow-y-auto pr-1">
                            <div class="ai-chat-bubble">
                                <span class="text-xs font-semibold text-gold">AI</span>
                                <p class="text-sm">Good morning! You have 7 quotations awaiting follow-up. I recommend contacting Accra Hotel first — they viewed their proposal 3 times yesterday.</p>
                            </div>
                            <div class="ai-chat-bubble user">
                                <span class="text-xs font-semibold text-gold/70">You</span>
                                <p class="text-sm">What should I say to Accra Hotel?</p>
                            </div>
                            <div class="ai-chat-bubble">
                                <span class="text-xs font-semibold text-gold">AI</span>
                                <p class="text-sm">Suggest a follow-up emphasizing their battery backup needs. Offer a payment plan option. I've drafted a message:</p>
                                <div class="bg-white/70 p-2 rounded-lg mt-1 text-xs border border-gold/20">
                                    <p class="italic">"Dear Accra Hotel, I noticed you've reviewed the proposal. We've had great results with similar hotels — backup power during outages and 35% lower energy costs. Can we schedule a quick call to discuss financing options?"</p>
                                </div>
                                <div class="flex gap-1.5 mt-1.5">
                                    <button class="text-[0.6rem] bg-deep text-white px-2.5 py-0.5 rounded-full">Copy</button>
                                    <button class="text-[0.6rem] border border-[#eef2f6] px-2.5 py-0.5 rounded-full">WhatsApp</button>
                                    <button class="text-[0.6rem] border border-[#eef2f6] px-2.5 py-0.5 rounded-full">Email</button>
                                </div>
                            </div>
                        </div>
                        <div class="flex items-center gap-2 mt-3 pt-2 border-t border-[#eef2f6]">
                            <input type="text" placeholder="Ask the AI assistant..." class="flex-1 px-3 py-2 border border-[#eef2f6] rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-gold/40" />
                            <button class="btn-gold text-xs px-4 py-2"><i class="fas fa-paper-plane"></i></button>
                        </div>
                    </div>

                    <!-- Lead Scoring -->
                    <div class="card-premium p-4 md:p-5">
                        <h3 class="font-bold text-deep flex items-center gap-2 mb-3">
                            <i class="fas fa-chart-line text-gold"></i> Lead Scoring
                        </h3>
                        <div class="space-y-3">
                            <div>
                                <div class="flex justify-between text-sm"><span>Accra Hotel</span><span class="font-semibold text-emerald-600">92 · Very Hot</span></div>
                                <div class="w-full bg-[#eef2f6] h-1.5 rounded-full overflow-hidden"><div class="bg-emerald-500 h-full" style="width:92%"></div></div>
                                <div class="text-xs text-slate-400 mt-0.5">💰 GHS 140k · Decision within 7d</div>
                            </div>
                            <div>
                                <div class="flex justify-between text-sm"><span>Lomé Clinic</span><span class="font-semibold text-amber-500">67 · Warm</span></div>
                                <div class="w-full bg-[#eef2f6] h-1.5 rounded-full overflow-hidden"><div class="bg-amber-500 h-full" style="width:67%"></div></div>
                                <div class="text-xs text-slate-400 mt-0.5">💰 GHS 42k · Needs site survey</div>
                            </div>
                            <div>
                                <div class="flex justify-between text-sm"><span>Tema Factory</span><span class="font-semibold text-amber-500">58 · Warm</span></div>
                                <div class="w-full bg-[#eef2f6] h-1.5 rounded-full overflow-hidden"><div class="bg-amber-500 h-full" style="width:58%"></div></div>
                                <div class="text-xs text-slate-400 mt-0.5">💰 GHS 180k · Follow-up overdue</div>
                            </div>
                            <div>
                                <div class="flex justify-between text-sm"><span>Kumasi Guest</span><span class="font-semibold text-blue-500">44 · Cool</span></div>
                                <div class="w-full bg-[#eef2f6] h-1.5 rounded-full overflow-hidden"><div class="bg-blue-500 h-full" style="width:44%"></div></div>
                                <div class="text-xs text-slate-400 mt-0.5">💰 GHS 64k · Initial contact</div>
                            </div>
                        </div>
                        <div class="text-xs text-slate-400 mt-3 pt-2 border-t border-[#eef2f6]">
                            <i class="fas fa-robot text-gold mr-1"></i> AI recommends: Focus on Accra Hotel — high conversion probability.
                        </div>
                    </div>

                    <!-- Quick actions -->
                    <div class="card-premium p-4 md:p-5 bg-deep text-white">
                        <div class="flex items-center gap-3">
                            <i class="fas fa-bullhorn text-gold text-xl"></i>
                            <div>
                                <div class="font-semibold text-sm">Daily Sales Briefing</div>
                                <div class="text-xs text-slate-300">14 leads to contact · 7 quotations to follow up</div>
                            </div>
                            <button class="btn-gold text-xs ml-auto px-4 py-1.5">View</button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- ========================================================== -->
            <!-- 4.  QUOTATIONS TABLE + FOLLOW-UP                            -->
            <!-- ========================================================== -->
            <div class="card-premium p-4 md:p-5 mb-6 fade-in delay-3">
                <div class="flex items-center justify-between mb-3">
                    <h2 class="text-lg font-bold text-deep flex items-center gap-2">
                        <i class="fas fa-list-ul text-gold"></i> Quotations Requiring Follow-up
                    </h2>
                    <button class="text-xs text-gold font-semibold hover:underline">View all 7 →</button>
                </div>
                <div class="overflow-x-auto">
                    <table class="w-full text-sm">
                        <thead>
                            <tr class="text-left text-xs text-slate-400 border-b border-[#eef2f6]">
                                <th class="pb-2 font-semibold">#</th>
                                <th class="pb-2 font-semibold">Customer</th>
                                <th class="pb-2 font-semibold">Value</th>
                                <th class="pb-2 font-semibold">Status</th>
                                <th class="pb-2 font-semibold">Sent</th>
                                <th class="pb-2 font-semibold">Action</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr><td class="py-2 font-medium">Q-00123</td><td>Accra Hotel</td><td>GHS 140,541</td><td><span class="status-dot proposal mr-1"></span> Sent</td><td>2d ago</td><td><button class="btn-gold text-[0.6rem] px-3 py-1 rounded-full">Follow up</button></td></tr>
                            <tr><td class="py-2 font-medium">Q-00120</td><td>Tema Port</td><td>GHS 340,000</td><td><span class="status-dot negotiation mr-1"></span> Negotiation</td><td>5d ago</td><td><button class="btn-gold text-[0.6rem] px-3 py-1 rounded-full">Follow up</button></td></tr>
                            <tr><td class="py-2 font-medium">Q-00118</td><td>Lomé Office</td><td>GHS 52,300</td><td><span class="status-dot proposal mr-1"></span> Sent</td><td>4d ago</td><td><button class="btn-gold text-[0.6rem] px-3 py-1 rounded-full">Follow up</button></td></tr>
                            <tr><td class="py-2 font-medium">Q-00115</td><td>Cotonou School</td><td>GHS 95,000</td><td><span class="status-dot qualified mr-1"></span> Qualified</td><td>7d ago</td><td><button class="btn-gold text-[0.6rem] px-3 py-1 rounded-full">Schedule call</button></td></tr>
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- ========================================================== -->
            <!-- 5.  PRICING & SUBSCRIPTION (SaaS plans)                    -->
            <!-- ========================================================== -->
            <div class="mb-6 fade-in delay-4">
                <div class="flex items-center justify-between mb-4">
                    <h2 class="text-xl font-bold text-deep flex items-center gap-2">
                        <i class="fas fa-crown text-gold"></i> Subscription Plans
                    </h2>
                    <div class="flex items-center gap-2 text-sm">
                        <span class="text-slate-400">Monthly</span>
                        <div class="toggle-track active" onclick="this.classList.toggle('active')">
                            <div class="toggle-thumb"></div>
                        </div>
                        <span class="font-semibold text-deep">Yearly <span class="text-xs text-emerald-600 font-normal">(save 20%)</span></span>
                    </div>
                </div>

                <div class="grid-pricing">
                    <!-- FREE -->
                    <div class="plan-card">
                        <div class="text-sm font-semibold text-slate-400 uppercase tracking-wider">Free</div>
                        <div class="text-2xl font-bold text-deep mt-1">GHS 0</div>
                        <div class="text-xs text-slate-400">/month</div>
                        <ul class="mt-4 space-y-2 text-sm">
                            <li class="flex items-start"><i class="fas fa-check feature-check"></i> 5 customers</li>
                            <li class="flex items-start"><i class="fas fa-check feature-check"></i> 3 quotations/month</li>
                            <li class="flex items-start"><i class="fas fa-check feature-check"></i> Basic CRM</li>
                            <li class="flex items-start"><i class="fas fa-check feature-check"></i> Solar calculator</li>
                            <li class="flex items-start text-slate-400"><i class="fas fa-times text-slate-300 mr-2"></i> AI Sales Assistant</li>
                            <li class="flex items-start text-slate-400"><i class="fas fa-times text-slate-300 mr-2"></i> PDF proposals</li>
                        </ul>
                        <button class="w-full mt-5 border border-[#eef2f6] rounded-full py-2 text-sm font-semibold text-deep hover:bg-[#f8fafc] transition">Current Plan</button>
                    </div>

                    <!-- PROFESSIONAL (Most Popular) -->
                    <div class="plan-card popular">
                        <div class="text-sm font-semibold text-gold uppercase tracking-wider">Professional</div>
                        <div class="text-2xl font-bold text-deep mt-1">GHS 299</div>
                        <div class="text-xs text-slate-400">/month</div>
                        <ul class="mt-4 space-y-2 text-sm">
                            <li class="flex items-start"><i class="fas fa-check feature-check"></i> Unlimited customers</li>
                            <li class="flex items-start"><i class="fas fa-check feature-check"></i> Unlimited quotations</li>
                            <li class="flex items-start"><i class="fas fa-check feature-check"></i> Full CRM + Pipeline</li>
                            <li class="flex items-start"><i class="fas fa-check feature-check"></i> AI Sales Assistant</li>
                            <li class="flex items-start"><i class="fas fa-check feature-check"></i> PDF quotations + proposals</li>
                            <li class="flex items-start"><i class="fas fa-check feature-check"></i> Solar design + technical reports</li>
                        </ul>
                        <button class="w-full mt-5 btn-gold rounded-full py-2 text-sm font-bold">Upgrade Now</button>
                        <div class="text-center text-[0.6rem] text-slate-400 mt-1.5">7-day free trial</div>
                    </div>

                    <!-- BUSINESS -->
                    <div class="plan-card">
                        <div class="text-sm font-semibold text-slate-400 uppercase tracking-wider">Business</div>
                        <div class="text-2xl font-bold text-deep mt-1">GHS 699</div>
                        <div class="text-xs text-slate-400">/month</div>
                        <ul class="mt-4 space-y-2 text-sm">
                            <li class="flex items-start"><i class="fas fa-check feature-check"></i> Everything in Professional</li>
                            <li class="flex items-start"><i class="fas fa-check feature-check"></i> Multiple users</li>
                            <li class="flex items-start"><i class="fas fa-check feature-check"></i> Inventory management</li>
                            <li class="flex items-start"><i class="fas fa-check feature-check"></i> Maintenance module</li>
                            <li class="flex items-start"><i class="fas fa-check feature-check"></i> Advanced AI insights</li>
                            <li class="flex items-start"><i class="fas fa-check feature-check"></i> Custom branding + portal</li>
                        </ul>
                        <button class="w-full mt-5 border border-deep rounded-full py-2 text-sm font-semibold text-deep hover:bg-deep hover:text-white transition">Upgrade</button>
                    </div>

                    <!-- ENTERPRISE -->
                    <div class="plan-card">
                        <div class="text-sm font-semibold text-slate-400 uppercase tracking-wider">Enterprise</div>
                        <div class="text-2xl font-bold text-deep mt-1">Custom</div>
                        <div class="text-xs text-slate-400">contact sales</div>
                        <ul class="mt-4 space-y-2 text-sm">
                            <li class="flex items-start"><i class="fas fa-check feature-check"></i> Everything in Business</li>
                            <li class="flex items-start"><i class="fas fa-check feature-check"></i> Dedicated support</li>
                            <li class="flex items-start"><i class="fas fa-check feature-check"></i> Custom integrations</li>
                            <li class="flex items-start"><i class="fas fa-check feature-check"></i> SLA + training</li>
                            <li class="flex items-start"><i class="fas fa-check feature-check"></i> Multi-country</li>
                        </ul>
                        <button class="w-full mt-5 border border-[#eef2f6] rounded-full py-2 text-sm font-semibold text-deep hover:bg-[#f8fafc] transition">Contact Sales</button>
                    </div>
                </div>
            </div>

            <!-- ========================================================== -->
            <!-- 6.  BILLING SUMMARY + PAYSTACK                             -->
            <!-- ========================================================== -->
            <div class="grid md:grid-cols-2 gap-4 mb-6 fade-in delay-4">
                <div class="card-premium p-4 md:p-5">
                    <h3 class="font-bold text-deep flex items-center gap-2 mb-2">
                        <i class="fas fa-credit-card text-gold"></i> Billing Summary
                    </h3>
                    <div class="space-y-1.5 text-sm">
                        <div class="flex justify-between"><span class="text-slate-500">Current Plan</span><span class="font-semibold text-deep">Professional</span></div>
                        <div class="flex justify-between"><span class="text-slate-500">Status</span><span class="font-semibold text-emerald-600 flex items-center gap-1"><i class="fas fa-circle text-[0.4rem]"></i> Active</span></div>
                        <div class="flex justify-between"><span class="text-slate-500">Next Payment</span><span class="font-semibold text-deep">Aug 28, 2026</span></div>
                        <div class="flex justify-between"><span class="text-slate-500">Amount</span><span class="font-semibold text-deep">GHS 299.00</span></div>
                        <div class="flex justify-between"><span class="text-slate-500">Payment Method</span><span class="font-semibold text-deep">Paystack · Visa ****4242</span></div>
                    </div>
                    <div class="flex flex-wrap gap-2 mt-3 pt-3 border-t border-[#eef2f6]">
                        <button class="text-xs bg-deep text-white px-4 py-1.5 rounded-full">Manage Subscription</button>
                        <button class="text-xs border border-[#eef2f6] px-4 py-1.5 rounded-full hover:bg-white transition">Update Payment</button>
                        <button class="text-xs text-red-500 border border-red-200 px-4 py-1.5 rounded-full hover:bg-red-50 transition">Cancel</button>
                    </div>
                </div>
                <div class="card-premium p-4 md:p-5 bg-gradient-to-br from-[#fefcf5] to-white border border-gold/20">
                    <h3 class="font-bold text-deep flex items-center gap-2 mb-2">
                        <i class="fas fa-robot text-gold"></i> AI Business Insight
                    </h3>
                    <div class="text-sm text-slate-700 bg-white rounded-xl p-3 border border-[#eef2f6]">
                        <p class="italic text-slate-400 text-xs mb-1">💰 Revenue Opportunity</p>
                        <p>Your <strong>7 open quotations</strong> represent <strong>GHS 842,000</strong> in potential revenue. Focus on <strong>Accra Hotel</strong> (GHS 140k) and <strong>Tema Port</strong> (GHS 340k) — both have high conversion probability.</p>
                        <div class="flex items-center gap-2 mt-2 text-xs">
                            <span class="bg-emerald-50 text-emerald-700 px-2 py-0.5 rounded-full"><i class="fas fa-arrow-up"></i> +12% vs last month</span>
                            <span class="bg-amber-50 text-amber-700 px-2 py-0.5 rounded-full"><i class="fas fa-clock"></i> 3 quotations expiring soon</span>
                        </div>
                    </div>
                </div>
            </div>

            <!-- ========================================================== -->
            <!-- 7.  PDF PREVIEW (mock)                                     -->
            <!-- ========================================================== -->
            <div class="card-premium p-4 md:p-5 fade-in delay-4">
                <div class="flex items-center justify-between mb-3">
                    <h3 class="font-bold text-deep flex items-center gap-2">
                        <i class="fas fa-file-pdf text-gold"></i> Quotation Preview — Q-00128
                    </h3>
                    <div class="flex items-center gap-2 text-xs">
                        <button class="bg-deep text-white px-3 py-1 rounded-full flex items-center gap-1.5"><i class="fas fa-download"></i> Download PDF</button>
                        <button class="border border-[#eef2f6] px-3 py-1 rounded-full flex items-center gap-1.5"><i class="fas fa-print"></i> Print</button>
                    </div>
                </div>
                <div class="pdf-preview">
                    <div class="header">
                        <div>
                            <span class="logo-placeholder">☀️ SolarPro Africa</span>
                            <div class="text-[0.6rem] text-slate-400 mt-0.5">Accra, Ghana · +233 50 123 4567</div>
                        </div>
                        <div class="text-right">
                            <div class="title">QUOTATION</div>
                            <div class="text-[0.6rem] text-slate-400">#Q-00128 · Aug 14, 2026</div>
                            <div class="text-[0.6rem] text-slate-400">Valid until Sep 14, 2026</div>
                        </div>
                    </div>
                    <div class="grid grid-cols-2 text-[0.7rem] mb-3">
                        <div><span class="text-slate-400">Customer:</span> <strong>Accra Hotel Ltd</strong></div>
                        <div class="text-right"><span class="text-slate-400">Project:</span> <strong>10kW Hybrid System</strong></div>
                    </div>
                    <table class="table-preview">
                        <thead><tr><th>Item</th><th>Brand</th><th>Model</th><th>Qty</th><th class="text-right">Unit Price</th><th class="text-right">Total</th></tr></thead>
                        <tbody>
                            <tr><td>Hybrid Inverter</td><td>Deye</td><td>SUN-5K-SG</td><td>2</td><td class="text-right">GHS 18,500</td><td class="text-right">GHS 37,000</td></tr>
                            <tr><td>Solar Panel</td><td>JA Solar</td><td>JAM72S30-550</td><td>12</td><td class="text-right">GHS 1,850</td><td class="text-right">GHS 22,200</td></tr>
                            <tr><td>Battery</td><td>Felicity</td><td>LPBF-5.12</td><td>4</td><td class="text-right">GHS 12,400</td><td class="text-right">GHS 49,600</td></tr>
                            <tr><td>Mounting + Acc.</td><td>—</td><td>—</td><td>1</td><td class="text-right">GHS 8,200</td><td class="text-right">GHS 8,200</td></tr>
                            <tr><td>Installation</td><td>—</td><td>—</td><td>1</td><td class="text-right">GHS 14,500</td><td class="text-right">GHS 14,500</td></tr>
                        </tbody>
                    </table>
                    <div class="mt-3 pt-2 border-t border-[#eef2f6] flex justify-end">
                        <div class="text-right">
                            <div class="text-[0.7rem] text-slate-400">Subtotal: GHS 131,500</div>
                            <div class="text-[0.7rem] text-slate-400">Discount (5%): -GHS 6,575</div>
                            <div class="text-[0.7rem] text-slate-400">Tax (12.5%): +GHS 15,616</div>
                            <div class="text-base font-bold text-deep mt-0.5">Grand Total: GHS 140,541</div>
                            <div class="text-[0.6rem] text-slate-400">Payment terms: 50% deposit, 50% on completion</div>
                        </div>
                    </div>
                    <div class="mt-3 pt-2 border-t border-[#eef2f6] text-[0.6rem] text-slate-400 flex justify-between">
                        <span>Warranty: 5 years on inverter, 10 years on panels, 5 years on battery</span>
                        <span>Page 1 of 3</span>
                    </div>
                </div>
            </div>

            <!-- ========================================================== -->
            <!-- 8.  FOOTER / STATUS                                         -->
            <!-- ========================================================== -->
            <div class="text-center text-[0.65rem] text-slate-400 pt-4 border-t border-[#eef2f6] mt-4">
                <p>SolarPro Africa AI v2.1 · Commercial SaaS Module · Paystack Ready</p>
                <p class="mt-0.5">All calculations are engineering aids. Final design must be verified by a qualified professional.</p>
            </div>

        </main>
    </div>

    <!-- ============================================================ -->
    <!-- JAVASCRIPT — TOGGLE, INTERACTIONS                            -->
    <!-- ============================================================ -->
    <script>
        // Toggle switch for monthly/yearly
        document.querySelectorAll('.toggle-track').forEach(el => {
            el.addEventListener('click', function() {
                this.classList.toggle('active');
                // In a real app, this would re-render pricing
                const isYearly = this.classList.contains('active');
                const prices = document.querySelectorAll('.plan-card .text-2xl');
                // just visual feedback
                if (isYearly) {
                    prices.forEach((p, i) => {
                        if (i === 1) p.textContent = 'GHS 287';
                        else if (i === 2) p.textContent = 'GHS 671';
                    });
                } else {
                    prices.forEach((p, i) => {
                        if (i === 1) p.textContent = 'GHS 299';
                        else if (i === 2) p.textContent = 'GHS 699';
                    });
                }
            });
        });

        // Quick follow-up button feedback
        document.querySelectorAll('.btn-gold.text-\\[0\\.6rem\\]').forEach(btn => {
            btn.addEventListener('click', function(e) {
                e.preventDefault();
                const original = this.textContent;
                this.textContent = '✓ Done';
                this.style.background = '#22c55e';
                this.style.color = '#fff';
                setTimeout(() => {
                    this.textContent = original;
                    this.style.background = '';
                    this.style.color = '';
                }, 2000);
            });
        });

        // AI chat input placeholder
        const chatInput = document.querySelector('.card-premium .flex input[type="text"]');
        if (chatInput) {
            chatInput.addEventListener('keydown', function(e) {
                if (e.key === 'Enter' && this.value.trim()) {
                    const msg = this.value.trim();
                    const container = this.closest('.card-premium').querySelector('.space-y-2');
                    const bubble = document.createElement('div');
                    bubble.className = 'ai-chat-bubble user';
                    bubble.innerHTML = `<span class="text-xs font-semibold text-gold/70">You</span><p class="text-sm">${msg}</p>`;
                    container.appendChild(bubble);
                    this.value = '';
                    // auto-scroll
                    container.scrollTop = container.scrollHeight;
                    // Simulate AI reply after 1s
                    setTimeout(() => {
                        const reply = document.createElement('div');
                        reply.className = 'ai-chat-bubble';
                        reply.innerHTML =
                            `<span class="text-xs font-semibold text-gold">AI</span><p class="text-sm">I'll look into that for you. One moment...</p>`;
                        container.appendChild(reply);
                        container.scrollTop = container.scrollHeight;
                    }, 800);
                }
            });
        }

        console.log('☀️ SolarPro Africa AI — Commercial SaaS Module loaded.');
        console.log('✅ Paystack-ready subscription architecture.');
        console.log('✅ AI Sales Assistant, Lead Scoring, Pipeline, Quotation Builder.');
        console.log('✅ Professional PDF generation ready.');
    </script>

</body>
</html>
