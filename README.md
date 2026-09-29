[egg-monster-word-hunter.html](https://github.com/user-attachments/files/32809604/egg-monster-word-hunter.html)

<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,minimum-scale=1.0,user-scalable=no,viewport-fit=cover">

<title>Egg Monster - Word Hunter</title>

<style>

*{
    box-sizing:border-box;
    user-select:none;
}

html,body{
    margin:0;
    width:100%;
    height:100%;
    overflow:hidden;
    background:#050914;
    font-family:Arial,sans-serif;
}

canvas{
    display:block;
    width:100%;
    height:100%;
    touch-action:none;
}

/* =====================================================
   TOUCH CONTROLS (MOBILE)
===================================================== */

#touchControls{
    position:fixed;
    inset:0;
    z-index:25;
    display:none;
    pointer-events:none;
}

#joystickBase{
    position:absolute;
    left:24px;
    bottom:24px;
    width:132px;
    height:132px;
    border-radius:50%;
    background:rgba(0,0,0,.32);
    border:2px solid rgba(94,232,255,.55);
    pointer-events:auto;
    touch-action:none;
}

#joystickKnob{
    position:absolute;
    left:50%;
    top:50%;
    width:56px;
    height:56px;
    margin:-28px 0 0 -28px;
    border-radius:50%;
    background:rgba(94,232,255,.75);
    border:2px solid rgba(255,255,255,.8);
    box-shadow:0 0 14px rgba(0,200,255,.6);
}

#attackButton{
    position:absolute;
    right:26px;
    bottom:34px;
    width:104px;
    height:104px;
    border-radius:50%;
    background:rgba(255,76,121,.82);
    border:3px solid rgba(255,255,255,.85);
    color:white;
    font-weight:bold;
    font-size:15px;
    line-height:1.1;
    text-align:center;
    display:flex;
    align-items:center;
    justify-content:center;
    pointer-events:auto;
    touch-action:none;
    user-select:none;
}

#attackButton:active{
    transform:scale(.94);
}

body.touch #controls{
    display:none !important;
}


/* =====================================================
   LOGIN
===================================================== */

#loginScreen{
    position:fixed;
    inset:0;
    z-index:1000;

    display:flex;
    align-items:center;
    justify-content:center;

    background:
        radial-gradient(
            circle at center,
            #254f7d,
            #0a1729 50%,
            #02050a
        );
}

.loginBox{
    width:460px;
    max-width:92%;

    padding:35px;

    text-align:center;

    border-radius:25px;

    background:rgba(4,10,22,.96);

    border:2px solid #28dfff;

    box-shadow:
        0 0 40px rgba(0,210,255,.4);
}

.loginBox h1{
    margin:0 0 5px;

    color:#67edff;

    font-size:42px;

    text-shadow:
        0 0 20px #00cfff;
}

.loginBox p{
    color:#abc9dc;
}

.loginButton{

    width:100%;

    padding:14px;

    margin-top:12px;

    border:0;

    border-radius:10px;

    color:white;

    font-size:17px;

    font-weight:bold;

    cursor:pointer;
}

.googleButton{
    background:#4285F4;
}

.facebookButton{
    background:#1877F2;
}

.guestButton{
    background:#1fa855;
}

.loginButton:hover{
    transform:scale(1.02);
}

#loginStatus{
    min-height:24px;
    margin-top:12px;
    color:#ff6677;
}


/* =====================================================
   PROFILE
===================================================== */

#profileScreen{

    position:fixed;
    inset:0;

    z-index:900;

    display:none;

    align-items:center;
    justify-content:center;

    background:
        radial-gradient(
            circle,
            #183e62,
            #06101d 65%,
            #02050a
        );
}

.profileBox{

    width:480px;
    max-width:92%;

    padding:35px;

    text-align:center;

    border-radius:25px;

    background:rgba(3,9,20,.97);

    border:2px solid #ffd34d;

    box-shadow:
        0 0 35px rgba(255,190,30,.25);
}

.profileBox h2{
    color:#ffe064;
}

#playerName{

    width:100%;

    padding:14px;

    border-radius:10px;

    border:2px solid #34dfff;

    background:#071422;

    color:white;

    font-size:18px;

    text-align:center;

    outline:none;

    user-select:text;
}

.startButton{

    margin-top:18px;

    padding:14px 45px;

    border:0;

    border-radius:12px;

    background:
        linear-gradient(
            135deg,
            #00d5ff,
            #5367ff
        );

    color:white;

    font-size:20px;

    font-weight:bold;

    cursor:pointer;
}


/* =====================================================
   MAIN MENU
===================================================== */

#menu{

    position:fixed;
    inset:0;

    z-index:800;

    display:none;

    align-items:center;
    justify-content:center;

    background:
        radial-gradient(
            circle,
            #214b76,
            #0b182b 55%,
            #03060c
        );
}

.menuBox{

    width:550px;
    max-width:92%;

    padding:35px;

    text-align:center;

    border-radius:25px;

    background:rgba(5,13,27,.95);

    border:2px solid #28d9ff;

    box-shadow:
        0 0 30px #00cfff;
}

.menuBox h1{

    margin:0;

    font-size:48px;

    color:#65ecff;

    text-shadow:
        0 0 20px #00d9ff;
}

.menuBox h2{
    color:#ffd34d;
}

.menuBox p{
    color:#b9d6e9;
    line-height:1.6;
}

#languageSelect{

    width:85%;

    padding:13px;

    border-radius:10px;

    background:#10243c;

    color:white;

    border:1px solid #27d9ff;

    font-size:17px;
}


/* =====================================================
   TOP UI
===================================================== */

#ui{

    position:fixed;

    top:15px;
    left:15px;
    right:15px;

    z-index:20;

    display:none;

    justify-content:space-between;

    pointer-events:none;
}

.uiBox{

    padding:10px 18px;

    border-radius:12px;

    background:rgba(0,0,0,.65);

    border:1px solid rgba(85,220,255,.5);

    color:white;
}

#score{
    color:#ffd447;
    font-weight:bold;
}

#level{
    color:#50e6ff;
    font-weight:bold;
}


/* =====================================================
   PROFILE BUTTON
===================================================== */

#profileButton{

    position:fixed;

    top:65px;
    right:15px;

    z-index:50;

    display:none;

    padding:9px 14px;

    border-radius:10px;

    background:rgba(0,0,0,.65);

    border:1px solid #5ee8ff;

    color:white;

    cursor:pointer;
}


/* =====================================================
   WORD
===================================================== */

#wordPanel{

    position:fixed;

    left:50%;
    bottom:25px;

    transform:translateX(-50%);

    z-index:30;

    display:none;

    width:min(650px,92%);

    padding:16px;

    border-radius:18px;

    background:rgba(3,8,17,.97);

    border:2px solid #36ddff;

    box-shadow:
        0 0 30px rgba(0,200,255,.35);

    text-align:center;
}

#instruction{
    color:#8fdfff;
}

#nativeWord{

    margin-top:5px;

    color:#ffdd66;

    font-size:20px;
}

#wordDisplay{

    min-height:45px;

    margin-top:7px;

    font-size:31px;

    letter-spacing:8px;

    font-weight:bold;

    color:white;
}

#wordInput{

    width:90%;

    padding:12px;

    margin-top:10px;

    border-radius:9px;

    border:2px solid #35dfff;

    background:#071321;

    color:white;

    font-size:22px;

    text-align:center;

    outline:none;

    user-select:text;
}

#wordInput.error{
    border-color:#ff3b54;
}

#wordInput.correct{
    border-color:#4dff79;
}

#inputMessage{

    min-height:20px;

    margin-top:7px;
}

.messageGood{
    color:#5cff7b;
}

.messageBad{
    color:#ff5365;
}


/* =====================================================
   LEADERBOARD
===================================================== */

#leaderboard{

    position:fixed;

    inset:0;

    z-index:1100;

    display:none;

    align-items:center;
    justify-content:center;

    background:rgba(0,0,0,.85);
}

.leaderboardBox{

    width:650px;
    max-width:94%;
    max-height:85vh;

    overflow:auto;

    padding:25px;

    border-radius:20px;

    background:#071321;

    border:2px solid #ffd34d;

    box-shadow:
        0 0 40px rgba(255,190,30,.25);
}

.leaderboardBox h2{

    text-align:center;

    color:#ffe064;

    margin-top:0;
}

.rankRow{

    display:grid;

    grid-template-columns:
        60px 1fr 120px;

    gap:10px;

    align-items:center;

    padding:12px;

    margin-bottom:7px;

    border-radius:10px;

    background:#0d2034;

    color:white;
}

.rank{

    color:#ffd34d;

    font-weight:bold;

    text-align:center;
}

.rankName{
    overflow:hidden;
    text-overflow:ellipsis;
}

.rankScore{

    color:#5ce7ff;

    text-align:right;

    font-weight:bold;
}

.closeButton{

    width:100%;

    padding:12px;

    margin-top:15px;

    border:0;

    border-radius:10px;

    background:#263c52;

    color:white;

    font-size:16px;

    cursor:pointer;
}


/* =====================================================
   CENTER MESSAGE
===================================================== */

#message{

    position:fixed;

    inset:0;

    z-index:50;

    display:none;

    align-items:center;
    justify-content:center;

    pointer-events:none;
}

.messageText{

    font-size:70px;

    font-weight:bold;

    text-shadow:
        0 0 15px white,
        0 0 40px currentColor;
}


/* =====================================================
   VICTORY
===================================================== */

#victory{

    position:fixed;

    inset:0;

    z-index:200;

    display:none;

    align-items:center;
    justify-content:center;

    background:rgba(0,0,0,.82);
}

.victoryText{

    text-align:center;

    font-size:90px;

    color:#ffe45c;

    font-weight:bold;

    text-shadow:
        0 0 15px white,
        0 0 35px #ffba00,
        0 0 70px #ff4d00;
}

.victorySub{
    color:white;
    font-size:22px;
}


/* =====================================================
   GAME OVER
===================================================== */

#gameover{

    position:fixed;
    inset:0;

    z-index:250;

    display:none;

    align-items:center;
    justify-content:center;

    background:rgba(0,0,0,.85);

}

.gameoverBox{

    width:460px;
    max-width:92%;

    padding:35px;

    text-align:center;

    border-radius:25px;

    background:rgba(20,4,10,.97);

    border:2px solid #ff4c5e;

    box-shadow:
        0 0 40px rgba(255,60,80,.4);

}

.gameoverText{

    font-size:52px;

    font-weight:bold;

    color:#ff5468;

    text-shadow:
        0 0 15px #fff,
        0 0 35px #ff2038;

}

.gameoverSub{

    margin:12px 0 22px;

    color:#ffd9de;

    font-size:19px;

    line-height:1.6;

}

#gameoverScore{
    color:#ffd447;
    font-weight:bold;
}


/* =====================================================
   CONTROLS
===================================================== */

#controls{

    position:fixed;

    bottom:20px;
    left:20px;

    z-index:15;

    display:none;

    padding:10px 14px;

    border-radius:10px;

    background:rgba(0,0,0,.45);

    color:#b9dff0;

    font-size:13px;
}

@media(max-width:700px){

    .menuBox h1{
        font-size:35px;
    }

    .victoryText{
        font-size:55px;
    }

    #wordDisplay{
        font-size:22px;
        letter-spacing:5px;
    }

    #wordPanel{
        top:64px;
        bottom:auto;
        width:94%;
        padding:10px;
    }

    #ui{
        top:8px;
        left:8px;
        right:8px;
    }

    .uiBox{
        padding:6px 10px;
        font-size:12px;
    }

}


/* =====================================================
   BRIGHT THEME (OVERRIDE)
===================================================== */

html,body{
    background:#8fd3ff;
}

#loginScreen{
    background:
        linear-gradient(
            135deg,
            #a1c4fd 0%,
            #c2e9fb 45%,
            #fbc2eb 100%
        );
}

.loginBox{
    background:rgba(255,255,255,.96);
    border:3px solid #ff9ec4;
    box-shadow:
        0 14px 44px rgba(255,120,180,.35),
        inset 0 0 0 4px rgba(255,255,255,.6);
}

.loginBox h1{
    color:#ff5e9c;
    text-shadow:
        0 2px 0 #fff,
        0 0 18px rgba(255,120,180,.55);
}

.loginBox p{
    color:#4a5b72;
}

#profileScreen{
    background:
        linear-gradient(
            135deg,
            #fbc2eb,
            #a6c1ee
        );
}

.profileBox{
    background:rgba(255,255,255,.96);
    border:3px solid #ffc46b;
    box-shadow:0 14px 44px rgba(255,180,80,.4);
}

.profileBox h2{
    color:#ff8c42;
}

.profileBox p{
    color:#4a5b72;
}

#playerName,#accUser,#accPass,#accUser2,#accPass2,#accName2{
    background:#fff;
    color:#22303f;
    border:2px solid #7fd4ff;
}

#menu{
    background:
        linear-gradient(
            135deg,
            #84fab0 0%,
            #8fd3f4 50%,
            #a1c4fd 100%
        );
}

.menuBox{
    background:rgba(255,255,255,.96);
    border:3px solid #59d0ff;
    box-shadow:0 14px 44px rgba(60,180,255,.4);
}

.menuBox h1{
    color:#22b8ff;
    text-shadow:0 2px 0 #fff,0 0 18px rgba(40,180,255,.5);
}

.menuBox h2{
    color:#ff8c42;
}

.menuBox p{
    color:#43536b;
}

