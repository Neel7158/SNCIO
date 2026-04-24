# SNCIO
SNCIO WEBSITE REP
<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>SNCIO | Stop the Profit Leak in Your Plant</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:wght@300;400;500;600&family=JetBrains+Mono:wght@400;600&display=swap" rel="stylesheet">
  <style>
    :root {
      --orange: #f97316;
      --blue: #3b82f6;
      --bg-deep: #0a0f1e;
      --bg-card: #0f172a;
      --bg-elevated: #1e293b;
      --text-primary: #f1f5f9;
      --text-muted: #94a3b8;
      --border: rgba(148,163,184,0.12);
    }

    * { box-sizing: border-box; }

    body {
      background-color: var(--bg-deep);
      color: var(--text-primary);
      font-family: 'DM Sans', sans-serif;
      overflow-x: hidden;
    }

    .font-display { font-family: 'Bebas Neue', sans-serif; }
    .font-mono { font-family: 'JetBrains Mono', monospace; }

    /* Grid blueprint background */
    .blueprint-bg {
      background-color: var(--bg-deep);
      background-image:
        linear-gradient(rgba(59,130,246,0.06) 1px, transparent 1px),
        linear-gradient(90deg, rgba(59,130,246,0.06) 1px, transparent 1px),
        linear-gradient(rgba(59,130,246,0.03) 1px, transparent 1px),
        linear-gradient(90deg, rgba(59,130,246,0.03) 1px, transparent 1px);
      background-size: 80px 80px, 80px 80px, 20px 20px, 20px 20px;
    }

    .noise-overlay::before {
      content: '';
      position: absolute;
      inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.03'/%3E%3C/svg%3E");
      pointer-events: none;
      z-index: 1;
    }

    .orange-glow { text-shadow: 0 0 40px rgba(249,115,22,0.4); }
    .blue-glow { box-shadow: 0 0 60px rgba(59,130,246,0.15); }

    .btn-orange {
      background: var(--orange);
      color: #fff;
      font-family: 'DM Sans', sans-serif;
      font-weight: 600;
      letter-spacing: 0.02em;
      transition: all 0.2s ease;
    }
    .btn-orange:hover {
      background: #ea6c0a;
      transform: translateY(-2px);
      box-shadow: 0 8px 32px rgba(249,115,22,0.35);
    }

    .btn-outline {
      border: 1px solid rgba(249,115,22,0.5);
      color: var(--orange);
      font-weight: 500;
      transition: all 0.2s ease;
    }
    .btn-outline:hover {
      background: rgba(249,115,22,0.1);
      border-color: var(--orange);
    }

    .card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: 12px;
    }

    .card-elevated {
      background: var(--bg-elevated);
      border: 1px solid rgba(148,163,184,0.15);
      border-radius: 12px;
    }

    .step-line::after {
      content: '';
      position: absolute;
      left: 28px;
      top: 60px;
      bottom: -20px;
      width: 1px;
      background: linear-gradient(to bottom, rgba(249,115,22,0.5), transparent);
    }

    .diagonal-stripe {
      background: repeating-linear-gradient(
        -45deg,
        transparent,
        transparent 6px,
        rgba(249,115,22,0.04) 6px,
        rgba(249,115,22,0.04) 12px
      );
    }

    /* Subsidy badge pulse */
    @keyframes pulse-ring {
      0% { box-shadow: 0 0 0 0 rgba(249,115,22,0.4); }
      70% { box-shadow: 0 0 0 16px rgba(249,115,22,0); }
      100% { box-shadow: 0 0 0 0 rgba(249,115,22,0); }
    }
    .pulse-badge { animation: pulse-ring 2.5s ease-out infinite; }

    /* Scroll reveal */
    .reveal {
      opacity: 0;
      transform: translateY(28px);
      transition: opacity 0.65s ease, transform 0.65s ease;
    }
    .reveal.visible {
      opacity: 1;
      transform: none;
    }

    /* Nav */
    nav { backdrop-filter: blur(16px); -webkit-backdrop-filter: blur(16px); }

    /* Blueprint SVG layout */
    .blueprint-room { fill: rgba(59,130,246,0.08); stroke: rgba(59,130,246,0.5); stroke-width: 1.5; }
    .blueprint-room-after { fill: rgba(249,115,22,0.08); stroke: rgba(249,115,22,0.5); stroke-width: 1.5; }
    .blueprint-text { fill: rgba(148,163,184,0.9); font-family: 'JetBrains Mono', monospace; font-size: 10px; }
    .blueprint-dim { stroke: rgba(59,130,246,0.35); stroke-width: 0.8; stroke-dasharray: 4 3; }
    .blueprint-arrow { fill: rgba(59,130,246,0.5); }
    .blueprint-arrow-after { fill: rgba(249,115,22,0.5); }
    .flow-line { stroke: rgba(239,68,68,0.7); stroke-width: 2; stroke-dasharray: 6 4; fill: none; }
    .flow-line-after { stroke: rgba(34,197,94,0.7); stroke-width: 2; stroke-dasharray: 6 4; fill: none; }

    input, select, textarea {
      background: var(--bg-elevated) !important;
      border: 1px solid var(--border) !important;
      color: var(--text-primary) !important;
      font-family: 'DM Sans', sans-serif;
      outline: none !important;
      transition: border-color 0.2s;
    }
    input:focus, select:focus, textarea:focus {
      border-color: rgba(249,115,22,0.5) !important;
      box-shadow: 0 0 0 3px rgba(249,115,22,0.08) !important;
    }
    input::placeholder, textarea::placeholder { color: #64748b; }
    select option { background: #1e293b; }

    .tag {
      font-family: 'JetBrains Mono', monospace;
      font-size: 11px;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--orange);
      border: 1px solid rgba(249,115,22,0.25);
      background: rgba(249,115,22,0.06);
      padding: 3px 10px;
      border-radius: 4px;
      display: inline-block;
    }

    .metric-card {
      border-left: 3px solid var(--orange);
      background: linear-gradient(135deg, rgba(249,115,22,0.05), transparent);
    }
  </style>
</head>
<body>

<!-- ═══════════════════════════════════════════
     NAV
═══════════════════════════════════════════ -->
<nav class="fixed top-0 left-0 right-0 z-50 border-b" style="background:rgba(10,15,30,0.85);border-color:var(--border);">
  <div class="max-w-6xl mx-auto px-6 py-4 flex items-center justify-between">
    <div class="flex items-center gap-3">
      <div class="w-8 h-8 rounded flex items-center justify-center" style="background:var(--orange);">
        <svg width="18" height="18" viewBox="0 0 18 18" fill="none">
          <rect x="2" y="2" width="6" height="6" fill="white" opacity="0.9"/>
          <rect x="10" y="2" width="6" height="6" fill="white" opacity="0.6"/>
          <rect x="2" y="10" width="6" height="6" fill="white" opacity="0.6"/>
          <rect x="10" y="10" width="6" height="6" fill="white" opacity="0.9"/>
        </svg>
      </div>
      <span class="font-display text-2xl tracking-widest" style="color:var(--text-primary);">SNCIO</span>
      <span class="hidden sm:block font-mono text-xs" style="color:var(--text-muted);">/ Industrial Optimization</span>
    </div>
    <a href="#contact" class="btn-orange px-5 py-2 rounded-lg text-sm font-semibold">Book Free Call</a>
  </div>
</nav>

<!-- ═══════════════════════════════════════════
     HERO
═══════════════════════════════════════════ -->
<section class="blueprint-bg noise-overlay relative min-h-screen flex items-center pt-20" style="position:relative;">
  <!-- Decorative orange gradient orb -->
  <div class="absolute top-0 right-0 w-[600px] h-[600px] rounded-full pointer-events-none" style="background:radial-gradient(circle at 70% 30%, rgba(249,115,22,0.12), transparent 70%);"></div>
  <div class="absolute bottom-0 left-0 w-[400px] h-[400px] rounded-full pointer-events-none" style="background:radial-gradient(circle at 30% 70%, rgba(59,130,246,0.08), transparent 70%);"></div>

  <div class="max-w-6xl mx-auto px-6 py-24 relative z-10">
    <div class="grid lg:grid-cols-2 gap-16 items-center">

      <!-- Copy -->
      <div>
        <div class="tag mb-6">Gujarat GIDC · MSME Specialists</div>
        <h1 class="font-display leading-none mb-6" style="font-size:clamp(3rem,7vw,5.5rem);letter-spacing:0.02em;">
          YOUR PLANT FLOOR<br/>
          <span style="color:var(--orange);" class="orange-glow">LEAKS 15–30%</span><br/>
          OF YOUR PROFIT.<br/>
          <span style="color:var(--text-muted);">EVERY. SINGLE. DAY.</span>
        </h1>
        <p class="text-lg mb-4" style="color:var(--text-muted);line-height:1.7;max-width:500px;">
          A chaotic floor plan isn't just an inconvenience — it's a <strong style="color:var(--text-primary);">Permanent Tax</strong> on every rupee you earn. Wasted motion, blocked material flow, and idle capacity silently drain your margins.
        </p>
        <p class="text-base mb-10" style="color:var(--text-muted);max-width:500px;">
          SNCIO brings <strong style="color:var(--text-primary);">North American industrial engineering precision</strong> to Gujarat's GIDC clusters — and thanks to the MSME Lean Scheme, you pay just <strong style="color:var(--orange);">10% of our fee.</strong>
        </p>
        <div class="flex flex-wrap gap-4">
          <a href="#contact" class="btn-orange px-8 py-4 rounded-xl text-base inline-block">
            → Book Free 30-Min Plant Efficiency Call
          </a>
          <a href="#system" class="btn-outline px-6 py-4 rounded-xl text-base inline-block">
            How It Works
          </a>
        </div>
        <p class="mt-5 font-mono text-xs" style="color:#64748b;">No obligation. No sales pitch. Just a diagnosis.</p>
      </div>

      <!-- Blueprint Image Placeholder -->
      <div class="relative">
        <div class="card blue-glow overflow-hidden" style="aspect-ratio:4/3;background:linear-gradient(135deg,#0d1829,#0f172a);">
          <!-- Blueprint grid lines -->
          <svg class="absolute inset-0 w-full h-full" viewBox="0 0 480 360" xmlns="http://www.w3.org/2000/svg" opacity="0.7">
            <defs>
              <pattern id="grid-sm" width="20" height="20" patternUnits="userSpaceOnUse">
                <path d="M 20 0 L 0 0 0 20" fill="none" stroke="rgba(59,130,246,0.15)" stroke-width="0.5"/>
              </pattern>
              <pattern id="grid-lg" width="80" height="80" patternUnits="userSpaceOnUse">
                <path d="M 80 0 L 0 0 0 80" fill="none" stroke="rgba(59,130,246,0.25)" stroke-width="1"/>
              </pattern>
            </defs>
            <rect width="480" height="360" fill="url(#grid-sm)"/>
            <rect width="480" height="360" fill="url(#grid-lg)"/>
            <!-- Plant layout sketch -->
            <rect x="40" y="40" width="180" height="120" fill="rgba(59,130,246,0.07)" stroke="rgba(59,130,246,0.4)" stroke-width="1.5"/>
            <text x="130" y="105" text-anchor="middle" fill="rgba(148,163,184,0.6)" font-family="monospace" font-size="10">MACHINING</text>
            <rect x="240" y="40" width="200" height="80" fill="rgba(59,130,246,0.07)" stroke="rgba(59,130,246,0.4)" stroke-width="1.5"/>
            <text x="340" y="85" text-anchor="middle" fill="rgba(148,163,184,0.6)" font-family="monospace" font-size="10">ASSEMBLY</text>
            <rect x="40" y="180" width="100" height="90" fill="rgba(59,130,246,0.07)" stroke="rgba(59,130,246,0.4)" stroke-width="1.5"/>
            <text x="90" y="230" text-anchor="middle" fill="rgba(148,163,184,0.6)" font-family="monospace" font-size="10">STORE</text>
            <rect x="160" y="180" width="120" height="90" fill="rgba(59,130,246,0.07)" stroke="rgba(59,130,246,0.4)" stroke-width="1.5"/>
            <text x="220" y="230" text-anchor="middle" fill="rgba(148,163,184,0.6)" font-family="monospace" font-size="10">QUALITY</text>
            <rect x="300" y="140" width="140" height="130" fill="rgba(59,130,246,0.07)" stroke="rgba(59,130,246,0.4)" stroke-width="1.5"/>
            <text x="370" y="210" text-anchor="middle" fill="rgba(148,163,184,0.6)" font-family="monospace" font-size="10">DISPATCH</text>
            <!-- Flow arrows -->
            <path d="M 130 160 L 130 180" stroke="rgba(249,115,22,0.6)" stroke-width="1.5" stroke-dasharray="4 3" marker-end="url(#arr)"/>
            <path d="M 220 120 L 300 160" stroke="rgba(249,115,22,0.6)" stroke-width="1.5" stroke-dasharray="4 3"/>
            <path d="M 140 225 L 160 225" stroke="rgba(249,115,22,0.6)" stroke-width="1.5" stroke-dasharray="4 3" marker-end="url(#arr)"/>
            <path d="M 280 225 L 300 225" stroke="rgba(249,115,22,0.6)" stroke-width="1.5" stroke-dasharray="4 3" marker-end="url(#arr)"/>
            <defs>
              <marker id="arr" markerWidth="6" markerHeight="6" refX="3" refY="3" orient="auto">
                <path d="M0,0 L0,6 L6,3 z" fill="rgba(249,115,22,0.7)"/>
              </marker>
            </defs>
            <!-- Dimension lines -->
            <line x1="40" y1="30" x2="220" y2="30" stroke="rgba(59,130,246,0.3)" stroke-width="0.8" stroke-dasharray="3 3"/>
            <text x="130" y="26" text-anchor="middle" fill="rgba(59,130,246,0.6)" font-family="monospace" font-size="8">48.0 m</text>
          </svg>
          <!-- Overlay label -->
          <div class="absolute bottom-0 left-0 right-0 p-4" style="background:linear-gradient(to top, rgba(10,15,30,0.95), transparent);">
            <p class="font-mono text-xs" style="color:var(--orange);">[ REPLACE WITH YOUR PLANT BLUEPRINT / FACILITY PHOTO ]</p>
            <p class="font-mono text-xs mt-1" style="color:#475569;">Recommended: 1200×900px · High-resolution facility or CAD layout</p>
          </div>
        </div>
        <!-- Corner accent -->
        <div class="absolute -top-3 -right-3 w-16 h-16 border-t-2 border-r-2" style="border-color:var(--orange);opacity:0.6;"></div>
        <div class="absolute -bottom-3 -left-3 w-16 h-16 border-b-2 border-l-2" style="border-color:var(--blue);opacity:0.6;"></div>
      </div>

    </div>

    <!-- Metrics bar -->
    <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mt-16">
      <div class="card metric-card p-4 reveal">
        <p class="font-display text-4xl" style="color:var(--orange);">15–30%</p>
        <p class="text-sm mt-1" style="color:var(--text-muted);">Avg. profit leakage in unoptimized MSME plants</p>
      </div>
      <div class="card metric-card p-4 reveal" style="border-left-color:var(--blue);background:linear-gradient(135deg,rgba(59,130,246,0.05),transparent);">
        <p class="font-display text-4xl" style="color:var(--blue);">90%</p>
        <p class="text-sm mt-1" style="color:var(--text-muted);">Government subsidy on consultant fees via MSME Lean Scheme</p>
      </div>
      <div class="card metric-card p-4 reveal">
        <p class="font-display text-4xl" style="color:var(--orange);">3</p>
        <p class="text-sm mt-1" style="color:var(--text-muted);">Countries of industrial engineering experience: USA · Mexico · Canada</p>
      </div>
      <div class="card metric-card p-4 reveal" style="border-left-color:var(--blue);background:linear-gradient(135deg,rgba(59,130,246,0.05),transparent);">
        <p class="font-display text-4xl" style="color:var(--blue);">1 Hr</p>
        <p class="text-sm mt-1" style="color:var(--text-muted);">Gemba Walk audit to pinpoint your biggest bottleneck</p>
      </div>
    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════
     GLOBAL CREDENTIALS
═══════════════════════════════════════════ -->
<section class="py-16 border-y diagonal-stripe" style="border-color:var(--border);">
  <div class="max-w-6xl mx-auto px-6">
    <div class="flex flex-col md:flex-row items-center gap-8 md:gap-16">
      <div class="flex-shrink-0">
        <div class="tag">Global Pedigree</div>
        <h2 class="font-display text-3xl mt-3">NORTH AMERICAN<br/>PRECISION. INDIAN GROUND.</h2>
      </div>
      <div class="h-px md:h-12 md:w-px w-full" style="background:var(--border);"></div>
      <div class="flex flex-wrap gap-6 items-center">

        <div class="flex items-center gap-3 card px-5 py-3">
          <span class="text-3xl">🇺🇸</span>
          <div>
            <p class="font-semibold text-sm">United States</p>
            <p class="font-mono text-xs" style="color:var(--text-muted);">Lean · Six Sigma · TPS</p>
          </div>
        </div>

        <div class="flex items-center gap-3 card px-5 py-3">
          <span class="text-3xl">🇲🇽</span>
          <div>
            <p class="font-semibold text-sm">Mexico</p>
            <p class="font-mono text-xs" style="color:var(--text-muted);">Maquiladora · Assembly Ops</p>
          </div>
        </div>

        <div class="flex items-center gap-3 card px-5 py-3">
          <span class="text-3xl">🇨🇦</span>
          <div>
            <p class="font-semibold text-sm">Canada</p>
            <p class="font-mono text-xs" style="color:var(--text-muted);">Process Optimization · EHS</p>
          </div>
        </div>

        <div class="flex items-center gap-3 card px-5 py-3" style="border-color:rgba(249,115,22,0.3);">
          <span class="text-3xl">🇮🇳</span>
          <div>
            <p class="font-semibold text-sm">India — GIDC</p>
            <p class="font-mono text-xs" style="color:var(--orange);">MSME Lean Scheme Qualified</p>
          </div>
        </div>

      </div>
    </div>
    <p class="mt-8 text-sm max-w-2xl" style="color:var(--text-muted);">
      Over a decade of hands-on industrial engineering across three of the world's most demanding manufacturing ecosystems. That cross-continental experience is now focused entirely on unlocking hidden capacity in Gujarat's GIDC clusters.
    </p>
  </div>
</section>

<!-- ═══════════════════════════════════════════
     3-STEP SYSTEM
═══════════════════════════════════════════ -->
<section id="system" class="py-24 blueprint-bg">
  <div class="max-w-6xl mx-auto px-6">
    <div class="mb-14 reveal">
      <div class="tag mb-4">The SNCIO Method</div>
      <h2 class="font-display" style="font-size:clamp(2.5rem,5vw,4rem);">THE 3-STEP<br/><span style="color:var(--orange);">OPTIMIZATION SYSTEM</span></h2>
      <p class="mt-4 max-w-xl" style="color:var(--text-muted);">We don't hand you a 200-page report and disappear. We Diagnose, Design, and Execute — on your floor, with your team.</p>
    </div>

    <div class="grid md:grid-cols-3 gap-6">

      <!-- Step 1 -->
      <div class="card p-8 reveal relative overflow-hidden">
        <div class="absolute top-0 right-0 w-24 h-24 rounded-bl-full" style="background:rgba(249,115,22,0.05);"></div>
        <div class="flex items-center gap-4 mb-6">
          <div class="w-12 h-12 rounded-xl flex items-center justify-center font-display text-2xl" style="background:rgba(249,115,22,0.12);color:var(--orange);">01</div>
          <div class="h-px flex-1" style="background:rgba(249,115,22,0.2);"></div>
        </div>
        <div class="w-10 h-10 mb-4 rounded-lg flex items-center justify-center" style="background:rgba(249,115,22,0.1);">
          <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
            <circle cx="10" cy="10" r="7" stroke="#f97316" stroke-width="1.5"/>
            <circle cx="10" cy="10" r="2" fill="#f97316"/>
            <line x1="10" y1="1" x2="10" y2="4" stroke="#f97316" stroke-width="1.5"/>
            <line x1="10" y1="16" x2="10" y2="19" stroke="#f97316" stroke-width="1.5"/>
            <line x1="1" y1="10" x2="4" y2="10" stroke="#f97316" stroke-width="1.5"/>
            <line x1="16" y1="10" x2="19" y2="10" stroke="#f97316" stroke-width="1.5"/>
          </svg>
        </div>
        <h3 class="font-display text-3xl mb-2">THE AUDIT</h3>
        <p class="font-mono text-xs mb-4" style="color:var(--orange);">DIAGNOSE</p>
        <p class="text-sm mb-5" style="color:var(--text-muted);line-height:1.7;">
          We conduct a structured <strong style="color:var(--text-primary);">1-Hour Gemba Walk</strong> — a live, on-floor inspection that goes beyond paperwork. We map actual material flow, measure walk distances, identify bottlenecks, and quantify the hidden cost of your current layout.
        </p>
        <ul class="space-y-2">
          <li class="flex items-start gap-2 text-sm" style="color:var(--text-muted);"><span style="color:var(--orange);">→</span> Flow & bottleneck mapping</li>
          <li class="flex items-start gap-2 text-sm" style="color:var(--text-muted);"><span style="color:var(--orange);">→</span> WIP & inventory pile-up analysis</li>
          <li class="flex items-start gap-2 text-sm" style="color:var(--text-muted);"><span style="color:var(--orange);">→</span> Quantified profit-leakage report</li>
        </ul>
      </div>

      <!-- Step 2 -->
      <div class="card p-8 reveal relative overflow-hidden" style="border-color:rgba(59,130,246,0.25);">
        <div class="absolute top-0 right-0 w-24 h-24 rounded-bl-full" style="background:rgba(59,130,246,0.05);"></div>
        <div class="flex items-center gap-4 mb-6">
          <div class="w-12 h-12 rounded-xl flex items-center justify-center font-display text-2xl" style="background:rgba(59,130,246,0.12);color:var(--blue);">02</div>
          <div class="h-px flex-1" style="background:rgba(59,130,246,0.2);"></div>
        </div>
        <div class="w-10 h-10 mb-4 rounded-lg flex items-center justify-center" style="background:rgba(59,130,246,0.1);">
          <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
            <rect x="2" y="2" width="7" height="7" stroke="#3b82f6" stroke-width="1.5"/>
            <rect x="11" y="2" width="7" height="7" stroke="#3b82f6" stroke-width="1.5" opacity="0.5"/>
            <rect x="2" y="11" width="7" height="7" stroke="#3b82f6" stroke-width="1.5" opacity="0.5"/>
            <rect x="11" y="11" width="7" height="7" stroke="#3b82f6" stroke-width="1.5"/>
          </svg>
        </div>
        <h3 class="font-display text-3xl mb-2">THE BLUEPRINT</h3>
        <p class="font-mono text-xs mb-4" style="color:var(--blue);">DESIGN</p>
        <p class="text-sm mb-5" style="color:var(--text-muted);line-height:1.7;">
          We deliver a <strong style="color:var(--text-primary);">CAD-based optimized floor plan</strong> — not a generic template, but a precise layout engineered for your specific product mix, machinery, and growth plan. Every square foot justified.
        </p>
        <ul class="space-y-2">
          <li class="flex items-start gap-2 text-sm" style="color:var(--text-muted);"><span style="color:var(--blue);">→</span> AutoCAD facility layout drawings</li>
          <li class="flex items-start gap-2 text-sm" style="color:var(--text-muted);"><span style="color:var(--blue);">→</span> Material flow optimization model</li>
          <li class="flex items-start gap-2 text-sm" style="color:var(--text-muted);"><span style="color:var(--blue);">→</span> Machine placement & aisle design</li>
        </ul>
      </div>

      <!-- Step 3 -->
      <div class="card p-8 reveal relative overflow-hidden">
        <div class="absolute top-0 right-0 w-24 h-24 rounded-bl-full" style="background:rgba(249,115,22,0.05);"></div>
        <div class="flex items-center gap-4 mb-6">
          <div class="w-12 h-12 rounded-xl flex items-center justify-center font-display text-2xl" style="background:rgba(249,115,22,0.12);color:var(--orange);">03</div>
          <div class="h-px flex-1" style="background:rgba(249,115,22,0.2);"></div>
        </div>
        <div class="w-10 h-10 mb-4 rounded-lg flex items-center justify-center" style="background:rgba(249,115,22,0.1);">
          <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
            <path d="M4 16 L4 8 L10 4 L16 8 L16 16 Z" stroke="#f97316" stroke-width="1.5" fill="none"/>
            <line x1="8" y1="16" x2="8" y2="11" stroke="#f97316" stroke-width="1.5"/>
            <line x1="12" y1="16" x2="12" y2="11" stroke="#f97316" stroke-width="1.5"/>
            <line x1="8" y1="11" x2="12" y2="11" stroke="#f97316" stroke-width="1.5"/>
          </svg>
        </div>
        <h3 class="font-display text-3xl mb-2">THE BUILD</h3>
        <p class="font-mono text-xs mb-4" style="color:var(--orange);">EXECUTE</p>
        <p class="text-sm mb-5" style="color:var(--text-muted);line-height:1.7;">
          We don't leave you with a blueprint and good luck. Our team manages <strong style="color:var(--text-primary);">on-ground implementation</strong> — supervising equipment relocation, establishing new SOPs, and training your workforce so gains are permanent.
        </p>
        <ul class="space-y-2">
          <li class="flex items-start gap-2 text-sm" style="color:var(--text-muted);"><span style="color:var(--orange);">→</span> Supervised floor rearrangement</li>
          <li class="flex items-start gap-2 text-sm" style="color:var(--text-muted);"><span style="color:var(--orange);">→</span> SOP creation & visual management</li>
          <li class="flex items-start gap-2 text-sm" style="color:var(--text-muted);"><span style="color:var(--orange);">→</span> Workforce training & Kaizen culture</li>
        </ul>
      </div>

    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════
     90% SUBSIDY BLOCK
═══════════════════════════════════════════ -->
<section class="py-24" style="background:var(--bg-card);">
  <div class="max-w-6xl mx-auto px-6">
    <div class="reveal" style="background:linear-gradient(135deg, rgba(249,115,22,0.08), rgba(249,115,22,0.02)); border:1px solid rgba(249,115,22,0.25); border-radius:20px; overflow:hidden; position:relative;">
      
      <!-- Diagonal stripe accent -->
      <div class="absolute top-0 right-0 w-1/3 h-full diagonal-stripe opacity-50" style="border-left:1px dashed rgba(249,115,22,0.15);"></div>

      <div class="p-10 md:p-14 grid md:grid-cols-2 gap-12 items-center relative z-10">
        <div>
          <div class="tag mb-5">Government of India · MSME Ministry</div>
          <h2 class="font-display mb-4" style="font-size:clamp(2rem,4vw,3.5rem);">WORLD-CLASS CONSULTING.<br/><span style="color:var(--orange);">AT 1/10TH THE COST.</span></h2>
          <p class="mb-6" style="color:var(--text-muted);line-height:1.7;">
            SNCIO is an approved consultant under the <strong style="color:var(--text-primary);">MSME Competitive (LEAN) Scheme</strong>. This means the Ministry of MSME, Government of India, subsidizes up to 90% of the consulting fee — directly.
          </p>
          <p style="color:var(--text-muted);line-height:1.7;">
            The scheme is designed specifically to help MSMEs implement Lean Manufacturing. If you're a registered MSME in Gujarat, you almost certainly qualify. We handle all the paperwork.
          </p>
          <div class="mt-8 flex gap-4">
            <a href="#contact" class="btn-orange px-6 py-3 rounded-xl text-sm inline-block">Check Your Eligibility →</a>
          </div>
        </div>

        <div class="space-y-4">
          <!-- Cost comparison card -->
          <div class="card-elevated p-6 rounded-2xl">
            <p class="font-mono text-xs mb-4" style="color:var(--text-muted);">// COST COMPARISON</p>
            <div class="flex items-end gap-4 mb-3">
              <div>
                <p class="text-sm" style="color:var(--text-muted);">Standard Market Rate</p>
                <p class="font-display text-4xl" style="color:#64748b;text-decoration:line-through;text-decoration-color:rgba(239,68,68,0.7);">₹5,00,000</p>
              </div>
              <div class="text-2xl mb-1" style="color:var(--orange);">→</div>
              <div>
                <p class="text-sm" style="color:var(--text-muted);">Your net cost</p>
                <p class="font-display text-4xl" style="color:var(--orange);">₹50,000</p>
              </div>
            </div>
            <div class="h-3 rounded-full overflow-hidden" style="background:rgba(148,163,184,0.1);">
              <div class="h-full rounded-full" style="width:10%;background:var(--orange);"></div>
            </div>
            <p class="font-mono text-xs mt-2" style="color:var(--text-muted);">You pay 10% → GOI covers 90%</p>
          </div>

          <!-- Features list -->
          <div class="grid grid-cols-2 gap-3">
            <div class="card p-4 text-center">
              <p class="font-display text-2xl" style="color:var(--orange);">₹0</p>
              <p class="text-xs mt-1" style="color:var(--text-muted);">Subsidy Application Fee</p>
            </div>
            <div class="card p-4 text-center">
              <p class="font-display text-2xl" style="color:var(--orange);">100%</p>
              <p class="text-xs mt-1" style="color:var(--text-muted);">Documentation Handled by Us</p>
            </div>
          </div>

          <!-- Pulse badge -->
          <div class="pulse-badge card p-4 flex items-center gap-3" style="border-color:rgba(249,115,22,0.4);">
            <div class="w-3 h-3 rounded-full flex-shrink-0" style="background:var(--orange);"></div>
            <p class="text-sm"><strong>Scheme is active and funded.</strong> <span style="color:var(--text-muted);">Limited slots per cluster per quarter.</span></p>
          </div>
        </div>

      </div>
    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════
     BEFORE / AFTER LAYOUT PROOF
═══════════════════════════════════════════ -->
<section class="py-24 blueprint-bg">
  <div class="max-w-6xl mx-auto px-6">
    <div class="mb-12 reveal">
      <div class="tag mb-4">Logic Proof</div>
      <h2 class="font-display" style="font-size:clamp(2rem,4vw,3.5rem);">THE FLOOR PLAN<br/><span style="color:var(--orange);">TRANSFORMATION</span></h2>
      <p class="mt-3 max-w-lg" style="color:var(--text-muted);">The same 5,000 sq ft. Two completely different financial outcomes. The difference is systematic layout engineering.</p>
    </div>

    <div class="grid md:grid-cols-2 gap-8">

      <!-- BEFORE -->
      <div class="reveal">
        <div class="flex items-center gap-3 mb-4">
          <div class="w-3 h-3 rounded-full" style="background:#ef4444;"></div>
          <p class="font-display text-2xl" style="color:#ef4444;">BEFORE — THE CHAOS TAX</p>
        </div>
        <div class="card p-4" style="border-color:rgba(239,68,68,0.2);">
          <svg viewBox="0 0 400 280" xmlns="http://www.w3.org/2000/svg" style="width:100%;height:auto;">
            <defs>
              <pattern id="bg-before" width="20" height="20" patternUnits="userSpaceOnUse">
                <path d="M 20 0 L 0 0 0 20" fill="none" stroke="rgba(59,130,246,0.08)" stroke-width="0.5"/>
              </pattern>
              <marker id="arr-red" markerWidth="6" markerHeight="6" refX="3" refY="3" orient="auto">
                <path d="M0,0 L0,6 L6,3 z" fill="rgba(239,68,68,0.8)"/>
              </marker>
            </defs>
            <rect width="400" height="280" fill="url(#bg-before)"/>
            <!-- Outer wall -->
            <rect x="10" y="10" width="380" height="260" fill="none" stroke="rgba(148,163,184,0.3)" stroke-width="2"/>
            <!-- Rooms - chaotic placement -->
            <rect x="20" y="20" width="90" height="100" class="blueprint-room"/>
            <text x="65" y="72" text-anchor="middle" class="blueprint-text">RAW STORE</text>
            <rect x="200" y="20" width="180" height="70" class="blueprint-room"/>
            <text x="290" y="58" text-anchor="middle" class="blueprint-text">MACHINING</text>
            <rect x="20" y="140" width="160" height="80" class="blueprint-room"/>
            <text x="100" y="183" text-anchor="middle" class="blueprint-text">ASSEMBLY</text>
            <rect x="240" y="140" width="140" height="80" class="blueprint-room"/>
            <text x="310" y="183" text-anchor="middle" class="blueprint-text">QUALITY</text>
            <rect x="120" y="20" width="60" height="100" class="blueprint-room"/>
            <text x="150" y="72" text-anchor="middle" class="blueprint-text">WIP</text>
            <rect x="20" y="240" width="360" height="25" class="blueprint-room"/>
            <text x="200" y="255" text-anchor="middle" class="blueprint-text">DISPATCH (BACK WALL)</text>
            <!-- Chaotic flow arrows - criss-crossing -->
            <path d="M 65 120 Q 290 135 290 140" stroke="rgba(239,68,68,0.7)" stroke-width="1.5" stroke-dasharray="5 3" fill="none" marker-end="url(#arr-red)"/>
            <path d="M 290 90 Q 150 120 100 140" stroke="rgba(239,68,68,0.7)" stroke-width="1.5" stroke-dasharray="5 3" fill="none" marker-end="url(#arr-red)"/>
            <path d="M 180 180 Q 230 200 240 180" stroke="rgba(239,68,68,0.7)" stroke-width="1.5" stroke-dasharray="5 3" fill="none" marker-end="url(#arr-red)"/>
            <path d="M 310 220 Q 200 232 30 240" stroke="rgba(239,68,68,0.7)" stroke-width="1.5" stroke-dasharray="5 3" fill="none" marker-end="url(#arr-red)"/>
            <!-- Distance annotation -->
            <text x="200" y="130" text-anchor="middle" fill="rgba(239,68,68,0.8)" font-family="monospace" font-size="9">⚠ avg. material travel: 480m/day</text>
          </svg>
          <div class="mt-3 space-y-2">
            <div class="flex items-center gap-2"><div class="w-2 h-2 rounded-full" style="background:#ef4444;"></div><p class="text-sm" style="color:var(--text-muted);">Raw store & dispatch at opposite ends — 120m wasted per pallet</p></div>
            <div class="flex items-center gap-2"><div class="w-2 h-2 rounded-full" style="background:#ef4444;"></div><p class="text-sm" style="color:var(--text-muted);">WIP island creates cross-traffic and collision risk</p></div>
            <div class="flex items-center gap-2"><div class="w-2 h-2 rounded-full" style="background:#ef4444;"></div><p class="text-sm" style="color:var(--text-muted);">Quality checkpoint at dead-end — rework doubles handling cost</p></div>
          </div>
        </div>
      </div>

      <!-- AFTER -->
      <div class="reveal">
        <div class="flex items-center gap-3 mb-4">
          <div class="w-3 h-3 rounded-full" style="background:#22c55e;"></div>
          <p class="font-display text-2xl" style="color:#22c55e;">AFTER — THE OPTIMIZED FLOW</p>
        </div>
        <div class="card p-4" style="border-color:rgba(34,197,94,0.2);">
          <svg viewBox="0 0 400 280" xmlns="http://www.w3.org/2000/svg" style="width:100%;height:auto;">
            <defs>
              <pattern id="bg-after" width="20" height="20" patternUnits="userSpaceOnUse">
                <path d="M 20 0 L 0 0 0 20" fill="none" stroke="rgba(249,115,22,0.05)" stroke-width="0.5"/>
              </pattern>
              <marker id="arr-green" markerWidth="6" markerHeight="6" refX="3" refY="3" orient="auto">
                <path d="M0,0 L0,6 L6,3 z" fill="rgba(34,197,94,0.8)"/>
              </marker>
            </defs>
            <rect width="400" height="280" fill="url(#bg-after)"/>
            <rect x="10" y="10" width="380" height="260" fill="none" stroke="rgba(148,163,184,0.3)" stroke-width="2"/>
            <!-- Optimized U-shaped flow layout -->
            <rect x="20" y="20" width="80" height="240" class="blueprint-room-after"/>
            <text x="60" y="143" text-anchor="middle" class="blueprint-text">RAW STORE</text>
            <rect x="120" y="20" width="100" height="110" class="blueprint-room-after"/>
            <text x="170" y="78" text-anchor="middle" class="blueprint-text">MACHINING</text>
            <rect x="240" y="20" width="140" height="110" class="blueprint-room-after"/>
            <text x="310" y="78" text-anchor="middle" class="blueprint-text">QUALITY</text>
            <rect x="120" y="150" width="100" height="110" class="blueprint-room-after"/>
            <text x="170" y="208" text-anchor="middle" class="blueprint-text">ASSEMBLY</text>
            <rect x="240" y="150" width="140" height="110" class="blueprint-room-after"/>
            <text x="310" y="208" text-anchor="middle" class="blueprint-text">DISPATCH</text>
            <!-- Clean linear flow -->
            <path d="M 100 80 L 120 80" stroke="rgba(34,197,94,0.8)" stroke-width="2" fill="none" marker-end="url(#arr-green)"/>
            <path d="M 220 80 L 240 80" stroke="rgba(34,197,94,0.8)" stroke-width="2" fill="none" marker-end="url(#arr-green)"/>
            <path d="M 310 130 L 310 150" stroke="rgba(34,197,94,0.8)" stroke-width="2" fill="none" marker-end="url(#arr-green)"/>
            <path d="M 240 205 L 220 205" stroke="rgba(34,197,94,0.8)" stroke-width="2" fill="none" marker-end="url(#arr-green)"/>
            <path d="M 120 205 L 100 205" stroke="rgba(34,197,94,0.8)" stroke-width="2" fill="none" marker-end="url(#arr-green)"/>
            <!-- Distance annotation -->
            <text x="200" y="270" text-anchor="middle" fill="rgba(34,197,94,0.8)" font-family="monospace" font-size="9">✓ avg. material travel: 95m/day (–80%)</text>
          </svg>
          <div class="mt-3 space-y-2">
            <div class="flex items-center gap-2"><div class="w-2 h-2 rounded-full" style="background:#22c55e;"></div><p class="text-sm" style="color:var(--text-muted);">U-shaped flow — raw in, finished out, zero cross-traffic</p></div>
            <div class="flex items-center gap-2"><div class="w-2 h-2 rounded-full" style="background:#22c55e;"></div><p class="text-sm" style="color:var(--text-muted);">Quality integrated inline — defects caught at source, not end</p></div>
            <div class="flex items-center gap-2"><div class="w-2 h-2 rounded-full" style="background:#22c55e;"></div><p class="text-sm" style="color:var(--text-muted);">80% reduction in material travel → direct throughput increase</p></div>
          </div>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════
     LEAD CAPTURE FORM
═══════════════════════════════════════════ -->
<section id="contact" class="py-24" style="background:var(--bg-card);">
  <div class="max-w-3xl mx-auto px-6">
    <div class="reveal text-center mb-12">
      <div class="tag mb-4">Free Strategy Session</div>
      <h2 class="font-display" style="font-size:clamp(2rem,4vw,3.5rem);">FIND OUT HOW MUCH<br/><span style="color:var(--orange);">YOUR LAYOUT IS COSTING YOU</span></h2>
      <p class="mt-4" style="color:var(--text-muted);">Fill in the details below. Neel Shah will personally call you within 24 hours to schedule a free, no-obligation 30-minute Plant Efficiency Review.</p>
    </div>

    <div class="card reveal p-8 md:p-10" style="border-color:rgba(249,115,22,0.2);">
      <form onsubmit="handleSubmit(event)">
        <div class="grid md:grid-cols-2 gap-5 mb-5">
          <div>
            <label class="block text-sm font-medium mb-2" style="color:var(--text-muted);">Full Name *</label>
            <input type="text" placeholder="Rajesh Patel" required class="w-full px-4 py-3 rounded-xl text-sm" style="border-radius:10px;"/>
          </div>
          <div>
            <label class="block text-sm font-medium mb-2" style="color:var(--text-muted);">Company / Factory Name *</label>
            <input type="text" placeholder="Patel Engineering Works Pvt. Ltd." required class="w-full px-4 py-3 rounded-xl text-sm" style="border-radius:10px;"/>
          </div>
        </div>

        <div class="grid md:grid-cols-2 gap-5 mb-5">
          <div>
            <label class="block text-sm font-medium mb-2" style="color:var(--text-muted);">Mobile Number *</label>
            <input type="tel" placeholder="+91 98765 43210" required class="w-full px-4 py-3 rounded-xl text-sm" style="border-radius:10px;"/>
          </div>
          <div>
            <label class="block text-sm font-medium mb-2" style="color:var(--text-muted);">Email Address</label>
            <input type="email" placeholder="rajesh@paateleng.com" class="w-full px-4 py-3 rounded-xl text-sm" style="border-radius:10px;"/>
          </div>
        </div>

        <div class="mb-5">
          <label class="block text-sm font-medium mb-2" style="color:var(--text-muted);">GIDC Location / Industrial Cluster *</label>
          <select required class="w-full px-4 py-3 rounded-xl text-sm" style="border-radius:10px;">
            <option value="" disabled selected>Select your GIDC cluster...</option>
            <option>Vatva, Ahmedabad</option>
            <option>Naroda, Ahmedabad</option>
            <option>Odhav, Ahmedabad</option>
            <option>Changodar, Ahmedabad</option>
            <option>GIDC Rajkot (Aji / Shapar)</option>
            <option>GIDC Surat</option>
            <option>GIDC Vadodara (Makarpura)</option>
            <option>GIDC Anand</option>
            <option>GIDC Vapi</option>
            <option>GIDC Bhavnagar</option>
            <option>Other Gujarat GIDC Cluster</option>
          </select>
        </div>

        <div class="mb-5">
          <label class="block text-sm font-medium mb-2" style="color:var(--text-muted);">Industry / Manufacturing Type *</label>
          <select required class="w-full px-4 py-3 rounded-xl text-sm" style="border-radius:10px;">
            <option value="" disabled selected>Select your industry...</option>
            <option>Engineering & Fabrication</option>
            <option>Auto Components & Parts</option>
            <option>Chemicals & Pharmaceuticals</option>
            <option>Plastics & Rubber</option>
            <option>Textiles & Garments</option>
            <option>Ceramics & Building Materials</option>
            <option>Food Processing & Packaging</option>
            <option>Electronics & Electrical</option>
            <option>Diamond & Jewellery</option>
            <option>Other Manufacturing</option>
          </select>
        </div>

        <div class="mb-6">
          <label class="block text-sm font-medium mb-3" style="color:var(--text-muted);">What best describes your current situation? *</label>
          <div class="grid md:grid-cols-3 gap-3">
            <label class="cursor-pointer">
              <input type="radio" name="situation" value="existing" class="sr-only peer" required/>
              <div class="card peer-checked:border-orange-500 peer-checked:bg-orange-500/10 p-3 text-center text-sm transition-all cursor-pointer hover:border-orange-400" style="border-radius:10px;--tw-border-opacity:1;">
                <p class="text-lg mb-1">🏭</p>
                <p class="font-medium text-sm">Optimizing existing plant</p>
              </div>
            </label>
            <label class="cursor-pointer">
              <input type="radio" name="situation" value="expanding" class="sr-only peer"/>
              <div class="card peer-checked:border-orange-500 peer-checked:bg-orange-500/10 p-3 text-center text-sm transition-all cursor-pointer hover:border-orange-400" style="border-radius:10px;">
                <p class="text-lg mb-1">📈</p>
                <p class="font-medium text-sm">Expanding / adding capacity</p>
              </div>
            </label>
            <label class="cursor-pointer">
              <input type="radio" name="situation" value="new" class="sr-only peer"/>
              <div class="card peer-checked:border-orange-500 peer-checked:bg-orange-500/10 p-3 text-center text-sm transition-all cursor-pointer hover:border-orange-400" style="border-radius:10px;">
                <p class="text-lg mb-1">🏗️</p>
                <p class="font-medium text-sm">Setting up new plant</p>
              </div>
            </label>
          </div>
        </div>

        <div class="mb-8">
          <label class="block text-sm font-medium mb-2" style="color:var(--text-muted);">Biggest operational challenge (optional)</label>
          <textarea rows="3" placeholder="e.g. 'Our material takes 2 hours to move from store to assembly. We can't figure out why output is inconsistent despite having the machines...'" class="w-full px-4 py-3 text-sm resize-none" style="border-radius:10px;"></textarea>
        </div>

        <button type="submit" class="btn-orange w-full py-4 rounded-xl text-base font-semibold">
          → Request My Free 30-Minute Plant Efficiency Call
        </button>
        <p class="text-center mt-3 font-mono text-xs" style="color:#64748b;">No spam. No hard sell. Neel calls personally within 24 hours.</p>
      </form>
    </div>

    <!-- Success message (hidden by default) -->
    <div id="success-msg" class="hidden card p-8 text-center mt-6" style="border-color:rgba(34,197,94,0.3);background:rgba(34,197,94,0.05);">
      <div class="text-4xl mb-4">✅</div>
      <h3 class="font-display text-3xl mb-2" style="color:#22c55e;">REQUEST RECEIVED</h3>
      <p style="color:var(--text-muted);">Neel Shah will personally contact you within 24 hours to schedule your free Plant Efficiency Review. Please keep your mobile on.</p>
    </div>

  </div>
</section>

<!-- ═══════════════════════════════════════════
     FOOTER
═══════════════════════════════════════════ -->
<footer class="border-t py-12" style="border-color:var(--border);background:var(--bg-deep);">
  <div class="max-w-6xl mx-auto px-6">
    <div class="grid md:grid-cols-3 gap-10 mb-10">
      <div>
        <div class="flex items-center gap-3 mb-4">
          <div class="w-8 h-8 rounded flex items-center justify-center" style="background:var(--orange);">
            <svg width="16" height="16" viewBox="0 0 18 18" fill="none">
              <rect x="2" y="2" width="6" height="6" fill="white" opacity="0.9"/>
              <rect x="10" y="2" width="6" height="6" fill="white" opacity="0.6"/>
              <rect x="2" y="10" width="6" height="6" fill="white" opacity="0.6"/>
              <rect x="10" y="10" width="6" height="6" fill="white" opacity="0.9"/>
            </svg>
          </div>
          <span class="font-display text-xl tracking-widest">SNCIO</span>
        </div>
        <p class="text-sm leading-relaxed" style="color:var(--text-muted);">Supply-Network-Centric Industrial Optimization. Bringing North American manufacturing discipline to India's MSME industrial clusters.</p>
      </div>

      <div>
        <h4 class="font-display text-lg mb-4" style="color:var(--orange);">CONTACT</h4>
        <div class="space-y-3">
          <div>
            <p class="text-sm font-semibold">Neel Shah</p>
            <p class="font-mono text-xs" style="color:var(--text-muted);">Principal Consultant · MSME Lean Scheme Qualified</p>
          </div>
          <a href="mailto:neels@sncio.in" class="font-mono text-sm block hover:underline" style="color:var(--orange);">neels@sncio.in</a>
          <p class="font-mono text-xs" style="color:var(--text-muted);">Gujarat, India (Serving all GIDC clusters)</p>
        </div>
      </div>

      <div>
        <h4 class="font-display text-lg mb-4" style="color:var(--blue);">SERVICES</h4>
        <ul class="space-y-2">
          <li class="font-mono text-xs" style="color:var(--text-muted);">→ Plant Layout Optimization</li>
          <li class="font-mono text-xs" style="color:var(--text-muted);">→ Lean Manufacturing Implementation</li>
          <li class="font-mono text-xs" style="color:var(--text-muted);">→ MSME Lean Scheme Consulting</li>
          <li class="font-mono text-xs" style="color:var(--text-muted);">→ New Plant Greenfield Design</li>
          <li class="font-mono text-xs" style="color:var(--text-muted);">→ Workforce & SOP Training</li>
        </ul>
      </div>
    </div>

    <div class="border-t pt-6 flex flex-col md:flex-row items-center justify-between gap-4" style="border-color:var(--border);">
      <p class="font-mono text-xs" style="color:#475569;">© 2025 SNCIO. All rights reserved. MSME Lean Scheme Approved Consultant.</p>
      <div class="flex gap-2 items-center">
        <span class="text-xs" style="color:#475569;">Serving</span>
        <span>🇮🇳</span><span>🇺🇸</span><span>🇲🇽</span><span>🇨🇦</span>
      </div>
    </div>
  </div>
</footer>

<script>
  // Scroll reveal
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) { e.target.classList.add('visible'); observer.unobserve(e.target); }
    });
  }, { threshold: 0.12 });
  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

  // Form submit
  function handleSubmit(e) {
    e.preventDefault();
    const radios = document.querySelectorAll('input[name="situation"]');
    const checked = Array.from(radios).some(r => r.checked);
    if (!checked) { alert('Please select your current situation.'); return; }
    e.target.closest('form').parentElement.innerHTML = document.getElementById('success-msg').outerHTML.replace('hidden ','');
  }

  // Radio card styling
  document.querySelectorAll('input[type="radio"]').forEach(radio => {
    radio.addEventListener('change', () => {
      document.querySelectorAll('input[name="situation"]').forEach(r => {
        const div = r.nextElementSibling;
        div.style.borderColor = '';
        div.style.background = '';
      });
      const div = radio.nextElementSibling;
      div.style.borderColor = 'var(--orange)';
      div.style.background = 'rgba(249,115,22,0.08)';
    });
  });
</script>
</body>
</html>
