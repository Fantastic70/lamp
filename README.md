<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LumiArch Pro - AL ARAB ARCHITECTURE</title>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;800&family=JetBrains+Mono:wght@400;600&display=swap" rel="stylesheet">
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        :root {
            --bg-primary: #0F172A;
            --bg-secondary: #1E293B;
            --bg-card: rgba(30, 41, 59, 0.7);
            --accent-gold: #D4AF37; /* الذهبي الخاص بلوجو العرب */
            --accent-blue: #3B82F6;
            --accent-cyan: #06B6D4;
            --danger: #EF4444;
            --text-main: #F8FAFC;
            --text-muted: #94A3B8;
            --border-color: rgba(212, 175, 55, 0.2);
            --card-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.4);
            --radius: 12px;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Cairo', sans-serif;
        }

        body {
            background-color: var(--bg-primary);
            color: var(--text-main);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            line-height: 1.6;
        }

        /* ----- Password Protection Overlay ----- */
        #auth-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background: rgba(15, 23, 42, 0.96);
            backdrop-filter: blur(15px);
            z-index: 9999;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 1.5rem;
        }

        .auth-card {
            background: var(--bg-secondary);
            border: 1px solid var(--border-color);
            border-radius: var(--radius);
            padding: 2.5rem;
            max-width: 420px;
            width: 100%;
            text-align: center;
            box-shadow: 0 20px 40px rgba(0,0,0,0.6);
        }

        .auth-card img {
            height: 60px;
            margin-bottom: 1rem;
            object-fit: contain;
        }

        .auth-card h2 {
            font-size: 1.3rem;
            color: var(--accent-gold);
            margin-bottom: 0.5rem;
        }

        .auth-card p {
            font-size: 0.85rem;
            color: var(--text-muted);
            margin-bottom: 1.5rem;
        }

        .auth-form {
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .auth-form input {
            text-align: center;
            font-size: 1.1rem;
            letter-spacing: 2px;
            padding: 0.85rem;
        }

        .error-msg {
            color: var(--danger);
            font-size: 0.8rem;
            display: none;
            margin-top: -0.5rem;
        }

        /* ----- Main Application Styles ----- */
        #app-content {
            display: none; /* مخفي لحين إدخال الباسورد */
            flex-direction: column;
            min-height: 100vh;
        }

        header {
            background: rgba(15, 23, 42, 0.95);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid var(--border-color);
            padding: 1rem 2rem;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 1rem;
        }

        .brand {
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .brand-logo {
            height: 48px;
            width: auto;
            object-fit: contain;
            border-radius: 4px;
        }

        .brand-info h1 {
            font-size: 1.3rem;
            font-weight: 800;
            letter-spacing: 0.5px;
            background: linear-gradient(135deg, #FFF, var(--accent-gold));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .brand-info p {
            font-size: 0.75rem;
            color: var(--accent-gold);
            font-weight: 600;
        }

        .badge {
            background: rgba(212, 175, 55, 0.15);
            color: var(--accent-gold);
            font-size: 0.8rem;
            padding: 0.35rem 0.8rem;
            border-radius: 20px;
            border: 1px solid rgba(212, 175, 55, 0.4);
            font-weight: 700;
            display: flex;
            align-items: center;
            gap: 0.4rem;
        }

        .container {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 1.5rem;
            flex: 1;
        }

        .grid-layout {
            display: grid;
            grid-template-columns: 1fr;
            gap: 2rem;
        }

        @media (min-width: 992px) {
            .grid-layout {
                grid-template-columns: 420px 1fr;
            }
        }

        .card {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: var(--radius);
            padding: 1.75rem;
            box-shadow: var(--card-shadow);
            backdrop-filter: blur(8px);
        }

        .card-title {
            font-size: 1.15rem;
            font-weight: 700;
            margin-bottom: 1.25rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            color: var(--text-main);
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 0.75rem;
        }

        .card-title i {
            color: var(--accent-gold);
        }

        .form-group {
            margin-bottom: 1.25rem;
        }

        label {
            display: block;
            font-size: 0.875rem;
            font-weight: 600;
            color: var(--text-muted);
            margin-bottom: 0.5rem;
        }

        input, select {
            width: 100%;
            padding: 0.75rem 1rem;
            background: rgba(15, 23, 42, 0.6);
            border: 1px solid var(--border-color);
            border-radius: 8px;
            color: var(--text-main);
            font-size: 0.95rem;
            transition: all 0.3s ease;
        }

        input:focus, select:focus {
            outline: none;
            border-color: var(--accent-gold);
            box-shadow: 0 0 0 3px rgba(212, 175, 55, 0.2);
        }

        .radio-group {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 0.5rem;
            margin-bottom: 1rem;
        }

        .radio-btn {
            background: rgba(15, 23, 42, 0.4);
            border: 1px solid var(--border-color);
            padding: 0.5rem;
            text-align: center;
            border-radius: 6px;
            cursor: pointer;
            font-size: 0.85rem;
            transition: all 0.2s;
        }

        .radio-btn.active {
            background: var(--accent-gold);
            color: #000;
            font-weight: 700;
            border-color: var(--accent-gold);
        }

        .advanced-toggle {
            background: none;
            border: none;
            color: var(--accent-gold);
            font-size: 0.85rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            margin-top: 1rem;
            font-weight: 600;
        }

        .advanced-content {
            display: none;
            margin-top: 1rem;
            padding-top: 1rem;
            border-top: 1px dashed var(--border-color);
        }

        .advanced-content.show {
            display: block;
        }

        .results-header {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1rem;
            margin-bottom: 2rem;
        }

        .metric-card {
            background: rgba(15, 23, 42, 0.5);
            border: 1px solid var(--border-color);
            padding: 1.25rem;
            border-radius: 10px;
            position: relative;
            overflow: hidden;
        }

        .metric-card::before {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 4px;
            height: 100%;
            background: var(--accent-gold);
        }

        .metric-card.blue::before { background: var(--accent-blue); }
        .metric-card.cyan::before { background: var(--accent-cyan); }

        .metric-label {
            font-size: 0.8rem;
            color: var(--text-muted);
            margin-bottom: 0.25rem;
        }

        .metric-value {
            font-size: 1.75rem;
            font-weight: 700;
            font-family: 'JetBrains Mono', monospace;
            color: #fff;
        }

        .metric-unit {
            font-size: 0.85rem;
            color: var(--text-muted);
            margin-left: 0.25rem;
        }

        .fixture-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
            gap: 1rem;
            margin-top: 1rem;
        }

        .fixture-card {
            background: rgba(15, 23, 42, 0.4);
            border: 1px solid var(--border-color);
            padding: 1rem;
            border-radius: 8px;
            display: flex;
            align-items: center;
            gap: 1rem;
            transition: transform 0.2s;
        }

        .fixture-card:hover {
            transform: translateY(-2px);
            border-color: var(--accent-gold);
        }

        .fixture-icon {
            width: 45px;
            height: 45px;
            border-radius: 50%;
            background: rgba(212, 175, 55, 0.15);
            color: var(--accent-gold);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
        }

        .fixture-details h4 {
            font-size: 0.95rem;
            color: #fff;
        }

        .fixture-details p {
            font-size: 0.8rem;
            color: var(--text-muted);
        }

        .fixture-count {
            margin-right: auto;
            font-size: 1.4rem;
            font-weight: 700;
            font-family: 'JetBrains Mono', monospace;
            color: var(--accent-gold);
        }

        .actions-bar {
            display: flex;
            gap: 1rem;
            margin-top: 2rem;
            justify-content: flex-end;
        }

        .btn {
            padding: 0.75rem 1.5rem;
            border-radius: 8px;
            border: none;
            font-weight: 600;
            cursor: pointer;
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            transition: all 0.2s;
            font-size: 0.9rem;
        }

        .btn-primary {
            background: var(--accent-gold);
            color: #000;
            font-weight: 700;
        }

        .btn-primary:hover {
            background: #b8952b;
        }

        .btn-outline {
            background: transparent;
            border: 1px solid var(--border-color);
            color: var(--text-main);
        }

        .btn-outline:hover {
            background: rgba(255, 255, 255, 0.05);
        }

        .formula-box {
            background: rgba(15, 23, 42, 0.8);
            border: 1px solid var(--border-color);
            padding: 1rem;
            border-radius: 8px;
            margin-top: 1.5rem;
            font-size: 0.85rem;
            color: var(--text-muted);
        }

        .formula-box code {
            font-family: 'JetBrains Mono', monospace;
            color: var(--accent-gold);
            display: block;
            margin: 0.5rem 0;
            direction: ltr;
            text-align: left;
        }

        footer {
            text-align: center;
            padding: 2rem 1.5rem;
            color: var(--text-muted);
            font-size: 0.9rem;
            border-top: 1px solid var(--border-color);
            margin-top: 3rem;
            background: rgba(15, 23, 42, 0.8);
        }

        footer .team-name {
            color: var(--accent-gold);
            font-weight: 700;
            font-size: 1.05rem;
        }

        footer .sub-services {
            font-size: 0.8rem;
            margin-top: 0.4rem;
            color: var(--text-muted);
        }

        @media print {
            #auth-overlay { display: none !important; }
            body { background: #fff; color: #000; }
            .card { border: 1px solid #ccc; box-shadow: none; background: #fff; }
            .actions-bar, header, .advanced-toggle { display: none; }
            .metric-value, .fixture-count { color: #000; }
        }
    </style>
</head>
<body>

    <!-- Lock Screen / Password Modal -->
    <div id="auth-overlay">
        <div class="auth-card">
            <img src="logo.png" alt="AL ARAB ARCHITECTURE" onerror="this.style.display='none'">
            <h2>AL ARAB ARCHITECTURE</h2>
            <p>يرجى أدخل كلمة السر للوصول إلى أداة حسابات الإضاءة المعمارية</p>
            
            <form class="auth-form" onsubmit="verifyPassword(event)">
                <input type="password" id="passInput" placeholder="أدخل كلمة السر هنا..." required autofocus>
                <div class="error-msg" id="errorMsg">كلمة السر غير صحيحة، حاول مرة أخرى.</div>
                <button type="submit" class="btn btn-primary" style="justify-content: center; width: 100%;">
                    <i class="fa-solid fa-lock-open"></i> دخول الأداة
                </button>
            </form>
        </div>
    </div>

    <!-- Main Content App -->
    <div id="app-content">
        <header>
            <div class="nav-container">
                <div class="brand">
                    <img src="logo.png" alt="AL ARAB ARCHITECTURE" class="brand-logo" onerror="this.style.display='none'">
                    <div class="brand-info">
                        <h1>AL ARAB ARCHITECTURE</h1>
                        <p>العرب للتشطيبات والاستشارات المعمارية</p>
                    </div>
                </div>
                <div class="badge">
                    <i class="fa-solid fa-compass-drafting"></i>
                    <span>حاسبة الإضاءة المعمارية الاحترافية</span>
                </div>
            </div>
        </header>

        <div class="container">
            <div class="grid-layout">
                
                <!-- Controls Panel -->
                <div class="card">
                    <div class="card-title">
                        <i class="fa-solid fa-sliders"></i>
                        <span>مدخلات المشروع المعماري</span>
                    </div>

                    <!-- Input Method Toggle -->
                    <div class="form-group">
                        <label>طريقة تحديد المساحة</label>
                        <div class="radio-group">
                            <div class="radio-btn active" onclick="setAreaMode('dimensions')" id="btn-dimensions">الطول × العرض</div>
                            <div class="radio-btn" onclick="setAreaMode('direct')" id="btn-direct">مساحة مباشرة ($m^2$)</div>
                        </div>
                    </div>

                    <!-- Dimensions Input -->
                    <div id="dimensions-inputs">
                        <div class="form-group">
                            <label for="length">طول الغرفة (متر)</label>
                            <input type="number" id="length" value="5" min="0.1" step="0.1" oninput="calculate()">
                        </div>
                        <div class="form-group">
                            <label for="width">عرض الغرفة (متر)</label>
                            <input type="number" id="width" value="4" min="0.1" step="0.1" oninput="calculate()">
                        </div>
                    </div>

                    <!-- Direct Area Input -->
                    <div id="direct-input" style="display: none;">
                        <div class="form-group">
                            <label for="area">المساحة الإجمالية (متر مربع)</label>
                            <input type="number" id="area" value="20" min="0.1" step="0.1" oninput="calculate()">
                        </div>
                    </div>

                    <!-- Room Type Selection -->
                    <div class="form-group">
                        <label for="roomType">نوع الفراغ المعماري</label>
                        <select id="roomType" onchange="calculate()">
                            <optgroup label="فراغات سكنية">
                                <option value="150" selected>غرفة معيشة (Living Room) - 150 Lux</option>
                                <option value="100">غرفة نوم - إضاءة عامة (Bedroom) - 100 Lux</option>
                                <option value="300">غرفة نوم - إضاءة القراءة (Reading) - 300 Lux</option>
                                <option value="300">مطبخ - تحضير الطعام (Kitchen) - 300 Lux</option>
                                <option value="500">مطبخ - تفاصيل دقيقة (Detailed Kitchen) - 500 Lux</option>
                                <option value="150">حمام - إضاءة عامة (Bathroom) - 150 Lux</option>
                                <option value="300">حمام - مرآة وتزيين (Vanity Area) - 300 Lux</option>
                                <option value="200">غرفة طعام (Dining Room) - 200 Lux</option>
                                <option value="100">ممرات وسلالم (Corridors/Stairs) - 100 Lux</option>
                            </optgroup>
                            <optgroup label="فراغات إدارية وتجارية">
                                <option value="500">مكتب عمل / دراسة (Home Office / Desk) - 500 Lux</option>
                                <option value="500">مكتب مفتوح / شركات (Open Office) - 500 Lux</option>
                                <option value="300">قاعة اجتماعات (Meeting Room) - 300 Lux</option>
                                <option value="500">صالة عرض / متجر (Retail Showroom) - 500 Lux</option>
                                <option value="200">استقبال / مدخل (Reception Area) - 200 Lux</option>
                            </optgroup>
                        </select>
                    </div>

                    <!-- Advanced Options Toggle -->
                    <button class="advanced-toggle" onclick="toggleAdvanced()">
                        <i class="fa-solid fa-gear"></i>
                        <span>معاملات متقدمة (UF / MF / Efficacy)</span>
                    </button>

                    <div class="advanced-content" id="advanced-panel">
                        <div class="form-group">
                            <label for="uf">معامل الاستفادة (Utilization Factor - UF)</label>
                            <input type="number" id="uf" value="0.6" min="0.1" max="1" step="0.05" oninput="calculate()">
                            <small style="color: var(--text-muted); font-size: 0.75rem;">يعتمد على انعكاسية الجدران والسقف (الافتراضي 0.6)</small>
                        </div>
                        <div class="form-group">
                            <label for="mf">معامل الصيانة (Maintenance Factor - MF)</label>
                            <input type="number" id="mf" value="0.8" min="0.1" max="1" step="0.05" oninput="calculate()">
                            <small style="color: var(--text-muted); font-size: 0.75rem;">فقدان الضوء بسبب الأتربة وتقادم المصابيح (الافتراضي 0.8)</small>
                        </div>
                        <div class="form-group">
                            <label for="efficacy">كفاءة الإضاءة (LED Efficacy - Lumens/Watt)</label>
                            <input type="number" id="efficacy" value="90" min="10" max="200" step="5" oninput="calculate()">
                            <small style="color: var(--text-muted); font-size: 0.75rem;">معدل اللومن لكل وات لتقنية LED (الافتراضي 90 lm/W)</small>
                        </div>
                    </div>

                </div>

                <!-- Output Display Panel -->
                <div>
                    <div class="card">
                        <div class="card-title">
                            <i class="fa-solid fa-chart-pie"></i>
                            <span>نتائج الحسابات الهندسية المعمارية</span>
                        </div>

                        <div class="results-header">
                            <div class="metric-card">
                                <div class="metric-label">المساحة المحسوبة</div>
                                <div class="metric-value" id="res-area">20.0<span class="metric-unit">$m^2$</span></div>
                            </div>
                            <div class="metric-card blue">
                                <div class="metric-label">إجمالي التدفق الضوئي (Lumens)</div>
                                <div class="metric-value" id="res-lumens">6,250<span class="metric-unit">lm</span></div>
                            </div>
                            <div class="metric-card cyan">
                                <div class="metric-label">القدرة الكهربائية المقدرة</div>
                                <div class="metric-value" id="res-power">69.4<span class="metric-unit">W</span></div>
                            </div>
                        </div>

                        <h3 style="font-size: 1rem; margin-bottom: 1rem; color: var(--text-main);">
                            <i class="fa-solid fa-border-all" style="color: var(--accent-gold); margin-left: 0.5rem;"></i>
                            توزيع وحدات الإضاءة المقترحة (Spotlights / Fixtures)
                        </h3>

                        <div class="fixture-grid">
                            <div class="fixture-card">
                                <div class="fixture-icon"><i class="fa-regular fa-lightbulb"></i></div>
                                <div class="fixture-details">
                                    <h4>سبوت لايت 7 Watt</h4>
                                    <p>~630 Lumen / unit</p>
                                </div>
                                <div class="fixture-count" id="count-7w">10</div>
                            </div>

                            <div class="fixture-card">
                                <div class="fixture-icon"><i class="fa-solid fa-lightbulb"></i></div>
                                <div class="fixture-details">
                                    <h4>سبوت لايت 12 Watt</h4>
                                    <p>~1080 Lumen / unit</p>
                                </div>
                                <div class="fixture-count" id="count-12w">6</div>
                            </div>

                            <div class="fixture-card">
                                <div class="fixture-icon"><i class="fa-solid fa-circle-dot"></i></div>
                                <div class="fixture-details">
                                    <h4>كشاف LED 18 Watt</h4>
                                    <p>~1620 Lumen / unit</p>
                                </div>
                                <div class="fixture-count" id="count-18w">4</div>
                            </div>

                            <div class="fixture-card">
                                <div class="fixture-icon"><i class="fa-solid fa-sun"></i></div>
                                <div class="fixture-details">
                                    <h4>بلاطة LED 24 Watt</h4>
                                    <p>~2160 Lumen / unit</p>
                                </div>
                                <div class="fixture-count" id="count-24w">3</div>
                            </div>
                        </div>

                        <div class="formula-box">
                            <strong>المعادلة الهندسية المعتمدة (Lumen Method):</strong>
                            <code>Total Lumens (Φ) = (Target Lux [E] × Area [A]) / (UF × MF)</code>
                            <span id="formula-explanation"></span>
                        </div>

                        <div class="actions-bar">
                            <button class="btn btn-outline" onclick="window.print()">
                                <i class="fa-solid fa-print"></i> طباعة التقرير الفني
                            </button>
                        </div>

                    </div>
                </div>

            </div>
        </div>

        <footer>
            <p>تم تطوير هذه الأداة بواسطة فريق <span class="team-name">AL ARAB ARCHITECTURE (العرب للتشطيبات)</span></p>
            <p class="sub-services">إنشاءات | تشطيبات | تصميم داخلي وخارجي</p>
        </footer>
    </div>

    <script>
        // 🔑 كلمة السر المقررة لفتح التطبيق
        const CORRECT_PASSWORD = "ALARAB2026";

        function verifyPassword(event) {
            event.preventDefault();
            const inputVal = document.getElementById('passInput').value;
            const errorMsg = document.getElementById('errorMsg');
            
            if (inputVal === CORRECT_PASSWORD) {
                document.getElementById('auth-overlay').style.display = 'none';
                document.getElementById('app-content').style.display = 'flex';
                calculate();
            } else {
                errorMsg.style.display = 'block';
                document.getElementById('passInput').value = '';
                document.getElementById('passInput').focus();
            }
        }

        let areaMode = 'dimensions';

        function setAreaMode(mode) {
            areaMode = mode;
            document.getElementById('btn-dimensions').classList.toggle('active', mode === 'dimensions');
            document.getElementById('btn-direct').classList.toggle('active', mode === 'direct');
            
            document.getElementById('dimensions-inputs').style.display = mode === 'dimensions' ? 'block' : 'none';
            document.getElementById('direct-input').style.display = mode === 'direct' ? 'block' : 'none';
            
            calculate();
        }

        function toggleAdvanced() {
            const panel = document.getElementById('advanced-panel');
            panel.classList.toggle('show');
        }

        function calculate() {
            let calculatedArea = 0;

            if (areaMode === 'dimensions') {
                const length = parseFloat(document.getElementById('length').value) || 0;
                const width = parseFloat(document.getElementById('width').value) || 0;
                calculatedArea = length * width;
            } else {
                calculatedArea = parseFloat(document.getElementById('area').value) || 0;
            }

            const targetLux = parseFloat(document.getElementById('roomType').value);
            const uf = parseFloat(document.getElementById('uf').value) || 0.6;
            const mf = parseFloat(document.getElementById('mf').value) || 0.8;
            const efficacy = parseFloat(document.getElementById('efficacy').value) || 90;

            if (calculatedArea <= 0 || uf <= 0 || mf <= 0) {
                return;
            }

            // Calculation using Lumen Method
            const totalLumens = (targetLux * calculatedArea) / (uf * mf);
            const totalWatts = totalLumens / efficacy;

            // Update DOM Results
            document.getElementById('res-area').innerHTML = `${calculatedArea.toFixed(1)} <span class="metric-unit">m²</span>`;
            document.getElementById('res-lumens').innerHTML = `${Math.round(totalLumens).toLocaleString()} <span class="metric-unit">lm</span>`;
            document.getElementById('res-power').innerHTML = `${totalWatts.toFixed(1)} <span class="metric-unit">W</span>`;

            // Calculate Fixture Counts (Rounded up)
            const lumen7w = 7 * efficacy;
            const lumen12w = 12 * efficacy;
            const lumen18w = 18 * efficacy;
            const lumen24w = 24 * efficacy;

            document.getElementById('count-7w').innerText = Math.ceil(totalLumens / lumen7w);
            document.getElementById('count-12w').innerText = Math.ceil(totalLumens / lumen12w);
            document.getElementById('count-18w').innerText = Math.ceil(totalLumens / lumen18w);
            document.getElementById('count-24w').innerText = Math.ceil(totalLumens / lumen24w);

            // Update Formula Text Explanation
            document.getElementById('formula-explanation').innerText = 
                `الحساب الحقيقي: (${targetLux} Lux × ${calculatedArea.toFixed(1)} m²) / (${uf} × ${mf}) = ${Math.round(totalLumens).toLocaleString()} Lumens`;
        }
    </script>

</body>
</html>
