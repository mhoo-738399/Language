<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>باريتو 20/80 - منصة اللغات المتعددة</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Segoe UI', system-ui, sans-serif; }
        body { background-color: #f4f7fc; color: #1e293b; padding: 20px; }
        :root { --primary: #4f6f8f; --accent: #38bdf8; --shadow: 0 8px 20px rgba(0,0,0,0.05); --radius: 16px; }
        .container { max-width: 1200px; margin: 0 auto; }
        .header { background: white; padding: 15px 30px; border-radius: var(--radius); box-shadow: var(--shadow); display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 15px; margin-bottom: 20px; }
        .logo { font-size: 22px; font-weight: 700; color: var(--primary); }
        .logo i { color: var(--accent); margin-left: 10px; }
        .lang-selector { display: flex; align-items: center; gap: 10px; }
        .lang-selector select { padding: 8px 16px; border-radius: 30px; border: 2px solid #e2e8f0; font-weight: 600; background: white; cursor: pointer; }
        .user-profile { display: flex; align-items: center; gap: 10px; }
        .avatar { width: 40px; height: 40px; border-radius: 50%; background: #e2e8f0; display: flex; align-items: center; justify-content: center; }
        .tabs { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 20px; background: white; padding: 12px 20px; border-radius: var(--radius); box-shadow: var(--shadow); }
        .tab-btn { padding: 8px 18px; border: none; background: transparent; border-radius: 40px; font-weight: 600; color: #64748b; cursor: pointer; transition: 0.3s; font-size: 14px; }
        .tab-btn:hover { background: #e2e8f0; }
        .tab-btn.active { background: var(--primary); color: white; }
        .content-section { display: none; background: white; padding: 25px; border-radius: var(--radius); box-shadow: var(--shadow); animation: fadeIn 0.3s; }
        .content-section.active { display: block; }
        @keyframes fadeIn { from { opacity:0; transform:translateY(10px); } to { opacity:1; transform:translateY(0); } }
        .card-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 20px; margin-top: 20px; }
        .word-card, .sentence-card { background: #f8fafc; padding: 18px; border-radius: 12px; border-right: 4px solid var(--accent); transition: 0.2s; }
        .word-card:hover { transform: translateY(-3px); box-shadow: var(--shadow); }
        .word-original { font-size: 20px; font-weight: 700; }
        .word-trans { color: #64748b; font-size: 14px; margin: 5px 0; }
        .word-ar { color: var(--primary); font-weight: 600; }
        .example { font-size: 14px; color: #475569; margin-top: 8px; background: white; padding: 8px; border-radius: 8px; }
        .btn-speak { background: none; border: none; color: var(--accent); font-size: 18px; cursor: pointer; margin-right: 10px; }
        .video-container { position: relative; width: 100%; max-width: 800px; margin: 20px auto; background: #0f172a; border-radius: var(--radius); overflow: hidden; aspect-ratio: 16/9; }
        .video-container video { width: 100%; height: 100%; display: block; }
        .interactive-overlay { position: absolute; bottom: 20px; left: 20px; right: 20px; display: flex; flex-wrap: wrap; gap: 12px; justify-content: center; }
        .interactive-overlay button { padding: 12px 24px; border: none; border-radius: 40px; background: rgba(255,255,255,0.9); backdrop-filter: blur(5px); font-weight: 600; color: #0f172a; cursor: pointer; box-shadow: 0 4px 10px rgba(0,0,0,0.3); transition: 0.2s; font-size: 14px; }
        .interactive-overlay button:hover { transform: scale(1.05); background: white; }
        .scene-text { position: absolute; top: 20px; right: 20px; background: rgba(0,0,0,0.7); color: white; padding: 12px 20px; border-radius: 30px; font-size: 14px; max-width: 70%; }
        .scenario-box { background: #f1f5f9; padding: 20px; border-radius: 12px; margin: 15px 0; }
        .scenario-options { display: flex; flex-wrap: wrap; gap: 12px; margin-top: 15px; }
        .scenario-options button { padding: 12px 25px; border: 2px solid var(--primary); background: white; border-radius: 40px; font-weight: 600; cursor: pointer; transition: 0.2s; }
        .scenario-options button:hover { background: var(--primary); color: white; }
        .feedback-box { background: white; padding: 15px; border-radius: 10px; margin-top: 15px; border-right: 5px solid var(--accent); }
        .ai-container { display: flex; flex-wrap: wrap; gap: 20px; margin: 20px 0; }
        .ai-box { flex: 1; min-width: 250px; background: #f1f5f9; padding: 20px; border-radius: 12px; }
        .mic-btn { background: var(--primary); color: white; border: none; padding: 15px 30px; border-radius: 60px; font-size: 18px; cursor: pointer; transition: 0.2s; }
        .mic-btn:hover { background: #2c3e50; }
        .mic-btn.recording { background: #ef4444; animation: pulse 1.5s infinite; }
        @keyframes pulse { 0% { opacity:1; } 50% { opacity:0.5; } 100% { opacity:1; } }
        .progress-bar { background: #e2e8f0; height: 8px; border-radius: 10px; margin: 15px 0; overflow: hidden; }
        .progress-fill { background: #22c55e; height: 100%; width: 0%; border-radius: 10px; }
        .stats-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: 15px; margin: 20px 0; }
        .stat-card { background: #f8fafc; padding: 20px; border-radius: 12px; text-align: center; }
        .stat-number { font-size: 32px; font-weight: 700; color: var(--primary); }
        .lang-badge { display: inline-block; background: #dbeafe; color: #1e40af; padding: 2px 12px; border-radius: 20px; font-size: 12px; }
        @media (max-width: 600px) { .header { flex-direction: column; align-items: stretch; } .lang-selector { justify-content: center; } }
    </style>
</head>
<body>
<div class="container" id="app">
    <header class="header">
        <div class="logo"><i class="fas fa-globe"></i> ParetoLingua</div>
        <div class="lang-selector">
            <i class="fas fa-language"></i>
            <select id="languageSelect" onchange="switchLanguage(this.value)">
                <option value="en">🇬🇧 الإنجليزية</option>
                <option value="es">🇪🇸 الإسبانية</option>
                <option value="ru">🇷🇺 الروسية</option>
                <option value="fr">🇫🇷 الفرنسية</option>
                <option value="de">🇩🇪 الألمانية</option>
                <option value="ko">🇰🇷 الكورية</option>
                <option value="zh">🇨🇳 الصينية</option>
            </select>
        </div>
        <div class="user-profile"><span>أهلاً، أحمد</span><div class="avatar"><i class="fas fa-user"></i></div></div>
    </header>

    <nav class="tabs" id="tabNav">
        <button class="tab-btn active" data-tab="dashboard"><i class="fas fa-chart-pie"></i> لوحة التحكم</button>
        <button class="tab-btn" data-tab="words"><i class="fas fa-book"></i> الكلمات (1000)</button>
        <button class="tab-btn" data-tab="sentences"><i class="fas fa-comment"></i> الجمل (300)</button>
        <button class="tab-btn" data-tab="video"><i class="fas fa-video"></i> الفيديو التفاعلي</button>
        <button class="tab-btn" data-tab="scenarios"><i class="fas fa-route"></i> السيناريوهات</button>
        <button class="tab-btn" data-tab="ai"><i class="fas fa-robot"></i> الذكاء الاصطناعي</button>
    </nav>

    <!-- لوحة التحكم -->
    <section id="dashboard" class="content-section active">
        <h2><i class="fas fa-chart-line"></i> تقدمك في <span id="dashLangName">الإنجليزية</span></h2>
        <div class="stats-grid">
            <div class="stat-card"><div class="stat-number">85</div> كلمات متقنة</div>
            <div class="stat-card"><div class="stat-number">42</div> جمل حفظتها</div>
            <div class="stat-card"><div class="stat-number">7</div> أيام متتالية</div>
            <div class="stat-card"><div class="stat-number">A2</div> المستوى الحالي</div>
        </div>
        <div style="margin: 20px 0;"><h3>خطة التعلم (30 يوم)</h3><div class="progress-bar"><div class="progress-fill" style="width:65%"></div></div><p>الأسبوع الثالث: ركز على مفردات السفر والمطاعم</p></div>
        <div style="background:#eef2ff; padding:15px; border-radius:12px;"><i class="fas fa-lightbulb" style="color:#fbbf24;"></i> اقتراح الذكاء الاصطناعي: راجع 10 كلمات عن "الطقس" اليوم.</div>
    </section>

    <!-- الكلمات -->
    <section id="words" class="content-section">
        <h2><i class="fas fa-book-open"></i> أهم الكلمات في <span id="wordsLangName">الإنجليزية</span></h2>
        <div style="display:flex; gap:10px; margin:15px 0; flex-wrap:wrap;">
            <select id="levelFilter" style="padding:8px 16px; border-radius:30px; border:1px solid #ddd;">
                <option value="all">الكل</option><option value="A1">A1</option><option value="A2">A2</option><option value="B1">B1</option>
            </select>
            <select id="topicFilter" style="padding:8px 16px; border-radius:30px; border:1px solid #ddd;">
                <option value="all">كل المواضيع</option><option value="عائلة">عائلة</option><option value="سفر">سفر</option><option value="طعام">طعام</option><option value="تحية">تحية</option>
            </select>
        </div>
        <div id="wordList" class="card-grid"></div>
        <p style="color:#64748b; margin-top:20px;">* نموذج 10 كلمات لكل لغة، يمكنك توسيعها إلى 1000 بنفس الهيكل.</p>
    </section>

    <!-- الجمل -->
    <section id="sentences" class="content-section">
        <h2><i class="fas fa-quote-right"></i> أهم الجمل اليومية في <span id="sentLangName">الإنجليزية</span></h2>
        <div id="sentenceList" class="card-grid"></div>
    </section>

    <!-- الفيديو التفاعلي -->
    <section id="video" class="content-section">
        <h2><i class="fas fa-play-circle"></i> الفيديو التفاعلي</h2>
        <div class="video-container" id="interactiveVideo">
            <video id="demoVideo" src="#" poster="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='800' height='450'%3E%3Crect width='800' height='450' fill='%233b82f6'/%3E%3Ctext x='400' y='225' font-size='28' fill='white' text-anchor='middle' font-family='sans-serif'%3Eفيديو تفاعلي%3C/text%3E%3C/svg%3E" controls></video>
            <div class="scene-text" id="videoSceneText">المشهد 1: مرحباً، هل تريد طلباً؟</div>
            <div class="interactive-overlay" id="videoBtns">
                <button onclick="changeScene(1)">📖 أريد القائمة</button>
                <button onclick="changeScene(2)">💧 ماء فقط</button>
            </div>
        </div>
        <div id="videoFeedback" style="margin-top:15px; padding:15px; background:#f1f5f9; border-radius:12px;"><i class="fas fa-comment-dots"></i> رد الفيديو: تفضل القائمة، سأحضرها لك الآن.</div>
    </section>

    <!-- السيناريوهات -->
    <section id="scenarios" class="content-section">
        <h2><i class="fas fa-people-arrows"></i> السيناريوهات التفاعلية</h2>
        <div style="display:flex; gap:10px; flex-wrap:wrap; margin:15px 0;">
            <button onclick="loadScenario(0)" class="tab-btn" style="background:#e2e8f0;">المطعم</button>
            <button onclick="loadScenario(1)" class="tab-btn" style="background:#e2e8f0;">المطار</button>
            <button onclick="loadScenario(2)" class="tab-btn" style="background:#e2e8f0;">التسوق</button>
            <button onclick="loadScenario(3)" class="tab-btn" style="background:#e2e8f0;">الفندق</button>
            <button onclick="loadScenario(4)" class="tab-btn" style="background:#e2e8f0;">التاكسي</button>
            <button onclick="loadScenario(5)" class="tab-btn" style="background:#e2e8f0;">المدرسة</button>
            <button onclick="loadScenario(6)" class="tab-btn" style="background:#e2e8f0;">العمل</button>
            <button onclick="loadScenario(7)" class="tab-btn" style="background:#e2e8f0;">التعارف</button>
        </div>
        <div id="scenarioDisplay" class="scenario-box">
            <h3 id="scenarioTitle">المطعم</h3>
            <p id="scenarioDesc">النادل: مرحباً، ما هو طلبك؟</p>
            <div id="scenarioOptions" class="scenario-options"></div>
            <div id="scenarioFeedback" class="feedback-box" style="display:none;"></div>
        </div>
    </section>

    <!-- الذكاء الاصطناعي -->
    <section id="ai" class="content-section">
        <h2><i class="fas fa-microchip"></i> الذكاء الاصطناعي - <span id="aiLangName">الإنجليزية</span></h2>
        <div class="ai-container">
            <div class="ai-box"><h4><i class="fas fa-robot"></i> اقتراح الدرس</h4><p id="aiSuggestion">بناءً على مستواك، ننصحك بدراسة الأفعال الشائعة.</p><button onclick="generateSuggestion()" style="margin-top:10px; padding:8px 20px; border:none; background:var(--primary); color:white; border-radius:30px;">اقتراح جديد</button></div>
            <div class="ai-box"><h4><i class="fas fa-microphone"></i> تحليل النطق</h4><p>انقر وتحدث بالجملة الظاهرة:</p><p style="background:white; padding:10px; border-radius:8px; font-weight:bold;" id="targetPhrase">Good morning, how are you?</p><button id="micButton" class="mic-btn" onclick="startListening()"><i class="fas fa-microphone"></i> اضغط وتحدث</button><div style="margin-top:15px;"><p>نتيجة التقييم: <span id="evaluationResult" style="font-weight:bold; color:var(--primary);">في انتظار النطق...</span></p><div class="progress-bar"><div id="accuracyBar" class="progress-fill" style="width:0%"></div></div></div></div>
        </div>
    </section>
</div>

<script>
// ================================================================
// 1. البيانات: 7 لغات (كل لغة: 10 كلمات + 8 جمل نموذجية)
// ================================================================
const allLanguageData = {
    en: {
        name: 'الإنجليزية', tts: 'en-US',
        words: [
            { id:1, word:"Mother", trans:"ماذَر", ar:"أمّ", topic:"عائلة", level:"A1", example:"My mother is a teacher." },
            { id:2, word:"Water", trans:"ووتَر", ar:"ماء", topic:"طعام", level:"A1", example:"I drink water daily." },
            { id:3, word:"Airport", trans:"إيربورت", ar:"مطار", topic:"سفر", level:"A1", example:"The airport is far." },
            { id:4, word:"Price", trans:"بْرَايْس", ar:"السعر", topic:"تسوق", level:"A2", example:"The price is high." },
            { id:5, word:"Office", trans:"أوفِس", ar:"مكتب", topic:"عمل", level:"A2", example:"I go to the office." },
            { id:6, word:"Medicine", trans:"مِدِسِن", ar:"دواء", topic:"صحة", level:"B1", example:"Take this medicine." },
            { id:7, word:"Hello", trans:"هالو", ar:"مرحباً", topic:"تحية", level:"A1", example:"Hello, how are you?" },
            { id:8, word:"Ticket", trans:"تِكِت", ar:"تذكرة", topic:"سفر", level:"A1", example:"I need a ticket." },
            { id:9, word:"Delicious", trans:"دِلِشَس", ar:"لذيذ", topic:"طعام", level:"A2", example:"This is delicious." },
            { id:10, word:"Interview", trans:"إِنْتَرْفْيُو", ar:"مقابلة", topic:"عمل", level:"B1", example:"I have an interview." }
        ],
        sentences: [
            { id:1, sentence:"How are you?", trans:"هاو آر يو؟", ar:"كيف حالك؟", level:"A1", context:"تحية" },
            { id:2, sentence:"I would like coffee.", trans:"آي وود لايك كوفي.", ar:"أريد قهوة.", level:"A1", context:"مطعم" },
            { id:3, sentence:"Where is the bathroom?", trans:"وير إز ذا باثروم؟", ar:"أين الحمام؟", level:"A1", context:"أماكن" },
            { id:4, sentence:"How much is it?", trans:"هاو ماتش إز إت؟", ar:"كم سعره؟", level:"A2", context:"تسوق" },
            { id:5, sentence:"I need a room.", trans:"آي نيد أ روم.", ar:"أحتاج غرفة.", level:"A2", context:"فندق" },
            { id:6, sentence:"I arrived yesterday.", trans:"آي أرايفد ييسترداي.", ar:"وصلت أمس.", level:"A2", context:"سفر" },
            { id:7, sentence:"I agree with you.", trans:"آي أغري ويث يو.", ar:"أوافق معك.", level:"B1", context:"عمل" },
            { id:8, sentence:"What is your name?", trans:"وات إز يور نيم؟", ar:"ما اسمك؟", level:"A1", context:"تعارف" }
        ]
    },
    es: {
        name: 'الإسبانية', tts: 'es-ES',
        words: [
            { id:1, word:"Madre", trans:"مَادْرِي", ar:"أمّ", topic:"عائلة", level:"A1", example:"Mi madre es maestra." },
            { id:2, word:"Agua", trans:"أَغْوَا", ar:"ماء", topic:"طعام", level:"A1", example:"Bebo agua cada día." },
            { id:3, word:"Aeropuerto", trans:"أَيْرُوبُوِيرْتُو", ar:"مطار", topic:"سفر", level:"A1", example:"El aeropuerto está lejos." },
            { id:4, word:"Precio", trans:"بْرِيسِيُو", ar:"السعر", topic:"تسوق", level:"A2", example:"El precio es alto." },
            { id:5, word:"Oficina", trans:"أُوفِيسِينَا", ar:"مكتب", topic:"عمل", level:"A2", example:"Voy a la oficina." },
            { id:6, word:"Medicina", trans:"مِيدِيسِينَا", ar:"دواء", topic:"صحة", level:"B1", example:"Toma esta medicina." },
            { id:7, word:"Hola", trans:"أُولَا", ar:"مرحباً", topic:"تحية", level:"A1", example:"¡Hola! ¿Cómo estás?" },
            { id:8, word:"Boleto", trans:"بُولِيتُو", ar:"تذكرة", topic:"سفر", level:"A1", example:"Necesito un boleto." },
            { id:9, word:"Delicioso", trans:"دِيلِيثِيُوسُو", ar:"لذيذ", topic:"طعام", level:"A2", example:"¡Esto es delicioso!" },
            { id:10, word:"Entrevista", trans:"إِنْتَرْفِيسْتَا", ar:"مقابلة", topic:"عمل", level:"B1", example:"Tengo una entrevista." }
        ],
        sentences: [
            { id:1, sentence:"¿Cómo estás?", trans:"كُومُو إِسْتَاسْ؟", ar:"كيف حالك؟", level:"A1", context:"تحية" },
            { id:2, sentence:"Quiero un café.", trans:"كِيِيرُو أُنْ كَافِيهْ.", ar:"أريد قهوة.", level:"A1", context:"مطعم" },
            { id:3, sentence:"¿Dónde está el baño?", trans:"دُونْدِي إِسْتَا إِلْ بَانْيُو؟", ar:"أين الحمام؟", level:"A1", context:"أماكن" },
            { id:4, sentence:"¿Cuánto cuesta?", trans:"كُوَانْتُو كُوِيسْتَا؟", ar:"كم سعره؟", level:"A2", context:"تسوق" },
            { id:5, sentence:"Necesito una habitación.", trans:"نِيثِيسِيتُو أُونَا أَبِيتَاثِيُونْ.", ar:"أحتاج غرفة.", level:"A2", context:"فندق" },
            { id:6, sentence:"Llegué ayer.", trans:"يِيغِي أَيِيرْ.", ar:"وصلت أمس.", level:"A2", context:"سفر" },
            { id:7, sentence:"Estoy de acuerdo.", trans:"إِسْتُوي دِي أَكُوِيرْدُو.", ar:"أنا موافق.", level:"B1", context:"عمل" },
            { id:8, sentence:"¿Cómo te llamas?", trans:"كُومُو تِي يَامَاسْ؟", ar:"ما اسمك؟", level:"A1", context:"تعارف" }
        ]
    },
    ru: {
        name: 'الروسية', tts: 'ru-RU',
        words: [
            { id:1, word:"Мама", trans:"مَامَا", ar:"أمّ", topic:"عائلة", level:"A1", example:"Моя мама учитель." },
            { id:2, word:"Вода", trans:"فَادَا", ar:"ماء", topic:"طعام", level:"A1", example:"Я пью воду каждый день." },
            { id:3, word:"Аэропорт", trans:"أَيْرَابُورْت", ar:"مطار", topic:"سفر", level:"A1", example:"Аэропорт далеко." },
            { id:4, word:"Цена", trans:"تْسِينَا", ar:"السعر", topic:"تسوق", level:"A2", example:"Цена высокая." },
            { id:5, word:"Офис", trans:"أُوفِيس", ar:"مكتب", topic:"عمل", level:"A2", example:"Я иду в офис." },
            { id:6, word:"Лекарство", trans:"لِيكَارْسْتْفَا", ar:"دواء", topic:"صحة", level:"B1", example:"Прими это лекарство." },
            { id:7, word:"Привет", trans:"بْرِيفْيِتْ", ar:"مرحباً", topic:"تحية", level:"A1", example:"Привет, как дела?" },
            { id:8, word:"Билет", trans:"بِيلْيِتْ", ar:"تذكرة", topic:"سفر", level:"A1", example:"Мне нужен билет." },
            { id:9, word:"Вкусный", trans:"فْكُوسْنِي", ar:"لذيذ", topic:"طعام", level:"A2", example:"Это вкусно." },
            { id:10, word:"Интервью", trans:"إِنْتَرْفْيُو", ar:"مقابلة", topic:"عمل", level:"B1", example:"У меня интервью." }
        ],
        sentences: [
            { id:1, sentence:"Как дела?", trans:"كَاكْ دِيلَا؟", ar:"كيف حالك؟", level:"A1", context:"تحية" },
            { id:2, sentence:"Я хочу кофе.", trans:"يَا خَاتْشُو كُوفِي.", ar:"أريد قهوة.", level:"A1", context:"مطعم" },
            { id:3, sentence:"Где туалет?", trans:"غْدِي تُالْيِتْ؟", ar:"أين الحمام؟", level:"A1", context:"أماكن" },
            { id:4, sentence:"Сколько стоит?", trans:"سْكُولْكَا سْتُويِتْ؟", ar:"كم سعره؟", level:"A2", context:"تسوق" },
            { id:5, sentence:"Мне нужна комната.", trans:"مْنِي نُوجْنَا كُومْنَاتَا.", ar:"أحتاج غرفة.", level:"A2", context:"فندق" },
            { id:6, sentence:"Я приехал вчера.", trans:"يَا بْرِيِيخَالْ فْشِيرَا.", ar:"وصلت أمس.", level:"A2", context:"سفر" },
            { id:7, sentence:"Я согласен.", trans:"يَا سَاغْلَاسِنْ.", ar:"أنا موافق.", level:"B1", context:"عمل" },
            { id:8, sentence:"Как тебя зовут?", trans:"كَاكْ تِيبْيَا زَافُوتْ؟", ar:"ما اسمك؟", level:"A1", context:"تعارف" }
        ]
    },
    fr: {
        name: 'الفرنسية', tts: 'fr-FR',
        words: [
            { id:1, word:"Mère", trans:"مِيرْ", ar:"أمّ", topic:"عائلة", level:"A1", example:"Ma mère est enseignante." },
            { id:2, word:"Eau", trans:"أُو", ar:"ماء", topic:"طعام", level:"A1", example:"Je bois de l'eau." },
            { id:3, word:"Aéroport", trans:"أَيْرُوبُورْ", ar:"مطار", topic:"سفر", level:"A1", example:"L'aéroport est loin." },
            { id:4, word:"Prix", trans:"بْرِي", ar:"السعر", topic:"تسوق", level:"A2", example:"Le prix est élevé." },
            { id:5, word:"Bureau", trans:"بُورُو", ar:"مكتب", topic:"عمل", level:"A2", example:"Je vais au bureau." },
            { id:6, word:"Médicament", trans:"مِيدِيكَامَانْ", ar:"دواء", topic:"صحة", level:"B1", example:"Prenez ce médicament." },
            { id:7, word:"Bonjour", trans:"بُونْجُورْ", ar:"مرحباً", topic:"تحية", level:"A1", example:"Bonjour, comment allez-vous?" },
            { id:8, word:"Billet", trans:"بِيِيِهْ", ar:"تذكرة", topic:"سفر", level:"A1", example:"J'ai besoin d'un billet." },
            { id:9, word:"Délicieux", trans:"دِيلِيسِيُو", ar:"لذيذ", topic:"طعام", level:"A2", example:"C'est délicieux." },
            { id:10, word:"Entretien", trans:"آنْتْرُوتِيَانْ", ar:"مقابلة", topic:"عمل", level:"B1", example:"J'ai un entretien." }
        ],
        sentences: [
            { id:1, sentence:"Comment ça va?", trans:"كُومَانْ سَا فَا؟", ar:"كيف حالك؟", level:"A1", context:"تحية" },
            { id:2, sentence:"Je voudrais un café.", trans:"جُو فُودْرِي أَنْ كَافِيهْ.", ar:"أريد قهوة.", level:"A1", context:"مطعم" },
            { id:3, sentence:"Où sont les toilettes?", trans:"أُو سُونْ لِي تُوَالِيتْ؟", ar:"أين الحمام؟", level:"A1", context:"أماكن" },
            { id:4, sentence:"Combien ça coûte?", trans:"كُومْبِيَانْ سَا كُوتْ؟", ar:"كم سعره؟", level:"A2", context:"تسوق" },
            { id:5, sentence:"J'ai besoin d'une chambre.", trans:"جِي بِزْوَانْ دُونْ شَانْبْرْ.", ar:"أحتاج غرفة.", level:"A2", context:"فندق" },
            { id:6, sentence:"Je suis arrivé hier.", trans:"جُو سُويْ زَارِيفِي إِيِيرْ.", ar:"وصلت أمس.", level:"A2", context:"سفر" },
            { id:7, sentence:"Je suis d'accord.", trans:"جُو سُويْ دَاكُورْ.", ar:"أنا موافق.", level:"B1", context:"عمل" },
            { id:8, sentence:"Comment tu t'appelles?", trans:"كُومَانْ تُو تَابِلْ؟", ar:"ما اسمك؟", level:"A1", context:"تعارف" }
        ]
    },
    de: {
        name: 'الألمانية', tts: 'de-DE',
        words: [
            { id:1, word:"Mutter", trans:"مُوتِر", ar:"أمّ", topic:"عائلة", level:"A1", example:"Meine Mutter ist Lehrerin." },
            { id:2, word:"Wasser", trans:"فَاسِر", ar:"ماء", topic:"طعام", level:"A1", example:"Ich trinke Wasser." },
            { id:3, word:"Flughafen", trans:"فْلُوكْهَافِن", ar:"مطار", topic:"سفر", level:"A1", example:"Der Flughafen ist weit." },
            { id:4, word:"Preis", trans:"بْرَايْس", ar:"السعر", topic:"تسوق", level:"A2", example:"Der Preis ist hoch." },
            { id:5, word:"Büro", trans:"بُورُو", ar:"مكتب", topic:"عمل", level:"A2", example:"Ich gehe ins Büro." },
            { id:6, word:"Medizin", trans:"مِيدِتْسِين", ar:"دواء", topic:"صحة", level:"B1", example:"Nehmen Sie diese Medizin." },
            { id:7, word:"Hallo", trans:"هَالُو", ar:"مرحباً", topic:"تحية", level:"A1", example:"Hallo, wie geht's?" },
            { id:8, word:"Ticket", trans:"تِكِت", ar:"تذكرة", topic:"سفر", level:"A1", example:"Ich brauche ein Ticket." },
            { id:9, word:"Lecker", trans:"لِيكِر", ar:"لذيذ", topic:"طعام", level:"A2", example:"Das ist lecker." },
            { id:10, word:"Vorstellungsgespräch", trans:"فُورْشْتِيلُونْغْسْغِبْرِيخ", ar:"مقابلة", topic:"عمل", level:"B1", example:"Ich habe ein Vorstellungsgespräch." }
        ],
        sentences: [
            { id:1, sentence:"Wie geht's?", trans:"فِي غِيتْسْ؟", ar:"كيف حالك؟", level:"A1", context:"تحية" },
            { id:2, sentence:"Ich hätte gerne einen Kaffee.", trans:"إِيخْ هِيته غِيرْنِ أَيْنِن كَافِيهْ.", ar:"أريد قهوة.", level:"A1", context:"مطعم" },
            { id:3, sentence:"Wo ist die Toilette?", trans:"فُو إِسْتْ دِي تُوَالِيتِهْ؟", ar:"أين الحمام؟", level:"A1", context:"أماكن" },
            { id:4, sentence:"Wie viel kostet es?", trans:"فِي فِيلْ كُوسْتِتْ إِسْ؟", ar:"كم سعره؟", level:"A2", context:"تسوق" },
            { id:5, sentence:"Ich brauche ein Zimmer.", trans:"إِيخْ بْرَاوْخِهْ أَيْن تْسِيمِر.", ar:"أحتاج غرفة.", level:"A2", context:"فندق" },
            { id:6, sentence:"Ich bin gestern angekommen.", trans:"إِيخْ بِنْ غِيسْتِرْنْ آنْغِكُومِن.", ar:"وصلت أمس.", level:"A2", context:"سفر" },
            { id:7, sentence:"Ich bin einverstanden.", trans:"إِيخْ بِنْ أَيْنْفِرْشْتَانْدِن.", ar:"أنا موافق.", level:"B1", context:"عمل" },
            { id:8, sentence:"Wie heißt du?", trans:"فِي هَايْسْتْ دُو؟", ar:"ما اسمك؟", level:"A1", context:"تعارف" }
        ]
    },
    ko: {
        name: 'الكورية', tts: 'ko-KR',
        words: [
            { id:1, word:"어머니", trans:"أُومُونِي", ar:"أمّ", topic:"عائلة", level:"A1", example:"제 어머니는 선생님이에요." },
            { id:2, word:"물", trans:"مُل", ar:"ماء", topic:"طعام", level:"A1", example:"저는 매일 물을 마셔요." },
            { id:3, word:"공항", trans:"كُونْغْهَانْغ", ar:"مطار", topic:"سفر", level:"A1", example:"공항이 멀어요." },
            { id:4, word:"가격", trans:"كَاغْيُوكْ", ar:"السعر", topic:"تسوق", level:"A2", example:"가격이 비싸요." },
            { id:5, word:"사무실", trans:"سَامُوشِل", ar:"مكتب", topic:"عمل", level:"A2", example:"사무실에 가요." },
            { id:6, word:"약", trans:"يَاكْ", ar:"دواء", topic:"صحة", level:"B1", example:"이 약을 드세요." },
            { id:7, word:"안녕하세요", trans:"أَنْنِيُونْغْهَاسِيهْيُو", ar:"مرحباً", topic:"تحية", level:"A1", example:"안녕하세요, 잘 지내요?" },
            { id:8, word:"티켓", trans:"تِيكِيتْ", ar:"تذكرة", topic:"سفر", level:"A1", example:"티켓이 필요해요." },
            { id:9, word:"맛있는", trans:"مَاسِتْنِن", ar:"لذيذ", topic:"طعام", level:"A2", example:"이거 맛있어요." },
            { id:10, word:"면접", trans:"مْيُونْجُوبْ", ar:"مقابلة", topic:"عمل", level:"B1", example:"면접이 있어요." }
        ],
        sentences: [
            { id:1, sentence:"잘 지내요?", trans:"جَالْ جِينَايُو؟", ar:"كيف حالك؟", level:"A1", context:"تحية" },
            { id:2, sentence:"커피 주세요.", trans:"كُوبِي جُوسِيهْيُو.", ar:"أريد قهوة.", level:"A1", context:"مطعم" },
            { id:3, sentence:"화장실이 어디에요?", trans:"هْوَاجَانْغْشِيلِي أُودِيِيهْيُو؟", ar:"أين الحمام؟", level:"A1", context:"أماكن" },
            { id:4, sentence:"얼마예요?", trans:"أُولْمَايِيهْيُو؟", ar:"كم سعره؟", level:"A2", context:"تسوق" },
            { id:5, sentence:"방이 필요해요.", trans:"بَانْغِي بِيلْيُوهَيهْيُو.", ar:"أحتاج غرفة.", level:"A2", context:"فندق" },
            { id:6, sentence:"어제 도착했어요.", trans:"أُوجِي تُوتْشَاكْهَاسُويُو.", ar:"وصلت أمس.", level:"A2", context:"سفر" },
            { id:7, sentence:"동의해요.", trans:"تُونْغْيِيهَيهْيُو.", ar:"أنا موافق.", level:"B1", context:"عمل" },
            { id:8, sentence:"이름이 뭐예요?", trans:"إِرِيمِي مْوَايِيهْيُو؟", ar:"ما اسمك؟", level:"A1", context:"تعارف" }
        ]
    },
    zh: {
        name: 'الصينية', tts: 'zh-CN',
        words: [
            { id:1, word:"妈妈", trans:"مَامَا", ar:"أمّ", topic:"عائلة", level:"A1", example:"我妈妈是老师。" },
            { id:2, word:"水", trans:"شُويْ", ar:"ماء", topic:"طعام", level:"A1", example:"我每天喝水。" },
            { id:3, word:"机场", trans:"جِي تْشَانْغ", ar:"مطار", topic:"سفر", level:"A1", example:"机场很远。" },
            { id:4, word:"价格", trans:"جِيَا غِي", ar:"السعر", topic:"تسوق", level:"A2", example:"价格很高。" },
            { id:5, word:"办公室", trans:"بَانْ غُونْ شِ", ar:"مكتب", topic:"عمل", level:"A2", example:"我去办公室。" },
            { id:6, word:"药", trans:"يَاوْ", ar:"دواء", topic:"صحة", level:"B1", example:"吃这个药。" },
            { id:7, word:"你好", trans:"نِي هَاوْ", ar:"مرحباً", topic:"تحية", level:"A1", example:"你好，你好吗？" },
            { id:8, word:"票", trans:"بِيَاوْ", ar:"تذكرة", topic:"سفر", level:"A1", example:"我需要票。" },
            { id:9, word:"好吃", trans:"هَاوْ تْشِي", ar:"لذيذ", topic:"طعام", level:"A2", example:"这个好吃。" },
            { id:10, word:"面试", trans:"مِيَانْ شِ", ar:"مقابلة", topic:"عمل", level:"B1", example:"我有面试。" }
        ],
        sentences: [
            { id:1, sentence:"你好吗？", trans:"نِي هَاوْ مَا؟", ar:"كيف حالك؟", level:"A1", context:"تحية" },
            { id:2, sentence:"我想要咖啡。", trans:"وُو شْيَانْغْ يَاوْ كَافِي.", ar:"أريد قهوة.", level:"A1", context:"مطعم" },
            { id:3, sentence:"厕所在哪里？", trans:"تْسُو سُوُوْ زَايْ نَالِي؟", ar:"أين الحمام؟", level:"A1", context:"أماكن" },
            { id:4, sentence:"多少钱？", trans:"دُو شَاوْ تْشِيَانْ؟", ar:"كم سعره؟", level:"A2", context:"تسوق" },
            { id:5, sentence:"我需要一个房间。", trans:"وُو شْيُوْ يَاوْ يِي غِ فَانْجِيَانْ.", ar:"أحتاج غرفة.", level:"A2", context:"فندق" },
            { id:6, sentence:"我昨天到了。", trans:"وُو زُو تُيَانْ دَاوْ لَ.", ar:"وصلت أمس.", level:"A2", context:"سفر" },
            { id:7, sentence:"我同意。", trans:"وُو تُونْغْ يِي.", ar:"أنا موافق.", level:"B1", context:"عمل" },
            { id:8, sentence:"你叫什么名字？", trans:"نِي جِيَاوْ شِنْ مِينْ زِي؟", ar:"ما اسمك؟", level:"A1", context:"تعارف" }
        ]
    }
};

// ================================================================
// 2. المتغيرات العامة والدوال الأساسية
// ================================================================
let currentLang = 'en';
let currentScenarioIdx = 0;
let currentSceneId = 0;
let recognition = null;

function getData() { return allLanguageData[currentLang]; }

// عرض الكلمات
function renderWords() {
    const data = getData();
    const container = document.getElementById('wordList');
    const level = document.getElementById('levelFilter').value;
    const topic = document.getElementById('topicFilter').value;
    let filtered = data.words;
    if (level !== 'all') filtered = filtered.filter(w => w.level === level);
    if (topic !== 'all') filtered = filtered.filter(w => w.topic === topic);
    container.innerHTML = filtered.map(w => `
        <div class="word-card">
            <div class="word-original">${w.word} <button class="btn-speak" onclick="speakText('${w.word}', '${data.tts}')"><i class="fas fa-volume-up"></i></button></div>
            <div class="word-trans">${w.trans} | ${w.level}</div>
            <div class="word-ar">${w.ar} <span class="lang-badge">${w.topic}</span></div>
            <div class="example">📌 ${w.example}</div>
        </div>
    `).join('');
    document.getElementById('wordsLangName').innerText = data.name;
}

// عرض الجمل
function renderSentences() {
    const data = getData();
    const container = document.getElementById('sentenceList');
    container.innerHTML = data.sentences.map(s => `
        <div class="word-card" style="border-right-color:#f59e0b;">
            <div style="font-size:18px; font-weight:600;">${s.sentence} <button class="btn-speak" onclick="speakText('${s.sentence}', '${data.tts}')"><i class="fas fa-volume-up"></i></button></div>
            <div class="word-trans">${s.trans}</div>
            <div class="word-ar">${s.ar} <span class="lang-badge">${s.context}</span></div>
            <div style="font-size:13px; color:#64748b;">المستوى: ${s.level}</div>
        </div>
    `).join('');
    document.getElementById('sentLangName').innerText = data.name;
}

// النطق الصوتي
function speakText(text, langCode) {
    if (!window.speechSynthesis) return alert('متصفحك لا يدعم النطق');
    const utterance = new SpeechSynthesisUtterance(text);
    utterance.lang = langCode;
    utterance.rate = 0.8;
    window.speechSynthesis.speak(utterance);
}

// تبديل اللغة
function switchLanguage(code) {
    currentLang = code;
    const data = getData();
    document.getElementById('dashLangName').innerText = data.name;
    document.getElementById('aiLangName').innerText = data.name;
    // تحديث جملة الذكاء الاصطناعي للنطق
    if (data.sentences.length > 0) {
        document.getElementById('targetPhrase').innerText = data.sentences[0].sentence;
    }
    renderWords();
    renderSentences();
    // إعادة تحميل السيناريو الحالي باللغة الجديدة
    loadScenario(currentScenarioIdx);
}

// ================================================================
// 3. الفيديو التفاعلي
// ================================================================
const videoScenes = [
    { text: 'المشهد 1: مرحباً، هل تريد طلباً؟', btns: ['أريد القائمة', 'ماء فقط'], feedback: 'تفضل القائمة، سأحضرها لك الآن.' },
    { text: 'المشهد 2: ماذا تفضل من القائمة؟', btns: ['دجاج', 'سمك'], feedback: 'خيار رائع! سيجهز طلبك خلال 10 دقائق.' },
    { text: 'المشهد 3: طلبك جاهز. بالهناء!', btns: ['شكراً', 'أريد فاتورة'], feedback: 'شكراً لزيارتك، نتمنى أن تعود مرة أخرى.' }
];
function changeScene(index) {
    if (index >= videoScenes.length) index = 0;
    const scene = videoScenes[index];
    document.getElementById('videoSceneText').innerText = scene.text;
    document.getElementById('videoFeedback').innerHTML = `<i class="fas fa-comment-dots"></i> ${scene.feedback}`;
    const btnContainer = document.getElementById('videoBtns');
    btnContainer.innerHTML = scene.btns.map((b, i) => `<button onclick="changeScene(${index + 1})">${b}</button>`).join('');
}

// ================================================================
// 4. السيناريوهات (8 مواقف) - نصوص ثابتة (عربية) للجميع
// ================================================================
const scenarios = [
    { title: "المطعم", scenes: [{ id:0, text:"النادل: مرحباً، هل تريد طلباً؟", options:[{text:"أريد القائمة",next:1},{text:"ماء فقط",next:2}]}, {id:1, text:"النادل: تفضل القائمة، ماذا تريد؟", options:[{text:"دجاج مع أرز",next:3},{text:"سمك مشوي",next:3}]}, {id:2, text:"النادل: حسناً، سأحضر لك الماء.", options:[{text:"شكراً",next:3}]}, {id:3, text:"النادل: طلبك جاهز، بالهناء!", options:[]}] },
    { title: "المطار", scenes: [{ id:0, text:"موظف الجوازات: جواز سفرك من فضلك.", options:[{text:"تفضل جوازي",next:1},{text:"لقد فقدته",next:2}]}, {id:1, text:"الموظف: شكراً، وجهتك إلى لندن. رقم البوابة 5.", options:[{text:"شكراً",next:3}]}, {id:2, text:"الموظف: يجب عليك التوجه إلى مكتب المفقودات.", options:[{text:"أين المكتب؟",next:3}]}, {id:3, text:"الموظف: أتمنى لك رحلة سعيدة.", options:[]}] },
    { title: "التسوق", scenes: [{ id:0, text:"البائع: أهلاً، هل تريد المساعدة؟", options:[{text:"أريد قميصاً",next:1},{text:"كم سعر هذا؟",next:1}]}, {id:1, text:"البائع: هذا القميص بـ 30 دولاراً.", options:[{text:"خصم؟",next:2},{text:"سأشتريه",next:2}]}, {id:2, text:"البائع: سأعطيك خصم 10%", options:[{text:"صفقة جيدة",next:3}]}, {id:3, text:"البائع: شكراً لتسوقك!", options:[]}] },
    { title: "الفندق", scenes: [{ id:0, text:"موظف الاستقبال: مساء الخير، هل لديك حجز؟", options:[{text:"نعم، لدي حجز",next:1},{text:"لا، أريد غرفة",next:2}]}, {id:1, text:"الموظف: مرحباً، غرفتك 402.", options:[{text:"شكراً",next:3}]}, {id:2, text:"الموظف: لدينا غرفة مفردة بـ 100 دولار.", options:[{text:"سأخذها",next:3}]}, {id:3, text:"الموظف: استمتع بإقامتك!", options:[]}] },
    { title: "التاكسي", scenes: [{ id:0, text:"السائق: إلى أين تذهب؟", options:[{text:"إلى المطار",next:1},{text:"إلى المدينة القديمة",next:1}]}, {id:1, text:"السائق: حسناً، سأوصلناك.", options:[{text:"كم الأجرة؟",next:2}]}, {id:2, text:"السائق: الأجرة 20 دولاراً.", options:[{text:"تفضل",next:3}]}, {id:3, text:"السائق: وصلنا. بالسلامة!", options:[]}] },
    { title: "المدرسة", scenes: [{ id:0, text:"المعلم: اشرح لي الدرس السابق.", options:[{text:"سأشرحه الآن",next:1},{text:"لم أفهمه",next:2}]}, {id:1, text:"المعلم: شرح ممتاز!", options:[{text:"شكراً",next:3}]}, {id:2, text:"المعلم: لا بأس، سأعيد شرحه.", options:[{text:"شكراً",next:3}]}, {id:3, text:"المعلم: تابع دروسك.", options:[]}] },
    { title: "العمل", scenes: [{ id:0, text:"المدير: أخبرني عن خبراتك.", options:[{text:"لدي 5 سنوات خبرة",next:1},{text:"أنا جديد لكني متحمس",next:2}]}, {id:1, text:"المدير: رائع، متى تستطيع البدء؟", options:[{text:"الأسبوع القادم",next:3}]}, {id:2, text:"المدير: الحماس مهم، سنمنحك فرصة.", options:[{text:"شكراً",next:3}]}, {id:3, text:"المدير: مرحباً بك في الفريق!", options:[]}] },
    { title: "التعارف", scenes: [{ id:0, text:"شخص: مرحباً، أنا سارة. ما اسمك؟", options:[{text:"أنا أحمد، تشرفت",next:1},{text:"مرحباً، أنا خالد",next:1}]}, {id:1, text:"سارة: من أي بلد أنت؟", options:[{text:"من مصر",next:2},{text:"من السعودية",next:2}]}, {id:2, text:"سارة: هل تحب السفر؟", options:[{text:"نعم، أحبه",next:3},{text:"أفضل الاسترخاء",next:3}]}, {id:3, text:"سارة: جميل، ربما نتقابل مرة أخرى.", options:[]}] }
];

function loadScenario(index) {
    currentScenarioIdx = index;
    const scenario = scenarios[index];
    document.getElementById('scenarioTitle').innerText = scenario.title;
    const firstScene = scenario.scenes.find(s => s.id === 0);
    if (firstScene) { currentSceneId = 0; displayScenario(index, 0); }
}
function displayScenario(scenarioIdx, sceneId) {
    const scenario = scenarios[scenarioIdx];
    const scene = scenario.scenes.find(s => s.id === sceneId);
    if (!scene) return;
    document.getElementById('scenarioDesc').innerText = scene.text;
    const optionsDiv = document.getElementById('scenarioOptions');
    const feedbackDiv = document.getElementById('scenarioFeedback');
    if (scene.options && scene.options.length > 0) {
        optionsDiv.innerHTML = scene.options.map((opt, idx) => `<button onclick="chooseScenarioOption(${scenarioIdx}, ${sceneId}, ${idx})">${opt.text}</button>`).join('');
        feedbackDiv.style.display = 'none';
    } else {
        optionsDiv.innerHTML = '<p style="color:green;">✅ انتهى السيناريو.</p>';
        feedbackDiv.style.display = 'block';
        feedbackDiv.innerHTML = '🎯 نهاية المحادثة. اختر سيناريو آخر.';
    }
}
function chooseScenarioOption(scenarioIdx, sceneId, optionIdx) {
    const scenario = scenarios[scenarioIdx];
    const scene = scenario.scenes.find(s => s.id === sceneId);
    if (!scene || !scene.options || !scene.options[optionIdx]) return;
    const nextSceneId = scene.options[optionIdx].next;
    const feedbackDiv = document.getElementById('scenarioFeedback');
    feedbackDiv.style.display = 'block';
    feedbackDiv.innerHTML = `✅ اخترت: "${scene.options[optionIdx].text}"`;
    setTimeout(() => {
        const nextScene = scenario.scenes.find(s => s.id === nextSceneId);
        if (nextScene) displayScenario(scenarioIdx, nextSceneId);
        else { document.getElementById('scenarioDesc').innerText = 'نهاية المحادثة.'; document.getElementById('scenarioOptions').innerHTML = ''; }
    }, 500);
}

// ================================================================
// 5. الذكاء الاصطناعي (تحليل النطق)
// ================================================================
function startListening() {
    const micBtn = document.getElementById('micButton');
    if (!('webkitSpeechRecognition' in window) && !('SpeechRecognition' in window)) {
        alert('متصفحك لا يدعم التعرف على الصوت. استخدم Chrome.');
        return;
    }
    if (recognition) { recognition.stop(); micBtn.classList.remove('recording'); micBtn.innerHTML = '<i class="fas fa-microphone"></i> اضغط وتحدث'; recognition = null; return; }
    const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
    recognition = new SpeechRecognition();
    const langCode = getData().tts;
    recognition.lang = langCode;
    recognition.continuous = false;
    recognition.interimResults = false;
    micBtn.classList.add('recording');
    micBtn.innerHTML = '<i class="fas fa-stop"></i> جارٍ الاستماع...';
    recognition.onresult = (event) => {
        const transcript = event.results[0][0].transcript;
        micBtn.classList.remove('recording');
        micBtn.innerHTML = '<i class="fas fa-microphone"></i> اضغط وتحدث';
        evaluatePronunciation(transcript);
        recognition = null;
    };
    recognition.onerror = () => {
        micBtn.classList.remove('recording');
        micBtn.innerHTML = '<i class="fas fa-microphone"></i> اضغط وتحدث';
        document.getElementById('evaluationResult').innerText = '⚠️ خطأ، حاول مجدداً.';
        recognition = null;
    };
    recognition.start();
}
function evaluatePronunciation(userText) {
    const target = document.getElementById('targetPhrase').innerText.toLowerCase().replace(/[^a-z0-9 ]/g, '');
    const spoken = userText.toLowerCase().replace(/[^a-z0-9 ]/g, '');
    const targetWords = target.split(' ').filter(w => w.length > 0);
    const spokenWords = spoken.split(' ').filter(w => w.length > 0);
    let matches = 0;
    const minLen = Math.min(targetWords.length, spokenWords.length);
    for (let i = 0; i < minLen; i++) if (targetWords[i] === spokenWords[i]) matches++;
    const accuracy = targetWords.length > 0 ? Math.round((matches / targetWords.length) * 100) : 0;
    document.getElementById('evaluationResult').innerHTML = `📊 الدقة: ${accuracy}%`;
    document.getElementById('accuracyBar').style.width = accuracy + '%';
    document.getElementById('evaluationResult').style.color = accuracy > 70 ? 'green' : 'orange';
}
function generateSuggestion() {
    const suggestions = [
        'ركز على الأفعال الشائعة في الزمن الماضي.', 'تدرب على جمل الحجز في الفنادق.', 'راجع أسماء الإشارة.', 'شاهد سيناريو المطار.', 'تعلم 5 كلمات جديدة عن الطقس.'
    ];
    document.getElementById('aiSuggestion').innerText = suggestions[Math.floor(Math.random() * suggestions.length)];
}

// ================================================================
// 6. التبويب والفلاتر
// ================================================================
document.querySelectorAll('.tab-btn').forEach(btn => {
    btn.addEventListener('click', function() {
        document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
        this.classList.add('active');
        document.querySelectorAll('.content-section').forEach(s => s.classList.remove('active'));
        document.getElementById(this.dataset.tab).classList.add('active');
    });
});
document.getElementById('levelFilter')?.addEventListener('change', renderWords);
document.getElementById('topicFilter')?.addEventListener('change', renderWords);

// ================================================================
// 7. التهيئة عند التحميل
// ================================================================
window.onload = function() {
    switchLanguage('en');
    loadScenario(0);
    changeScene(0);
    generateSuggestion();
    // تعيين أول جملة للذكاء الاصطناعي
    document.getElementById('targetPhrase').innerText = getData().sentences[0].sentence;
};
</script>
</body>
</html>