#languageSelect,#mapSelect{
    background:#fff;
    color:#22303f;
    border:2px solid #7fd4ff;
}

.uiBox{
    background:rgba(255,255,255,.9);
    border:2px solid #59d0ff;
    color:#1f3a52;
    font-weight:bold;
    box-shadow:0 4px 14px rgba(0,140,220,.25);
}

#score{ color:#ff7a00; }
#level{ color:#0aa5e0; }

#profileButton{
    background:rgba(255,255,255,.92);
    border:2px solid #ff9ec4;
    color:#ff5e9c;
    font-weight:bold;
}

#wordPanel{
    background:rgba(255,255,255,.97);
    border:3px solid #36ddff;
    box-shadow:0 12px 34px rgba(0,180,255,.35);
}

#instruction{ color:#2f8fbf; }
#nativeWord{ color:#ff8c42; }
#wordDisplay{ color:#1f3a52; }

#wordInput{
    background:#fff;
    color:#22303f;
    border:2px solid #35dfff;
}

#leaderboard{ background:rgba(30,60,90,.55); }

.leaderboardBox{
    background:#fff;
    border:3px solid #ffc46b;
    box-shadow:0 16px 50px rgba(255,180,80,.45);
}

.leaderboardBox h2{ color:#ff8c42; }

.rankRow{
    background:linear-gradient(135deg,#e8f7ff,#fff0f6);
    color:#22303f;
    border:1px solid #cfe9ff;
}

.rank{ color:#ff7a00; }
.rankScore{ color:#0aa5e0; }

.closeButton{
    background:linear-gradient(135deg,#74ebd5,#7fd4ff);
    color:#0b3d55;
    font-weight:bold;
}

#gameover{ background:rgba(60,20,40,.55); }

.gameoverBox{
    background:#fff;
    border:3px solid #ff7a92;
    box-shadow:0 16px 50px rgba(255,90,120,.45);
}

.gameoverText{
    color:#ff4d6d;
    text-shadow:0 2px 0 #fff,0 0 24px rgba(255,80,110,.5);
}

.gameoverSub{ color:#5a4048; }
#gameoverScore{ color:#ff7a00; }

#controls{
    background:rgba(255,255,255,.85);
    color:#2f6f8f;
    border:1px solid #9fe0ff;
}


/* =====================================================
   ACCOUNT FORM
===================================================== */

.accField{
    width:100%;
    padding:13px;
    margin-top:10px;
    border-radius:11px;
    border:2px solid #7fd4ff;
    background:#fff;
    color:#22303f;
    font-size:16px;
    text-align:center;
    outline:none;
    user-select:text;
}

.accTabs{
    display:flex;
    gap:8px;
    margin:8px 0 4px;
}

.accTab{
    flex:1;
    padding:10px;
    border:0;
    border-radius:10px;
    background:#e6f3ff;
    color:#3b6b8a;
    font-weight:bold;
    font-size:15px;
    cursor:pointer;
}

.accTab.active{
    background:linear-gradient(135deg,#ff9ec4,#ff5e9c);
    color:#fff;
}

.accMsg{
    min-height:22px;
    margin-top:10px;
    font-size:14px;
    color:#e0446a;
}

.linkRow{
    display:flex;
    gap:10px;
    margin-top:12px;
}

.linkRow .loginButton{
    margin-top:0;
}


/* =====================================================
   LOADING SCREEN
===================================================== */

#loadingScreen{
    position:fixed;
    inset:0;
    z-index:2000;
    display:flex;
    flex-direction:column;
    align-items:center;
    justify-content:center;
    background:
        linear-gradient(
            135deg,
            #84fab0,
            #8fd3f4 55%,
            #fbc2eb
        );
}

#loadTitle{
    font-size:44px;
    font-weight:bold;
    color:#fff;
    letter-spacing:2px;
    text-shadow:
        0 3px 0 rgba(0,120,180,.45),
        0 0 26px rgba(255,255,255,.8);
    margin-bottom:26px;
    animation:loadPulse 1.4s ease-in-out infinite;
}

@keyframes loadPulse{
    0%,100%{ transform:scale(1); }
    50%{ transform:scale(1.06); }
}

#loadBarOuter{
    width:min(420px,80%);
    height:26px;
    border-radius:14px;
    background:rgba(255,255,255,.55);
    border:3px solid #fff;
    box-shadow:0 6px 20px rgba(0,120,180,.3);
    overflow:hidden;
}

#loadBarFill{
    width:0%;
    height:100%;
    border-radius:11px;
    background:linear-gradient(90deg,#ff9ec4,#ffd166,#4dd0ff,#7CFC00);
    background-size:300% 100%;
    animation:barShift 1.6s linear infinite;
    transition:width .18s ease;
}

@keyframes barShift{
    0%{ background-position:0% 0; }
    100%{ background-position:300% 0; }
}

#loadPercent{
    margin-top:14px;
    font-size:20px;
    font-weight:bold;
    color:#0b5f86;
}


/* =====================================================
   WELCOME ANIMATION
===================================================== */

#welcomeOverlay{
    position:fixed;
    inset:0;
    z-index:1500;
    display:none;
    align-items:center;
    justify-content:center;
    pointer-events:none;
}

#welcomeBig{
    font-size:60px;
    font-weight:bold;
    color:#fff;
    text-align:center;
    padding:0 20px;
    text-shadow:
        0 4px 0 rgba(0,120,180,.5),
        0 0 30px rgba(255,255,255,.9),
        0 0 60px #ffd166;
    opacity:0;
    transform:scale(.3);
}

#welcomeBig.play{
    animation:welcomePop 1.8s ease forwards;
}

@keyframes welcomePop{
    0%{ opacity:0; transform:scale(.3); }
    35%{ opacity:1; transform:scale(1.15); }
    55%{ transform:scale(1); }
    80%{ opacity:1; transform:scale(1.05); }
    100%{ opacity:0; transform:scale(1.6); }
}


/* =====================================================
   MAP + SKIN PICKER
===================================================== */

.pickLabel{
    margin-top:16px;
    font-weight:bold;
    color:#2f6f8f;
}

#skinPicker{
    display:flex;
    gap:10px;
    justify-content:center;
    flex-wrap:wrap;
    margin-top:10px;
}

.skinCard{
    width:84px;
    padding:8px 4px;
    border-radius:14px;
    border:3px solid #cfe9ff;
    background:#f2fbff;
    cursor:pointer;
    text-align:center;
    font-size:12px;
    color:#3b6b8a;
    font-weight:bold;
    transition:transform .12s ease;
}

.skinCard canvas{
    width:56px;
    height:56px;
    display:block;
    margin:0 auto 4px;
}

.skinCard.sel{
    border-color:#ff5e9c;
    background:#fff0f6;
    transform:scale(1.06);
    box-shadow:0 6px 18px rgba(255,90,150,.4);
}

#mapPicker{
    display:flex;
    gap:10px;
    justify-content:center;
    flex-wrap:wrap;
    margin-top:10px;
}

.mapCard{
    width:96px;
    padding:8px 4px;
    border-radius:14px;
    border:3px solid #cfe9ff;
    background:#f2fbff;
    cursor:pointer;
    text-align:center;
    font-size:12px;
    color:#3b6b8a;
    font-weight:bold;
    transition:transform .12s ease;
}

.mapCard .swatch{
    width:100%;
    height:40px;
    border-radius:9px;
    margin-bottom:5px;
}

.mapCard.sel{
    border-color:#22b8ff;
    background:#eaf7ff;
    transform:scale(1.06);
    box-shadow:0 6px 18px rgba(40,180,255,.4);
}

@media(max-width:700px){
    #loadTitle{ font-size:30px; }
    #welcomeBig{ font-size:34px; }
    .skinCard{ width:70px; }
    .mapCard{ width:78px; }
}

</style>
</head>


<body>


<!-- =====================================================
     LOADING SCREEN
===================================================== -->

<div id="loadingScreen">

    <div id="loadTitle">🥚 EGG MONSTER 🐣</div>

    <div id="loadBarOuter">
        <div id="loadBarFill"></div>
    </div>

    <div id="loadPercent">0%</div>

</div>


<!-- =====================================================
     WELCOME ANIMATION
===================================================== -->

<div id="welcomeOverlay">
    <div id="welcomeBig"></div>
</div>


<!-- =====================================================
     LOGIN SCREEN
===================================================== -->

<div id="loginScreen">

    <div class="loginBox">

        <h1>EGG MONSTER</h1>

        <p>
            Đăng nhập, tạo tài khoản hoặc liên kết Facebook/Gmail.
        </p>

        <div class="accTabs">
            <button
                class="accTab active"
                id="tabLogin"
                onclick="switchToLogin()"
            >
                ĐĂNG NHẬP
            </button>
            <button
                class="accTab"
                id="tabRegister"
                onclick="switchToRegister()"
            >
                TẠO TÀI KHOẢN
            </button>
        </div>

        <!-- FORM ĐĂNG NHẬP -->
        <div id="loginForm">
            <input
                class="accField"
                id="accUser"
                maxlength="20"
                placeholder="Tên tài khoản"
                autocomplete="username"
            >
            <input
                class="accField"
                id="accPass"
                type="password"
                maxlength="30"
                placeholder="Mật khẩu"
                autocomplete="current-password"
            >
            <button
                class="loginButton guestButton"
                style="background:linear-gradient(135deg,#22b8ff,#5367ff)"
                onclick="loginAccount()"
            >
                🔑 ĐĂNG NHẬP
            </button>
        </div>

        <!-- FORM ĐĂNG KÝ -->
        <div id="registerForm" style="display:none">
            <input
                class="accField"
                id="accName2"
                maxlength="20"
                placeholder="Tên nhân vật"
            >
            <input
                class="accField"
                id="accUser2"
                maxlength="20"
                placeholder="Tên tài khoản (duy nhất)"
                autocomplete="username"
            >
            <input
                class="accField"
                id="accPass2"
                type="password"
                maxlength="30"
                placeholder="Mật khẩu (≥ 4 ký tự)"
                autocomplete="new-password"
            >
            <button
                class="loginButton guestButton"
                onclick="registerAccount()"
            >
                📝 ĐĂNG KÝ
            </button>
        </div>

        <div class="linkRow">
            <button
                class="loginButton googleButton"
                onclick="loginGoogle()"
            >
                ✉️ Gmail
            </button>
            <button
                class="loginButton facebookButton"
                onclick="loginFacebook()"
            >
                📘 Facebook
            </button>
        </div>

        <button
            class="loginButton guestButton"
            onclick="loginGuest()"
        >
            🎮 Chơi khách (không cần mạng)
        </button>

        <div id="loginStatus" class="accMsg"></div>

    </div>

</div>


<!-- =====================================================
     PLAYER NAME
===================================================== -->

<div id="profileScreen">

    <div class="profileBox">

        <h2>🎮 Tạo nhân vật</h2>

        <p>
            Hãy đặt tên cho nhân vật của bạn.
        </p>

        <input
            id="playerName"
            maxlength="20"
            placeholder="Tên nhân vật..."
        >

        <br>

        <button
            class="startButton"
            onclick="savePlayerName()"
        >
            TIẾP TỤC
        </button>

    </div>

</div>


<!-- =====================================================
     MENU
===================================================== -->

<div id="menu">

    <div class="menuBox">

        <h1>EGG MONSTER</h1>

        <h2>WORD HUNTER</h2>

        <p id="welcomeText"></p>

        <p>
            Chọn ngôn ngữ:
        </p>

        <select id="languageSelect">

            <option value="vi">
                🇻🇳 Tiếng Việt
            </option>

            <option value="en">
                🇬🇧 English
            </option>

            <option value="fr">
                🇫🇷 Français
            </option>

            <option value="de">
                🇩🇪 Deutsch
            </option>

            <option value="es">
                🇪🇸 Español
            </option>

            <option value="it">
                🇮🇹 Italiano
            </option>

            <option value="pt">
                🇵🇹 Português
            </option>

            <option value="ja">
                🇯🇵 日本語
            </option>

            <option value="ko">
                🇰🇷 한국어
            </option>

            <option value="zh">
                🇨🇳 中文
            </option>

        </select>

        <div class="pickLabel">🗺️ Chọn bản đồ</div>
        <div id="mapPicker">
            <div class="mapCard sel" data-map="forest" onclick="selectMap('forest')">
                <div class="swatch" style="background:linear-gradient(135deg,#7ed957,#2f8f4e)"></div>
                Khu rừng
            </div>
            <div class="mapCard" data-map="desert" onclick="selectMap('desert')">
                <div class="swatch" style="background:linear-gradient(135deg,#ffe08a,#e0a94f)"></div>
                Sa mạc
            </div>
            <div class="mapCard" data-map="temple" onclick="selectMap('temple')">
                <div class="swatch" style="background:linear-gradient(135deg,#d9c7a3,#9c7b4f)"></div>
                Đền thờ
            </div>
            <div class="mapCard" data-map="coast" onclick="selectMap('coast')">
                <div class="swatch" style="background:linear-gradient(135deg,#8ff0ff,#3aa0d0)"></div>
                Bờ biển
            </div>
        </div>

        <div class="pickLabel">🧑‍🎤 Chọn nhân vật</div>
        <div id="skinPicker">
            <div class="skinCard sel" data-skin="0" onclick="selectSkin(0)">
                <canvas width="56" height="56"></canvas>
                Mèo xanh
            </div>
            <div class="skinCard" data-skin="1" onclick="selectSkin(1)">
                <canvas width="56" height="56"></canvas>
                Nữ xanh
            </div>
            <div class="skinCard" data-skin="2" onclick="selectSkin(2)">
                <canvas width="56" height="56"></canvas>
                Nữ trắng
            </div>
            <div class="skinCard" data-skin="3" onclick="selectSkin(3)">
                <canvas width="56" height="56"></canvas>
                Hiệp sĩ
            </div>
        </div>

        <br>

        <button
            class="startButton"
            onclick="startGame()"
        >
            START GAME
        </button>

        <br><br>

        <button
            class="startButton"
            onclick="openLeaderboard()"
            style="
                background:
                linear-gradient(
                    135deg,
                    #ffb300,
                    #ff4d4d
                );
            "
        >
            🏆 BẢNG XẾP HẠNG
        </button>

        <p>
            W A S D = Di chuyển<br>
            SPACE = Đập trứng
        </p>

    </div>

