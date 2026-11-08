<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Alislamiah AI Browser</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent}
html{width:100%;min-height:100%;scroll-behavior:smooth}
body{width:100%;min-height:100vh;background:radial-gradient(circle at 50% 25%, rgba(0,115,255,.18), transparent 34%),radial-gradient(circle at 100% 70%, rgba(0,190,255,.10), transparent 35%),linear-gradient(145deg, #040a17 0%, #07142a 55%, #06172c 100%);color:#fff;font-family:Arial,"Segoe UI",Tahoma,sans-serif;overflow-x:hidden}
:root{--blue:#087fff;--blue-light:#08b9ef;--text:#fff;--muted:#aebbd2;--border:rgba(255,255,255,.14);--card:rgba(255,255,255,.075)}
.app{width:100%;max-width:700px;min-height:100vh;margin:0 auto;padding:14px 14px 30px}
.topbar{width:100%;height:48px;display:flex;align-items:center;justify-content:flex-start;gap:15px;margin-bottom:8px}
.top-button{width:44px;height:44px;border-radius:14px;border:1px solid rgba(255,255,255,.13);background:rgba(255,255,255,.055);color:#fff;display:flex;align-items:center;justify-content:center;font-size:21px;cursor:pointer;transition:.18s}
.top-button:active{transform:scale(.92)}
.top-title{font-size:15px;font-weight:700;letter-spacing:.3px;flex:1}
.account-icon{width:44px;height:44px;min-width:44px;border-radius:50%;border:1px solid rgba(255,255,255,.20);background:rgba(255,255,255,.08);display:flex;align-items:center;justify-content:center;font-size:22px;cursor:pointer;overflow:hidden;position:relative}
.account-icon img{width:100%;height:100%;object-fit:cover}
.account-icon:active{transform:scale(.92)}
.brand{text-align:center;margin-top:4px}
.brand-name{color:#168cff;font-size:34px;line-height:1.2;font-weight:800;letter-spacing:-1px;text-shadow:0 0 30px rgba(22,140,255,.25)}
.brand-line{width:94%;height:1px;margin:12px auto 0;background:linear-gradient(90deg,transparent,rgba(255,255,255,.70),transparent)}
.ai-logo{width:165px;height:165px;margin:28px auto 20px;border-radius:43px;display:flex;align-items:center;justify-content:center;background:linear-gradient(145deg,#087cff 0%,#08b9ee 100%);box-shadow:0 18px 55px rgba(0,120,255,.32),inset 0 1px 1px rgba(255,255,255,.38);position:relative;overflow:hidden}
.ai-logo::before{content:"";position:absolute;inset:-5px;border-radius:47px;border:1px solid rgba(70,185,255,.20)}
.ai-logo span{color:#fff;font-size:60px;font-weight:800;position:relative;z-index:2}
.ai-logo img{width:100%;height:100%;object-fit:cover;position:relative;z-index:2}
.hero{width:100%;text-align:center}
.hero h1{font-size:31px;line-height:1.3;font-weight:800}
.hero-line{width:87%;height:1px;margin:17px auto 14px;background:rgba(255,255,255,.65)}
.hero p{color:#bdc9df;font-size:18px;line-height:1.8}

/* === هنا التثبيت فقط === */
.search-area{
    width:100%;
    margin-top:23px;
    position:sticky;
    top:0;
    z-index:999;
    padding:12px 0 14px 0;
    margin-left:-14px;
    margin-right:-14px;
    padding-left:14px;
    padding-right:14px;
    background:radial-gradient(circle at 50% 25%, rgba(0,115,255,.18), transparent 34%),radial-gradient(circle at 100% 70%, rgba(0,190,255,.10), transparent 35%),linear-gradient(145deg, #040a17 0%, #07142a 55%, #06172c 100%);
}
.search-box{width:100%;height:64px;display:flex;direction:ltr;background:#fff;border-radius:21px;overflow:hidden;box-shadow:0 15px 45px rgba(0,0,0,.27),0 0 30px rgba(0,130,255,.08)}
.search-button{width:84px;min-width:84px;border:none;outline:none;background:linear-gradient(145deg,#087fff,#0870e4);color:#fff;font-size:27px;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:.15s}
.search-button:active{transform:scale(.96)}
.search-input{width:100%;min-width:0;border:none;outline:none;background:#fff;color:#1d2938;font-size:17px;padding:0 18px;text-align:right;direction:rtl}
.search-input::placeholder{color:#999}
.shortcuts-title{text-align:center;color:#aebbd2;font-size:15px;margin:27px 0 14px}
.shortcuts{width:100%;display:grid;grid-template-columns:repeat(3,1fr);gap:12px}
.shortcut{min-height:142px;border-radius:24px;border:1px solid rgba(255,255,255,.14);background:linear-gradient(145deg,rgba(255,255,255,.095),rgba(255,255,255,.045));box-shadow:0 12px 30px rgba(0,0,0,.15),inset 0 1px 0 rgba(255,255,255,.04);display:flex;flex-direction:column;align-items:center;justify-content:center;gap:10px;cursor:pointer;user-select:none;transition:transform .16s ease,background .16s ease,border-color .16s ease}
.shortcut:hover{background:rgba(255,255,255,.11);border-color:rgba(25,145,255,.40)}
.shortcut:active{transform:scale(.94)}
.shortcut-icon{width:60px;height:60px;border-radius:18px;display:flex;align-items:center;justify-content:center;font-size:38px}
.shortcut-name{color:#fff;font-size:15px;font-weight:600}
.promo-cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(310px,1fr));gap:24px;direction:rtl;font-family:'Segoe UI',system-ui,-apple-system,sans-serif;margin-top:32px}
.promo-card{border-radius:28px;overflow:hidden;box-shadow:0 20px 40px rgba(0,0,0,.25);transition:transform .35s ease,box-shadow .35s ease}
.promo-card:hover{transform:translateY(-10px);box-shadow:0 28px 50px rgba(0,0,0,.35)}
.promo-card.arabiya{background:#0f1c2e}
.promo-card.islamiya{background:#0c4a5c}
.card-image{height:190px;overflow:hidden}
.card-image img{width:100%;height:100%;object-fit:cover;display:block}
.card-content{padding:24px 26px 30px;position:relative;overflow:hidden}
.card-content::before{content:'';position:absolute;width:180px;height:180px;border-radius:50%;background:rgba(255,255,255,.04);top:-40px;left:-40px}
.card-content::after{content:'';position:absolute;width:120px;height:120px;border-radius:50%;background:rgba(255,255,255,.03);bottom:-30px;right:-30px}
.card-label{display:inline-block;background:rgba(255,255,255,.15);color:rgba(255,255,255,.9);font-size:12px;font-weight:600;padding:6px 16px;border-radius:30px;margin-bottom:18px}
.card-title{color:#fff;font-size:26px;font-weight:700;margin:0 0 12px 0;letter-spacing:-.4px}
.card-desc{color:rgba(255,255,255,.78);font-size:14.5px;line-height:1.7;margin:0 0 24px 0}
.card-btn{display:inline-block;background:#fff;color:#0f1c2e!important;text-decoration:none;padding:12px 24px;border-radius:50px;font-weight:700;font-size:14.5px;transition:all .3s ease;box-shadow:0 6px 16px rgba(0,0,0,.12)}
.islamiya .card-btn{color:#0c4a5c!important}
.card-btn:hover{transform:translateY(-3px);box-shadow:0 10px 22px rgba(0,0,0,.2)}
.footer{text-align:center;margin-top:30px;padding-bottom:5px;color:#91a5c5;font-size:14px;line-height:1.8}
.footer strong{color:#b9c8e2}
.menu-overlay{position:fixed;inset:0;background:rgba(0,0,0,.62);opacity:0;visibility:hidden;transition:.25s;z-index:1000}
.menu-overlay.show{opacity:1;visibility:visible}
.side-menu{position:absolute;top:0;right:0;width:82%;max-width:330px;height:100%;padding:24px 17px;background:linear-gradient(160deg,#0b1930,#07101f);border-left:1px solid rgba(255,255,255,.09);transform:translateX(100%);transition:.30s;overflow-y:auto}
.menu-overlay.show .side-menu{transform:translateX(0)}
.menu-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:28px}
.menu-header h2{font-size:20px}
.close-menu{width:42px;height:42px;border:1px solid rgba(255,255,255,.13);border-radius:13px;background:rgba(255,255,255,.06);color:#fff;font-size:19px;cursor:pointer}
.menu-item{width:100%;height:56px;margin-bottom:10px;border:none;border-radius:15px;background:rgba(255,255,255,.055);color:#fff;display:flex;align-items:center;gap:14px;padding:0 17px;font-size:15px;cursor:pointer;text-align:right}
.menu-item:active{background:rgba(20,130,255,.20)}
</style>
</head>
<body>
<div class="app">
<div class="topbar"><button class="top-button" onclick="openMenu()">☰</button><div class="top-title">Alislamiah AI</div><div class="account-icon" id="accountIcon" onclick="openAccount()" title="الإعدادات">👤</div></div>
<div class="brand"><div class="brand-name">Alislamiah</div><div class="brand-line"></div></div>
<div class="ai-logo" id="mainAiLogo"><span>AI</span></div>
<div class="hero"><h1>Alislamiah-AI Browser</h1><div class="hero-line"></div><p>الذكاء الاصطناعي • البحث • السرعة • الخصوصية</p></div>

<div class="search-area">
<div class="search-box">
<button class="search-button" onclick="performSearch()">🔍</button>
<input id="searchInput" class="search-input" type="search" placeholder="ابحث في Alislamiah..." onkeydown="handleSearchKey(event)">
</div>
</div>

<div class="shortcuts-title">الوصول السريع</div>
<div class="shortcuts">
<div class="shortcut" onclick="searchShortcut('YouTube','')"><div class="shortcut-icon">▶️</div><div class="shortcut-name">YouTube</div></div>
<div class="shortcut" onclick="searchShortcut('AI','')"><div class="shortcut-icon">🤖</div><div class="shortcut-name">AI</div></div>
<div class="shortcut" onclick="searchShortcut('Alislamiah','')"><div class="shortcut-icon">🌐</div><div class="shortcut-name">Alislamiah</div></div>
<div class="shortcut" onclick="searchShortcut('Explore','')"><div class="shortcut-icon">📱</div><div class="shortcut-name">Explore</div></div>
<div class="shortcut" onclick="searchShortcut('Settings','')"><div class="shortcut-icon">⚙️</div><div class="shortcut-name">Settings</div></div>
<div class="shortcut" onclick="searchShortcut('Quran','')"><div class="shortcut-icon">📖</div><div class="shortcut-name">Quran</div></div>
</div>

<div style="margin-top:32px;text-align:center;color:#aebbd2">🌤️ Today's weather - 📍 اختر منطقتك - LIVE WEATHER - ⚽ مباريات اليوم - 🌍 أخبار عالمية - 📰 أخبار عربية - 🇸🇦 أخبار السعودية - 🇩🇿 أخبار الجزائر</div>

<div class="promo-cards">
<div class="promo-card arabiya"><div class="card-image"><img src="https://via.placeholder.com/400x190?text=Arabiya"></div><div class="card-content"><div class="card-label">مادة إعلانية</div><div class="card-title">Alarabiya.net</div><div class="card-desc">تابعوا جميع الأخبار العربية والعالمية في منصة العربية.نت</div><a class="card-btn" href="#">عرض النتائج</a></div></div>
<div class="promo-card islamiya"><div class="card-image"><img src="https://via.placeholder.com/400x190?text=Islamiah"></div><div class="card-content"><div class="card-label">مادة إعلانية</div><div class="card-title">Alislamiah.net</div><div class="card-desc">حيث تجدون برامج ومنصات إسلامية على Alislamiah.net</div><a class="card-btn" href="#">عرض النتائج</a></div></div>
</div>

<div class="footer">2026 © <strong>Alislamiah AI Browser</strong></div>
</div>

<div id="menuOverlay" class="menu-overlay" onclick="closeMenu(event)">
<div class="side-menu">
<div class="menu-header"><h2>القائمة</h2><button class="close-menu" onclick="closeMenu()">✕</button></div>
<button class="menu-item">🏠 الرئيسية</button>
<button class="menu-item">⚙️ الإعدادات</button>
<button class="menu-item">📖 القرآن</button>
</div>
</div>

<script>
const RESULTS_PAGE="results.html";const HISTORY_KEY="alislamiah_history";
function addToHistory(title,url,icon){try{let h=JSON.parse(localStorage.getItem(HISTORY_KEY))||[];h.unshift({title:title,url:url,icon:icon||"",time:Date.now()});if(h.length>100){h=h.slice(0,100)}localStorage.setItem(HISTORY_KEY,JSON.stringify(h))}catch(e){console.error(e)}}
function updateMainAiLogo(){const engine=localStorage.getItem("searchEngine")||"Alislamiah AI";const logoContainer=document.getElementById("mainAiLogo");if(!logoContainer)return;if(engine==="Alislamiah AI"){logoContainer.innerHTML='<img src="icon.png" alt="Alislamiah AI">'}else if(engine==="Alislamiah"){logoContainer.innerHTML='<img src="icon.jpg" alt="Alislamiah">'}else if(engine==="Google"){logoContainer.innerHTML='<img src="https://www.google.com/favicon.ico" alt="Google" style="width:70px;height:70px;object-fit:contain;">'}else if(engine==="Microsoft Bing"){logoContainer.innerHTML='<img src="https://www.bing.com/sa/simg/favicon-2x.ico" alt="Microsoft Bing" style="width:70px;height:70px;object-fit:contain;">'}}
window.addEventListener("load",function(){updateMainAiLogo()});
window.addEventListener("storage",function(event){if(event.key==="searchEngine"){updateMainAiLogo()}});
function searchShortcut(name,icon){const targetUrl=RESULTS_PAGE+"?q="+encodeURIComponent(name);addToHistory(name,targetUrl,icon);window.location.href=targetUrl}
function performSearch(){const input=document.getElementById("searchInput");const query=input.value.trim();if(query===""){input.focus();return}const targetUrl=RESULTS_PAGE+"?q="+encodeURIComponent(query);const engine=localStorage.getItem("searchEngine")||"Alislamiah AI";let histIcon="icon.png";if(engine==="Google")histIcon="https://www.google.com/favicon.ico";else if(engine==="Microsoft Bing")histIcon="https://www.bing.com/favicon.ico";else if(engine==="Alislamiah")histIcon="icon.jpg";addToHistory(query,targetUrl,histIcon);window.location.href=targetUrl}
function handleSearchKey(event){if(event.key==="Enter"){event.preventDefault();performSearch()}}
function openMenu(){const overlay=document.getElementById("menuOverlay");overlay.classList.add("show");document.body.style.overflow="hidden"}
function closeMenu(event){if(event){const overlay=document.getElementById("menuOverlay");if(event.target!==overlay)return}const overlay=document.getElementById("menuOverlay");overlay.classList.remove("show");document.body.style.overflow=""}
document.addEventListener("keydown",function(event){if(event.key==="Escape"){document.getElementById("menuOverlay").classList.remove('show');document.body.style.overflow=""}});
(function(){const currentUser=localStorage.getItem("alislamiah_current_user");if(!currentUser){window.location.href="signin.html"}})();
function getLanguage(){return localStorage.getItem("appLanguage")||"en"}
function applyLanguage(lang){document.documentElement.lang=lang;document.documentElement.dir=(lang==="ar")?"rtl":"ltr"}
document.addEventListener("DOMContentLoaded",function(){applyLanguage(getLanguage())});
window.addEventListener("storage",function(e){if(e.key==="appLanguage"){applyLanguage(e.newValue||"en")}});

function openAccount(){ window.location.href="Settings.html"; }
function updateAccountIcon(){
  const el=document.getElementById("accountIcon");
  if(!el) return;
  try{
    const raw=localStorage.getItem("alislamiah_current_user");
    if(!raw){ el.innerHTML="👤"; return; }
    let user=null;
    try{ user=JSON.parse(raw); }catch(e){ user=null; }
    // اذا كان المستخدم نص فقط أو بدون صورة -> أيقونة عامة بدون اسم
    let photo = "";
    if(user && typeof user==="object"){
      photo = user.photo || user.avatar || user.picture || user.image || user.profilePic || "";
    }
    if(photo){ el.innerHTML='<img src="'+photo+'" alt="حسابي">'; }
    else{ el.innerHTML="👤"; }
  }catch(e){ el.innerHTML="👤"; }
}
window.addEventListener("load", updateAccountIcon);
document.addEventListener("DOMContentLoaded", updateAccountIcon);
window.addEventListener("storage", function(e){ if(e.key==="alislamiah_current_user") updateAccountIcon(); });
</script>
</body>
</html>
