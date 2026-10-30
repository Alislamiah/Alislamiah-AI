<!DOCTYPE html>
<html lang="ar" dir="rtl">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#08142b">
<link rel="search" type="application/opensearchdescription+xml" href="opensearch.xml" title="Alislamiah AI">
<link rel="stylesheet" href="style.css">

<title>Alislamiah-AI Browser</title>
<script>
    // تطبيق وضع سطح المكتب تلقائياً إذا كان مفَعّلاً في الإعدادات
    if (localStorage.getItem("desktopSite") === "true") {
        let viewportMeta = document.querySelector('meta[name="viewport"]');
        if (!viewportMeta) {
            viewportMeta = document.createElement('meta');
            viewportMeta.name = 'viewport';
            document.head.appendChild(viewportMeta);
        }
        viewportMeta.content = 'width=1024';
    }
</script>

<style>
/* =====================================================
   RESET
===================================================== */
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    -webkit-tap-highlight-color:transparent;
}

html{
    width:100%;
    min-height:100%;
    scroll-behavior:smooth;
}

body{
    width:100%;
    min-height:100vh;
    background:
        radial-gradient(circle at 50% 25%, rgba(0,115,255,.18), transparent 34%),
        radial-gradient(circle at 100% 70%, rgba(0,190,255,.10), transparent 35%),
        linear-gradient(145deg, #040a17 0%, #07142a 55%, #06172c 100%);
    color:#ffffff;
    font-family: Arial, "Segoe UI", Tahoma, sans-serif;
    overflow-x:hidden;
}

:root{
    --blue:#087fff;
    --blue-light:#08b9ef;
    --text:#ffffff;
    --muted:#aebbd2;
    --border: rgba(255,255,255,.14);
    --card: rgba(255,255,255,.075);
}

.app{
    width:100%;
    max-width:700px;
    min-height:100vh;
    margin:0 auto;
    padding: 14px 14px 30px;
}

.topbar{
    width:100%;
    height:48px;
    display:flex;
    align-items:center;
    justify-content:flex-start;
    gap:15px;
    margin-bottom:8px;
}

.top-button{
    width:44px;
    height:44px;
    border-radius:14px;
    border: 1px solid rgba(255,255,255,.13);
    background: rgba(255,255,255,.055);
    color:#ffffff;
    display:flex;
    align-items:center;
    justify-content:center;
    font-size:21px;
    cursor:pointer;
    transition:.18s;
}

.top-button:active{
    transform:scale(.92);
}

.top-title{
    font-size:15px;
    font-weight:700;
    letter-spacing:.3px;
}

.brand{
    text-align:center;
    margin-top:4px;
}

.brand-name{
    color:#168cff;
    font-size:34px;
    line-height:1.2;
    font-weight:800;
    letter-spacing:-1px;
    text-shadow: 0 0 30px rgba(22,140,255,.25);
}

.brand-line{
    width:94%;
    height:1px;
    margin: 12px auto 0;
    background: linear-gradient(90deg, transparent, rgba(255,255,255,.70), transparent);
}

.ai-logo{
    width:165px;
    height:165px;
    margin: 28px auto 20px;
    border-radius:43px;
    display:flex;
    align-items:center;
    justify-content:center;
    background: linear-gradient(145deg, #087cff 0%, #08b9ee 100%);
    box-shadow: 0 18px 55px rgba(0,120,255,.32), inset 0 1px 1px rgba(255,255,255,.38);
    position:relative;
    overflow:hidden;
}

.ai-logo::before{
    content:"";
    position:absolute;
    inset:-5px;
    border-radius:47px;
    border: 1px solid rgba(70,185,255,.20);
}

.ai-logo span{
    color:#ffffff;
    font-size:60px;
    font-weight:800;
    position:relative;
    z-index:2;
}

.ai-logo img{
    width:100%;
    height:100%;
    object-fit:cover;
    position:relative;
    z-index:2;
}

.hero{
    width:100%;
    text-align:center;
}

.hero h1{
    font-size:31px;
    line-height:1.3;
    font-weight:800;
}

.hero-line{
    width:87%;
    height:1px;
    margin: 17px auto 14px;
    background: rgba(255,255,255,.65);
}

.hero p{
    color:#bdc9df;
    font-size:18px;
    line-height:1.8;
}

.search-area{
    width:100%;
    margin-top:23px;
    position: sticky;
    top: 0;
    z-index: 999;
    padding: 10px 0;
    background: transparent;
}

.search-box{
    width:100%;
    height:64px;
    display:flex;
    direction:ltr;
    background:#ffffff;
    border-radius:21px;
    overflow:hidden;
    box-shadow: 0 15px 45px rgba(0,0,0,.27), 0 0 30px rgba(0,130,255,.08);
}

.search-button{
    width:84px;
    min-width:84px;
    border:none;
    outline:none;
    background: linear-gradient(145deg, #087fff, #0870e4);
    color:#ffffff;
    font-size:27px;
    cursor:pointer;
    display:flex;
    align-items:center;
    justify-content:center;
    transition:.15s;
}

.search-button:active{
    transform:scale(.96);
}

.search-input{
    width:100%;
    min-width:0;
    border:none;
    outline:none;
    background:#ffffff;
    color:#1d2938;
    font-size:17px;
    padding: 0 18px;
    text-align:right;
    direction:rtl;
}

.search-input::placeholder{
    color:#999999;
}

.shortcuts-title{
    text-align:center;
    color:#aebbd2;
    font-size:15px;
    margin: 27px 0 14px;
}

.shortcuts{
    width:100%;
    display:grid;
    grid-template-columns: repeat(3,1fr);
    gap:12px;
}

.shortcut{
    min-height:142px;
    border-radius:24px;
    border: 1px solid rgba(255,255,255,.14);
    background: linear-gradient(145deg, rgba(255,255,255,.095), rgba(255,255,255,.045));
    box-shadow: 0 12px 30px rgba(0,0,0,.15), inset 0 1px 0 rgba(255,255,255,.04);
    display:flex;
    flex-direction:column;
    align-items:center;
    justify-content:center;
    gap:10px;
    cursor:pointer;
    user-select:none;
    transition: transform .16s ease, background .16s ease, border-color .16s ease;
}

.shortcut:hover{
    background: rgba(255,255,255,.11);
    border-color: rgba(25,145,255,.40);
}

.shortcut:active{
    transform:scale(.94);
}

.shortcut-icon{
    width:60px;
    height:60px;
    border-radius:18px;
    display:flex;
    align-items:center;
    justify-content:center;
    font-size:38px;
}

.shortcut-name{
    color:#ffffff;
    font-size:15px;
    font-weight:600;
}

/* =====================================================
   PROMO CARDS STYLES (تنسيقات البطاقات الإعلانية)
===================================================== */
.promo-cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(310px, 1fr));
  gap: 24px;
  direction: rtl;
  font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
  margin-top: 32px;
}

.promo-card {
  border-radius: 28px;
  overflow: hidden;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.25);
  transition: transform 0.35s ease, box-shadow 0.35s ease;
}