</div>


<!-- =====================================================
     UI
===================================================== -->

<div id="ui">

    <div class="uiBox">

        LEVEL:
        <span id="level">1</span>

    </div>

    <div class="uiBox">

        HP:
        <span id="health">❤❤❤❤❤❤❤❤❤❤</span>

    </div>

    <div class="uiBox">

        SCORE:
        <span id="score">0</span>

    </div>

</div>


<button
    id="profileButton"
    onclick="openLeaderboard()"
>
    🏆 Ranking
</button>


<!-- =====================================================
     CANVAS
===================================================== -->

<canvas id="game"></canvas>


<!-- =====================================================
     WORD PANEL
===================================================== -->

<div id="wordPanel">

    <div id="instruction">
        Nhìn các chữ cái đã lộ và đoán từ còn thiếu
    </div>

    <div id="nativeWord"></div>

    <div id="wordDisplay"></div>

    <input
        id="wordInput"
        type="text"
        autocomplete="off"
        spellcheck="false"
        placeholder="Nhập các chữ còn thiếu..."
    >

    <div id="inputMessage"></div>

</div>


<!-- =====================================================
     MESSAGE
===================================================== -->

<div id="message">

    <div
        class="messageText"
        id="messageText"
    ></div>

</div>


<!-- =====================================================
     VICTORY
===================================================== -->

<div id="victory">

    <div class="victoryText">

        VICTORY!

        <div class="victorySub">
            🎉 Bạn đã hoàn thành 5 level!
        </div>

    </div>

</div>


<!-- =====================================================
     GAME OVER
===================================================== -->

<div id="gameover">

    <div class="gameoverBox">

        <div class="gameoverText">
            💀 THUA RỒI!
        </div>

        <div class="gameoverSub">
            Quái vật đã hạ gục bạn.<br>
            Điểm của bạn:
            <span id="gameoverScore">0</span>
        </div>

        <button
            class="startButton"
            onclick="restartGame()"
        >
            🔁 CHƠI LẠI
        </button>

        <br>

        <button
            class="startButton"
            onclick="backToMenu()"
            style="
                background:
                linear-gradient(
                    135deg,
                    #55606e,
                    #2b3442
                );
            "
        >
            🏠 VỀ MENU
        </button>

    </div>

</div>


<!-- =====================================================
     LEADERBOARD
===================================================== -->

<div id="leaderboard">

    <div class="leaderboardBox">

        <h2>
            🏆 BẢNG XẾP HẠNG ĐIỂM CAO
        </h2>

        <div id="rankingList">

            Đang tải...

        </div>

        <button
            class="closeButton"
            onclick="closeLeaderboard()"
        >
            ĐÓNG
        </button>

    </div>

</div>


<div id="controls">

    W A S D = Di chuyển
    &nbsp;|&nbsp;
    SPACE = Đập trứng

</div>


<div id="touchControls">

    <div id="joystickBase">
        <div id="joystickKnob"></div>
    </div>

    <div id="attackButton">
        ĐẬP<br>TRỨNG
    </div>

</div>



<!-- =====================================================
     FIREBASE
===================================================== -->

<script type="module">

/* =====================================================
   TRẠNG THÁI ĐĂNG NHẬP
===================================================== */

let firebaseReady = false;

let guestMode = false;

let currentUser = null;

let characterName = "";

let auth = null;

let db = null;

let googleProvider = null;

let facebookProvider = null;

let signInWithPopup = null;

let doc = null;

let getDoc = null;

let setDoc = null;

let collection = null;

let query = null;

let orderBy = null;

let limit = null;

let getDocs = null;


/* =====================================================
   TRẠNG THÁI GIAO DIỆN / GAME (MỚI)
===================================================== */

const TAU = Math.PI*2;

let currentSkin = 0;

let currentMap = "forest";

let usedWords = new Set();

let bullets = [];


/* =====================================================
   ÂM THANH (WEB AUDIO TỔNG HỢP)
===================================================== */

let audioCtx = null;


function ensureAudio(){

    if(!audioCtx){

        try{

            audioCtx =
                new (
                    window.AudioContext ||
                    window.webkitAudioContext
                )();

        }catch(e){

            audioCtx=null;

        }

    }


    if(
        audioCtx &&
        audioCtx.state==="suspended"
    ){

        audioCtx.resume();

    }


    return audioCtx;

}


function playTone(o){

    const ac=ensureAudio();

    if(!ac)return;


    const t0=ac.currentTime+(o.delay||0);

    const dur=o.dur||.15;

    const osc=ac.createOscillator();

    const g=ac.createGain();


    osc.type=o.type||"sine";

    osc.frequency.setValueAtTime(
        o.freq||440,
        t0
    );


    if(o.to){

        osc.frequency.exponentialRampToValueAtTime(
            Math.max(1,o.to),
            t0+dur
        );

    }


    g.gain.setValueAtTime(0,t0);

    g.gain.linearRampToValueAtTime(
        o.vol||.2,
        t0+.012
    );

    g.gain.exponentialRampToValueAtTime(
        .0001,
        t0+dur
    );


    osc.connect(g);

    g.connect(ac.destination);

    osc.start(t0);

    osc.stop(t0+dur+.03);

}


function playNoise(o){

    const ac=ensureAudio();

    if(!ac)return;


    const dur=o.dur||.2;

    const t0=ac.currentTime+(o.delay||0);

    const len=Math.max(
        1,
        Math.floor(ac.sampleRate*dur)
    );


    const buf=ac.createBuffer(1,len,ac.sampleRate);

    const data=buf.getChannelData(0);


    for(let i=0;i<len;i++){

        data[i]=
            (Math.random()*2-1)*(1-i/len);

    }


    const src=ac.createBufferSource();

    src.buffer=buf;


    const f=ac.createBiquadFilter();

    f.type=o.filter||"lowpass";

    f.frequency.value=o.freq||1000;


    const g=ac.createGain();

    g.gain.setValueAtTime(o.vol||.2,t0);

    g.gain.exponentialRampToValueAtTime(
        .0001,
        t0+dur
    );


    src.connect(f);

    f.connect(g);

    g.connect(ac.destination);

    src.start(t0);

    src.stop(t0+dur);

}


function sfxClick(){

    playTone({freq:720,to:1200,dur:.1,type:"triangle",vol:.16});

    playTone({freq:1250,dur:.07,type:"sine",vol:.09,delay:.06});

}


function sfxShoot(){

    playNoise({dur:.1,vol:.22,freq:2800,filter:"highpass"});

    playTone({freq:950,to:120,dur:.13,type:"sawtooth",vol:.15});

}


function sfxHammer(){

    playTone({freq:170,to:60,dur:.2,type:"sine",vol:.3});

    playNoise({dur:.09,vol:.18,freq:700});

}


function sfxCry(){

    playTone({freq:115,to:70,dur:.6,type:"sawtooth",vol:.15});

    playTone({freq:92,to:58,dur:.55,type:"square",vol:.06,delay:.05});

    playNoise({dur:.5,vol:.07,freq:520});

}


function sfxDeath(){

    playTone({freq:320,to:40,dur:.5,type:"sawtooth",vol:.2});

    playNoise({dur:.4,vol:.16,freq:900});

}


/*
   Tiếng "tách" đặc trưng mỗi khi bấm
   một nút bất kỳ ở ngoài sảnh.
*/

document.addEventListener(
"click",
e=>{

    const t=e.target;


    if(
        t.closest &&
        t.closest(
            "#loginScreen button,"+
            "#menu button,"+
            "#profileScreen button,"+
            "#leaderboard button,"+
            "#gameover button,"+
            ".mapCard,.skinCard,.accTab"
        )
    ){

        sfxClick();

    }

});


/* =====================================================
   TÀI KHOẢN LOCAL (OFFLINE)
===================================================== */

const ACC_KEY="emwh_accounts";

const SES_KEY="emwh_session";

let accountUser=null;


function loadAccounts(){

    try{

        return JSON.parse(
            localStorage.getItem(ACC_KEY)
        )||{};

    }catch(e){

        return {};

    }

}


function saveAccounts(a){

    try{

        localStorage.setItem(
            ACC_KEY,
            JSON.stringify(a)
        );

    }catch(e){}

}


function getSession(){

    try{

        return localStorage.getItem(SES_KEY);

    }catch(e){

        return null;

    }

}


function setSession(u){

    try{

        if(u)
            localStorage.setItem(SES_KEY,u);

        else
            localStorage.removeItem(SES_KEY);

    }catch(e){}

}


function persistSelection(){

    if(!accountUser)
        return;


    const accs=loadAccounts();


    if(!accs[accountUser])
        return;


    accs[accountUser].skin=currentSkin;

    accs[accountUser].map=currentMap;

    accs[accountUser].language=selectedLanguage;


    saveAccounts(accs);

}


function syncPickers(){

    document
        .querySelectorAll(".skinCard")
        .forEach(c=>{

            c.classList.toggle(
                "sel",
                +c.dataset.skin===currentSkin
            );

        });


    document
        .querySelectorAll(".mapCard")
        .forEach(c=>{

            c.classList.toggle(
                "sel",
                c.dataset.map===currentMap
            );

        });


    const lang=
        document.getElementById(
            "languageSelect"
        );


    if(lang)
        lang.value=selectedLanguage;

}


function enterGameAsUser(acc){

    characterName=
        acc.name||acc.username||"Bạn";


    currentSkin=acc.skin||0;

    currentMap=acc.map||"forest";

    selectedLanguage=acc.language||"vi";


    syncPickers();


    document.getElementById(
        "loginScreen"
    ).style.display="none";


    document.getElementById(
        "profileScreen"
    ).style.display="none";


    showMainMenu();

}


window.switchToLogin=function(){

    document.getElementById(
        "loginForm"
    ).style.display="block";

    document.getElementById(
        "registerForm"
    ).style.display="none";

    document.getElementById(
        "tabLogin"
    ).classList.add("active");

    document.getElementById(
        "tabRegister"
    ).classList.remove("active");

    document.getElementById(
        "loginStatus"
    ).textContent="";

};


window.switchToRegister=function(){

    document.getElementById(
        "loginForm"
    ).style.display="none";

    document.getElementById(
        "registerForm"
    ).style.display="block";

    document.getElementById(
        "tabRegister"
    ).classList.add("active");

    document.getElementById(
        "tabLogin"
    ).classList.remove("active");

    document.getElementById(
        "loginStatus"
    ).textContent="";

};


function accMsg(text){

    document.getElementById(
        "loginStatus"
    ).textContent=text;

}


window.registerAccount=function(){

    const name=
        document.getElementById("accName2")
            .value.trim();

    const user=
        document.getElementById("accUser2")
            .value.trim().toLowerCase();

    const pass=
        document.getElementById("accPass2").value;


    if(name.length<2){

        accMsg("Tên nhân vật ≥ 2 ký tự.");
        return;

    }


    if(user.length<3){

        accMsg("Tên tài khoản ≥ 3 ký tự.");
        return;

    }


    if(!/^[a-z0-9_.]+$/.test(user)){

        accMsg("Tài khoản chỉ gồm chữ/số/_ .");
        return;

    }


    if(pass.length<4){

        accMsg("Mật khẩu ≥ 4 ký tự.");
        return;

    }


    const accs=loadAccounts();


    if(accs[user]){

        accMsg("❌ Tên tài khoản đã tồn tại!");
        return;

    }


    accs[user]={

        name:name,

        username:user,

        password:pass,

        highScore:0,

        skin:0,

        map:"forest",

        language:"vi",

        createdAt:Date.now()

    };


    saveAccounts(accs);

    setSession(user);

    accountUser=user;

    accMsg("✅ Đăng ký thành công!");


    setTimeout(
        ()=>enterGameAsUser(accs[user]),
        400
    );

};


window.loginAccount=function(){

    const user=
        document.getElementById("accUser")
            .value.trim().toLowerCase();

    const pass=
        document.getElementById("accPass").value;


    const accs=loadAccounts();


    if(!accs[user]){

        accMsg("❌ Không tìm thấy tài khoản.");
        return;

    }


    if(accs[user].password!==pass){

        accMsg("❌ Sai mật khẩu.");
        return;

    }


    setSession(user);

    accountUser=user;

    accMsg("✅ Xin chào "+(accs[user].name||user)+"!");


    setTimeout(
        ()=>enterGameAsUser(accs[user]),
        400
    );

};


/* =====================================================
   MÀN HÌNH LOADING + CHÀO MỪNG
===================================================== */

