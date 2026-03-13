<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cyclophyllidea Interactive - Vet Helminthology</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&family=JetBrains+Mono:wght@400;700&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Inter', sans-serif;
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
            min-height: 100vh;
            color: #eaeaea;
            overflow-x: hidden;
        }
        
        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }
        
        /* Header Animation */
        .header {
            text-align: center;
            padding: 40px 20px;
            position: relative;
            overflow: hidden;
        }
        
        .header::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(233, 69, 96, 0.1) 0%, transparent 70%);
            animation: pulse 4s ease-in-out infinite;
        }
        
        @keyframes pulse {
            0%, 100% { transform: scale(1); opacity: 0.5; }
            50% { transform: scale(1.1); opacity: 0.8; }
        }
        
        h1 {
            font-size: 3rem;
            font-weight: 800;
            background: linear-gradient(45deg, #e94560, #ff6b6b, #feca57);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: titleGlow 2s ease-in-out infinite alternate;
            position: relative;
            z-index: 1;
        }
        
        @keyframes titleGlow {
            from { filter: drop-shadow(0 0 20px rgba(233, 69, 96, 0.5)); }
            to { filter: drop-shadow(0 0 30px rgba(254, 202, 87, 0.8)); }
        }
        
        .subtitle {
            color: #a0a0a0;
            margin-top: 10px;
            font-size: 1.1rem;
        }
        
        /* Navigation Tabs */
        .nav-tabs {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin: 30px 0;
            flex-wrap: wrap;
        }
        
        .tab-btn {
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid rgba(233, 69, 96, 0.3);
            color: #eaeaea;
            padding: 12px 24px;
            border-radius: 30px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 600;
            backdrop-filter: blur(10px);
        }
        
        .tab-btn:hover, .tab-btn.active {
            background: rgba(233, 69, 96, 0.2);
            border-color: #e94560;
            transform: translateY(-2px);
            box-shadow: 0 5px 20px rgba(233, 69, 96, 0.3);
        }
        
        /* Content Sections */
        .section {
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
        .section.active {
            display: block;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        /* Cards */
        .card {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            padding: 30px;
            margin: 20px 0;
            backdrop-filter: blur(10px);
            transition: transform 0.3s ease;
        }
        
        .card:hover {
            transform: translateY(-5px);
            border-color: rgba(233, 69, 96, 0.5);
        }
        
        /* Morphology Animation */
        .morphology-container {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 400px;
            position: relative;
        }
        
        .tapeworm-svg {
            width: 100%;
            max-width: 800px;
            height: auto;
        }
        
        .scolex {
            animation: scolexPulse 3s ease-in-out infinite;
            transform-origin: center;
        }
        
        @keyframes scolexPulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }
        
        .sucker {
            animation: suckerBlink 2s ease-in-out infinite;
        }
        
        .sucker:nth-child(2) { animation-delay: 0.5s; }
        .sucker:nth-child(3) { animation-delay: 1s; }
        .sucker:nth-child(4) { animation-delay: 1.5s; }
        
        @keyframes suckerBlink {
            0%, 100% { opacity: 0.6; fill: #e94560; }
            50% { opacity: 1; fill: #ff6b6b; }
        }
        
        .hook {
            animation: hookRotate 4s linear infinite;
            transform-origin: center;
        }
        
        @keyframes hookRotate {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        .proglottid {
            animation: proglottidWave 2s ease-in-out infinite;
        }
        
        .proglottid:nth-child(even) {
            animation-delay: 0.5s;
        }
        
        @keyframes proglottidWave {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-5px); }
        }
        
        /* Life Cycle Animation */
        .lifecycle-container {
            position: relative;
            height: 600px;
            background: radial-gradient(circle at center, rgba(15, 52, 96, 0.5) 0%, transparent 70%);
            border-radius: 20px;
            overflow: hidden;
        }
        
        .cycle-path {
            position: absolute;
            width: 100%;
            height: 100%;
        }
        
        .cycle-node {
            position: absolute;
            width: 120px;
            height: 120px;
            background: rgba(233, 69, 96, 0.2);
            border: 3px solid #e94560;
            border-radius: 50%;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s ease;
            backdrop-filter: blur(5px);
            z-index: 10;
        }
        
        .cycle-node:hover {
            transform: scale(1.1);
            background: rgba(233, 69, 96, 0.4);
            box-shadow: 0 0 30px rgba(233, 69, 96, 0.5);
        }
        
        .cycle-node.active {
            background: rgba(254, 202, 87, 0.3);
            border-color: #feca57;
            box-shadow: 0 0 40px rgba(254, 202, 87, 0.6);
        }
        
        .node-icon {
            font-size: 2rem;
            margin-bottom: 5px;
        }
        
        .node-label {
            font-size: 0.8rem;
            text-align: center;
            font-weight: 600;
        }
        
        .connector {
            position: absolute;
            height: 3px;
            background: linear-gradient(90deg, #e94560, #feca57);
            transform-origin: left center;
            opacity: 0.6;
            animation: flowLine 2s linear infinite;
        }
        
        @keyframes flowLine {
            0% { background-position: 0% 50%; }
            100% { background-position: 100% 50%; }
        }
        
        .particle {
            position: absolute;
            width: 8px;
            height: 8px;
            background: #feca57;
            border-radius: 50%;
            animation: moveAlongPath 8s linear infinite;
            box-shadow: 0 0 10px #feca57;
        }
        
        @keyframes moveAlongPath {
            0% { offset-distance: 0%; }
            100% { offset-distance: 100%; }
        }
        
        /* Info Panel */
        .info-panel {
            background: rgba(0, 0, 0, 0.3);
            border-left: 4px solid #e94560;
            padding: 20px;
            margin-top: 20px;
            border-radius: 0 10px 10px 0;
            animation: slideIn 0.3s ease;
        }
        
        @keyframes slideIn {
            from { opacity: 0; transform: translateX(-20px); }
            to { opacity: 1; transform: translateX(0); }
        }
        
        /* Families Grid */
        .families-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }
        
        .family-card {
            background: linear-gradient(135deg, rgba(233, 69, 96, 0.1) 0%, rgba(15, 52, 96, 0.2) 100%);
            border: 1px solid rgba(233, 69, 96, 0.3);
            border-radius: 15px;
            padding: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .family-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.1), transparent);
            transition: left 0.5s ease;
        }
        
        .family-card:hover::before {
            left: 100%;
        }
        
        .family-card:hover {
            transform: translateY(-5px) scale(1.02);
            border-color: #e94560;
            box-shadow: 0 10px 30px rgba(233, 69, 96, 0.2);
        }
        
        .family-name {
            font-size: 1.3rem;
            font-weight: 700;
            color: #feca57;
            margin-bottom: 10px;
        }
        
        .family-features {
            font-size: 0.9rem;
            color: #a0a0a0;
            line-height: 1.6;
        }
        
        /* Quiz Section */
        .quiz-container {
            max-width: 800px;
            margin: 0 auto;
        }
        
        .question-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            padding: 30px;
            margin: 20px 0;
            border: 2px solid transparent;
            transition: all 0.3s ease;
        }
        
        .question-card:hover {
            border-color: rgba(233, 69, 96, 0.5);
        }
        
        .options {
            display: grid;
            gap: 10px;
            margin-top: 20px;
        }
        
        .option {
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid rgba(255, 255, 255, 0.1);
            padding: 15px;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.2s ease;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .option:hover {
            background: rgba(233, 69, 96, 0.1);
            border-color: rgba(233, 69, 96, 0.5);
            transform: translateX(10px);
        }
        
        .option.correct {
            background: rgba(46, 213, 115, 0.2);
            border-color: #2ed573;
            animation: correctPulse 0.5s ease;
        }
        
        .option.wrong {
            background: rgba(255, 71, 87, 0.2);
            border-color: #ff4757;
            animation: shake 0.5s ease;
        }
        
        @keyframes correctPulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }
        
        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-10px); }
            75% { transform: translateX(10px); }
        }
        
        .progress-bar {
            height: 6px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 3px;
            margin: 20px 0;
            overflow: hidden;
        }
        
        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #e94560, #feca57);
            width: 0%;
            transition: width 0.5s ease;
            border-radius: 3px;
        }
        
        /* Floating Elements */
        .float-element {
            position: fixed;
            pointer-events: none;
            opacity: 0.1;
            z-index: 0;
        }
        
        .egg-float {
            width: 30px;
            height: 30px;
            background: radial-gradient(circle, #feca57 0%, transparent 70%);
            border-radius: 50%;
            animation: float 10s infinite ease-in-out;
        }
        
        @keyframes float {
            0%, 100% { transform: translate(0, 0) rotate(0deg); }
            33% { transform: translate(30px, -30px) rotate(120deg); }
            66% { transform: translate(-20px, 20px) rotate(240deg); }
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            h1 { font-size: 2rem; }
            .cycle-node { width: 80px; height: 80px; font-size: 0.7rem; }
            .families-grid { grid-template-columns: 1fr; }
        }
        
        /* Memory Trick Cards */
        .trick-card {
            background: linear-gradient(135deg, rgba(254, 202, 87, 0.1) 0%, rgba(233, 69, 96, 0.1) 100%);
            border: 2px dashed rgba(254, 202, 87, 0.5);
            border-radius: 15px;
            padding: 20px;
            margin: 15px 0;
            position: relative;
        }
        
        .trick-label {
            position: absolute;
            top: -12px;
            left: 20px;
            background: #1a1a2e;
            padding: 0 10px;
            color: #feca57;
            font-weight: 700;
            font-size: 0.9rem;
        }
        
        .trick-content {
            font-style: italic;
            color: #eaeaea;
            font-size: 1.1rem;
        }
        
        /* Comparison Table */
        .comp-table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
            background: rgba(255, 255, 255, 0.02);
            border-radius: 10px;
            overflow: hidden;
        }
        
        .comp-table th {
            background: rgba(233, 69, 96, 0.3);
            padding: 15px;
            text-align: left;
            font-weight: 600;
        }
        
        .comp-table td {
            padding: 12px 15px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.05);
        }
        
        .comp-table tr:hover {
            background: rgba(233, 69, 96, 0.1);
        }
        
        /* Drug Animation */
        .drug-container {
            display: flex;
            justify-content: center;
            gap: 30px;
            flex-wrap: wrap;
            margin: 30px 0;
        }
        
        .drug-pill {
            width: 150px;
            height: 80px;
            background: linear-gradient(135deg, #e94560 0%, #ff6b6b 100%);
            border-radius: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            font-size: 1.2rem;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(233, 69, 96, 0.3);
        }
        
        .drug-pill::before {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transform: translateX(-100%);
            transition: transform 0.5s ease;
        }
        
        .drug-pill:hover::before {
            transform: translateX(100%);
        }
        
        .drug-pill:hover {
            transform: translateY(-10px) rotate(5deg);
            box-shadow: 0 20px 40px rgba(233, 69, 96, 0.4);
        }
        
        .drug-pill.albendazole {
            background: linear-gradient(135deg, #feca57 0%, #ff9f43 100%);
            box-shadow: 0 10px 30px rgba(254, 202, 87, 0.3);
        }
        
        .drug-info {
            position: absolute;
            bottom: -40px;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(0,0,0,0.8);
            padding: 5px 15px;
            border-radius: 20px;
            font-size: 0.8rem;
            opacity: 0;
            transition: all 0.3s ease;
            white-space: nowrap;
        }
        
        .drug-pill:hover .drug-info {
            opacity: 1;
            bottom: -50px;
        }
    </style>
</head>
<body>
    <!-- Floating Background Elements -->
    <div class="float-element egg-float" style="top: 10%; left: 10%;"></div>
    <div class="float-element egg-float" style="top: 20%; right: 15%; animation-delay: 2s;"></div>
    <div class="float-element egg-float" style="bottom: 30%; left: 20%; animation-delay: 4s;"></div>
    
    <div class="container">
        <header class="header">
            <h1>🪱 CYCLOPHYLLIDEA</h1>
            <p class="subtitle">Order under Class Eucestoda | 4 Suckers + Rostellum with Hooks</p>
        </header>
        
        <nav class="nav-tabs">
            <button class="tab-btn active" onclick="showSection('morphology')">🔬 Morphology</button>
            <button class="tab-btn" onclick="showSection('lifecycle')">🔄 Life Cycle</button>
            <button class="tab-btn" onclick="showSection('families')">👨‍👩‍👧‍👦 Families</button>
            <button class="tab-btn" onclick="showSection('species')">🎯 Key Species</button>
            <button class="tab-btn" onclick="showSection('treatment')">💊 Treatment</button>
            <button class="tab-btn" onclick="showSection('quiz')">📝 Quiz</button>
        </nav>
        
        <!-- MORPHOLOGY SECTION -->
        <section id="morphology" class="section active">
            <div class="card">
                <h2 style="color: #feca57; margin-bottom: 20px;">Anatomy of Cyclophyllidea</h2>
                
                <div class="morphology-container">
                    <svg class="tapeworm-svg" viewBox="0 0 800 400" xmlns="http://www.w3.org/2000/svg">
                        <!-- Definitions for gradients -->
                        <defs>
                            <linearGradient id="bodyGrad" x1="0%" y1="0%" x2="100%" y2="0%">
                                <stop offset="0%" style="stop-color:#e94560;stop-opacity:0.8" />
                                <stop offset="100%" style="stop-color:#ff6b6b;stop-opacity:0.6" />
                            </linearGradient>
                            <radialGradient id="suckerGrad" cx="50%" cy="50%" r="50%">
                                <stop offset="0%" style="stop-color:#ff6b6b;stop-opacity:1" />
                                <stop offset="100%" style="stop-color:#e94560;stop-opacity:0.8" />
                            </radialGradient>
                        </defs>
                        
                        <!-- Strobila (Chain of proglottids) -->
                        <g class="proglottid-chain">
                            <rect class="proglottid" x="200" y="180" width="60" height="40" rx="5" fill="url(#bodyGrad)" stroke="#e94560" stroke-width="2"/>
                            <rect class="proglottid" x="270" y="180" width="60" height="40" rx="5" fill="url(#bodyGrad)" stroke="#e94560" stroke-width="2" opacity="0.9"/>
                            <rect class="proglottid" x="340" y="180" width="60" height="40" rx="5" fill="url(#bodyGrad)" stroke="#e94560" stroke-width="2" opacity="0.8"/>
                            <rect class="proglottid" x="410" y="180" width="60" height="40" rx="5" fill="url(#bodyGrad)" stroke="#e94560" stroke-width="2" opacity="0.7"/>
                            <rect class="proglottid" x="480" y="180" width="60" height="40" rx="5" fill="url(#bodyGrad)" stroke="#e94560" stroke-width="2" opacity="0.6"/>
                            <rect class="proglottid" x="550" y="180" width="60" height="40" rx="5" fill="url(#bodyGrad)" stroke="#e94560" stroke-width="2" opacity="0.5"/>
                        </g>
                        
                        <!-- Neck -->
                        <rect x="160" y="190" width="30" height="20" fill="#ff6b6b" opacity="0.9"/>
                        
                        <!-- Scolex (Head) -->
                        <g class="scolex">
                            <circle cx="100" cy="200" r="50" fill="url(#bodyGrad)" stroke="#e94560" stroke-width="3"/>
                            
                            <!-- 4 Suckers -->
                            <circle class="sucker" cx="75" cy="175" r="12" fill="url(#suckerGrad)"/>
                            <circle class="sucker" cx="125" cy="175" r="12" fill="url(#suckerGrad)"/>
                            <circle class="sucker" cx="75" cy="225" r="12" fill="url(#suckerGrad)"/>
                            <circle class="sucker" cx="125" cy="225" r="12" fill="url(#suckerGrad)"/>
                            
                            <!-- Rostellum with Hooks -->
                            <circle cx="100" cy="200" r="20" fill="none" stroke="#feca57" stroke-width="2"/>
                            <path class="hook" d="M 100 180 L 100 170 M 100 220 L 100 230 M 80 200 L 70 200 M 120 200 L 130 200" 
                                  stroke="#feca57" stroke-width="3" stroke-linecap="round"/>
                            <path class="hook" d="M 85 185 L 78 178 M 115 215 L 122 222 M 115 185 L 122 178 M 85 215 L 78 222" 
                                  stroke="#feca57" stroke-width="2" stroke-linecap="round"/>
                        </g>
                        
                        <!-- Labels -->
                        <text x="100" y="280" text-anchor="middle" fill="#feca57" font-size="14" font-weight="bold">SCOLEX</text>
                        <text x="100" y="295" text-anchor="middle" fill="#a0a0a0" font-size="11">4 Suckers + Hooks</text>
                        
                        <text x="175" y="240" text-anchor="middle" fill="#feca57" font-size="14" font-weight="bold">NECK</text>
                        <text x="175" y="255" text-anchor="middle" fill="#a0a0a0" font-size="11">Growth Zone</text>
                        
                        <text x="400" y="280" text-anchor="middle" fill="#feca57" font-size="14" font-weight="bold">STROBILA</text>
                        <text x="400" y="295" text-anchor="middle" fill="#a0a0a0" font-size="11">Chain of Proglottids</text>
                        
                        <!-- Gravid segment indicator -->
                        <rect x="620" y="170" width="80" height="60" rx="5" fill="none" stroke="#feca57" stroke-width="2" stroke-dasharray="5,5"/>
                        <text x="660" y="205" text-anchor="middle" fill="#feca57" font-size="12" font-weight="bold">GRAVID</text>
                        <text x="660" y="220" text-anchor="middle" fill="#feca57" font-size="10">(Eggs Inside)</text>
                    </svg>
                </div>
                
                <div class="trick-card">
                    <span class="trick-label">💡 MEMORY TRICK</span>
                    <p class="trick-content">"CYCLO = CYCLE of 4" → 4 suckers arranged in a circle! Plus rostellum with hooks for extra grip.</p>
                </div>
                
                <table class="comp-table">
                    <tr>
                        <th>Feature</th>
                        <th>Description</th>
                        <th>Function</th>
                    </tr>
                    <tr>
                        <td><strong>Scolex</strong></td>
                        <td>Head with 4 suckers + rostellum with hooks</td>
                        <td>Attachment to intestine</td>
                    </tr>
                    <tr>
                        <td><strong>Neck</strong></td>
                        <td>Narrow, unsegmented region</td>
                        <td>Growth zone - produces proglottids</td>
                    </tr>
                    <tr>
                        <td><strong>Strobila</strong></td>
                        <td>Chain of proglottids (segments)</td>
                        <td>Reproduction (hermaphrodite segments)</td>
                    </tr>
                    <tr>
                        <td><strong>Digestive</strong></td>
                        <td>ABSENT - No mouth or gut</td>
                        <td>Absorb nutrients via tegument (skin)</td>
                    </tr>
                    <tr>
                        <td><strong>Excretory</strong></td>
                        <td>Flame cells (protonephridia)</td>
                        <td>Filter waste like primitive kidneys</td>
                    </tr>
                </table>
            </div>
        </section>
        
        <!-- LIFE CYCLE SECTION -->
        <section id="lifecycle" class="section">
            <div class="card">
                <h2 style="color: #feca57; margin-bottom: 20px;">Complete Life Cycle Animation</h2>
                <p style="margin-bottom: 20px; color: #a0a0a0;">Click on each stage to learn details. Watch the particles flow through the cycle!</p>
                
                <div class="lifecycle-container" id="lifecycleContainer">
                    <!-- SVG connectors will be drawn here -->
                    <svg style="position: absolute; width: 100%; height: 100%; pointer-events: none;">
                        <defs>
                            <marker id="arrowhead" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
                                <polygon points="0 0, 10 3, 0 6" fill="#e94560" />
                            </marker>
                        </defs>
                        <path id="path1" d="M 150 100 Q 300 50 450 100" fill="none" stroke="rgba(233,69,96,0.3)" stroke-width="2" marker-end="url(#arrowhead)"/>
                        <path id="path2" d="M 450 100 Q 600 150 650 300" fill="none" stroke="rgba(233,69,96,0.3)" stroke-width="2" marker-end="url(#arrowhead)"/>
                        <path id="path3" d="M 650 300 Q 500 400 350 450" fill="none" stroke="rgba(233,69,96,0.3)" stroke-width="2" marker-end="url(#arrowhead)"/>
                        <path id="path4" d="M 350 450 Q 200 400 150 300" fill="none" stroke="rgba(233,69,96,0.3)" stroke-width="2" marker-end="url(#arrowhead)"/>
                        <path id="path5" d="M 150 300 Q 100 200 150 100" fill="none" stroke="rgba(233,69,96,0.3)" stroke-width="2" marker-end="url(#arrowhead)"/>
                    </svg>
                    
                    <!-- Cycle Nodes -->
                    <div class="cycle-node" style="top: 10%; left: 10%;" onclick="showStageInfo('adult')">
                        <span class="node-icon">🪱</span>
                        <span class="node-label">ADULT<br><small>Definitive Host</small></span>
                    </div>
                    
                    <div class="cycle-node" style="top: 10%; left: 50%; transform: translateX(-50%);" onclick="showStageInfo('eggs')">
                        <span class="node-icon">🥚</span>
                        <span class="node-label">EGGS<br><small>In Environment</small></span>
                    </div>
                    
                    <div class="cycle-node" style="top: 50%; right: 10%;" onclick="showStageInfo('oncosphere')">
                        <span class="node-icon">🔱</span>
                        <span class="node-label">ONCOSPHERE<br><small>Hexacanth Larva</small></span>
                    </div>
                    
                    <div class="cycle-node" style="bottom: 10%; left: 40%;" onclick="showStageInfo('cysticercus')">
                        <span class="node-icon">🫧</span>
                        <span class="node-label">CYSTICERCUS<br><small>Bladderworm</small></span>
                    </div>
                    
                    <div class="cycle-node" style="top: 50%; left: 10%;" onclick="showStageInfo('intermediate')">
                        <span class="node-icon">🐷</span>
                        <span class="node-label">INTERMEDIATE<br><small>Host Infected</small></span>
                    </div>
                    
                    <!-- Animated particles -->
                    <div class="particle" style="offset-path: path('M 150 100 Q 300 50 450 100'); animation-delay: 0s;"></div>
                    <div class="particle" style="offset-path: path('M 450 100 Q 600 150 650 300'); animation-delay: 1.6s;"></div>
                    <div class="particle" style="offset-path: path('M 650 300 Q 500 400 350 450'); animation-delay: 3.2s;"></div>
                    <div class="particle" style="offset-path: path('M 350 450 Q 200 400 150 300'); animation-delay: 4.8s;"></div>
                    <div class="particle" style="offset-path: path('M 150 300 Q 100 200 150 100'); animation-delay: 6.4s;"></div>
                </div>
                
                <div id="stageInfo" class="info-panel" style="display: none;">
                    <h3 id="stageTitle" style="color: #feca57; margin-bottom: 10px;"></h3>
                    <p id="stageDesc" style="line-height: 1.6;"></p>
                </div>
                
                <div class="trick-card" style="margin-top: 20px;">
                    <span class="trick-label">🔄 CYCLE MEMORY</span>
                    <p class="trick-content">"Adult → Eggs → Oncosphere → Cysticercus → Adult"<br>
                    Remember: <strong>Embryophore</strong> dissolves in stomach → <strong>6 hooks</strong> penetrate gut → Migrate to muscles → Develop into bladderworm!</p>
                </div>
            </div>
        </section>
        
        <!-- FAMILIES SECTION -->
        <section id="families" class="section">
            <div class="card">
                <h2 style="color: #feca57; margin-bottom: 10px;">7 Important Families</h2>
                <p style="color: #a0a0a0; margin-bottom: 20px;">Memory Trick: <strong>"TAD DHMT"</strong> - Taeniidae, Anoplocephalidae, Dipylidiidae, Davaineidae, Hymenolepididae, Mesocestoididae, Thysanosomidae</p>
                
                <div class="families-grid">
                    <div class="family-card" onclick="toggleFamily(this)">
                        <div class="family-name">1. TAENIIDAE</div>
                        <div class="family-features">
                            • 4 suckers + rostellum with 2 rows of hooks<br>
                            • Large worms<br>
                            • <strong>Important:</strong> Taenia solium, T. saginata, Echinococcus<br>
                            • Hosts: Humans, dogs, livestock
                        </div>
                        <div style="margin-top: 10px; padding: 10px; background: rgba(233,69,96,0.2); border-radius: 5px; display: none;" class="detail-box">
                            <strong>Key Feature:</strong> Most medically important family! Causes cysticercosis and hydatid disease.
                        </div>
                    </div>
                    
                    <div class="family-card" onclick="toggleFamily(this)">
                        <div class="family-name">2. ANOPLOCEPHALIDAE</div>
                        <div class="family-features">
                            • <strong>NO rostellum/hooks!</strong> Only 4 suckers<br>
                            • Wide proglottids<br>
                            • <strong>Important:</strong> Anoplocephala, Moniezia<br>
                            • Hosts: Horses, ruminants
                        </div>
                        <div style="margin-top: 10px; padding: 10px; background: rgba(233,69,96,0.2); border-radius: 5px; display: none;" class="detail-box">
                            <strong>Memory:</strong> "Anoplo" = No hooks! Just suckers.
                        </div>
                    </div>
                    
                    <div class="family-card" onclick="toggleFamily(this)">
                        <div class="family-name">3. DIPYLIDIIDAE</div>
                        <div class="family-features">
                            • Double-pored proglottids<br>
                            • Rostellum with rose-thorn hooks<br>
                            • <strong>Important:</strong> Dipylidium caninum<br>
                            • Hosts: Dogs, cats (flea intermediate)
                        </div>
                        <div style="margin-top: 10px; padding: 10px; background: rgba(233,69,96,0.2); border-radius: 5px; display: none;" class="detail-box">
                            <strong>Memory:</strong> "DIPY = DOUBLE PORE" - One genital pore on each side!
                        </div>
                    </div>
                    
                    <div class="family-card" onclick="toggleFamily(this)">
                        <div class="family-name">4. DAVAINEIDAE</div>
                        <div class="family-features">
                            • Rostellum with hammer-shaped hooks<br>
                            • Small worms<br>
                            • <strong>Important:</strong> Davainea, Raillietina<br>
                            • Hosts: Birds, poultry
                        </div>
                        <div style="margin-top: 10px; padding: 10px; background: rgba(233,69,96,0.2); border-radius: 5px; display: none;" class="detail-box">
                            <strong>Key:</strong> Hammer-shaped hooks unique to this family!
                        </div>
                    </div>
                    
                    <div class="family-card" onclick="toggleFamily(this)">
                        <div class="family-name">5. HYMENOLEPIDIDAE</div>
                        <div class="family-features">
                            • Small worms<br>
                            • <strong>Direct OR indirect life cycle</strong><br>
                            • <strong>Important:</strong> Hymenolepis nana (dwarf tapeworm)<br>
                            • Hosts: Humans, rodents
                        </div>
                        <div style="margin-top: 10px; padding: 10px; background: rgba(233,69,96,0.2); border-radius: 5px; display: none;" class="detail-box">
                            <strong>Critical:</strong> H. nana is the ONLY tapeworm that doesn't need an intermediate host! Direct life cycle possible.
                        </div>
                    </div>
                    
                    <div class="family-card" onclick="toggleFamily(this)">
                        <div class="family-name">6. MESOCESTOIDIDAE</div>
                        <div class="family-features">
                            • 4 suckers, NO rostellum<br>
                            • Tetrathyridium larva stage<br>
                            • <strong>Important:</strong> Mesocestoides<br>
                            • Hosts: Dogs, cats, wild carnivores
                        </div>
                        <div style="margin-top: 10px; padding: 10px; background: rgba(233,69,96,0.2); border-radius: 5px; display: none;" class="detail-box">
                            <strong>Unique:</strong> Tetrathyridium larva - different from cysticercus!
                        </div>
                    </div>
                    
                    <div class="family-card" onclick="toggleFamily(this)">
                        <div class="family-name">7. THYSANOSOMIDAE</div>
                        <div class="family-features">
                            • Fringed or lanceolate suckers<br>
                            • Lives in bile ducts<br>
                            • <strong>Important:</strong> Thysanosoma (fringed tapeworm)<br>
                            • Hosts: Sheep, goats, ruminants
                        </div>
                        <div style="margin-top: 10px; padding: 10px; background: rgba(233,69,96,0.2); border-radius: 5px; display: none;" class="detail-box">
                            <strong>Memory:</strong> "THYSAN" = THYme + SANd → grows in bile (bitter like herbs!)
                        </div>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- KEY SPECIES SECTION -->
        <section id="species" class="section">
            <div class="card">
                <h2 style="color: #feca57; margin-bottom: 20px;">Vet-Important Species</h2>
                
                <div style="display: grid; gap: 20px;">
                    <div style="background: rgba(233,69,96,0.1); border-left: 4px solid #e94560; padding: 20px; border-radius: 0 10px 10px 0;">
                        <h3 style="color: #ff6b6b; margin-bottom: 10px;">🐷 Taenia solium (Pork Tapeworm)</h3>
                        <p><strong>Definitive Host:</strong> Human | <strong>Intermediate:</strong> Pig</p>
                        <p style="margin-top: 10px;"><strong>Larva:</strong> Cysticercus cellulosae</p>
                        <p><strong style="color: #ff4757;">⚠️ CRITICAL:</strong> Causes <strong>Cysticercosis</strong> in brain/muscles - DEADLY!</p>
                    </div>
                    
                    <div style="background: rgba(46,213,115,0.1); border-left: 4px solid #2ed573; padding: 20px; border-radius: 0 10px 10px 0;">
                        <h3 style="color: #2ed573; margin-bottom: 10px;">🐄 Taenia saginata (Beef Tapeworm)</h3>
                        <p><strong>Definitive Host:</strong> Human | <strong>Intermediate:</strong> Cattle</p>
                        <p style="margin-top: 10px;"><strong>Larva:</strong> Cysticercus bovis</p>
                        <p><strong>✓ Milder:</strong> Only gut infection (taeniasis), no cysticercosis</p>
                    </div>
                    
                    <div style="background: rgba(254,202,87,0.1); border-left: 4px solid #feca57; padding: 20px; border-radius: 0 10px 10px 0;">
                        <h3 style="color: #feca57; margin-bottom: 10px;">🐕 Echinococcus granulosus (Dog Tapeworm)</h3>
                        <p><strong>Definitive Host:</strong> Dog, fox | <strong>Intermediate:</strong> Sheep, cattle, <strong>HUMANS</strong></p>
                        <p style="margin-top: 10px;"><strong>Larva:</strong> Hydatid cyst</p>
                        <p><strong style="color: #feca57;">⚠️ ZOONOTIC:</strong> Hydatid disease - huge cysts in liver/lung!</p>
                        <div class="trick-card" style="margin-top: 10px;">
                            <span class="trick-label">💡 MEMORY</span>
                            <p class="trick-content">"Echinococcus = ECHO" → cysts echo through organs, keep growing!</p>
                        </div>
                    </div>
                    
                    <div style="background: rgba(255,71,87,0.1); border-left: 4px solid #ff4757; padding: 20px; border-radius: 0 10px 10px 0;">
                        <h3 style="color: #ff4757; margin-bottom: 10px;">🦊 Echinococcus multilocularis (Fox Tapeworm)</h3>
                        <p><strong>Definitive Host:</strong> Fox, dog | <strong>Intermediate:</strong> Rodents, <strong>HUMANS</strong></p>
                        <p style="margin-top: 10px;"><strong>Larva:</strong> Alveolar hydatid</p>
                        <p><strong style="color: #ff4757;">☠️ WORSE:</strong> Alveolar echinococcosis - invasive, tumor-like, very dangerous!</p>
                    </div>
                    
                    <div style="background: rgba(112,161,255,0.1); border-left: 4px solid #70a1ff; padding: 20px; border-radius: 0 10px 10px 0;">
                        <h3 style="color: #70a1ff; margin-bottom: 10px;">🐕 Dipylidium caninum (Cucumber Tapeworm)</h3>
                        <p><strong>Definitive Host:</strong> Dog, cat, fox | <strong>Intermediate:</strong> Flea larvae, lice</p>
                        <p style="margin-top: 10px;"><strong>Key ID:</strong> Proglottids look like <strong>cucumber seeds</strong> or rice grains in feces</p>
                    </div>
                    
                    <div style="background: rgba(255,165,2,0.1); border-left: 4px solid #ffa502; padding: 20px; border-radius: 0 10px 10px 0;">
                        <h3 style="color: #ffa502; margin-bottom: 10px;">🐁 Hymenolepis nana (Dwarf Tapeworm)</h3>
                        <p><strong>Definitive Host:</strong> Human, mouse | <strong>Intermediate:</strong> <strong>NONE!</strong> (or beetles)</p>
                        <p style="margin-top: 10px;"><strong>🌟 UNIQUE:</strong> <strong>Direct life cycle possible</strong> - only tapeworm that doesn't need intermediate host!</p>
                        <div class="trick-card" style="margin-top: 10px;">
                            <span class="trick-label">💡 MEMORY</span>
                            <p class="trick-content">"H. nana = NANO" = small + no intermediate host needed!</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- TREATMENT SECTION -->
        <section id="treatment" class="section">
            <div class="card">
                <h2 style="color: #feca57; margin-bottom: 20px;">Treatment & Control</h2>
                
                <div class="drug-container">
                    <div class="drug-pill" onclick="showDrugInfo('praziquantel')">
                        PRAZIQUANTEL
                        <div class="drug-info">Drug of Choice for most tapeworms!</div>
                    </div>
                    <div class="drug-pill albendazole" onclick="showDrugInfo('albendazole')">
                        ALBENDAZOLE
                        <div class="drug-info">For hydatid & cysticercosis</div>
                    </div>
                    <div class="drug-pill" onclick="showDrugInfo('niclosamide')">
                        NICLOSAMIDE
                        <div class="drug-info">Alternative option</div>
                    </div>
                </div>
                
                <div id="drugDetail" style="display: none; margin-top: 20px; padding: 20px; background: rgba(0,0,0,0.3); border-radius: 10px;">
                    <h3 id="drugName" style="color: #feca57; margin-bottom: 10px;"></h3>
                    <p id="drugDesc" style="line-height: 1.6;"></p>
                </div>
                
                <div style="margin-top: 30px;">
                    <h3 style="color: #feca57; margin-bottom: 15px;">🛡️ Prevention Strategies</h3>
                    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 15px;">
                        <div style="background: rgba(46,213,115,0.1); padding: 15px; border-radius: 10px; border: 1px solid rgba(46,213,115,0.3);">
                            <strong style="color: #2ed573;">🍖 Meat Safety</strong><br>
                            • Cook meat >60°C<br>
                            • Freeze meat -10°C for 10 days<br>
                            • Meat inspection at slaughter
                        </div>
                        <div style="background: rgba(70,161,255,0.1); padding: 15px; border-radius: 10px; border: 1px solid rgba(70,161,255,0.3);">
                            <strong style="color: #70a1ff;">🐕 Dog Control</strong><br>
                            • Regular deworming with praziquantel<br>
                            • Don't feed raw offal to dogs<br>
                            • Health education
                        </div>
                        <div style="background: rgba(254,202,87,0.1); padding: 15px; border-radius: 10px; border: 1px solid rgba(254,202,87,0.3);">
                            <strong style="color: #feca57;">🧼 Hygiene</strong><br>
                            • Hand washing<br>
                            • Flea control (for Dipylidium)<br>
                            • Sanitation
                        </div>
                    </div>
                </div>
                
                <div class="trick-card" style="margin-top: 20px;">
                    <span class="trick-label">📝 EXAM TIP</span>
                    <p class="trick-content"><strong>Drug of choice:</strong> Praziquantel for most tapeworms; <strong>Albendazole</strong> specifically for hydatid disease and cysticercosis!</p>
                </div>
            </div>
        </section>
        
        <!-- QUIZ SECTION -->
        <section id="quiz" class="section">
            <div class="card quiz-container">
                <h2 style="color: #feca57; margin-bottom: 20px; text-align: center;">🎯 Quick Quiz</h2>
                
                <div class="progress-bar">
                    <div class="progress-fill" id="progressBar"></div>
                </div>
                
                <div id="quizContent">
                    <div class="question-card" id="question1">
                        <h3 style="margin-bottom: 20px;">1. How many suckers does Cyclophyllidea have?</h3>
                        <div class="options">
                            <div class="option" onclick="checkAnswer(this, false)">
                                <span>A</span> 2 suckers
                            </div>
                            <div class="option" onclick="checkAnswer(this, true)">
                                <span>B</span> 4 suckers
                            </div>
                            <div class="option" onclick="checkAnswer(this, false)">
                                <span>C</span> 6 suckers
                            </div>
                            <div class="option" onclick="checkAnswer(this, false)">
                                <span>D</span> No suckers
                            </div>
                        </div>
                    </div>
                    
                    <div class="question-card" id="question2" style="display: none;">
                        <h3 style="margin-bottom: 20px;">2. Which tapeworm does NOT need an intermediate host?</h3>
                        <div class="options">
                            <div class="option" onclick="checkAnswer(this, false)">
                                <span>A</span> Taenia solium
                            </div>
                            <div class="option" onclick="checkAnswer(this, false)">
                                <span>B</span> Dipylidium caninum
                            </div>
                            <div class="option" onclick="checkAnswer(this, true)">
                                <span>C</span> Hymenolepis nana
                            </div>
                            <div class="option" onclick="checkAnswer(this, false)">
                                <span>D</span> Echinococcus granulosus
                            </div>
                        </div>
                    </div>
                    
                    <div class="question-card" id="question3" style="display: none;">
                        <h3 style="margin-bottom: 20px;">3. What is the larval stage of Taenia solium called?</h3>
                        <div class="options">
                            <div class="option" onclick="checkAnswer(this, false)">
                                <span>A</span> Hydatid cyst
                            </div>
                            <div class="option" onclick="checkAnswer(this, true)">
                                <span>B</span> Cysticercus cellulosae
                            </div>
                            <div class="option" onclick="checkAnswer(this, false)">
                                <span>C</span> Tetrathyridium
                            </div>
                            <div class="option" onclick="checkAnswer(this, false)">
                                <span>D</span> Oncosphere
                            </div>
                        </div>
                    </div>
                    
                    <div class="question-card" id="question4" style="display: none;">
                        <h3 style="margin-bottom: 20px;">4. Which family has NO rostellum or hooks?</h3>
                        <div class="options">
                            <div class="option" onclick="checkAnswer(this, true)">
                                <span>A</span> Anoplocephalidae
                            </div>
                            <div class="option" onclick="checkAnswer(this, false)">
                                <span>B</span> Taeniidae
                            </div>
                            <div class="option" onclick="checkAnswer(this, false)">
                                <span>C</span> Dipylidiidae
                            </div>
                            <div class="option" onclick="checkAnswer(this, false)">
                                <span>D</span> Davaineidae
                            </div>
                        </div>
                    </div>
                    
                    <div class="question-card" id="question5" style="display: none;">
                        <h3 style="margin-bottom: 20px;">5. Drug of choice for hydatid disease?</h3>
                        <div class="options">
                            <div class="option" onclick="checkAnswer(this, false)">
                                <span>A</span> Praziquantel
                            </div>
                            <div class="option" onclick="checkAnswer(this, true)">
                                <span>B</span> Albendazole
                            </div>
                            <div class="option" onclick="checkAnswer(this, false)">
                                <span>C</span> Niclosamide
                            </div>
                            <div class="option" onclick="checkAnswer(this, false)">
                                <span>D</span> Ivermectin
                            </div>
                        </div>
                    </div>
                    
                    <div id="quizComplete" style="display: none; text-align: center; padding: 40px;">
                        <h2 style="color: #2ed573; font-size: 3rem; margin-bottom: 20px;">🎉 Complete!</h2>
                        <p style="font-size: 1.2rem; margin-bottom: 20px;">You scored <span id="finalScore" style="color: #feca57; font-weight: bold; font-size: 2rem;">0</span>/5</p>
                        <button onclick="resetQuiz()" class="tab-btn" style="margin-top: 20px;">Try Again</button>
                    </div>
                </div>
            </div>
        </section>
    </div>
    
    <script>
        // Tab Navigation
        function showSection(sectionId) {
            // Hide all sections
            document.querySelectorAll('.section').forEach(section => {
                section.classList.remove('active');
            });
            
            // Remove active class from all buttons
            document.querySelectorAll('.tab-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            
            // Show selected section
            document.getElementById(sectionId).classList.add('active');
            
            // Add active class to clicked button
            event.target.classList.add('active');
        }
        
        // Life Cycle Stage Info
        const stageData = {
            adult: {
                title: "🪱 ADULT STAGE",
                desc: "Adult tapeworm lives in definitive host intestine (human/dog). Gravid proglottids (filled with eggs) break off and pass out in feces. This is the reproductive stage - each proglottid contains both male and female organs (hermaphrodite)!"
            },
            eggs: {
                title: "🥚 EGG STAGE",
                desc: "Eggs released from proglottids into environment (water/grass). Each egg has a thick protective shell called EMBRYOPHORE. Inside is the infective larva waiting to hatch."
            },
            oncosphere: {
                title: "🔱 ONCOSPHERE (HEXACANTH)",
                desc: "When intermediate host eats egg, stomach acids dissolve the embryophore. The 6-hooked larva (hexacanth = six hooks) hatches and uses its hooks to penetrate the gut wall. Then migrates to muscles/tissues."
            },
            cysticercus: {
                title: "🫧 CYSTICERCUS STAGE",
                desc: "In muscle/tissue, oncosphere develops into cysticercus (bladderworm) - a fluid-filled cyst containing one scolex (head). This is the resting stage waiting to be eaten by definitive host. For Echinococcus, this becomes a HYDATID CYST with many scolices."
            },
            intermediate: {
                title: "🐷 INTERMEDIATE HOST",
                desc: "Pig, cattle, sheep, or other herbivores eat eggs with grass. They become infected with larval stages. When humans/dogs eat undercooked infected meat, the cycle completes. Humans can also be accidental intermediate hosts for T. solium (cysticercosis)!"
            }
        };
        
        function showStageInfo(stage) {
            // Remove active class from all nodes
            document.querySelectorAll('.cycle-node').forEach(node => {
                node.classList.remove('active');
            });
            
            // Add active class to clicked node
            event.currentTarget.classList.add('active');
            
            // Show info
            const info = stageData[stage];
            const panel = document.getElementById('stageInfo');
            document.getElementById('stageTitle').textContent = info.title;
            document.getElementById('stageDesc').textContent = info.desc;
            panel.style.display = 'block';
        }
        
        // Family Card Toggle
        function toggleFamily(card) {
            const detail = card.querySelector('.detail-box');
            detail.style.display = detail.style.display === 'none' ? 'block' : 'none';
        }
        
        // Drug Info
        const drugData = {
            praziquantel: {
                name: "Praziquantel",
                desc: "✅ <strong>Drug of Choice</strong> for most tapeworm infections!<br><br>• Mechanism: Increases membrane permeability to calcium → paralysis<br>• Effective against: Taenia spp., Dipylidium, Hymenolepis<br>• Dosage: Single dose usually sufficient<br>• Side effects: Minimal, occasional GI upset"
            },
            albendazole: {
                name: "Albendazole",
                desc: "🎯 <strong>Specific for tissue-dwelling larvae</strong><br><br>• Mechanism: Inhibits microtubule synthesis<br>• Best for: Hydatid disease (Echinococcus), Cysticercosis<br>• Requires: Longer course (28 days for hydatid)<br>• Note: Combined with praziquantel for some cases"
            },
            niclosamide: {
                name: "Niclosamide",
                desc: "🔄 <strong>Alternative/Older drug</strong><br><br>• Mechanism: Uncouples oxidative phosphorylation<br>• Used for: Intestinal tapeworms (not tissue stages)<br>• Limitation: Not absorbed, so ineffective for cysticercosis<br>• Mostly replaced by praziquantel now"
            }
        };
        
        function showDrugInfo(drug) {
            const data = drugData[drug];
            const panel = document.getElementById('drugDetail');
            document.getElementById('drugName').textContent = data.name;
            document.getElementById('drugDesc').innerHTML = data.desc;
            panel.style.display = 'block';
        }
        
        // Quiz Logic
        let currentQuestion = 1;
        let score = 0;
        const totalQuestions = 5;
        
        function checkAnswer(element, isCorrect) {
            // Prevent multiple clicks
            if (element.parentElement.querySelector('.correct') || element.parentElement.querySelector('.wrong')) {
                return;
            }
            
            if (isCorrect) {
                element.classList.add('correct');
                score++;
            } else {
                element.classList.add('wrong');
                // Show correct answer
                element.parentElement.querySelectorAll('.option').forEach(opt => {
                    if (opt.onclick.toString().includes('true')) {
                        opt.classList.add('correct');
                    }
                });
            }
            
            // Update progress
            const progress = (currentQuestion / totalQuestions) * 100;
            document.getElementById('progressBar').style.width = progress + '%';
            
            // Move to next question after delay
            setTimeout(() => {
                document.getElementById('question' + currentQuestion).style.display = 'none';
                currentQuestion++;
                
                if (currentQuestion <= totalQuestions) {
                    document.getElementById('question' + currentQuestion).style.display = 'block';
                } else {
                    document.getElementById('quizComplete').style.display = 'block';
                    document.getElementById('finalScore').textContent = score;
                }
            }, 1500);
        }
        
        function resetQuiz() {
            currentQuestion = 1;
            score = 0;
            document.getElementById('progressBar').style.width = '0%';
            document.getElementById('quizComplete').style.display = 'none';
            
            // Reset all questions
            for (let i = 1; i <= totalQuestions; i++) {
                const q = document.getElementById('question' + i);
                q.style.display = i === 1 ? 'block' : 'none';
                
                // Remove classes from options
                q.querySelectorAll('.option').forEach(opt => {
                    opt.classList.remove('correct', 'wrong');
                });
            }
        }
        
        // Initialize first question
        document.getElementById('question1').style.display = 'block';
    </script>
</body>
</html>