.promo-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 28px 50px rgba(0, 0, 0, 0.35);
}

.promo-card.arabiya {
  background: #0f1c2e;
}

.promo-card.islamiya {
  background: #0c4a5c;
}

.card-image {
  height: 190px;
  overflow: hidden;
}

.card-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

.card-content {
  padding: 24px 26px 30px;
  position: relative;
  overflow: hidden;
}

.card-content::before {
  content: '';
  position: absolute;
  width: 180px;
  height: 180px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.04);
  top: -40px;
  left: -40px;
}

.card-content::after {
  content: '';
  position: absolute;
  width: 120px;
  height: 120px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.03);
  bottom: -30px;
  right: -30px;
}

.card-label {
  display: inline-block;
  background: rgba(255, 255, 255, 0.15);
  color: rgba(255, 255, 255, 0.9);
  font-size: 12px;
  font-weight: 600;
  padding: 6px 16px;
  border-radius: 30px;
  margin-bottom: 18px;
}

.card-title {
  color: #ffffff;
  font-size: 26px;
  font-weight: 700;
  margin: 0 0 12px 0;
  letter-spacing: -0.4px;
}

.card-desc {
  color: rgba(255, 255, 255, 0.78);
  font-size: 14.5px;
  line-height: 1.7;
  margin: 0 0 24px 0;
}

.card-btn {
  display: inline-block;
  background: #ffffff;
  color: #0f1c2e !important;
  text-decoration: none;
  padding: 12px 24px;
  border-radius: 50px;
  font-weight: 700;
  font-size: 14.5px;
  transition: all 0.3s ease;
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.12);
}

.islamiya .card-btn {
  color: #0c4a5c !important;
}

.card-btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 10px 22px rgba(0, 0, 0, 0.2);
}

.footer{
    text-align:center;
    margin-top:30px;
    padding-bottom:5px;
    color:#91a5c5;
    font-size:14px;
    line-height:1.8;
}

.footer strong{
    color:#b9c8e2;
}

.menu-overlay{
    position:fixed;
    inset:0;
    background: rgba(0,0,0,.62);
    opacity:0;
    visibility:hidden;
    transition:.25s;
    z-index:1000;
}

.menu-overlay.show{
    opacity:1;
    visibility:visible;
}