function bootLoading(){

    renderSkinPreviews();


    const fill=
        document.getElementById("loadBarFill");

    const pct=
        document.getElementById("loadPercent");


    let p=0;


    const iv=setInterval(
        ()=>{

            p+=Math.random()*13+5;


            if(p>=100){

                p=100;

                clearInterval(iv);

                setTimeout(finishLoading,320);

            }


            fill.style.width=p+"%";

            pct.textContent=Math.floor(p)+"%";

        },
        130
    );

}


function finishLoading(){

    document.getElementById(
        "loadingScreen"
    ).style.display="none";


    const s=getSession();

    const accs=loadAccounts();


    if(s && accs[s]){

        accountUser=s;

        enterGameAsUser(accs[s]);

    }else{

        document.getElementById(
            "loginScreen"
        ).style.display="flex";

    }

}


function showWelcome(name){

    const ov=
        document.getElementById("welcomeOverlay");

    const big=
        document.getElementById("welcomeBig");


    big.textContent=
        "CHÀO MỪNG, "+
        (name||"").toUpperCase()+
        "!";


    ov.style.display="flex";

    big.classList.remove("play");


    void big.offsetWidth;


    big.classList.add("play");


    setTimeout(
        ()=>{

            ov.style.display="none";

            big.classList.remove("play");

        },
        1850
    );

}


/* =====================================================
   SKIN NHÂN VẬT
===================================================== */

window.selectSkin=function(n){

    currentSkin=n;

    syncPickers();

    persistSelection();

};


window.selectMap=function(m){

    currentMap=m;

    syncPickers();

    buildDecor(m);

    persistSelection();

};


function drawCharacter(c,cx,cy,s,skin){

    c.save();

    c.translate(cx,cy);

    c.scale(s,s);


    if(skin===1)
        drawSkinGirl(c,"#2b6fd6","#ffffff","#ffffff");

    else if(skin===2)
        drawSkinGirl(c,"#ffffff","#3aa0ff","#ffffff");

    else if(skin===3)
        drawSkinKnight(c);

    else
        drawSkinRobot(c);


    c.restore();

}


function drawSkinRobot(c){

    c.fillStyle="#1e9fd0";

    c.beginPath();
    c.arc(0,0,37,0,TAU);
    c.fill();


    c.fillStyle="#f5fbff";

    c.beginPath();
    c.arc(0,-2,29,0,TAU);
    c.fill();


    c.fillStyle="#1e9fd0";

    c.beginPath();
    c.arc(-24,-29,12,0,TAU);
    c.arc(24,-29,12,0,TAU);
    c.fill();


    c.fillStyle="#111";

    c.beginPath();
    c.arc(-9,-8,4,0,TAU);
    c.arc(9,-8,4,0,TAU);
    c.fill();


    c.fillStyle="#e63232";

    c.beginPath();
    c.arc(0,1,5,0,TAU);
    c.fill();

}


function drawSkinGirl(c,pants,shirt,sleeve){

    /* chân */
    c.fillStyle=pants;
    c.fillRect(-14,8,11,30);
    c.fillRect(3,8,11,30);


    /* giày */
    c.fillStyle="#5b3a29";
    c.fillRect(-15,36,13,8);
    c.fillRect(2,36,13,8);


    /* thân áo */
    c.fillStyle=shirt;
    c.fillRect(-16,-16,32,28);


    /* tay áo */
    c.fillStyle=sleeve;
    c.fillRect(-25,-14,9,26);
    c.fillRect(16,-14,9,26);


    /* bàn tay */
    c.fillStyle="#f2c9a0";
    c.beginPath();
    c.arc(-20,14,5,0,TAU);
    c.arc(21,14,5,0,TAU);
    c.fill();


    /* đầu */
    c.fillStyle="#f7d3b0";
    c.beginPath();
    c.arc(0,-30,16,0,TAU);
    c.fill();


    /* tóc */
    c.fillStyle="#5a3825";
    c.beginPath();
    c.arc(0,-33,17,Math.PI,0);
    c.fill();
    c.fillRect(-17,-33,5,22);
    c.fillRect(12,-33,5,22);


    /* mắt */
    c.fillStyle="#22303f";
    c.beginPath();
    c.arc(-6,-30,2.6,0,TAU);
    c.arc(6,-30,2.6,0,TAU);
    c.fill();


    /* miệng */
    c.strokeStyle="#c9736a";
    c.lineWidth=2;
    c.beginPath();
    c.arc(0,-25,5,.2,Math.PI-.2);
    c.stroke();

}


function drawSkinKnight(c){

    /* chân */
    c.fillStyle="#6b7280";
    c.fillRect(-14,8,11,30);
    c.fillRect(3,8,11,30);


    c.fillStyle="#4b5563";
    c.fillRect(-15,36,13,8);
    c.fillRect(2,36,13,8);


    /* giáp thân */
    c.fillStyle="#9aa4b2";
    c.fillRect(-17,-16,34,28);

    c.fillStyle="#c9d2de";
    c.fillRect(-17,-16,34,8);

    c.fillStyle="#ffcf4d";
    c.fillRect(-3,-14,6,24);


    /* tay */
    c.fillStyle="#8b95a3";
    c.fillRect(-26,-14,9,26);
    c.fillRect(17,-14,9,26);


    /* mũ sắt */
    c.fillStyle="#b7c0cd";
    c.beginPath();
    c.arc(0,-30,16,0,TAU);
    c.fill();


    c.fillStyle="#2b3442";
    c.fillRect(-12,-33,24,7);


    /* chóp lông */
    c.fillStyle="#ff4d6d";
    c.beginPath();
    c.moveTo(0,-48);
    c.lineTo(7,-30);
    c.lineTo(-7,-30);
    c.closePath();
    c.fill();

}


function renderSkinPreviews(){

    document
        .querySelectorAll(".skinCard")
        .forEach(card=>{

            const cv=card.querySelector("canvas");

            if(!cv)
                return;


            const c=cv.getContext("2d");

            c.clearRect(0,0,56,56);

            drawCharacter(
                c,
                28,
                30,
                .58,
                +card.dataset.skin
            );

        });

}


/* =====================================================
   ĐẠN (BẮN KHI GÕ CHỮ)
===================================================== */

function fireBullet(target){

    if(!target)
        return;


    bullets.push({

        x:player.x,

        y:player.y,

        target:target,

        speed:1100,

        alive:true

    });


    player.gunRecoil=.14;

    sfxShoot();

}


function updateBullets(dt){

    for(const b of bullets){

        if(!b.alive)
            continue;


        const t=b.target;


        if(!t || !t.alive){

            b.alive=false;

            continue;

        }


        const dx=t.x-b.x;

        const dy=t.y-b.y;

        const d=Math.sqrt(dx*dx+dy*dy);

        const step=b.speed*dt;


        if(d<=step){

            b.alive=false;

            t.hitFlash=.14;

            continue;

        }


        b.x+=dx/d*step;

        b.y+=dy/d*step;

    }


    bullets=bullets.filter(b=>b.alive);

}


function drawBullets(){

    for(const b of bullets){

        const x=b.x-cameraX;

        const y=b.y-cameraY;


        ctx.fillStyle="rgba(255,220,90,.5)";

        ctx.beginPath();
        ctx.arc(x,y,7,0,TAU);
        ctx.fill();


        ctx.fillStyle="#fff3a0";

        ctx.beginPath();
        ctx.arc(x,y,4,0,TAU);
        ctx.fill();

    }

}


/* =====================================================
   FIREBASE CONFIG
=====================================================

   BẠN PHẢI THAY BẰNG CONFIG CỦA BẠN.

===================================================== */

const firebaseConfig = {

    apiKey:
        "YOUR_API_KEY",

    authDomain:
        "YOUR_PROJECT.firebaseapp.com",

    projectId:
        "YOUR_PROJECT_ID",

    storageBucket:
        "YOUR_PROJECT.firebasestorage.app",

    messagingSenderId:
        "YOUR_MESSAGING_SENDER_ID",

    appId:
        "YOUR_APP_ID"

};


/* =====================================================
   NẠP FIREBASE ĐỘNG
=====================================================

   Chỉ tải Firebase khi người chơi bấm đăng nhập
   Google/Facebook. Chế độ khách chạy offline hoàn toàn
   và không bao giờ gọi hàm này.

===================================================== */

async function initFirebase(){

    if(firebaseReady)
        return true;

    try{

        const [appMod, authMod, fsMod] =
            await Promise.all([

                import(
                    "https://www.gstatic.com/firebasejs/11.0.2/firebase-app.js"
                ),

                import(
                    "https://www.gstatic.com/firebasejs/11.0.2/firebase-auth.js"
                ),

                import(
                    "https://www.gstatic.com/firebasejs/11.0.2/firebase-firestore.js"
                )

            ]);

        const app =
            appMod.initializeApp(
                firebaseConfig
            );

        auth =
            authMod.getAuth(app);

        db =
            fsMod.getFirestore(app);

        googleProvider =
            new authMod.GoogleAuthProvider();

        facebookProvider =
            new authMod.FacebookAuthProvider();

        signInWithPopup =
            authMod.signInWithPopup;

        doc = fsMod.doc;
        getDoc = fsMod.getDoc;
        setDoc = fsMod.setDoc;
        collection = fsMod.collection;
        query = fsMod.query;
        orderBy = fsMod.orderBy;
        limit = fsMod.limit;
        getDocs = fsMod.getDocs;

        firebaseReady = true;

        authMod.onAuthStateChanged(
            auth,
            async user => {

                if(user){

                    currentUser = user;

                    await loadPlayerProfile();

                }else{

                    currentUser = null;

                    characterName = "";

                }

            }
        );

        return true;

    }catch(error){

        console.error(error);

        return false;

    }

}


/* =====================================================
   GOOGLE LOGIN
===================================================== */

window.loginGoogle =
async function(){

    const status =
        document.getElementById(
            "loginStatus"
        );

    status.textContent =
        "Đang đăng nhập...";


    const ok =
        await initFirebase();


    if(!ok){

        status.textContent =
            "Không kết nối được Firebase. Hãy chọn \"Chơi khách\".";

        return;

    }


    try{

        const result =
            await signInWithPopup(
                auth,
                googleProvider
            );


        currentUser =
            result.user;


        guestMode=false;

        await loadPlayerProfile();


    }catch(error){

        console.error(error);

        status.textContent =
            "Đăng nhập Google thất bại.";

    }

};


/* =====================================================
   FACEBOOK LOGIN
===================================================== */

window.loginFacebook =
async function(){

    const status =
        document.getElementById(
            "loginStatus"
        );

    status.textContent =
        "Đang đăng nhập...";


    const ok =
        await initFirebase();


    if(!ok){

        status.textContent =
            "Không kết nối được Firebase. Hãy chọn \"Chơi khách\".";

        return;

    }


    try{

        const result =
            await signInWithPopup(
                auth,
                facebookProvider
            );


        currentUser =
            result.user;


        guestMode=false;

        await loadPlayerProfile();


    }catch(error){

        console.error(error);

        status.textContent =
            "Đăng nhập Facebook thất bại.";

    }

};


/* =====================================================
   GUEST LOGIN (OFFLINE)
=====================================================

   Không dùng Firebase. Chỉ cần đặt tên nhân vật
   rồi vào menu chơi.

===================================================== */

window.loginGuest =
function(){

    guestMode = true;

    currentUser = null;

    accountUser = null;

    setSession(null);

    document.getElementById(
        "loginScreen"
    ).style.display =
        "none";

    document.getElementById(
        "profileScreen"
    ).style.display =
        "flex";

};


/* =====================================================
   LOAD PROFILE
===================================================== */

async function loadPlayerProfile(){

    const ref =
        doc(
            db,
            "players",
            currentUser.uid
        );


    const snap =
        await getDoc(ref);


    if(snap.exists()){

        const data =
            snap.data();


        characterName =
            data.characterName ||
            "";


        document.getElementById(
            "loginScreen"
        ).style.display =
            "none";


        document.getElementById(
            "profileScreen"
        ).style.display =
            "none";


        showMainMenu();


    }else{

        document.getElementById(
            "loginScreen"
        ).style.display =
            "none";


        document.getElementById(
            "profileScreen"
        ).style.display =
            "flex";

    }

}


/* =====================================================
   SAVE CHARACTER NAME
===================================================== */

window.savePlayerName =
async function(){

    const input =
        document.getElementById(
            "playerName"
        );


    let name =
        input.value.trim();


    if(name.length < 2){

        alert(
            "Tên nhân vật phải có ít nhất 2 ký tự."
        );

        return;

    }


    if(name.length > 20){

        alert(
            "Tên nhân vật tối đa 20 ký tự."
        );

        return;

    }


    characterName =
        name;


    if(!guestMode && currentUser){

        await setDoc(

            doc(
                db,
                "players",
                currentUser.uid
            ),

            {

                characterName:
                    characterName,

                email:
                    currentUser.email || "",

                photoURL:
                    currentUser.photoURL || "",

                highScore:
                    0,

                updatedAt:
                    Date.now()

            },

            {
                merge:true
            }

        );

    }


    document.getElementById(
        "profileScreen"
    ).style.display =
        "none";


    showMainMenu();

};


/* =====================================================
   SHOW MENU
===================================================== */

function showMainMenu(){

    document.getElementById(
        "welcomeText"
    ).textContent =
        "Xin chào, " +
        characterName +
        "!";


    document.getElementById(
        "menu"
    ).style.display =
        "flex";


    document.getElementById(
        "profileButton"
    ).style.display =
        "block";

}


/* =====================================================
   SAVE HIGH SCORE
===================================================== */

