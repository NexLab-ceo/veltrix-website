<script lang="ts">
  import { ArrowDownRight, ArrowRight, ArrowUpRight, Activity, Bot, Box, Check, ChevronDown, CircleHelp, Code2, Command, Cpu, ExternalLink, GitBranch, Github, Globe2, HardDrive, Layers3, Menu, Network, Play, Rocket, Server, ShieldCheck, Smartphone, Terminal, X, Zap } from 'lucide-svelte';
  let menuOpen = $state(false);
  let activeFaq = $state(0);
  const features = [
    {icon:Server,title:'Android hosting',desc:'Turn the device in your pocket into a place where your projects can live.',tag:'CORE',kind:'host'},
    {icon:Layers3,title:'Project management',desc:'Keep applications, environments and project settings in one clear workspace.',tag:'WORKSPACE',kind:'projects'},
    {icon:Rocket,title:'Deployments',desc:'Move from source code to a running application with a workflow built for Android.',tag:'DELIVERY',kind:'deploy'},
    {icon:Bot,title:'AI agents',desc:'A future layer of specialized agents to help build, ship and maintain projects.',tag:'COMING SOON',kind:'agents'},
    {icon:Cpu,title:'Build management',desc:'See build jobs, output and available execution methods in one place.',tag:'BUILD',kind:'build'},
    {icon:Activity,title:'Monitoring',desc:'Understand device load, memory, storage and the activity of your apps.',tag:'VISIBILITY',kind:'monitor'},
    {icon:GitBranch,title:'Git integration',desc:'Bring your repositories into the same workflow as your deployments.',tag:'SOURCE',kind:'git'},
    {icon:Box,title:'Templates',desc:'Start from practical project templates instead of a blank directory.',tag:'STARTER KIT',kind:'templates'},
    {icon:Terminal,title:'Logs & events',desc:'A clear timeline of what happened across your projects and services.',tag:'OBSERVABILITY',kind:'logs'}
  ];
  const faqs = [
    {q:'What is Yevqo?',a:'Yevqo is a platform designed to turn an Android device into a personal server environment. A lightweight agent runs in Termux while a web interface provides a place to manage projects and applications.'},
    {q:'Why Termux?',a:'Termux provides a Linux-like command-line environment on Android without requiring root access for typical workflows. It gives Yevqo a practical foundation for running tools and project processes directly on your device.'},
    {q:'Can I host websites on Android?',a:'Yes, Android can run web servers and suitable applications through Termux. Public reachability depends on your network, carrier, device power settings and how you configure access.'},
    {q:'Do I need a VPS?',a:'No dedicated VPS is required to get started. Your Android device is the machine running the workloads. A VPS or external tunnel may still be useful for stable public access.'},
    {q:'Does Yevqo support AI agents?',a:'AI agents are part of the product direction and are planned for a future release. They are not presented as an available feature today.'},
    {q:'Which application templates are available?',a:'The planned starter catalogue includes Static Website, Node.js, PHP and Go templates. Exact runtime requirements depend on the selected project.'},
    {q:'Can I connect multiple devices?',a:'The initial Free plan is scoped to one connected Android device. Multi-device management is a future consideration.'},
    {q:'Is Yevqo open source?',a:'Check the official Yevqo GitHub repository for the current source-code availability and licence. The website does not assume a licence that has not been published.'}
  ];
  const templates = [
    {name:'Static Website',desc:'A lightweight home for your frontend.',lang:'HTML · CSS · JS',mark:'</>'},
    {name:'Node.js',desc:'Build APIs and JavaScript services.',lang:'JavaScript · TypeScript',mark:'JS'},
    {name:'PHP',desc:'Run familiar PHP applications.',lang:'PHP',mark:'php'},
    {name:'Go',desc:'Compile and run efficient services.',lang:'Go',mark:'GO'}
  ];
</script>

<svelte:head>
  <title>Yevqo — Your Android. Your Server. Your Control.</title>
  <meta name="description" content="Turn your Android device into a personal server with Termux and Yevqo. Manage projects, applications and deployments from one dashboard." />
  <meta property="og:title" content="Yevqo — Your Android. Your Server. Your Control." />
  <meta property="og:description" content="A personal server platform powered by Android + Termux." />
</svelte:head>