.side-menu{
    position:absolute;
    top:0;
    right:0;
    width:82%;
    max-width:330px;
    height:100%;
    padding: 24px 17px;
    background: linear-gradient(160deg, #0b1930, #07101f);
    border-left: 1px solid rgba(255,255,255,.09);
    transform: translateX(100%);
    transition:.30s;
    overflow-y:auto;
}

.menu-overlay.show .side-menu{
    transform: translateX(0);
}

.menu-header{
    display:flex;
    align-items:center;
    justify-content:space-between;
    margin-bottom:28px;
}

.menu-header h2{
    font-size:20px;
}

.close-menu{
    width:42px;
    height:42px;
    border: 1px solid rgba(255,255,255,.13);
    border-radius:13px;
    background: rgba(255,255,255,.06);
    color:#ffffff;
    font-size:19px;
    cursor:pointer;
}

.menu-item{
    width:100%;
    height:56px;
    margin-bottom:10px;
    border:none;
    border-radius:15px;
    background: rgba(255,255,255,.055);
    color:#ffffff;
    display:flex;
    align-items:center;
    gap:14px;
    padding: 0 17px;
    font-size:15px;
    cursor:pointer;
    text-align:right;
}

.menu-item:active{
    background: rgba(20,130,255,.20);
}
</style>

</head>

<body>

<!-- =====================================================
     MAIN APP (القسم الرئيسي)
===================================================== -->
<div id="home-view" class="app">

    <!-- TOP BAR -->
    <div class="topbar">
        <button class="top-button" type="button" onclick="openMenu()">☰</button>
        <div class="top-title">Alislamiah AI</div>
    </div>

    <!-- BRAND -->
    <div class="brand">
        <div class="brand-name">Alislamiah-AI</div>
        <div class="brand-line"></div>
    </div>

    <!-- AI LOGO -->
    <div class="ai-logo" id="mainAiLogo">
        <span>AI</span>
    </div>

    <!-- HERO -->
    <div class="hero">
        <h1>Alislamiah AI Browser</h1>
        <div class="hero-line"></div>
        <p>الذكاء الاصطناعي • البحث • السرعة • الخصوصية</p>
    </div>

    <!-- SEARCH -->
    <div class="search-area">
        <div class="search-box">
            <button class="search-button" type="button" onclick="performSearch()">🔍</button>
            <input id="searchInput" class="search-input" type="text" autocomplete="off" placeholder="ابحث في الويب أو اطرح سؤالاً..." onkeydown="handleSearchKey(event)">
        </div>
    </div>

    <!-- SHORTCUT TITLE -->
    <div class="shortcuts-title">الوصول السريع</div>

    <!-- SHORTCUTS -->
    <div class="shortcuts">
        <div class="shortcut" onclick="searchShortcut('YouTube', 'https://www.youtube.com/favicon.ico')">
            <div class="shortcut-icon">▶️</div>
            <div class="shortcut-name">YouTube</div>
        </div>

        <div class="shortcut"
onclick="window.location.href='chat.html'">
            <div class="shortcut-icon">🤖</div>
            <div class="shortcut-name">AI</div>
        </div>

        <div class="shortcut" onclick="searchShortcut('Alislamiah', 'icon.png')">
            <div class="shortcut-icon">🌐</div>
            <div class="shortcut-name">Alislamiah</div>
        </div>

        <div class="shortcut" onclick="window.location.href='browsing.html'">
            <div class="shortcut-icon">📱</div>
            <div class="shortcut-name">Explore</div>
        </div>

        <div class="shortcut" onclick="window.location.href='Settings.html'">
            <div class="shortcut-icon">⚙️</div>
            <div class="shortcut-name">Settings</div>
        </div>

        <div class="shortcut" onclick="searchShortcut('Quran', '')">
            <div class="shortcut-icon">📖</div>
            <div class="shortcut-name">Quran</div>
        </div>
    </div>

    <!-- =====================================================
         PROMO CARDS (البطاقات الإعلانية المضافة)
    ===================================================== -->
    <div class="promo-cards">

<!-- =========================
     Today's Weather
========================= -->

<div class="promo-card todays-weather">

  <!-- الفقاعات -->
  <div class="weather-bubble bubble-1"></div>
  <div class="weather-bubble bubble-2"></div>
  <div class="weather-bubble bubble-3"></div>

  <div class="weather-content">

    <span class="weather-label">LIVE WEATHER</span>

    <h3 class="weather-title">Today's weather</h3>

    <!-- اختيار المنطقة -->
    <div class="weather-selector">

      <div class="selector-title">
        📍 اختر منطقتك
      </div>

      <div class="selector-row">
        <input
          type="text"
          id="cityInput"
          placeholder="اكتب اسم المدينة..."
          autocomplete="off"
        >

        <button id="searchWeatherBtn" type="button">
          بحث
        </button>
      </div>

      <div id="searchStatus" class="search-status"></div>

      <!-- نتائج المدن -->
      <div id="cityResults" class="city-results"></div>

    </div>

    <!-- معلومات الموقع -->
    <div class="weather-location" id="weatherLocation">
      📍 لم يتم اختيار منطقة
    </div>

    <!-- درجة الحرارة -->
    <div class="weather-main">

      <div id="weatherIcon" class="weather-icon">
        🌤️
      </div>

      <div id="weatherTemp" class="weather-temp">
        --°C
      </div>

    </div>

    <div id="weatherDescription" class="weather-description">
      اختر منطقتك لعرض حالة الطقس الحقيقية.
    </div>

    <!-- التفاصيل -->
    <div class="weather-details">

      <div class="weather-detail">
        <span>💧</span>
        <strong id="weatherHumidity">--%</strong>
        <small>الرطوبة</small>
      </div>

      <div class="weather-detail">
        <span>💨</span>
        <strong id="weatherWind">-- km/h</strong>
        <small>الرياح</small>
      </div>

    </div>

  </div>
</div>


<style>

/* =========================
   البطاقة
========================= */

.todays-weather {
  position: relative;
  overflow: hidden;

  width: 100%;

  border-radius: 30px;

  background: linear-gradient(
    135deg,
    #f3e7a3,
    #e8d98a
  );

  border: 1px solid rgba(160,140,55,.25);

  box-shadow:
    0 12px 30px rgba(120,100,30,.15);

  animation: none !important;
  transition: none !important;
}


/* =========================
   الفقاعات
========================= */

.weather-bubble {
  position: absolute;
  border-radius: 50%;
  pointer-events: none;
}

.bubble-1 {
  width: 230px;
  height: 230px;

  top: -110px;
  right: -70px;

  background: rgba(255,255,255,.25);
}

.bubble-2 {
  width: 170px;
  height: 170px;

  bottom: -90px;
  left: -65px;

  background: rgba(140,120,40,.08);
}

.bubble-3 {
  width: 65px;
  height: 65px;

  top: 55px;
  left: 30px;

  border: 2px solid rgba(255,255,255,.28);
}


/* =========================
   المحتوى
========================= */

.weather-content {
  position: relative;
  z-index: 5;

  padding: 30px;
}


/* =========================
   العنوان
========================= */

.weather-label {
  display: inline-block;

  padding: 7px 15px;

  border-radius: 20px;

  background: rgba(255,255,255,.30);

  color: #62582c;

  font-size: 12px;
  font-weight: 800;

  letter-spacing: 1px;
}

.weather-title {
  margin: 18px 0 18px;

  color: #403a20;

  font-size: 34px;
  font-weight: 800;
}


/* =========================
   اختيار المنطقة
========================= */

.weather-selector {
  position: relative;

  padding: 16px;

  margin-bottom: 18px;

  border-radius: 20px;

  background: rgba(255,255,255,.24);

  border: 1px solid rgba(255,255,255,.3);
}

.selector-title {
  color: #514a29;

  font-size: 15px;

  font-weight: bold;

  margin-bottom: 10px;
}

.selector-row {
  display: flex;

  gap: 8px;
}

.selector-row input {
  flex: 1;

  min-width: 0;

  padding: 12px 14px;

  border: none;

  outline: none;

  border-radius: 14px;

  background: rgba(255,255,255,.72);

  color: #403a20;

  font-size: 14px;
}

.selector-row input::placeholder {
  color: #81784d;
}

.selector-row button {
  padding: 12px 18px;

  border: none;

  border-radius: 14px;

  background: #75692f;

  color: white;

  font-weight: bold;

  cursor: pointer;
}


/* حالة البحث */

.search-status {
  margin-top: 8px;

  color: #665d35;

  font-size: 12px;
}


/* =========================
   نتائج المدن
========================= */

.city-results {
  display: none;

  margin-top: 10px;

  max-height: 180px;

  overflow-y: auto;
}

.city-result {
  padding: 11px 13px;

  margin-top: 6px;

  border-radius: 13px;

  background: rgba(255,255,255,.45);

  color: #403a20;

  font-size: 14px;

  cursor: pointer;
}

.city-result:hover {
  background: rgba(255,255,255,.65);
}


/* =========================
   الموقع
========================= */

.weather-location {
  color: #62582c;

  font-size: 15px;

  margin-top: 8px;
}


/* =========================
   الحرارة
========================= */

.weather-main {
  display: flex;

  align-items: center;

  gap: 18px;

  margin-top: 20px;
}

.weather-icon {
  font-size: 58px;
}

.weather-temp {
  color: #403a20;

  font-size: 48px;

  font-weight: 800;
}


/* الوصف */

.weather-description {
  margin-top: 5px;

  color: #5d5734;

  font-size: 18px;

  font-weight: 600;
}


/* =========================
   التفاصيل
========================= */

.weather-details {
  display: flex;

  gap: 12px;

  margin-top: 25px;
}

.weather-detail {
  min-width: 110px;

  padding: 13px;

  text-align: center;

  border-radius: 18px;

  background: rgba(255,255,255,.25);

  border: 1px solid rgba(255,255,255,.25);
}

.weather-detail span {
  display: block;

  font-size: 20px;

  margin-bottom: 5px;
}

.weather-detail strong {
  display: block;

  color: #403a20;

  font-size: 15px;
}

.weather-detail small {
  display: block;

  margin-top: 3px;

  color: #665f39;

  font-size: 11px;
}


/* =========================
   بدون حركة
========================= */

.todays-weather,
.todays-weather * {
  animation: none !important;
  transition: none !important;
}


/* الهاتف */
@media (max-width: 500px) {

  .weather-content {
    padding: 24px;
  }

  .weather-title {
    font-size: 29px;
  }

  .selector-row button {
    padding: 12px 14px;
  }

  .weather-temp {
    font-size: 42px;
  }

}

</style>


<script>
(function () {

  const cityInput =
    document.getElementById("cityInput");

  const searchButton =
    document.getElementById("searchWeatherBtn");

  const cityResults =
    document.getElementById("cityResults");

  const searchStatus =
    document.getElementById("searchStatus");

  const locationEl =
    document.getElementById("weatherLocation");

  const tempEl =
    document.getElementById("weatherTemp");

  const iconEl =
    document.getElementById("weatherIcon");

  const descriptionEl =
    document.getElementById("weatherDescription");

  const humidityEl =
    document.getElementById("weatherHumidity");

  const windEl =
    document.getElementById("weatherWind");


  /* =========================
     حالة الطقس
  ========================= */

  function weatherInfo(code) {

    if (code === 0)
      return ["☀️", "سماء صافية"];

    if ([1,2,3].includes(code))
      return ["🌤️", "غائم جزئياً"];

    if ([45,48].includes(code))
      return ["🌫️", "ضباب"];

    if ([51,53,55,56,57].includes(code))
      return ["🌦️", "رذاذ"];

    if ([61,63,65,66,67].includes(code))
      return ["🌧️", "أمطار"];

    if ([71,73,75,77].includes(code))
      return ["❄️", "ثلوج"];

    if ([80,81,82].includes(code))
      return ["🌦️", "زخات مطر"];

    if ([95,96,99].includes(code))
      return ["⛈️", "عواصف رعدية"];

    return ["🌤️", "حالة جوية متغيرة"];
  }


  /* =========================
     جلب الطقس
  ========================= */

  async function loadWeather(latitude, longitude, name) {

    try {

      locationEl.textContent =
        "📍 " + name;

      descriptionEl.textContent =
        "جاري تحديث الطقس...";

      const url =
        "https://api.open-meteo.com/v1/forecast" +
        "?latitude=" + encodeURIComponent(latitude) +
        "&longitude=" + encodeURIComponent(longitude) +
        "&current=temperature_2m,relative_humidity_2m,weather_code,wind_speed_10m" +
        "&timezone=auto";


      const response =
        await fetch(url);


      if (!response.ok)
        throw new Error("Weather API error");


      const data =
        await response.json();

      const current =
        data.current;


      const info =
        weatherInfo(current.weather_code);


      iconEl.textContent =
        info[0];

      descriptionEl.textContent =
        info[1];

      tempEl.textContent =
        Math.round(current.temperature_2m) +
        "°C";

      humidityEl.textContent =
        Math.round(current.relative_humidity_2m) +
        "%";

      windEl.textContent =
        Math.round(current.wind_speed_10m) +
        " km/h";


      /* حفظ اختيار المستخدم */
      localStorage.setItem(
        "alislamiah_weather_location",
        JSON.stringify({
          latitude: latitude,
          longitude: longitude,
          name: name
        })
      );

    }

    catch (error) {

      console.error(error);

      descriptionEl.textContent =
        "تعذر جلب بيانات الطقس حالياً.";

    }

  }


  /* =========================
     البحث عن المدينة
  ========================= */

  async function searchCity() {

    const query =
      cityInput.value.trim();


    if (!query) {

      searchStatus.textContent =
        "اكتب اسم مدينة أولاً.";

      return;
    }


    searchStatus.textContent =
      "جاري البحث...";

    cityResults.innerHTML = "";

    cityResults.style.display =
      "none";


    try {

      const url =
        "https://geocoding-api.open-meteo.com/v1/search" +
        "?name=" + encodeURIComponent(query) +
        "&count=8" +
        "&language=ar" +
        "&format=json";


      const response =
        await fetch(url);


      if (!response.ok)
        throw new Error("Geocoding error");


      const data =
        await response.json();


      if (!data.results ||
          data.results.length === 0) {

        searchStatus.textContent =
          "لم يتم العثور على المنطقة.";

        return;
      }


      searchStatus.textContent =
        "اختر المنطقة:";


      cityResults.style.display =
        "block";


      data.results.forEach(function (city) {

        const item =
          document.createElement("div");

        item.className =
          "city-result";


        const country =
          city.country || "";

        const admin =
          city.admin1 || "";


        item.textContent =
          city.name +
          (admin ? "، " + admin : "") +
          (country ? "، " + country : "");


        item.addEventListener(
          "click",
          function () {

            const fullName =
              city.name +
              (country ? "، " + country : "");


            cityInput.value =
              city.name;


            cityResults.style.display =
              "none";


            searchStatus.textContent =
              "تم اختيار المنطقة";


            loadWeather(
              city.latitude,
              city.longitude,
              fullName
            );

          }
        );


        cityResults.appendChild(item);

      });

    }

    catch (error) {

      console.error(error);

      searchStatus.textContent =
        "حدث خطأ أثناء البحث.";

    }

  }


  /* زر البحث */

  searchButton.addEventListener(
    "click",
    searchCity
  );


  /* Enter */

  cityInput.addEventListener(
    "keydown",
    function (event) {

      if (event.key === "Enter") {
        searchCity();
      }

    }
  );


  /* =========================
     استرجاع المنطقة المختارة
  ========================= */

  try {

    const saved =
      localStorage.getItem(
        "alislamiah_weather_location"
      );


    if (saved) {

      const location =
        JSON.parse(saved);


      cityInput.value =
        location.name.split("،")[0];


      loadWeather(
        location.latitude,
        location.longitude,
        location.name
      );

    }

  }

  catch (error) {

    console.error(error);

  }

})();
</script>

<div class="matches-card" id="matchesCard">
  <div class="card-header">
    <span class="icon">⚽</span>
    <h2>مباريات اليوم</h2>
    <span class="icon">🏆</span>
  </div>
  
  <div class="date-line" id="todayDate">جاري التحميل...</div>
  
  <div class="matches-list" id="matchesList">
    <div class="loading">جاري جلب المباريات...</div>
  </div>
  
  <div class="card-footer">
    <a href="https://sportscore.com/" target="_blank" rel="noopener">Powered by SportScore</a>
  </div>
</div>

<style>
  .matches-card {
    background: linear-gradient(145deg, #0f0f0f, #1a1a1a);
    border-radius: 20px;
    padding: 16px;
    width: 100%;
    max-width: 340px;
    margin: 12px auto;
    box-shadow: 0 8px 24px rgba(0,0,0,0.5);
    font-family: 'Segoe UI', Tahoma, Arial, sans-serif;
    color: #f0f0f0;
    direction: rtl;
    box-sizing: border-box;
  }
  .card-header {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    margin-bottom: 4px;
  }
  .card-header h2 {
    margin: 0;
    font-size: 1.25rem;
    font-weight: 700;
    background: linear-gradient(90deg, #ffd700, #ffaa00);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .icon { font-size: 1.3rem; }
  .date-line {
    text-align: center;
    font-size: 0.82rem;
    color: #aaa;
    margin-bottom: 12px;
  }
  .matches-list {
    display: flex;
    flex-direction: column;
    gap: 10px;
    max-height: 380px;
    overflow-y: auto;
  }
  .match-item {
    background: #161616;
    border-radius: 12px;
    padding: 10px 12px;
    border: 1px solid #2a2a2a;
  }
  .competition {
    font-size: 0.72rem;
    color: #ffd700;
    margin-bottom: 6px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .teams {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 6px;
  }
  .team {
    display: flex;
    align-items: center;
    gap: 6px;
    flex: 1;
    min-width: 0;
  }
  .team.home { justify-content: flex-start; }
  .team.away { justify-content: flex-end; }
  .team img {
    width: 22px;
    height: 22px;
    object-fit: contain;
    border-radius: 50%;
    background: #222;
    flex-shrink: 0;
  }
  .team-name {
    font-size: 0.84rem;
    font-weight: 600;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .score-box {
    min-width: 58px;
    text-align: center;
    font-weight: 700;
    font-size: 1rem;
    flex-shrink: 0;
  }
  .score-box .score { color: #fff; }
  .score-box .status {
    display: block;
    font-size: 0.68rem;
    font-weight: 500;
    margin-top: 1px;
  }
  .status.finished { color: #4caf50; }
  .status.live { color: #ff4444; }
  .status.upcoming { color: #aaa; }
  .loading, .error {
    text-align: center;
    padding: 24px 8px;
    color: #888;
    font-size: 0.9rem;
  }
  .error { color: #ff6b6b; }
  .card-footer {
    margin-top: 12px;
    text-align: center;
    font-size: 0.7rem;
  }
  .card-footer a { color: #666; text-decoration: none; }
</style>

<script>
(function() {
  function loadMatches() {
    var list = document.getElementById('matchesList');
    var dateEl = document.getElementById('todayDate');
    if (!list || !dateEl) return;

    var now = new Date();
    var y = now.getFullYear();
    var m = ('0' + (now.getMonth() + 1)).slice(-2);
    var d = ('0' + now.getDate()).slice(-2);
    var today = y + '-' + m + '-' + d;

    dateEl.innerHTML = now.toLocaleDateString('ar-EG', {
      weekday: 'long', year: 'numeric', month: 'long', day: 'numeric'
    });

    list.innerHTML = '<div class="loading">جاري جلب المباريات...</div>';

    var xhr = new XMLHttpRequest();
    xhr.open('GET', 'https://sportscore.com/api/v1/fixtures/?sport=football&date=' + today + '&limit=30', true);
    xhr.timeout = 12000;

    xhr.onreadystatechange = function() {
      if (xhr.readyState === 4) {
        if (xhr.status === 200) {
          try {
            var data = JSON.parse(xhr.responseText);
            if (data.matches && data.matches.length > 0) {
              render(data.matches);
            } else {
              loadFallback();
            }
          } catch(e) {
            loadFallback();
          }
        } else {
          loadFallback();
        }
      }
    };

    xhr.onerror = loadFallback;
    xhr.ontimeout = loadFallback;
    xhr.send();
  }

  function loadFallback() {
    var xhr = new XMLHttpRequest();
    xhr.open('GET', 'https://sportscore.com/api/widget/matches/?sport=football&limit=25', true);
    xhr.timeout = 10000;

    xhr.onreadystatechange = function() {
      if (xhr.readyState === 4) {
        if (xhr.status === 200) {
          try {
            var data = JSON.parse(xhr.responseText);
            if (data.matches && data.matches.length > 0) {
              render(data.matches);
            } else {
              document.getElementById('matchesList').innerHTML = '<div class="error">لا توجد مباريات</div>';
            }
          } catch(e) {
            document.getElementById('matchesList').innerHTML = '<div class="error">خطأ في البيانات</div>';
          }
        } else {
          document.getElementById('matchesList').innerHTML = '<div class="error">فشل الاتصال</div>';
        }
      }
    };
    xhr.send();
  }

  function render(matches) {
    var list = document.getElementById('matchesList');
    matches.sort(function(a, b) {
      var o = {live:0, finished:1, upcoming:2};
      return (o[a.status]||3) - (o[b.status]||3);
    });

    var html = '';
    for (var i = 0; i < matches.length; i++) {
      var m = matches[i];
      var finished = m.status === 'finished';
      var live = m.status === 'live';
      var score = (finished || live) ? (m.home_score||'0') + ' - ' + (m.away_score||'0') : 'vs';
      var stClass = finished ? 'finished' : (live ? 'live' : 'upcoming');
      var stText = finished ? 'انتهت' : (live ? 'مباشر' : 'قادمة');

      html += '<div class="match-item">' +
        '<div class="competition">' + (m.competition || 'دوري') + '</div>' +
        '<div class="teams">' +
          '<div class="team home">' +
            (m.home_logo ? '<img src="'+m.home_logo+'" onerror="this.style.display=\'none\'">' : '') +
            '<span class="team-name">' + (m.home||'') + '</span>' +
          '</div>' +
          '<div class="score-box">' +
            '<span class="score">' + score + '</span>' +
            '<span class="status ' + stClass + '">' + stText + '</span>' +
          '</div>' +
          '<div class="team away">' +
            '<span class="team-name">' + (m.away||'') + '</span>' +
            (m.away_logo ? '<img src="'+m.away_logo+'" onerror="this.style.display=\'none\'">' : '') +
          '</div>' +
        '</div>' +
      '</div>';
    }
    list.innerHTML = html;
  }

  setTimeout(loadMatches, 400);
  setInterval(loadMatches, 180000);
})();
</script>

<!-- بطاقة Outhub -->
<div class="promo-card outhub" style="background-color: #87CEEB; border-radius: 16px; overflow: hidden; box-shadow: 0 4px 12px rgba(0,0,0,0.08);">
  <div class="card-image">
    <video src="outhub.mp4" controls playsinline style="width: 100%; display: block; object-fit: cover;"></video>
  </div>
  <div class="card-content" style="padding: 16px 18px;">
    <span class="card-label" style="font-size: 12px; color: #0D47A1; font-weight: 500;">مادة إعلانية</span>
    <h3 class="card-title" style="margin: 8px 0 6px; font-size: 18px; color: #01579B;">Outhub</h3>
    <p class="card-desc" style="margin: 0 0 14px; font-size: 14px; line-height: 1.5; color: #0277BD;">طور تطبيقاتك مواقعك بواسطتنا Alislamiah</p>
    <a href="https://Alislamiah.github.io/Alislamiah-AI/results.html?q=Outhub" class="card-btn" style="display: inline-block; background: #0288D1; color: #FFFFFF; padding: 8px 16px; border-radius: 8px; text-decoration: none; font-size: 14px; font-weight: 500;">
      ← عرض النتائج
    </a>
  </div>
</div>


<!-- بطاقة مداد -->
<div class="promo-card madad" style="background-color: #FFF8DC; border-radius: 16px; overflow: hidden; box-shadow: 0 4px 12px rgba(0,0,0,0.08);">
  <div class="card-image">
    <img src="Screenshot_20261011-191020.jpg" alt="مداد" style="width: 100%; display: block; object-fit: cover;">
  </div>
  <div class="card-content" style="padding: 16px 18px;">
    <span class="card-label" style="font-size: 12px; color: #8B7355; font-weight: 500;">مادة إعلانية</span>
    <h3 class="card-title" style="margin: 8px 0 6px; font-size: 18px; color: #3D2B1F;">مداد</h3>
    <p class="card-desc" style="margin: 0 0 14px; font-size: 14px; line-height: 1.5; color: #5C4A3A;">حول أفكارك إلى واقع ،منصة مداد. من أقوى منصات صنع المواقع والألعاب.</p>
    <a href="https://Alislamiah.github.io/Alislamiah-AI/results.html?q=%D9%85%D8%AF%D8%A7%D8%AF" class="card-btn" style="display: inline-block; background: #E8D5A3; color: #3D2B1F; padding: 8px 16px; border-radius: 8px; text-decoration: none; font-size: 14px; font-weight: 500;">
      ← عرض النتائج
    </a>
  </div>
</div>

      <!-- بطاقة العربية -->
      <div class="promo-card arabiya">
        <div class="card-image">
          <img src="Screenshot_20260905-180328.jpg" alt="العربية">
        </div>
        <div class="card-content">
          <span class="card-label">مادة إعلانية</span>
          <h3 class="card-title">Alarabiya.net</h3>
          <p class="card-desc">تابعوا جميع الأخبار العربية والعالمية في منصة العربية.نت</p>
          <a href="results.html?q=%D8%A7%D9%84%D8%B9%D8%B1%D8%A8%D9%8A%D8%A9.%D9%86%D8%AA" class="card-btn">
            ← عرض النتائج
          </a>
        </div>
      </div>

      <!-- بطاقة الإسلامية -->
      <div class="promo-card islamiya">
        <div class="card-image">
          <img src="Screenshot_20260905-180622.jpg" alt="الإسلامية">
        </div>
        <div class="card-content">
          <span class="card-label">مادة إعلانية</span>
          <h3 class="card-title">Alislamiah.net</h3>
          <p class="card-desc">حيث تجدون برامج ومنصات إسلامية على Alislamiah.net، دروس الدعم في مادة الإسلامية وجميع الخدمات المدمجة.</p>
          <a href="results.html?q=%D8%A7%D9%84%D8%A5%D8%B3%D9%84%D8%A7%D9%85%D9%8A%D8%A9%20%D9%86%D8%AA" class="card-btn">
            ← عرض النتائج
          </a>
        </div>
      </div>

    </div>

<div class="news-wrapper">

  <div class="news-card">
    <div class="news-header">
      <span class="icon">🌍</span>
      <h2>أخبار عالمية</h2>
    </div>
    <div class="news-list" id="worldNews">
      <div class="loading">جاري التحميل...</div>
    </div>
  </div>

  <div class="news-card">
    <div class="news-header">
      <span class="icon">📰</span>
      <h2>أخبار عربية</h2>
    </div>
    <div class="news-list" id="arabNews">
      <div class="loading">جاري التحميل...</div>
    </div>
  </div>

  <div class="news-card">
    <div class="news-header">
      <span class="icon">🇸🇦</span>
      <h2>أخبار السعودية</h2>
    </div>
    <div class="news-list" id="saudiNews">
      <div class="loading">جاري التحميل...</div>
    </div>
  </div>

  <div class="news-card">
    <div class="news-header">
      <span class="icon">🇩🇿</span>
      <h2>أخبار الجزائر</h2>
    </div>
    <div class="news-list" id="algeriaNews">
      <div class="loading">جاري التحميل...</div>
    </div>
  </div>

</div>

<style>
  .news-wrapper {
    display: flex;
    flex-direction: column;
    gap: 16px;
    max-width: 340px;
    margin: 0 auto;
  }
  .news-card {
    background: linear-gradient(145deg, #0f0f0f, #1a1a1a);
    border-radius: 20px;
    padding: 16px;
    width: 100%;
    box-shadow: 0 8px 24px rgba(0,0,0,0.5);
    font-family: 'Segoe UI', Tahoma, Arial, sans-serif;
    color: #f0f0f0;
    direction: rtl;
    box-sizing: border-box;
  }
  .news-header {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    margin-bottom: 12px;
  }
  .news-header h2 {
    margin: 0;
    font-size: 1.2rem;
    font-weight: 700;
    background: linear-gradient(90deg, #ffd700, #ffaa00);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .news-header .icon { font-size: 1.25rem; }
  .news-list {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }
  .news-item {
    background: #161616;
    border-radius: 12px;
    overflow: hidden;
    border: 1px solid #2a2a2a;
  }
  .news-item a {
    color: inherit;
    text-decoration: none;
    display: block;
  }
  .news-image {
    width: 100%;
    height: 140px;
    object-fit: cover;
    display: block;
    background: #222;
  }
  .news-content {
    padding: 11px 12px;
  }
  .news-title {
    font-size: 0.9rem;
    font-weight: 600;
    line-height: 1.4;
    margin-bottom: 5px;
  }
  .news-meta {
    font-size: 0.7rem;
    color: #888;
  }
  .loading, .error {
    text-align: center;
    padding: 22px 8px;
    color: #888;
    font-size: 0.88rem;
  }
  .error { color: #ff6b6b; }
</style>

<script>
(function() {
  var sources = {
    world: [
      'https://feeds.bbci.co.uk/arabic/rss.xml',
      'https://www.france24.com/ar/rss',
      'https://www.skynewsarabia.com/rss'
    ],
    arab: [
      'https://feeds.bbci.co.uk/arabic/rss.xml',
      'https://www.france24.com/ar/rss',
      'https://www.skynewsarabia.com/rss'
    ],
    saudi: [
      'https://feeds.bbci.co.uk/arabic/rss.xml',
      'https://www.france24.com/ar/rss'
    ],
    algeria: [
      'https://www.echoroukonline.com/feed'
    ]
  };

  var CORX_KEY = 'corx_wurhkSx9Z5GkXBs85bu8iyqJ-963qATW';

  function loadSection(id, urls) {
    var list = document.getElementById(id);
    if (!list) return;
    list.innerHTML = '<div class="loading">جاري التحميل...</div>';

    var allItems = [];
    var finished = 0;

    function done() {
      finished++;
      if (finished < urls.length) return;

      if (allItems.length === 0) {
        list.innerHTML = '<div class="error">فشل جلب الأخبار</div>';
        return;
      }

      var unique = [];
      var seen = {};
      for (var i = 0; i < allItems.length; i++) {
        var t = allItems[i].title;
        if (!seen[t]) {
          seen[t] = true;
          unique.push(allItems[i]);
        }
      }

      unique.sort(function(a, b) {
        return new Date(b.date) - new Date(a.date);
      });

      renderItems(list, unique);
    }

    for (var i = 0; i < urls.length; i++) {
      fetchRss(urls[i], function(items) {
        if (items && items.length) allItems = allItems.concat(items);
        done();
      });
    }
  }

  function getImage(item) {
    // 1. enclosure
    var enc = item.querySelector('enclosure');
    if (enc) {
      var type = enc.getAttribute('type') || '';
      var url = enc.getAttribute('url') || '';
      if (url && (type.indexOf('image') !== -1 || url.match(/\.(jpg|jpeg|png|webp|gif)/i))) {
        return url;
      }
    }

    // 2. media:content أو media:thumbnail
    var media = item.getElementsByTagName('media:content')[0] || 
                item.getElementsByTagName('media:thumbnail')[0] ||
                item.querySelector('content');
    if (media) {
      var murl = media.getAttribute('url') || media.getAttribute('src');
      if (murl) return murl;
    }

    // 3. من الوصف (description أو content:encoded)
    var desc = '';
    var d1 = item.querySelector('description');
    var d2 = item.getElementsByTagName('content:encoded')[0];
    if (d1) desc += d1.textContent || '';
    if (d2) desc += d2.textContent || '';

    // ابحث عن أول صورة
    var match = desc.match(/<img[^>]+src=["']([^"']+)["']/i);
    if (match && match[1]) return match[1];

    // ابحث عن روابط صور مباشرة
    match = desc.match(/(https?:\/\/[^\s"'<>]+\.(jpg|jpeg|png|webp|gif))/i);
    if (match) return match[1];

    return '';
  }

  function fetchRss(rssUrl, callback) {
    var proxyUrl = 'https://corx.envx.cn/fetch?url=' + encodeURIComponent(rssUrl) + '&corx-key=' + CORX_KEY;

    var xhr = new XMLHttpRequest();
    xhr.open('GET', proxyUrl, true);
    xhr.timeout = 14000;

    xhr.onreadystatechange = function() {
      if (xhr.readyState === 4) {
        if (xhr.status === 200 && xhr.responseText && xhr.responseText.length > 100) {
          try {
            var parser = new DOMParser();
            var xml = parser.parseFromString(xhr.responseText, 'text/xml');
            var items = xml.querySelectorAll('item');
            if (!items.length) items = xml.querySelectorAll('entry');

            if (items.length > 0) {
              var result = [];
              for (var i = 0; i < Math.min(items.length, 10); i++) {
                var item = items[i];
                var title = (item.querySelector('title') || {}).textContent || '';
                var linkEl = item.querySelector('link');
                var link = linkEl ? (linkEl.textContent || linkEl.getAttribute('href') || '#') : '#';
                var dateEl = item.querySelector('pubDate') || item.querySelector('published') || item.querySelector('updated');
                var date = dateEl ? dateEl.textContent : '';
                var image = getImage(item);

                if (title) {
                  result.push({
                    title: title.trim(),
                    link: link.trim(),
                    date: date,
                    image: image
                  });
                }
              }
              callback(result);
              return;
            }
          } catch(e) {}
        }
        callback([]);
      }
    };

    xhr.onerror = function() { callback([]); };
    xhr.ontimeout = function() { callback([]); };
    xhr.send();
  }

  function renderItems(list, items) {
    var html = '';
    var max = Math.min(items.length, 8);
    for (var i = 0; i < max; i++) {
      var item = items[i];
      var dateStr = '';
      if (item.date) {
        try {
          dateStr = new Date(item.date).toLocaleDateString('ar-EG', {
            day: 'numeric', month: 'short', hour: '2-digit', minute: '2-digit'
          });
        } catch(e) {}
      }

      html += '<div class="news-item">' +
        '<a href="' + item.link + '" target="_blank" rel="noopener">';

      if (item.image) {
        html += '<img class="news-image" src="' + item.image + '" onerror="this.style.display=\'none\'" loading="lazy">';
      }

      html += '<div class="news-content">' +
          '<div class="news-title">' + item.title + '</div>' +
          '<div class="news-meta">' + dateStr + '</div>' +
        '</div>' +
        '</a>' +
      '</div>';
    }
    list.innerHTML = html;
  }

  setTimeout(function() {
    loadSection('worldNews', sources.world);
    loadSection('arabNews', sources.arab);
    loadSection('saudiNews', sources.saudi);
    loadSection('algeriaNews', sources.algeria);
  }, 500);
})();
</script>

    <!-- FOOTER -->
    <div class="footer">
        <strong>Alislamiah AI Browser</strong><br>2026 ©
    </div>

</div>

<!-- =====================================================
     SIDE MENU
===================================================== -->
<div id="menuOverlay" class="menu-overlay" onclick="closeMenu(event)">
    <div class="side-menu" onclick="event.stopPropagation()">
        <div class="menu-header">
            <h2>Alislamiah AI</h2>
            <button class="close-menu" type="button" onclick="closeMenu()">✕</button>
        </div>

        <button class="menu-item" type="button" onclick="window.location.href='index.html'; closeMenu();">🏠 الرئيسية</button>
        <button class="menu-item" type="button" onclick="searchShortcut('Quran', ''); closeMenu();">📖 Quran</button>
        <button class="menu-item" type="button" onclick="window.location.href='favorite.html'; closeMenu();">⭐ Favorites</button>
        <button class="menu-item" type="button" onclick="searchShortcut('AI Assistant', ''); closeMenu();">🤖 AI</button>
        <button class="menu-item" type="button" onclick="window.location.href='Settings.html'">⚙️ Settings</button>
        <button class="menu-item" type="button" onclick="searchShortcut('Alislamiah', 'icon.png'); closeMenu();">🌐 Alislamiah</button>
        <button class="menu-item" type="button" onclick="searchShortcut('YouTube', 'https://www.youtube.com/favicon.ico'); closeMenu();">▶️ YouTube</button>
        <button class="menu-item" type="button" onclick="window.location.href='history.html'; closeMenu();">🕒 History</button>
    </div>
</div>

<script>
const RESULTS_PAGE = "results.html";
const HISTORY_KEY = "alislamiah_history";

/* حفظ السجل */
function addToHistory(title, url, icon) {
    try {
        let history = JSON.parse(localStorage.getItem(HISTORY_KEY)) || [];
        history.unshift({
            title: title,
            url: url,
            icon: icon || "",
            time: Date.now()
        });
        if (history.length > 100) {
            history = history.slice(0, 100);
        }
        localStorage.setItem(HISTORY_KEY, JSON.stringify(history));
    } catch (e) {
        console.error(e);
    }
}

/* تحديث أيقونة AI حسب محرك البحث */
function updateMainAiLogo() {
    const engine = localStorage.getItem("searchEngine") || "Alislamiah AI";
    const logoContainer = document.getElementById("mainAiLogo");

    if (!logoContainer) return;

    if (engine === "Alislamiah AI") {
        logoContainer.innerHTML = '<img src="icon.png" alt="Alislamiah AI">';
    } else if (engine === "Alislamiah") {
        logoContainer.innerHTML = '<img src="icon.jpg" alt="Alislamiah">';
    } else if (engine === "Google") {
        logoContainer.innerHTML = '<img src="https://www.google.com/favicon.ico" alt="Google" style="width:70px; height:70px; object-fit:contain;">';
    } else if (engine === "Microsoft Bing") {
        logoContainer.innerHTML = '<img src="https://www.bing.com/sa/simg/favicon-2x.ico" alt="Microsoft Bing" style="width:70px; height:70px; object-fit:contain;">';
    }
}

window.addEventListener("load", function() {
    updateMainAiLogo();
});

window.addEventListener("storage", function(event) {
    if (event.key === "searchEngine") {
        updateMainAiLogo();
    }
});

/* وظيفة لتوجيه الاختصارات للبحث باسم الاختصار في النتائج */
function searchShortcut(name, icon){
    const targetUrl = RESULTS_PAGE + "?q=" + encodeURIComponent(name);
    addToHistory(name, targetUrl, icon);
    window.location.href = targetUrl;
}

/* وظيفة البحث المعتادة عبر شريط البحث */
function performSearch(){
    const input = document.getElementById("searchInput");
    const query = input.value.trim();
    if(query === ""){ input.focus(); return; }

    const targetUrl = RESULTS_PAGE + "?q=" + encodeURIComponent(query);
    const engine = localStorage.getItem("searchEngine") || "Alislamiah AI";

    let histIcon = "icon.png";
    if (engine === "Google") histIcon = "https://www.google.com/favicon.ico";
    else if (engine === "Microsoft Bing") histIcon = "https://www.bing.com/favicon.ico";
    else if (engine === "Alislamiah") histIcon = "icon.jpg";
    addToHistory(query, targetUrl, histIcon);

    window.location.href = targetUrl;
}

function handleSearchKey(event){
    if(event.key === "Enter"){
        event.preventDefault();
        performSearch();
    }
}

function openMenu(){
    const overlay = document.getElementById("menuOverlay");
    overlay.classList.add("show");
    document.body.style.overflow = "hidden";
}

function closeMenu(event){
    if(event){
        const overlay = document.getElementById("menuOverlay");
        if(event.target !== overlay) return;
    }
    const overlay = document.getElementById("menuOverlay");
    overlay.classList.remove("show");
    document.body.style.overflow = "";
}

document.addEventListener("keydown", function(event){
    if(event.key === "Escape"){
        document.getElementById("menuOverlay").classList.remove('show');
        document.body.style.overflow = "";
    }
});
document.addEventListener("keydown", function(event){
    if(event.key === "Escape"){
        document.getElementById("menuOverlay").classList.remove('show');
        document.body.style.overflow = "";
    }
});

// ===== كود الحماية (أضفه هنا) =====
(function () {
  const currentUser = localStorage.getItem("alislamiah_current_user");
  if (!currentUser) {
    window.location.href = "signin.html";
  }
})();
/* =========================================
   نظام اللغة الموحد - Alislamiah
========================================= */

function getLanguage() {
    return localStorage.getItem("appLanguage") || "en";
}

function applyLanguage(lang) {
    // ضبط اتجاه الصفحة
    document.documentElement.lang = lang;
    document.documentElement.dir = (lang === "ar") ? "rtl" : "ltr";

    // يمكنك هنا إضافة أي تعديلات خاصة بكل صفحة
    // مثال: تغيير نصوص معينة
}

// عند فتح الصفحة
document.addEventListener("DOMContentLoaded", function () {
    applyLanguage(getLanguage());
});

// عند تغيير اللغة من صفحة الإعدادات
window.addEventListener("storage", function (e) {
    if (e.key === "appLanguage") {
        applyLanguage(e.newValue || "en");
    }
});

</script>

</body>
</html>