window.saveHighScore =
async function(){

    /*
       Tài khoản local (offline): lưu
       điểm cao nhất vào localStorage.
    */

    if(accountUser){

        const accs=loadAccounts();

        const acc=accs[accountUser];

        if(acc && score>(acc.highScore||0)){

            acc.highScore=score;

            acc.name=characterName;

            saveAccounts(accs);

        }

    }


    if(!currentUser)
        return;


    const ref =
        doc(
            db,
            "players",
            currentUser.uid
        );


    const snap =
        await getDoc(ref);


    let oldScore = 0;


    if(snap.exists()){

        oldScore =
            snap.data().highScore || 0;

    }


    /*
       Chỉ ghi nếu điểm mới cao hơn
       điểm cũ.
    */

    if(score > oldScore){

        await setDoc(

            ref,

            {

                characterName:
                    characterName,

                highScore:
                    score,

                updatedAt:
                    Date.now()

            },

            {
                merge:true
            }

        );

    }

};


/* =====================================================
   LEADERBOARD
===================================================== */

window.openLeaderboard =
async function(){

    document.getElementById(
        "leaderboard"
    ).style.display =
        "flex";


    await loadLeaderboard();

};


window.closeLeaderboard =
function(){

    document.getElementById(
        "leaderboard"
    ).style.display =
        "none";

};


/* =====================================================
   LOAD LEADERBOARD
===================================================== */

function renderLocalLeaderboard(container){

    const accs=loadAccounts();

    const rows=
        Object.values(accs)
            .map(a=>({
                name:a.name||a.username,
                score:a.highScore||0
            }))
            .sort((a,b)=>b.score-a.score)
            .slice(0,100);


    if(rows.length===0){

        container.innerHTML=
            "Chưa có người chơi nào.<br><br>"+
            "Tạo tài khoản để lưu điểm và "+
            "xuất hiện trên bảng xếp hạng.";

        return;

    }


    container.innerHTML="";


    rows.forEach((r,i)=>{

        const row=document.createElement("div");

        row.className="rankRow";


        const rank=document.createElement("div");

        rank.className="rank";
        rank.textContent="#"+(i+1);


        const name=document.createElement("div");

        name.className="rankName";
        name.textContent=r.name;


        const sc=document.createElement("div");

        sc.className="rankScore";
        sc.textContent=r.score;


        row.appendChild(rank);
        row.appendChild(name);
        row.appendChild(sc);

        container.appendChild(row);

    });

}


async function loadLeaderboard(){

    const container =
        document.getElementById(
            "rankingList"
        );


    if(guestMode || !db){

        renderLocalLeaderboard(container);

        return;

    }


    container.innerHTML =
        "⏳ Đang tải bảng xếp hạng...";


    try{

        /*
           Sắp xếp điểm từ cao xuống thấp.
        */

        const rankingQuery =
            query(

                collection(
                    db,
                    "players"
                ),

                orderBy(
                    "highScore",
                    "desc"
                ),

                limit(100)

            );


        const snapshot =
            await getDocs(
                rankingQuery
            );


        container.innerHTML =
            "";


        if(snapshot.empty){

            container.innerHTML =
                "Chưa có người chơi.";

            return;

        }


        let rank = 1;


        snapshot.forEach(
            documentSnapshot => {

                const data =
                    documentSnapshot.data();


                const row =
                    document.createElement(
                        "div"
                    );


                row.className =
                    "rankRow";


                const rankElement =
                    document.createElement(
                        "div"
                    );


                rankElement.className =
                    "rank";


                rankElement.textContent =
                    "#" + rank;


                const nameElement =
                    document.createElement(
                        "div"
                    );


                nameElement.className =
                    "rankName";


                nameElement.textContent =
                    data.characterName ||
                    "Player";


                const scoreElement =
                    document.createElement(
                        "div"
                    );


                scoreElement.className =
                    "rankScore";


                scoreElement.textContent =
                    (
                        data.highScore || 0
                    ) +
                    " điểm";


                row.appendChild(
                    rankElement
                );

                row.appendChild(
                    nameElement
                );

                row.appendChild(
                    scoreElement
                );


                container.appendChild(
                    row
                );


                rank++;

            }
        );


    }catch(error){

        console.error(error);


        container.innerHTML =
            `
            Không thể tải bảng xếp hạng.
            <br><br>
            Kiểm tra Firestore Rules
            và Firebase configuration.
            `;

    }

}


/* =====================================================
   GAME OVER / VICTORY HOOK
=====================================================

   Các hàm game bên dưới sẽ gọi:

       saveHighScore();

   khi người chơi hoàn thành game
   hoặc khi cần lưu điểm.

===================================================== */

window.firebaseReady = true;


/* =====================================================
   CANVAS GAME
===================================================== */

const canvas =
    document.getElementById(
        "game"
    );

const ctx =
    canvas.getContext("2d");


function resizeCanvas(){

    canvas.width =
        window.innerWidth;

    canvas.height =
        window.innerHeight;

}

resizeCanvas();

window.addEventListener(
    "resize",
    resizeCanvas
);


/* =====================================================
   GAME VARIABLES
===================================================== */

let gameRunning = false;

let level = 1;

let score = 0;

let selectedLanguage = "vi";

let eggsDestroyed = 0;

let infiniteMode = false;

let activeMonster = null;

let cameraX = 0;

let cameraY = 0;

let lastTime = 0;

const MAX_HEALTH = 10;

const keys = {};

let touchDX = 0;

let touchDY = 0;


const LEVEL_SPEED = {

    1:20,
    2:30,
    3:50,
    4:70,
    5:100,
    6:150

};


/* =====================================================
   WORD DATABASE
===================================================== */

const WORD_DATABASE = {

vi:[
["MÁY TÍNH","MAYTINH"],
["QUÁI VẬT","QUAIVAT"],
["TRÒ CHƠI","TROCHOI"],
["PHIÊU LƯU","PHIEULUU"],
["KHỦNG LONG","KHUNGLONG"],
["BẠN BÈ","BANBE"],
["MẶT TRỜI","MATTROI"],
["CHIẾN BINH","CHIENBINH"],
["KHO BÁU","KHOBAU"],
["NGÔI SAO","NGOISAO"],
["DÒNG SÔNG","DONGSONG"],
["NGỌN NÚI","NGONNUI"],
["CÁNH RỪNG","CANHRUNG"],
["ĐẠI DƯƠNG","DAIDUONG"],
["BẦU TRỜI","BAUTROI"],
["THÀNH PHỐ","THANHPHO"],
["NGÔI NHÀ","NGOINHA"],
["TRƯỜNG HỌC","TRUONGHOC"],
["SỨC MẠNH","SUCMANH"],
["ÁNH SÁNG","ANHSANG"],
["BÓNG TỐI","BONGTOI"],
["NIỀM VUI","NIEMVUI"],
["GIA ĐÌNH","GIADINH"],
["THẦY GIÁO","THAYGIAO"],
["HỌC SINH","HOCSINH"],
["QUYỂN SÁCH","QUYENSACH"],
["CÂY BÚT","CAYBUT"],
["CON MÈO","CONMEO"],
["CON CHÓ","CONCHO"],
["BÔNG HOA","BONGHOA"],
["LÁ CÂY","LACAY"],
["TRÁI TIM","TRAITIM"],
["ĐÔI CÁNH","DOICANH"],
["NGỌN LỬA","NGONLUA"],
["GIỌT NƯỚC","GIOTNUOC"],
["CÁNH ĐỒNG","CANHDONG"],
["HÒN ĐẢO","HONDAO"],
["CẦU VỒNG","CAUVONG"],
["THẦN THOẠI","THANTHOAI"],
["DŨNG CẢM","DUNGCAM"]
],

en:[
["MONSTER","MONSTER"],
["COMPUTER","COMPUTER"],
["FRIEND","FRIEND"],
["ADVENTURE","ADVENTURE"],
["DRAGON","DRAGON"],
["FOREST","FOREST"],
["WARRIOR","WARRIOR"],
["TREASURE","TREASURE"],
["CASTLE","CASTLE"],
["KINGDOM","KINGDOM"],
["MAGIC","MAGIC"],
["SHIELD","SHIELD"],
["SWORD","SWORD"],
["HERO","HERO"],
["VILLAGE","VILLAGE"],
["MOUNTAIN","MOUNTAIN"],
["RIVER","RIVER"],
["OCEAN","OCEAN"],
["DESERT","DESERT"],
["ISLAND","ISLAND"],
["PYRAMID","PYRAMID"],
["ROBOT","ROBOT"],
["ROCKET","ROCKET"],
["PLANET","PLANET"],
["GALAXY","GALAXY"],
["STAR","STAR"],
["MOON","MOON"],
["THUNDER","THUNDER"],
["LIGHTNING","LIGHTNING"],
["STORM","STORM"],
["SHADOW","SHADOW"],
["SPIRIT","SPIRIT"],
["GOBLIN","GOBLIN"],
["WIZARD","WIZARD"],
["KNIGHT","KNIGHT"],
["PRINCESS","PRINCESS"],
["EMPEROR","EMPEROR"],
["PHOENIX","PHOENIX"],
["UNICORN","UNICORN"],
["LEGEND","LEGEND"]
],

fr:[
["MONSTRE","MONSTRE"],
["ORDINATEUR","ORDINATEUR"],
["AMI","AMI"],
["AVENTURE","AVENTURE"],
["DRAGON","DRAGON"],
["SOLEIL","SOLEIL"],
["FORÊT","FORET"],
["GUERRIER","GUERRIER"],
["TRÉSOR","TRESOR"],
["CHÂTEAU","CHATEAU"],
["ÉTOILE","ETOILE"],
["LUNE","LUNE"],
["MONTAGNE","MONTAGNE"],
["RIVIÈRE","RIVIERE"],
["OCÉAN","OCEAN"],
["CHEVALIER","CHEVALIER"],
["MAGIE","MAGIE"],
["ÉPÉE","EPEE"],
["BOUCLIER","BOUCLIER"],
["ROYAUME","ROYAUME"],
["VILLAGE","VILLAGE"],
["SORCIER","SORCIER"],
["PRINCESSE","PRINCESSE"],
["ESPRIT","ESPRIT"],
["OMBRE","OMBRE"],
["TEMPÊTE","TEMPETE"],
["ÉCLAIR","ECLAIR"],
["PHÉNIX","PHENIX"],
["LÉGENDE","LEGENDE"],
["HÉROS","HEROS"]
],

de:[
["MONSTER","MONSTER"],
["COMPUTER","COMPUTER"],
["FREUND","FREUND"],
["ABENTEUER","ABENTEUER"],
["DRACHE","DRACHE"],
["SONNE","SONNE"],
["WALD","WALD"],
["KRIEGER","KRIEGER"],
["SCHATZ","SCHATZ"],
["SCHLOSS","SCHLOSS"],
["STERN","STERN"],
["MOND","MOND"],
["BERG","BERG"],
["FLUSS","FLUSS"],
["MEER","MEER"],
["RITTER","RITTER"],
["MAGIE","MAGIE"],
["SCHWERT","SCHWERT"],
["SCHILD","SCHILD"],
["KÖNIGREICH","KONIGREICH"],
["DORF","DORF"],
["ZAUBERER","ZAUBERER"],
["PRINZESSIN","PRINZESSIN"],
["GEIST","GEIST"],
["SCHATTEN","SCHATTEN"],
["STURM","STURM"],
["BLITZ","BLITZ"],
["HELD","HELD"],
["LEGEND","LEGEND"],
["FEUER","FEUER"]
],

es:[
["MONSTRUO","MONSTRUO"],
["ORDENADOR","ORDENADOR"],
["AMIGO","AMIGO"],
["AVENTURA","AVENTURA"],
["DRAGÓN","DRAGON"],
["BOSQUE","BOSQUE"],
["GUERRERO","GUERRERO"],
["TESORO","TESORO"],
["CASTILLO","CASTILLO"],
["ESTRELLA","ESTRELLA"],
["LUNA","LUNA"],
["SOL","SOL"],
["MONTAÑA","MONTANA"],
["RÍO","RIO"],
["OCÉANO","OCEANO"],
["CABALLERO","CABALLERO"],
["MAGIA","MAGIA"],
["ESPADA","ESPADA"],
["ESCUDO","ESCUDO"],
["REINO","REINO"],
["PUEBLO","PUEBLO"],
["HECHICERO","HECHICERO"],
["PRINCESA","PRINCESA"],
["ESPÍRITU","ESPIRITU"],
["SOMBRA","SOMBRA"],
["TORMENTA","TORMENTA"],
["RELÁMPAGO","RELAMPAGO"],
["FÉNIX","FENIX"],
["LEYENDA","LEYENDA"],
["HÉROE","HEROE"]
],

it:[
["MOSTRO","MOSTRO"],
["COMPUTER","COMPUTER"],
["AMICO","AMICO"],
["AVVENTURA","AVVENTURA"],
["DRAGO","DRAGO"],
["SOLE","SOLE"],
["FORESTA","FORESTA"],
["GUERRIERO","GUERRIERO"],
["TESORO","TESORO"],
["CASTELLO","CASTELLO"],
["STELLA","STELLA"],
["LUNA","LUNA"],
["MONTAGNA","MONTAGNA"],
["FIUME","FIUME"],
["OCEANO","OCEANO"],
["CAVALIERE","CAVALIERE"],
["MAGIA","MAGIA"],
["SPADA","SPADA"],
["SCUDO","SCUDO"],
["REGNO","REGNO"],
["VILLAGGIO","VILLAGGIO"],
["STREGONE","STREGONE"],
["PRINCIPESSA","PRINCIPESSA"],
["SPIRITO","SPIRITO"],
["OMBRA","OMBRA"],
["TEMPESTA","TEMPESTA"],
["FULMINE","FULMINE"],
["FENICE","FENICE"],
["LEGGENDA","LEGGENDA"],
["EROE","EROE"]
],

pt:[
["MONSTRO","MONSTRO"],
["COMPUTADOR","COMPUTADOR"],
["AMIGO","AMIGO"],
["AVENTURA","AVENTURA"],
["DRAGÃO","DRAGAO"],
["FLORESTA","FLORESTA"],
["GUERREIRO","GUERREIRO"],
["TESOURO","TESOURO"],
["CASTELO","CASTELO"],
["ESTRELA","ESTRELA"],
["LUA","LUA"],
["SOL","SOL"],
["MONTANHA","MONTANHA"],
["RIO","RIO"],
["OCEANO","OCEANO"],
["CAVALEIRO","CAVALEIRO"],
["MAGIA","MAGIA"],
["ESPADA","ESPADA"],
["ESCUDO","ESCUDO"],
["REINO","REINO"],
["VILA","VILA"],
["FEITICEIRO","FEITICEIRO"],
["PRINCESA","PRINCESA"],
["ESPÍRITO","ESPIRITO"],
["SOMBRA","SOMBRA"],
["TEMPESTADE","TEMPESTADE"],
["RELÂMPAGO","RELAMPAGO"],
["FÊNIX","FENIX"],
["LENDA","LENDA"],
["HERÓI","HEROI"]
],

ja:[
["未来","MIRAI"],
["友達","TOMODACHI"],
["桜","SAKURA"],
["冒険","BOUKEN"],
["宝物","TAKARAMONO"],
["龍","RYU"],
["森","MORI"],
["勇者","YUUSHA"],
["怪物","KAIBUTSU"],
["太陽","TAIYOU"],
["月","TSUKI"],
["星","HOSHI"],
["海","UMI"],
["山","YAMA"],
["川","KAWA"],
["花","HANA"],
["風","KAZE"],
["火","HI"],
["水","MIZU"],
["空","SORA"],
["夢","YUME"],
["光","HIKARI"],
["刀","KATANA"],
["侍","SAMURAI"],
["忍者","NINJA"]
],

ko:[
["친구","CHINGU"],
["미래","MIRAE"],
["게임","GEIM"],
["용","YONG"],
["보물","BOMUL"],
["전사","JEONSA"],
["숲","SUP"],
["태양","TAEYANG"],
["모험","MOHEOM"],
["별","BYEOL"],
["달","DAL"],
["바다","BADA"],
["산","SAN"],
["강","GANG"],
["꽃","KKOT"],
["바람","BARAM"],
["불","BUL"],
["물","MUL"],
["꿈","KKUM"],
["빛","BIT"],
["기사","GISA"],
["성","SEONG"],
["마법","MABEOP"],
["영웅","YEONGUNG"],
["왕","WANG"]
],

zh:[
["朋友","PENGYOU"],
["未来","WEILAI"],
["游戏","YOUXI"],
["龙","LONG"],
["宝物","BAOWU"],
["森林","SENLIN"],
["战士","ZHANSHI"],
["太阳","TAIYANG"],
["冒险","MAOXIAN"],
["星星","XINGXING"],
["月亮","YUELIANG"],
["海洋","HAIYANG"],
["山","SHAN"],
["河","HE"],
["花","HUA"],
["风","FENG"],
["火","HUO"],
["水","SHUI"],
["天空","TIANKONG"],
["梦","MENG"],
["光","GUANG"],
["剑","JIAN"],
["英雄","YINGXIONG"],
["国王","GUOWANG"],
["魔法","MOFA"]
]

};