<header class="topbar">
  <a class="brand" href="#top" aria-label="Yevqo home"><span class="brand-mark"><span></span><span></span><span></span></span><span>yevqo</span></a>
  <nav class:open={menuOpen} aria-label="Main navigation">
    <a href="#features" onclick={() => menuOpen = false}>Features</a><a href="#how" onclick={() => menuOpen = false}>How it works</a><a href="#templates" onclick={() => menuOpen = false}>Templates</a><a href="#docs" onclick={() => menuOpen = false}>Documentation</a><a href="#pricing" onclick={() => menuOpen = false}>Pricing</a>
  </nav>
  <div class="nav-actions"><a class="github-link" href="https://github.com/NexLab-ceo" target="_blank" rel="noreferrer"><Github size={15}/> GitHub</a><a class="signin" href="#pricing">Sign in</a><a class="button button-small" href="#how">Get started <ArrowUpRight size={14}/></a></div>
  <button class="mobile-toggle" aria-label={menuOpen ? 'Close menu' : 'Open menu'} onclick={() => menuOpen = !menuOpen}>{#if menuOpen}<X size={20}/>{:else}<Menu size={20}/>{/if}</button>
</header>

<main id="top">
  <section class="hero section-wrap">
    <div class="hero-copy">
      <div class="eyebrow"><span class="live-dot"></span> THE PERSONAL SERVER PLATFORM <span class="eyebrow-line"></span> ANDROID × TERMUX</div>
      <h1>Your Android.<br/>Your Server.<br/><span>Your Control.</span></h1>
      <p class="hero-lead">Turn your Android device into a personal server with Termux and Yevqo. Your projects, your applications, your infrastructure — all in one place.</p>
      <div class="hero-actions"><a class="button" href="#how">Get started <ArrowUpRight size={16}/></a><a class="button button-ghost" href="#features">Explore features <ArrowRight size={16}/></a></div>
      <div class="hero-foot"><span><ShieldCheck size={15}/> No dedicated server to get started</span><span class="foot-divider"></span><span><Terminal size={15}/> Powered by Android + Termux</span></div>
    </div>
    <div class="hero-visual" aria-label="Yevqo dashboard preview">
      <div class="visual-glow"></div>
      <div class="float-label label-top"><span class="live-dot"></span> DEVICE CONNECTED <b>01</b></div>
      <div class="dashboard-window">
        <div class="dash-top"><div class="dash-brand"><span class="mini-mark">y.</span><b>yevqo</b><span class="dash-sep">/</span><span>Overview</span></div><div class="dash-user"><span class="dash-status"></span> Online <span class="avatar">N</span></div></div>
        <div class="dash-body">
          <aside class="dash-side"><div class="side-label">WORKSPACE</div><div class="side-item selected"><Activity size={13}/> Overview</div><div class="side-item"><Layers3 size={13}/> Projects</div><div class="side-item"><Rocket size={13}/> Deployments</div><div class="side-item"><Terminal size={13}/> Console</div><div class="side-label side-spacer">DEVICE</div><div class="side-item"><Smartphone size={13}/> Android server</div><div class="side-item"><Activity size={13}/> Monitoring</div><div class="side-item"><Command size={13}/> Settings</div><div class="side-device"><span class="live-dot"></span><div><b>Pixel device</b><small>Termux agent</small></div></div></aside>
          <div class="dash-main"><div class="dash-heading"><div><small>WORKSPACE / OVERVIEW</small><h3>Good to see you.</h3><p>Here's what's happening on your server.</p></div><span class="demo-pill">DEMO PREVIEW</span></div>
            <div class="server-card"><div class="server-icon"><Smartphone size={19}/></div><div class="server-info"><b>Android Server</b><small>Android · Termux environment</small></div><span class="connected"><i></i> Connected</span><div class="server-meta"><small>DEVICE</small><b>Pixel 8 Pro</b></div><div class="server-meta"><small>UPTIME</small><b>04d 12h</b></div></div>
            <div class="metric-grid"><div class="metric"><div><span>CPU usage</span><Cpu size={14}/></div><b>24<span>%</span></b><div class="spark spark-cpu"><i></i></div><small>Across 8 cores</small></div><div class="metric"><div><span>Memory</span><Activity size={14}/></div><b>3.2<span> GB</span></b><div class="memory-bar"><i></i></div><small>Of 8 GB available</small></div><div class="metric"><div><span>Storage</span><HardDrive size={14}/></div><b>48<span>%</span></b><div class="memory-bar storage"><i></i></div><small>112 GB of 256 GB</small></div></div>
            <div class="dash-lower"><div class="panel projects-panel"><div class="panel-head"><b>Active projects</b><span>View all <ArrowUpRight size={11}/></span></div><div class="project-row"><span class="project-symbol purple">N</span><div><b>nex-api</b><small>Node.js · Port 3000</small></div><em>Running</em></div><div class="project-row"><span class="project-symbol orange">W</span><div><b>web-frontend</b><small>Static · Port 8080</small></div><em>Running</em></div><div class="project-row"><span class="project-symbol blue">G</span><div><b>go-service</b><small>Go · Port 4000</small></div><em class="stopped">Stopped</em></div></div><div class="panel activity-panel"><div class="panel-head"><b>Resource activity</b><span>Last hour</span></div><div class="chart-legend"><i></i> CPU <i class="ram-dot"></i> RAM</div><div class="chart"><div class="chart-grid"></div><svg viewBox="0 0 260 90" preserveAspectRatio="none"><defs><linearGradient id="area" x1="0" x2="0" y1="0" y2="1"><stop offset="0" stop-color="#9be66d" stop-opacity=".2"/><stop offset="1" stop-color="#9be66d" stop-opacity="0"/></linearGradient></defs><path d="M0 65 C15 55 18 68 32 52 S55 55 67 42 S88 57 102 45 S122 51 135 34 S156 49 170 37 S190 48 205 26 S226 38 240 20 S252 27 260 15 L260 90 L0 90Z" fill="url(#area)"/><path d="M0 65 C15 55 18 68 32 52 S55 55 67 42 S88 57 102 45 S122 51 135 34 S156 49 170 37 S190 48 205 26 S226 38 240 20 S252 27 260 15" fill="none" stroke="#9be66d" stroke-width="2"/><path d="M0 76 C18 70 24 74 40 68 S65 71 82 63 S105 70 120 60 S146 67 160 56 S185 62 202 52 S228 57 244 46 S252 48 260 43" fill="none" stroke="#7891bb" stroke-width="1.5" stroke-dasharray="3 3"/></svg></div><div class="chart-labels"><span>10:00</span><span>10:15</span><span>10:30</span><span>10:45</span></div></div></div>
          </div>
        </div>
      </div>
      <div class="float-label label-bottom"><span class="pulse-ring"></span> BUILT AROUND YOUR DEVICE <ArrowUpRight size={13}/></div>
      <div class="visual-index">01 <span>/</span> PRODUCT PREVIEW</div>
    </div>
  </section>

  <div class="ticker"><div class="ticker-inner"><span>YOUR DEVICE</span><i>✳</i><span>YOUR PROJECTS</span><i>✳</i><span>YOUR ENVIRONMENT</span><i>✳</i><span>YOUR RULES</span><i>✳</i><span>YOUR DEVICE</span><i>✳</i><span>YOUR PROJECTS</span><i>✳</i><span>YOUR ENVIRONMENT</span></div></div>

  <section class="preview-section section-wrap" id="product">
    <div class="section-kicker">01 / THE WORKSPACE</div><div class="section-heading split-heading"><div><h2>One interface.<br/><span>Your entire stack.</span></h2></div><p>A clear view of what's running on your Android device. Yevqo brings server status, projects and activity together — without hiding the details.</p></div>
    <div class="wide-preview">
      <div class="preview-top"><div class="preview-dots"><i></i><i></i><i></i></div><span>app.yevqo.dev <b>·</b> workspace</span><div class="preview-top-right"><span class="live-dot"></span> DEVICE ONLINE</div></div>
      <div class="preview-content"><div class="preview-sidebar"><div class="preview-logo">y<span>.</span> <b>YEVQO</b></div><div class="preview-nav-active"><Activity size={14}/> Overview</div><div><Layers3 size={14}/> Projects</div><div><Rocket size={14}/> Deployments</div><div><Bot size={14}/> Agents <small>SOON</small></div><div class="preview-nav-label">MANAGE</div><div><Smartphone size={14}/> Devices</div><div><Terminal size={14}/> Logs</div><div><Command size={14}/> Settings</div><div class="preview-sidebar-bottom"><div class="avatar">N</div><span><b>My workspace</b><small>Free plan</small></span><ChevronDown size={13}/></div></div>
        <div class="preview-work"><div class="preview-work-head"><div><small>WEDNESDAY, 18 NOVEMBER</small><h3>Overview</h3><p>Your server at a glance.</p></div><button class="preview-device"><span class="live-dot"></span> My Android <ChevronDown size={12}/></button></div>
          <div class="preview-stats"><div><small>SERVER STATUS</small><b class="stat-online"><i></i> Online</b><span>Last heartbeat · just now</span></div><div><small>CPU USAGE</small><b>24.8<span>%</span></b><span>8 logical cores</span></div><div><small>MEMORY</small><b>3.2 <span>GB</span></b><span>of 8 GB total</span></div><div><small>RUNNING APPS</small><b>02</b><span>1 project idle</span></div></div>
          <div class="preview-main-grid"><div class="preview-chart-card"><div class="preview-card-head"><b>Resource usage</b><span>Last 24 hours <ChevronDown size={12}/></span></div><div class="big-chart"><div class="y-labels"><span>100%</span><span>75%</span><span>50%</span><span>25%</span><span>0%</span></div><svg viewBox="0 0 660 180" preserveAspectRatio="none"><defs><linearGradient id="bigarea" x1="0" x2="0" y1="0" y2="1"><stop offset="0" stop-color="#9be66d" stop-opacity=".22"/><stop offset="1" stop-color="#9be66d" stop-opacity="0"/></linearGradient></defs><path d="M0 120 C30 115 35 90 65 100 S100 128 130 94 S160 85 190 102 S230 60 260 80 S300 95 330 68 S360 88 390 72 S430 54 460 65 S500 42 530 55 S570 25 600 45 S635 34 660 22 L660 180 L0 180Z" fill="url(#bigarea)"/><path d="M0 120 C30 115 35 90 65 100 S100 128 130 94 S160 85 190 102 S230 60 260 80 S300 95 330 68 S360 88 390 72 S430 54 460 65 S500 42 530 55 S570 25 600 45 S635 34 660 22" fill="none" stroke="#9be66d" stroke-width="2.5"/><path d="M0 145 C30 130 55 142 80 135 S125 145 155 127 S200 135 230 120 S275 135 305 119 S350 128 380 112 S420 122 450 105 S490 119 520 99 S560 111 590 90 S630 101 660 85" fill="none" stroke="#8196ba" stroke-width="2" stroke-dasharray="5 5"/></svg><div class="x-labels"><span>00:00</span><span>06:00</span><span>12:00</span><span>18:00</span><span>NOW</span></div></div></div>
            <div class="preview-activity"><div class="preview-card-head"><b>Recent activity</b><ArrowUpRight size={13}/></div><div class="event"><span class="event-icon"><Rocket size={13}/></span><div><b>Deployment completed</b><small>web-frontend · 12 min ago</small></div><i></i></div><div class="event"><span class="event-icon"><GitBranch size={13}/></span><div><b>Repository synced</b><small>nex-api · 38 min ago</small></div><i></i></div><div class="event"><span class="event-icon"><Server size={13}/></span><div><b>Agent connected</b><small>Android device · 1h ago</small></div><i></i></div><div class="event"><span class="event-icon"><Check size={13}/></span><div><b>Build successful</b><small>go-service · 2h ago</small></div><i></i></div></div></div>
        </div>
      </div>
      <div class="preview-caption"><span>FIG. 01 — YEVQO WORKSPACE</span><span>ILLUSTRATIVE PRODUCT PREVIEW · NOT A LIVE CONNECTION</span></div>
    </div>
  </section>

  <section class="features-section section-wrap" id="features">
    <div class="section-kicker">02 / CAPABILITIES</div><div class="section-heading"><h2>Everything you need<br/><span>to manage your server.</span></h2><p>From the first process to a growing collection of projects. A focused toolkit, designed around the way Android actually works.</p></div>
    <div class="feature-grid">{#each features as feature, i}{@const FeatureIcon = feature.icon}<article class="feature-card"><div class="feature-card-top"><div class="feature-icon"><FeatureIcon size={19}/></div><span>{feature.tag}</span></div><h3>{feature.title}</h3><p>{feature.desc}</p><div class="feature-art" class:art-host={feature.kind==='host'} class:art-projects={feature.kind==='projects'} class:art-deploy={feature.kind==='deploy'} class:art-agents={feature.kind==='agents'} class:art-build={feature.kind==='build'} class:art-monitor={feature.kind==='monitor'} class:art-git={feature.kind==='git'} class:art-templates={feature.kind==='templates'} class:art-logs={feature.kind==='logs'}>
      {#if feature.kind==='host'}<div class="phone-outline"><div class="phone-speaker"></div><div class="phone-screen"><span class="live-dot"></span><b>yevqo-agent</b><small>device ready</small><div class="phone-wave"></div></div></div><span class="art-chip">ANDROID <ArrowUpRight size={10}/></span>
      {:else if feature.kind==='projects'}<div class="stack-card"><span class="stack-dot green"></span><b>api-service</b><small>Running</small></div><div class="stack-card offset"><span class="stack-dot purple"></span><b>web-client</b><small>Ready</small></div>
      {:else if feature.kind==='deploy'}<div class="deploy-line"><span></span><span></span><span></span><span></span></div><div class="deploy-label"><Check size={12}/> Build completed</div>
      {:else if feature.kind==='agents'}<div class="agent-orbit"><span><Bot size={21}/></span><i></i><i></i><i></i></div><span class="soon-float">COMING SOON</span>
      {:else if feature.kind==='build'}<div class="terminal-art"><small>BUILD OUTPUT</small><code><b>$</b> npm run build</code><code class="terminal-success">✓ build complete</code><code>dist/ generated</code></div>
      {:else if feature.kind==='monitor'}<div class="bars">{#each [30,48,39,70,53,83,61,92,69,77,48,62] as h}<i style={'height:'+h+'%'}></i>{/each}</div><span class="monitor-readout">CPU <b>24.8%</b></span>
      {:else if feature.kind==='git'}<div class="git-branch"><span></span><span></span><span></span><i></i><i></i></div><span class="git-commit">main <b>·</b> synced</span>
      {:else if feature.kind==='templates'}<div class="template-mini"><span>JS</span><span>Go</span><span>PHP</span><span>&lt;/&gt;</span></div>
      {:else}<div class="log-lines"><span><i></i> agent.connected</span><span><i></i> build.completed</span><span><i></i> app.started</span></div>{/if}
    </div></article>{/each}</div>
  </section>

  <section class="how-section section-wrap" id="how">
    <div class="section-kicker">03 / GETTING STARTED</div><div class="section-heading split-heading"><h2>From Android to<br/><span>your own server.</span></h2><p>No rack. No dedicated machine. Start with the Android device you already own and connect it to a workspace built to manage it.</p></div>
    <div class="steps"><article><div class="step-number">01 <span>— PREPARE</span></div><div class="step-icon"><Smartphone size={22}/></div><h3>Install Termux</h3><p>Prepare your Android device and install Termux to get a capable command-line environment.</p><div class="step-code"><span>$</span> pkg update && pkg upgrade</div></article><div class="step-connector"><span></span><ArrowRight size={17}/></div><article><div class="step-number">02 <span>— CONNECT</span></div><div class="step-icon"><Terminal size={22}/></div><h3>Install Yevqo Agent</h3><p>Set up the Yevqo Agent in Termux. It will handle supported operations directly on your device.</p><div class="step-code"><span>$</span> yevqo agent setup</div></article><div class="step-connector"><span></span><ArrowRight size={17}/></div><article><div class="step-number">03 <span>— MANAGE</span></div><div class="step-icon"><Globe2 size={22}/></div><h3>Manage everything</h3><p>Open the web workspace to view your device, organize projects and manage your applications.</p><div class="step-code"><span>↗</span> app.yevqo.dev</div></article></div>
    <div class="flow-strip"><div><Smartphone size={19}/><span><b>ANDROID</b><small>Your hardware</small></span></div><div class="flow-arrow"><span></span><ArrowRight size={15}/></div><div><Terminal size={19}/><span><b>TERMUX</b><small>Yevqo Agent</small></span></div><div class="flow-arrow"><span></span><ArrowRight size={15}/></div><div><Layers3 size={19}/><span><b>YEVQO DASHBOARD</b><small>Your control plane</small></span></div></div>
  </section>

  <section class="agents-section section-wrap">
    <div class="agent-copy"><div class="section-kicker">04 / THE NEXT LAYER <span class="coming-tag">COMING SOON</span></div><h2>Automation meets<br/><span>your Android server.</span></h2><p>Yevqo is being designed to make routine infrastructure work easier with specialized AI agents. Define what an agent can access, choose its tools and decide how independently it can act.</p><div class="agent-types"><span><Code2 size={14}/> Coding Agent</span><span><Rocket size={14}/> Deployment Agent</span><span><Activity size={14}/> Monitoring Agent</span><span><Globe2 size={14}/> Research Agent</span><span><Bot size={14}/> Custom Agent</span></div></div>
    <div class="agent-builder"><div class="builder-top"><div><span class="builder-spark">✳</span><b>Agent Builder</b></div><span class="coming-tag">CONCEPT</span></div><div class="builder-body"><div class="builder-title"><div class="builder-avatar"><Bot size={21}/></div><div><b>Deployment Assistant</b><small>Specialized agent · Draft configuration</small></div></div><label>AGENT INSTRUCTIONS</label><div class="builder-input">Help me prepare and review deployments for my projects. Ask before making changes.</div><label>AVAILABLE TOOLS</label><div class="tool-pills"><span><Check size={11}/> Project files</span><span><Check size={11}/> Build logs</span><span class="muted-tool">Terminal access</span><span class="muted-tool">Git actions</span></div><label>AUTONOMY LEVEL</label><div class="autonomy"><span class="active-auto">Suggest only</span><span>Ask before action</span><span>Autonomous</span></div><div class="builder-foot"><span><ShieldCheck size={13}/> Permission-first by design</span><button disabled>Save agent <ArrowUpRight size={13}/></button></div></div></div>
  </section>

  <section class="templates-section section-wrap" id="templates">
    <div class="section-kicker">05 / QUICK STARTS</div><div class="section-heading split-heading"><h2>Start with<br/><span>a template.</span></h2><p>A practical starting point for the projects you want to run. Templates are starter configurations — actual runtime support depends on your Android environment.</p></div>
    <div class="template-grid">{#each templates as item, i}<article class="template-card"><div class="template-card-head"><span class="template-logo" class:node={i===1} class:php={i===2} class:go={i===3}>{item.mark}</span><span class="template-arrow"><ArrowUpRight size={16}/></span></div><h3>{item.name}</h3><p>{item.desc}</p><div class="template-lang"><Code2 size={13}/>{item.lang}</div></article>{/each}</div>
    <p class="template-note"><span class="live-dot"></span> Built around native Android + Termux workflows. Docker-based builders such as Nixpacks or Railpack require a separate Linux execution environment.</p>
  </section>

  <section class="why-section section-wrap">
    <div class="why-visual"><div class="why-orbit orbit-one"></div><div class="why-orbit orbit-two"></div><div class="why-core"><span class="brand-mark"><span></span><span></span><span></span></span><b>yevqo</b><small>YOUR INFRASTRUCTURE</small></div><div class="orbit-node node-a"><Smartphone size={17}/></div><div class="orbit-node node-b"><Terminal size={17}/></div><div class="orbit-node node-c"><Code2 size={17}/></div><div class="orbit-node node-d"><Network size={17}/></div></div>
    <div class="why-copy"><div class="section-kicker">06 / WHY YEVQO</div><h2>Your infrastructure.<br/><span>Your rules.</span></h2><p>Infrastructure doesn't have to start in a data center. Yevqo gives your existing Android hardware a new purpose — with a management experience that stays yours.</p><ul><li><Check size={15}/> No dedicated server required to get started</li><li><Check size={15}/> Put hardware you already own to work</li><li><Check size={15}/> Manage projects from one dashboard</li><li><Check size={15}/> Open, flexible development environment</li><li><Check size={15}/> Control your own applications</li><li><Check size={15}/> Built around Android and Termux</li></ul></div>
  </section>

  <section class="pricing-section section-wrap" id="pricing">
    <div class="section-kicker">07 / SIMPLE BY DESIGN</div><div class="section-heading"><h2>Everything to get<br/><span>your first server running.</span></h2><p>Start with the essentials. Future capabilities will be introduced as they become ready.</p></div>
    <div class="pricing-card"><div class="pricing-main"><span class="plan-label"><span class="live-dot"></span> AVAILABLE PLAN</span><h3>Free</h3><p>Everything you need to start exploring your own Android server.</p><div class="price">€0 <small>/ forever</small></div><a class="button" href="#how">Get started <ArrowUpRight size={15}/></a></div><div class="pricing-includes"><span>INCLUDED</span><ul><li><Check size={15}/> 1 connected Android device</li><li><Check size={15}/> Project management</li><li><Check size={15}/> Basic hosting tools</li><li><Check size={15}/> Basic monitoring</li><li><Check size={15}/> Application templates</li></ul></div><div class="pricing-future"><span>ON THE ROADMAP</span><div><Bot size={16}/><b>AI agents</b><em>Planned</em></div><div><Network size={16}/><b>Multi-device workspace</b><em>Planned</em></div><div><Zap size={16}/><b>Advanced automation</b><em>Planned</em></div><small>No paid plans or future prices are being announced at this stage.</small></div></div>
  </section>

  <section class="faq-section section-wrap" id="faq">
    <div class="faq-intro"><div class="section-kicker">08 / QUESTIONS</div><h2>Good questions.<br/><span>Clear answers.</span></h2><p>Everything you might want to know before turning your Android into a server.</p><a href="https://github.com/NexLab-ceo" target="_blank" rel="noreferrer">More on GitHub <ArrowUpRight size={14}/></a></div>
    <div class="faq-list">{#each faqs as faq, i}<div class:faq-open={activeFaq===i} class="faq-item"><button onclick={() => activeFaq = activeFaq===i ? -1 : i}><span>{faq.q}</span><span class="faq-plus">{activeFaq===i ? '−' : '+'}</span></button>{#if activeFaq===i}<p>{faq.a}</p>{/if}</div>{/each}</div>
  </section>

  <section class="final-cta section-wrap" id="docs"><div class="cta-glow"></div><div class="section-kicker">YOUR POCKET-SIZED INFRASTRUCTURE</div><h2>It's your device.<br/><span>Make it your server.</span></h2><p>Start with Android. Add Termux. Take control with Yevqo.</p><div class="hero-actions"><a class="button" href="#how">Get started <ArrowUpRight size={16}/></a><a class="button button-ghost" href="https://github.com/NexLab-ceo" target="_blank" rel="noreferrer"><Github size={15}/> Explore GitHub</a></div><div class="cta-foot"><span><span class="live-dot"></span> ANDROID + TERMUX</span><span>YOUR SERVER. YOUR RULES.</span></div></section>
</main>

<footer class="footer section-wrap"><div class="footer-top"><div class="footer-brand"><a class="brand" href="#top"><span class="brand-mark"><span></span><span></span><span></span></span><span>yevqo</span></a><p>Your Android.<br/>Your Server. Your Control.</p></div><div class="footer-col"><b>PRODUCT</b><a href="#features">Features</a><a href="#how">How it works</a><a href="#templates">Templates</a><a href="#pricing">Pricing</a></div><div class="footer-col"><b>RESOURCES</b><a href="#docs">Documentation</a><a href="#faq">FAQ</a><a href="https://github.com/NexLab-ceo" target="_blank" rel="noreferrer">GitHub <ExternalLink size={11}/></a></div><div class="footer-col"><b>COMMUNITY</b><a href="https://github.com/NexLab-ceo" target="_blank" rel="noreferrer">GitHub Discussions</a><a href="https://github.com/NexLab-ceo" target="_blank" rel="noreferrer">Contribute</a></div><div class="footer-col"><b>LEGAL</b><a href="#footer">Privacy</a><a href="#footer">Terms</a></div></div><div class="footer-bottom" id="footer"><span>© 2026 Yevqo. All rights reserved.</span><span>BUILT FOR THE ANDROID-POWERED FUTURE <span class="live-dot"></span></span><a href="#top">BACK TO TOP ↑</a></div></footer>