/* =====================================================
   WORLD
===================================================== */

const WORLD_WIDTH =
    2400;

const WORLD_HEIGHT =
    1300;


/* =====================================================
   PLAYER
===================================================== */

const player = {

    x:300,

    y:600,

    speed:260,

    size:40,

    hammerTimer:0,

    gunRecoil:0,

    health:MAX_HEALTH,

    invulnTimer:0,

    regenTimer:0

};


/* =====================================================
   EGGS
===================================================== */

let eggs=[];


function createEggs(){

    eggs=[

        {x:600,y:300,alive:true},

        {x:1000,y:300,alive:true},

        {x:1500,y:350,alive:true},

        {x:800,y:850,alive:true},

        {x:1500,y:800,alive:true}

    ];

}


/* =====================================================
   MONSTERS
===================================================== */

let monsters=[];


/* =====================================================
   NORMALIZE
===================================================== */

function normalizeText(text){

    return text
        .normalize("NFD")
        .replace(/[\u0300-\u036f]/g,"")
        .replace(/Đ/g,"D")
        .replace(/đ/g,"d")
        .replace(/[^A-Za-z]/g,"")
        .toUpperCase();

}


/* =====================================================
   CHOOSE WORD
===================================================== */

function chooseWord(){

    const list =
        WORD_DATABASE[
            selectedLanguage
        ];


    /*
       Loại bỏ các từ đã gặp để không
       bao giờ lặp lại từ cũ.
    */

    let pool =
        list.filter(
            it=>!usedWords.has(it[1])
        );


    if(pool.length===0){

        usedWords.clear();

        pool=list.slice();

    }


    /*
       Điểm càng cao → từ càng dài/khó.
       Sắp xếp theo độ dài rồi chọn dải
       phù hợp với bậc điểm hiện tại.
    */

    pool.sort(
        (a,b)=>a[1].length-b[1].length
    );


    const n=pool.length;

    const tier =
        score<150 ? 0 :
        score<400 ? 1 :
        score<800 ? 2 :
        3;


    let start,end;

    if(tier===0){
        start=0;
        end=Math.max(1,Math.floor(n*.45));
    }else if(tier===1){
        start=Math.floor(n*.25);
        end=Math.max(start+1,Math.floor(n*.7));
    }else if(tier===2){
        start=Math.floor(n*.5);
        end=Math.max(start+1,Math.floor(n*.9));
    }else{
        start=Math.floor(n*.65);
        end=n;
    }


    end=Math.min(end,n);

    if(end<=start)
        end=start+1;


    const idx=
        start+
        Math.floor(
            Math.random()*(end-start)
        );


    const item=
        pool[Math.min(idx,n-1)];


    usedWords.add(item[1]);


    return {

        display:item[0],

        answer:item[1]

    };

}


/* =====================================================
   CREATE PUZZLE
===================================================== */

function createPuzzle(word){

    const chars =
        word.answer.split("");

    let percent =
        level===1 ? .35 :
        level===2 ? .40 :
        level===3 ? .50 :
        level===4 ? .60 :
        .65;


    let count =
        Math.floor(
            chars.length*percent
        );


    count =
        Math.max(
            1,
            Math.min(
                chars.length-1,
                count
            )
        );


    const indexes=[];


    for(
        let i=0;
        i<chars.length;
        i++
    ){

        indexes.push(i);

    }


    for(
        let i=indexes.length-1;
        i>0;
        i--
    ){

        const j =
            Math.floor(
                Math.random()*(i+1)
            );

        [
            indexes[i],
            indexes[j]
        ] =
        [
            indexes[j],
            indexes[i]
        ];

    }


    const hidden =
        indexes
        .slice(0,count)
        .sort(
            (a,b)=>a-b
        );


    const hiddenSet =
        new Set(hidden);


    let pattern="";


    for(
        let i=0;
        i<chars.length;
        i++
    ){

        pattern +=
            hiddenSet.has(i)
            ? "_"
            : chars[i];

    }


    return {

        answer:word.answer,

        pattern:pattern,

        hiddenPositions:hidden,

        typed:""

    };

}


/* =====================================================
   START GAME
===================================================== */

window.startGame =
function(){

    selectedLanguage =
        document.getElementById(
            "languageSelect"
        ).value;


    bullets=[];

    usedWords.clear();

    buildDecor(currentMap);

    persistSelection();


    gameRunning=true;

    level=1;

    score=0;

    eggsDestroyed=0;

    infiniteMode=false;

    monsters=[];

    activeMonster=null;

    player.x=300;

    player.y=600;

    player.health=MAX_HEALTH;

    player.invulnTimer=0;

    player.regenTimer=0;

    createEggs();

    document.getElementById(
        "menu"
    ).style.display="none";

    document.getElementById(
        "gameover"
    ).style.display="none";

    document.getElementById(
        "ui"
    ).style.display="flex";

    document.getElementById(
        "controls"
    ).style.display="block";


    if(isTouchDevice){

        touchControls.style.display="block";

    }


    updateUI();

    showWelcome(characterName);

    lastTime =
        performance.now();

    requestAnimationFrame(
        gameLoop
    );

};


/* =====================================================
   KEYBOARD
===================================================== */

window.addEventListener(
"keydown",
e=>{

    keys[
        e.key.toLowerCase()
    ]=true;


    if(
        e.code==="Space"
    ){

        e.preventDefault();

        attackEgg();

    }

});


window.addEventListener(
"keyup",
e=>{

    keys[
        e.key.toLowerCase()
    ]=false;

});


/* =====================================================
   TOUCH CONTROLS (MOBILE)
===================================================== */

const isTouchDevice =
    ("ontouchstart" in window) ||
    navigator.maxTouchPoints>0;


if(isTouchDevice){

    document.body.classList.add("touch");

}


const joystickBase =
    document.getElementById("joystickBase");

const joystickKnob =
    document.getElementById("joystickKnob");

const attackButton =
    document.getElementById("attackButton");

const touchControls =
    document.getElementById("touchControls");


let joystickTouchId = null;

const JOYSTICK_RADIUS = 48;


function joystickUpdate(touch){

    const rect =
        joystickBase.getBoundingClientRect();

    const cx =
        rect.left+rect.width/2;

    const cy =
        rect.top+rect.height/2;

    let dx =
        touch.clientX-cx;

    let dy =
        touch.clientY-cy;

    const dist =
        Math.sqrt(dx*dx+dy*dy);


    if(dist>JOYSTICK_RADIUS){

        dx = dx/dist*JOYSTICK_RADIUS;
        dy = dy/dist*JOYSTICK_RADIUS;

    }


    joystickKnob.style.transform =
        "translate("+dx+"px,"+dy+"px)";


    touchDX = dx/JOYSTICK_RADIUS;
    touchDY = dy/JOYSTICK_RADIUS;

}


function joystickReset(){

    joystickTouchId=null;

    joystickKnob.style.transform =
        "translate(0px,0px)";

    touchDX=0;
    touchDY=0;

}


joystickBase.addEventListener(
"touchstart",
e=>{

    e.preventDefault();

    const touch =
        e.changedTouches[0];

    joystickTouchId =
        touch.identifier;

    joystickUpdate(touch);

},
{passive:false}
);


joystickBase.addEventListener(
"touchmove",
e=>{

    e.preventDefault();

    for(
        const touch of e.changedTouches
    ){

        if(
            touch.identifier===
            joystickTouchId
        ){

            joystickUpdate(touch);

        }

    }

},
{passive:false}
);


joystickBase.addEventListener(
"touchend",
e=>{

    e.preventDefault();
    joystickReset();

},
{passive:false}
);


joystickBase.addEventListener(
"touchcancel",
e=>{

    e.preventDefault();
    joystickReset();

},
{passive:false}
);


attackButton.addEventListener(
"touchstart",
e=>{

    e.preventDefault();

    if(gameRunning){

        attackEgg();

    }

},
{passive:false}
);


/*
   Ngăn trang cuộn / phóng to khi
   chạm vào vùng game trên điện thoại.
*/

document.addEventListener(
"touchmove",
e=>{

    if(
        e.target===canvas
    ){

        e.preventDefault();

    }

},
{passive:false}
);


document.addEventListener(
"gesturestart",
e=>e.preventDefault()
);


/* =====================================================
   PLAYER
===================================================== */

function updatePlayer(dt){

    let dx=0;
    let dy=0;


    if(keys.w)dy--;

    if(keys.s)dy++;

    if(keys.a)dx--;

    if(keys.d)dx++;


    dx+=touchDX;

    dy+=touchDY;


    if(dx||dy){

        const length =
            Math.sqrt(
                dx*dx+dy*dy
            );


        dx/=length;
        dy/=length;


        player.x +=
            dx*player.speed*dt;


        player.y +=
            dy*player.speed*dt;

    }


    player.x =
        Math.max(
            50,
            Math.min(
                WORLD_WIDTH-50,
                player.x
            )
        );


    player.y =
        Math.max(
            180,
            Math.min(
                WORLD_HEIGHT-50,
                player.y
            )
        );


    if(
        player.hammerTimer>0
    ){

        player.hammerTimer-=dt;

    }


    if(
        player.gunRecoil>0
    ){

        player.gunRecoil-=dt;

    }


    if(
        player.invulnTimer>0
    ){

        player.invulnTimer-=dt;

    }


    /*
       Hồi máu: sau 10 giây không bị
       quái vật đánh trúng thì +1 máu.
    */

    player.regenTimer+=dt;


    if(
        player.regenTimer>=10
    ){

        player.regenTimer=0;


        if(
            player.health<MAX_HEALTH
        ){

            player.health++;

            updateUI();

        }

    }

}


/* =====================================================
   ATTACK EGG
===================================================== */

function attackEgg(){

    player.hammerTimer=.35;

    sfxHammer();


    for(
        const egg of eggs
    ){

        if(!egg.alive)
            continue;


        const d =
            distance(
                player.x,
                player.y,
                egg.x,
                egg.y
            );


        if(d<115){

            egg.alive=false;

            spawnMonster(
                egg
            );

            break;

        }

    }

}


/* =====================================================
   SPAWN MONSTER
===================================================== */

function spawnMonster(egg){

    const word =
        chooseWord();


    const puzzle =
        createPuzzle(
            word
        );


    const monster={

        x:egg.x,

        y:egg.y,

        size:70,

        displayWord:
            word.display,

        answer:
            puzzle.answer,

        pattern:
            puzzle.pattern,

        hiddenPositions:
            puzzle.hiddenPositions,

        typed:"",

        speed:
            LEVEL_SPEED[
                infiniteMode
                ? 6
                : level
            ],

        alive:true,

        dying:false,

        flash:true,

        flashCount:0,

        flashTimer:0,

        hitFlash:0,

        shotsFired:0,

        cryTimer:1.5

    };


    monsters.push(
        monster
    );


    activeMonster =
        monster;


    sfxCry();


    openWordPanel(
        monster
    );

}


/* =====================================================
   MONSTERS
===================================================== */

function updateMonsters(dt){

    for(
        const monster of monsters
    ){

        if(!monster.alive)
            continue;


        if(monster.dying){

            monster.flashTimer-=dt;


            if(
                monster.flashTimer<=0
            ){

                monster.flash=
                    !monster.flash;

                monster.flashTimer=.2;

                monster.flashCount++;

            }


            if(
                monster.flashCount>=10
            ){

                monster.alive=false;

                score+=50;

                eggsDestroyed++;

                if(
                    activeMonster===monster
                ){

                    activeMonster=null;

                }


                closeWordPanel();

                updateUI();

                checkLevel();

            }


            continue;

        }


        const dx =
            player.x-monster.x;

        const dy =
            player.y-monster.y;

        const d =
            Math.sqrt(
                dx*dx+dy*dy
            );


        if(d>1){

            const speed =
                monster.speed*2.2;


            monster.x +=
                dx/d*speed*dt;


            monster.y +=
                dy/d*speed*dt;

        }


        if(monster.hitFlash>0)
            monster.hitFlash-=dt;


        if(monster===activeMonster){

            monster.cryTimer-=dt;


            if(monster.cryTimer<=0){

                monster.cryTimer=
                    3+Math.random()*3;

                sfxCry();

            }

        }


        /*
           Quái vật chạm vào người chơi
           thì mất 1 máu.
        */

        const hitRange =
            monster.size*0.7 +
            player.size*0.5;


        if(
            d<hitRange &&
            player.invulnTimer<=0
        ){

            damagePlayer();

        }

    }

}


/* =====================================================
   LEVEL
===================================================== */

function checkLevel(){

    if(
        eggsDestroyed<5
    )
        return;


    if(
        monsters.some(
            m=>m.alive
        )
    )
        return;


    if(level<5){

        level++;

        eggsDestroyed=0;

        createEggs();

        monsters=[];

        showMessage(
            "LEVEL "+level,
            "#55e8ff"
        );

    }else{

        infiniteMode=true;

        level=6;

        eggsDestroyed=0;

        createEggs();

        monsters=[];

        showMessage(
            "INFINITE MODE",
            "#ff4c79"
        );

    }


    updateUI();

}


/* =====================================================
   WORD PANEL
===================================================== */

function openWordPanel(monster){

    const panel =
        document.getElementById(
            "wordPanel"
        );


    /*
       Không hiện từ gợi ý nữa:
       người chơi tự đoán từ qua các
       chữ cái đã lộ.
    */

    document.getElementById(
        "nativeWord"
    ).textContent="";


    document.getElementById(
        "wordInput"
    ).value="";


    updateWordDisplay(
        monster
    );


    panel.style.display=
        "block";


    setTimeout(
        ()=>{
            document
                .getElementById(
                    "wordInput"
                )
                .focus();
        },
        50
    );

}


function closeWordPanel(){

    document.getElementById(
        "wordPanel"
    ).style.display=
        "none";


    document.getElementById(
        "wordInput"
    ).value="";

}


/* =====================================================
   WORD DISPLAY
===================================================== */

function updateWordDisplay(monster){

    let result="";

    let typedIndex=0;


    for(
        let i=0;
        i<monster.answer.length;
        i++
    ){

        if(
            monster.pattern[i]!=="_"
        ){

            result+=
                monster.pattern[i];

        }else{

            result+=
                monster.typed[
                    typedIndex
                ] || "_";

            typedIndex++;

        }

    }


    document.getElementById(
        "wordDisplay"
    ).textContent=
        result;

}


/* =====================================================
   CHECK LETTERS
===================================================== */

document
.getElementById(
    "wordInput"
)
.addEventListener(
"input",
function(){

    if(!activeMonster)
        return;


    if(activeMonster.dying)
        return;


    const input =
        normalizeText(
            this.value
        );


    const hidden =
        activeMonster
            .hiddenPositions;


    let correct=true;

    let wrong=-1;


    for(
        let i=0;
        i<input.length;
        i++
    ){

        if(
            i>=hidden.length
        )
            break;


        const answerIndex =
            hidden[i];


        const expected =
            activeMonster
                .answer[
                    answerIndex
                ];


        if(
            input[i]!==expected
        ){

            correct=false;

            wrong=i;

            break;

        }

    }


    if(!correct){

        this.classList.add(
            "error"
        );

        this.classList.remove(
            "correct"
        );


        document.getElementById(
            "inputMessage"
        ).textContent=
            "❌ Sai chữ ở vị trí "+
            (wrong+1);


        document.getElementById(
            "inputMessage"
        ).className=
            "messageBad";


        activeMonster.typed =
            input.substring(
                0,
                wrong
            );


        this.value =
            activeMonster.typed;


        updateWordDisplay(
            activeMonster
        );


        return;

    }


    activeMonster.typed =
        input.substring(
            0,
            hidden.length
        );


    const firedCount =
        activeMonster.typed.length;


    if(
        firedCount>
        activeMonster.shotsFired
    ){

        for(
            let k=activeMonster.shotsFired;
            k<firedCount;
            k++
        ){

            fireBullet(
                activeMonster
            );

        }


        activeMonster.shotsFired=
            firedCount;

    }


    this.classList.remove(
        "error"
    );

    this.classList.add(
        "correct"
    );


    document.getElementById(
        "inputMessage"
    ).textContent=
        "✓ Đúng";


    document.getElementById(
        "inputMessage"
    ).className=
        "messageGood";


    updateWordDisplay(
        activeMonster
    );


    if(
        activeMonster.typed.length
        ===
        hidden.length
    ){

        destroyMonster(
            activeMonster
        );

    }

});


/* =====================================================
   DESTROY MONSTER
===================================================== */

function destroyMonster(monster){

    if(monster.dying)
        return;


    monster.dying=true;

    monster.flash=true;

    monster.flashCount=0;

    monster.flashTimer=.2;


    sfxDeath();

}


/* =====================================================
   UI
===================================================== */

function updateUI(){

    document.getElementById(
        "score"
    ).textContent=
        score;


    document.getElementById(
        "level"
    ).textContent=
        infiniteMode
        ? "∞"
        : level;


    const hearts =
        "❤".repeat(
            Math.max(0,player.health)
        ) +
        "🖤".repeat(
            Math.max(
                0,
                MAX_HEALTH-player.health
            )
        );


    document.getElementById(
        "health"
    ).textContent=
        hearts;

}


/* =====================================================
   MESSAGE
===================================================== */

function showMessage(text,color){

    const box =
        document.getElementById(
            "message"
        );


    const textBox =
        document.getElementById(
            "messageText"
        );


    textBox.textContent=text;

    textBox.style.color=color;

    box.style.display="flex";


    setTimeout(
        ()=>{
            box.style.display="none";
        },
        2000
    );

}


/* =====================================================
   DAMAGE / GAME OVER
===================================================== */

function damagePlayer(){

    player.health--;

    player.invulnTimer=1;

    player.regenTimer=0;

    updateUI();


    if(player.health<=0){

        endGame();

    }

}


function endGame(){

    if(!gameRunning)
        return;


    gameRunning=false;

    closeWordPanel();


    document.getElementById(
        "ui"
    ).style.display="none";

    document.getElementById(
        "controls"
    ).style.display="none";


    touchControls.style.display="none";

    joystickReset();


    document.getElementById(
        "gameoverScore"
    ).textContent=score;

    document.getElementById(
        "gameover"
    ).style.display="flex";


    if(window.saveHighScore)
        window.saveHighScore();

}


window.restartGame=
function(){

    document.getElementById(
        "gameover"
    ).style.display="none";


    window.startGame();

};


window.backToMenu=
function(){

    document.getElementById(
        "gameover"
    ).style.display="none";


    showMainMenu();

};


/* =====================================================
   DISTANCE
===================================================== */

function distance(
    x1,y1,x2,y2
){

    const dx=x2-x1;

    const dy=y2-y1;

    return Math.sqrt(
        dx*dx+dy*dy
    );

}


/* =====================================================
   CAMERA
===================================================== */

function updateCamera(){

    cameraX =
        player.x -
        canvas.width*.5;


    cameraX =
        Math.max(
            0,
            Math.min(
                WORLD_WIDTH-
                canvas.width,
                cameraX
            )
        );


    cameraY =
        player.y -
        canvas.height*.5;


    cameraY =
        Math.max(
            0,
            Math.min(
                WORLD_HEIGHT-
                canvas.height,
                cameraY
            )
        );

}


/* =====================================================
   BACKGROUND
===================================================== */

/*
   Vật trang trí rải khắp thế giới,
   cuộn theo cả hai trục camera và
   thay đổi theo từng bản đồ.
*/

const TREES=[];


const MAPS={

    forest:{
        ground:["#a7e878","#4caf50"],
        grid:"rgba(255,255,255,.18)",
        decor:["tree","tree","bush","flower"]
    },

    desert:{
        ground:["#ffe6a7","#e8b563"],
        grid:"rgba(255,255,255,.14)",
        decor:["cactus","rock","dune","dune"]
    },

    temple:{
        ground:["#e8d9b8","#c2a878"],
        grid:"rgba(255,255,255,.12)",
        decor:["pillar","statue","block","block"]
    },

    coast:{
        ground:["#ffe9b8","#f0d18a"],
        grid:"rgba(255,255,255,.16)",
        band:{y0:180,y1:430,color:["#63d7ff","#2b8fd6"]},
        decor:["palm","shell","rock"]
    }

};


function buildDecor(map){

    TREES.length=0;


    let seed=987654321;


    function rnd(){

        seed=
            (seed*1103515245+12345)&0x7fffffff;

        return seed/0x7fffffff;

    }


    const types=
        (MAPS[map]||MAPS.forest).decor;


    for(let i=0;i<84;i++){

        TREES.push({

            x:60+rnd()*(WORLD_WIDTH-120),

            y:250+rnd()*(WORLD_HEIGHT-320),

            r:22+rnd()*20,

            shade:rnd(),

            flip:rnd()<.5?-1:1,

            type:types[
                Math.floor(rnd()*types.length)
            ]

        });

    }


    TREES.sort((a,b)=>a.y-b.y);

}


buildDecor("forest");


function drawDecor(t,x,y){

    ctx.fillStyle="rgba(0,0,0,.18)";

    ctx.beginPath();
    ctx.ellipse(x,y+24,22,8,0,0,TAU);
    ctx.fill();


    if(t.type==="tree"){

        ctx.fillStyle="#8b5a2b";
        ctx.fillRect(x-6,y-6,12,32);

        ctx.fillStyle=
            t.shade>.5?"#3fa656":"#2f8f4e";
        ctx.beginPath();
        ctx.arc(x,y-10,t.r,0,TAU);
        ctx.fill();

        ctx.fillStyle="rgba(255,255,255,.18)";
        ctx.beginPath();
        ctx.arc(x-t.r*.3,y-10-t.r*.3,t.r*.45,0,TAU);
        ctx.fill();

    }

    else if(t.type==="bush"){

        ctx.fillStyle="#4caf50";
        ctx.beginPath();
        ctx.arc(x,y,t.r*.6,0,TAU);
        ctx.arc(x-t.r*.5,y+4,t.r*.45,0,TAU);
        ctx.arc(x+t.r*.5,y+4,t.r*.45,0,TAU);
        ctx.fill();

    }

    else if(t.type==="flower"){

        ctx.strokeStyle="#3f9b57";
        ctx.lineWidth=3;
        ctx.beginPath();
        ctx.moveTo(x,y+18);
        ctx.lineTo(x,y-6);
        ctx.stroke();

        const cols=["#ff5e9c","#ffd166","#ff8c42","#c77dff"];
        ctx.fillStyle=cols[Math.floor(t.shade*cols.length)];
        for(let k=0;k<5;k++){
            const a=k/5*TAU;
            ctx.beginPath();
            ctx.arc(x+Math.cos(a)*7,y-8+Math.sin(a)*7,5,0,TAU);
            ctx.fill();
        }
        ctx.fillStyle="#fff3a0";
        ctx.beginPath();
        ctx.arc(x,y-8,4,0,TAU);
        ctx.fill();

    }

    else if(t.type==="cactus"){

        ctx.fillStyle="#3fae6a";
        ctx.fillRect(x-7,y-24,14,48);
        ctx.fillRect(x-20,y-8,13,8);
        ctx.fillRect(x-20,y-8,8,20);
        ctx.fillRect(x+7,y-16,13,8);
        ctx.fillRect(x+12,y-16,8,22);

        ctx.fillStyle="rgba(255,255,255,.15)";
        ctx.fillRect(x-7,y-24,4,48);

    }

    else if(t.type==="rock"){

        ctx.fillStyle= t.shade>.5 ? "#b9a88f" : "#a9987f";
        ctx.beginPath();
        ctx.moveTo(x-t.r,y+16);
        ctx.lineTo(x-t.r*.5,y-t.r*.5);
        ctx.lineTo(x+t.r*.4,y-t.r*.6);
        ctx.lineTo(x+t.r,y+16);
        ctx.closePath();
        ctx.fill();

    }

    else if(t.type==="dune"){

        ctx.fillStyle="rgba(255,255,255,.22)";
        ctx.beginPath();
        ctx.ellipse(x,y,t.r*1.6,t.r*.7,0,Math.PI,0);
        ctx.fill();

    }

    else if(t.type==="pillar"){

        ctx.fillStyle="#efe3c8";
        ctx.fillRect(x-12,y-40,24,64);
        ctx.fillStyle="#d8c7a3";
        ctx.fillRect(x-16,y-46,32,10);
        ctx.fillRect(x-16,y+22,32,10);
        ctx.strokeStyle="rgba(0,0,0,.12)";
        ctx.lineWidth=2;
        for(let k=-1;k<=1;k++){
            ctx.beginPath();
            ctx.moveTo(x+k*6,y-36);
            ctx.lineTo(x+k*6,y+20);
            ctx.stroke();
        }

    }

    else if(t.type==="statue"){

        ctx.fillStyle="#d9cbb0";
        ctx.fillRect(x-14,y+10,28,12);
        ctx.fillRect(x-8,y-24,16,34);
        ctx.beginPath();
        ctx.arc(x,y-30,10,0,TAU);
        ctx.fill();

    }

    else if(t.type==="block"){

        ctx.fillStyle="#cbbb98";
        ctx.fillRect(x-18,y-14,36,32);
        ctx.fillStyle="rgba(255,255,255,.2)";
        ctx.fillRect(x-18,y-14,36,8);
        ctx.strokeStyle="rgba(0,0,0,.12)";
        ctx.strokeRect(x-18,y-14,36,32);

    }

    else if(t.type==="palm"){

        ctx.strokeStyle="#a5713d";
        ctx.lineWidth=8;
        ctx.beginPath();
        ctx.moveTo(x,y+22);
        ctx.quadraticCurveTo(x+10*t.flip,y-14,x+18*t.flip,y-34);
        ctx.stroke();

        ctx.fillStyle="#39b568";
        const cx=x+18*t.flip, cy=y-34;
        for(let k=0;k<6;k++){
            const a=k/6*TAU;
            ctx.beginPath();
            ctx.ellipse(cx+Math.cos(a)*16,cy+Math.sin(a)*10,18,7,a,0,TAU);
            ctx.fill();
        }
        ctx.fillStyle="#8b5a2b";
        ctx.beginPath();
        ctx.arc(cx,cy,5,0,TAU);
        ctx.fill();

    }

    else if(t.type==="shell"){

        ctx.fillStyle= t.shade>.5 ? "#ffd6e7" : "#fff0c9";
        ctx.beginPath();
        ctx.arc(x,y,12,Math.PI,0);
        ctx.fill();
        ctx.strokeStyle="rgba(0,0,0,.15)";
        ctx.lineWidth=2;
        for(let k=-2;k<=2;k++){
            ctx.beginPath();
            ctx.moveTo(x,y);
            ctx.lineTo(x+k*5,y-11);
            ctx.stroke();
        }

    }

}


function drawBackground(){

    const map=MAPS[currentMap]||MAPS.forest;


    const ground=
        ctx.createLinearGradient(
            0,0,0,canvas.height
        );


    ground.addColorStop(0,map.ground[0]);

    ground.addColorStop(1,map.ground[1]);


    ctx.fillStyle=ground;

    ctx.fillRect(0,0,canvas.width,canvas.height);


    /* dải nước / khu vực đặc biệt */

    if(map.band){

        const y0=map.band.y0-cameraY;

        const y1=map.band.y1-cameraY;

        const wg=ctx.createLinearGradient(0,y0,0,y1);

        wg.addColorStop(0,map.band.color[0]);

        wg.addColorStop(1,map.band.color[1]);

        ctx.fillStyle=wg;

        ctx.fillRect(0,y0,canvas.width,y1-y0);


        ctx.fillStyle="rgba(255,255,255,.35)";

        for(let i=0;i<5;i++){

            const wy=y0+20+i*((y1-y0)/5);

            ctx.beginPath();
            ctx.ellipse(
                (i*260-cameraX*.5)%canvas.width,
                wy,
                60,5,0,0,TAU
            );
            ctx.fill();

        }

    }


    /* lưới cuộn */

    ctx.strokeStyle=map.grid;

    ctx.lineWidth=2;

    const grid=160;


    const offX=-(cameraX%grid);

    for(let x=offX;x<canvas.width;x+=grid){

        ctx.beginPath();
        ctx.moveTo(x,0);
        ctx.lineTo(x,canvas.height);
        ctx.stroke();

    }


    const offY=-(cameraY%grid);

    for(let y=offY;y<canvas.height;y+=grid){

        ctx.beginPath();
        ctx.moveTo(0,y);
        ctx.lineTo(canvas.width,y);
        ctx.stroke();

    }


    for(const t of TREES){

        const x=t.x-cameraX;

        const y=t.y-cameraY;


        if(
            x<-110||
            x>canvas.width+110||
            y<-110||
            y>canvas.height+110
        )
            continue;


        drawDecor(t,x,y);

    }

}


/* =====================================================
   EGGS
===================================================== */

function drawEggs(){

    for(
        const egg of eggs
    ){

        if(!egg.alive)
            continue;


        const x=
            egg.x-cameraX;

        const y=
            egg.y-cameraY;


        ctx.fillStyle=
            "rgba(0,0,0,.3)";


        ctx.beginPath();

        ctx.ellipse(
            x,
            y+38,
            35,
            10,
            0,
            0,
            Math.PI*2
        );

        ctx.fill();


        const gradient=
            ctx.createLinearGradient(
                x-30,
                y-40,
                x+30,
                y+40
            );


        gradient.addColorStop(
            0,
            "#fff"
        );

        gradient.addColorStop(
            .5,
            "#ffe879"
        );

        gradient.addColorStop(
            1,
            "#ff9347"
        );


        ctx.fillStyle=gradient;

        ctx.beginPath();

        ctx.ellipse(
            x,
            y,
            27,
            37,
            0,
            0,
            Math.PI*2
        );

        ctx.fill();


        ctx.strokeStyle="#754218";

        ctx.lineWidth=3;

        ctx.beginPath();

        ctx.moveTo(
            x-10,
            y-10
        );

        ctx.lineTo(
            x,
            y-2
        );

        ctx.lineTo(
            x-7,
            y+8
        );

        ctx.lineTo(
            x+8,
            y
        );

        ctx.stroke();

    }

}


/* =====================================================
   PLAYER
===================================================== */

function drawPlayer(){

    const x=
        player.x-cameraX;

    const y=
        player.y-cameraY;


    /*
       Nhấp nháy trong lúc bất tử
       sau khi bị trúng đòn.
    */

    if(
        player.invulnTimer>0 &&
        Math.floor(
            player.invulnTimer*12
        )%2===0
    ){

        return;

    }


    ctx.fillStyle=
        "rgba(0,0,0,.28)";

    ctx.beginPath();
    ctx.ellipse(x,y+44,34,12,0,0,TAU);
    ctx.fill();


    drawCharacter(ctx,x,y,1,currentSkin);


    drawWeapon(x,y);

}


function drawWeapon(x,y){

    /*
       Súng luôn cầm trên tay, chĩa về
       phía quái vật đang active.
    */

    let ang=0;


    if(
        activeMonster &&
        activeMonster.alive
    ){

        ang=Math.atan2(
            activeMonster.y-player.y,
            activeMonster.x-player.x
        );

    }


    const recoil=
        player.gunRecoil>0
        ? player.gunRecoil*46
        : 0;


    ctx.save();

    ctx.translate(
        x+Math.cos(ang)*12,
        y+Math.sin(ang)*12+4
    );

    ctx.rotate(ang);

    ctx.translate(-recoil,0);


    ctx.fillStyle="#3b4252";
    ctx.fillRect(0,-4,26,8);

    ctx.fillStyle="#59616f";
    ctx.fillRect(2,3,8,12);

    ctx.fillStyle="#2b303b";
    ctx.fillRect(22,-3,7,6);


    if(player.gunRecoil>.07){

        ctx.fillStyle="#ffe066";
        ctx.beginPath();
        ctx.moveTo(29,-7);
        ctx.lineTo(46,0);
        ctx.lineTo(29,7);
        ctx.closePath();
        ctx.fill();

        ctx.fillStyle="#fff6c0";
        ctx.beginPath();
        ctx.arc(30,0,5,0,TAU);
        ctx.fill();

    }


    ctx.restore();


    /*
       Búa vung mượt khi đập trứng.
    */

    if(player.hammerTimer>0){

        const p=
            1-player.hammerTimer/.35;

        const ease=
            p<.5
            ? 2*p*p
            : 1-Math.pow(-2*p+2,2)/2;

        const swing=
            -2.1+ease*2.9;


        ctx.save();

        ctx.translate(x+6,y-6);

        ctx.rotate(swing);


        ctx.fillStyle="#8b562c";
        ctx.fillRect(-4,-4,9,52);


        ctx.fillStyle="#c3ccd4";
        ctx.fillRect(-17,-18,34,22);

        ctx.strokeStyle="#7d878f";
        ctx.lineWidth=2;
        ctx.strokeRect(-17,-18,34,22);


        ctx.restore();

    }

}


/* =====================================================
   MONSTERS
===================================================== */

function drawMonsters(){

    for(
        const monster of monsters
    ){

        if(!monster.alive)
            continue;


        if(
            monster.dying &&
            monster.flash
        )
            continue;


        const x=
            monster.x-cameraX;

        const y=
            monster.y-cameraY;


        ctx.fillStyle=
            "rgba(0,0,0,.35)";


        ctx.beginPath();

        ctx.ellipse(
            x,
            y+70,
            55,
            18,
            0,
            0,
            Math.PI*2
        );

        ctx.fill();


        ctx.fillStyle="#6d1744";

        ctx.beginPath();

        ctx.arc(
            x,
            y,
            monster.size,
            0,
            Math.PI*2
        );

        ctx.fill();


        ctx.fillStyle="#ff243d";

        ctx.beginPath();

        ctx.arc(
            x-22,
            y-18,
            10,
            0,
            Math.PI*2
        );

        ctx.arc(
            x+22,
            y-18,
            10,
            0,
            Math.PI*2
        );

        ctx.fill();


        ctx.fillStyle="#12020b";

        ctx.beginPath();

        ctx.ellipse(
            x,
            y+25,
            30,
            18,
            0,
            0,
            Math.PI*2
        );

        ctx.fill();


        if(monster.hitFlash>0){

            ctx.fillStyle=
                "rgba(255,255,255,"+
                (monster.hitFlash/.14*.6)+
                ")";

            ctx.beginPath();
            ctx.arc(
                x,
                y,
                monster.size+3,
                0,
                TAU
            );
            ctx.fill();

        }


        drawMonsterWord(
            monster
        );

    }

}


/* =====================================================
   WORD ON MONSTER
===================================================== */

function drawMonsterWord(monster){

    const x=
        monster.x-cameraX;

    const y=
        monster.y-
        cameraY-
        monster.size-
        45;


    const width=
        monster.answer.length*42+30;


    ctx.fillStyle=
        "rgba(0,0,0,.88)";


    ctx.fillRect(
        x-width/2,
        y,
        width,
        48
    );


    for(
        let i=0;
        i<monster.answer.length;
        i++
    ){

        let letter=
            monster.pattern[i];


        if(
            letter==="_"
        ){

            const hiddenIndex=
                monster
                .hiddenPositions
                .indexOf(i);


            if(
                hiddenIndex>=0 &&
                monster.typed[
                    hiddenIndex
                ]
            ){

                letter=
                    monster.typed[
                        hiddenIndex
                    ];

            }

        }


        ctx.font=
            "bold 25px Arial";

        ctx.textAlign=
            "center";

        ctx.fillStyle=
            letter==="_"
            ? "#fff"
            : "#65ff7c";


        ctx.fillText(
            letter,
            x-width/2+
            25+
            i*42,
            y+32
        );

    }

}


/* =====================================================
   DRAW
===================================================== */

function draw(){

    drawBackground();

    drawEggs();

    drawMonsters();

    drawPlayer();

    drawBullets();

}


/* =====================================================
   GAME LOOP
===================================================== */

function gameLoop(now){

    if(!gameRunning)
        return;


    const dt=
        Math.min(
            (now-lastTime)/1000,
            .05
        );


    lastTime=now;


    updatePlayer(dt);

    updateMonsters(dt);

    updateBullets(dt);

    updateCamera();

    draw();


    if(
        infiniteMode &&
        eggs.every(
            e=>!e.alive
        ) &&
        monsters.every(
            m=>!m.alive
        )
    ){

        eggsDestroyed=0;

        createEggs();

    }


    requestAnimationFrame(
        gameLoop
    );

}


createEggs();


bootLoading();


</script>

</body>
</html>
