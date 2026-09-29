# king-egg[egg-monster-word-hunter.html](https://github.com/user-attachments/files/32794286/egg-monster-word-hunter.html)
<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">

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

}

</style>
</head>


<body>


<!-- =====================================================
     LOGIN SCREEN
===================================================== -->

<div id="loginScreen">

    <div class="loginBox">

        <h1>EGG MONSTER</h1>

        <p>
            Đăng nhập để lưu điểm và tham gia bảng xếp hạng.
        </p>

        <button
            class="loginButton googleButton"
            onclick="loginGoogle()"
        >
            🔵 Đăng nhập bằng Google
        </button>

        <button
            class="loginButton facebookButton"
            onclick="loginFacebook()"
        >
            🔵 Đăng nhập bằng Facebook
        </button>

        <button
            class="loginButton guestButton"
            onclick="loginGuest()"
        >
            🎮 Chơi khách (không cần mạng)
        </button>

        <div id="loginStatus"></div>

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

async function loadLeaderboard(){

    const container =
        document.getElementById(
            "rankingList"
        );


    if(guestMode || !db){

        container.innerHTML =
            "Bạn đang chơi ở chế độ khách (offline).<br><br>" +
            "Đăng nhập bằng Google hoặc Facebook để lưu điểm " +
            "và xem bảng xếp hạng trực tuyến.";

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

    const item =
        list[
            Math.floor(
                Math.random() *
                list.length
            )
        ];

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

    updateUI();

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
   PLAYER
===================================================== */

function updatePlayer(dt){

    let dx=0;
    let dy=0;


    if(keys.w)dy--;

    if(keys.s)dy++;

    if(keys.a)dx--;

    if(keys.d)dx++;


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

        flashTimer:0

    };


    monsters.push(
        monster
    );


    activeMonster =
        monster;


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
   Cây trang trí rải khắp thế giới,
   cuộn theo cả hai trục camera.
*/

const TREES=[];

(function(){

    let seed=987654321;

    function rnd(){

        seed=
            (seed*1103515245+12345)&0x7fffffff;

        return seed/0x7fffffff;

    }

    for(let i=0;i<70;i++){

        TREES.push({

            x:60+rnd()*(WORLD_WIDTH-120),

            y:220+rnd()*(WORLD_HEIGHT-280),

            r:26+rnd()*20

        });

    }

})();


function drawBackground(){

    const ground =
        ctx.createLinearGradient(
            0,
            0,
            0,
            canvas.height
        );


    ground.addColorStop(
        0,
        "#2f6b3f"
    );

    ground.addColorStop(
        1,
        "#1d4a30"
    );


    ctx.fillStyle=ground;

    ctx.fillRect(
        0,
        0,
        canvas.width,
        canvas.height
    );


    /*
       Lưới cuộn giúp thấy nhân vật
       đang di chuyển trong thế giới.
    */

    ctx.strokeStyle=
        "rgba(255,255,255,.05)";

    ctx.lineWidth=2;

    const grid=160;


    const offX=-(cameraX%grid);

    for(
        let x=offX;
        x<canvas.width;
        x+=grid
    ){

        ctx.beginPath();

        ctx.moveTo(x,0);

        ctx.lineTo(x,canvas.height);

        ctx.stroke();

    }


    const offY=-(cameraY%grid);

    for(
        let y=offY;
        y<canvas.height;
        y+=grid
    ){

        ctx.beginPath();

        ctx.moveTo(0,y);

        ctx.lineTo(canvas.width,y);

        ctx.stroke();

    }


    for(const t of TREES){

        const x=
            t.x-cameraX;

        const y=
            t.y-cameraY;


        if(
            x<-90||
            x>canvas.width+90||
            y<-90||
            y>canvas.height+90
        )
            continue;


        ctx.fillStyle=
            "rgba(0,0,0,.22)";

        ctx.beginPath();

        ctx.ellipse(
            x,
            y+26,
            24,
            9,
            0,
            0,
            Math.PI*2
        );

        ctx.fill();


        ctx.fillStyle="#704527";

        ctx.fillRect(
            x-6,
            y-4,
            12,
            32
        );


        ctx.fillStyle="#28784a";

        ctx.beginPath();

        ctx.arc(
            x,
            y-6,
            t.r,
            0,
            Math.PI*2
        );

        ctx.fill();

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
        "rgba(0,0,0,.3)";


    ctx.beginPath();

    ctx.ellipse(
        x,
        y+43,
        35,
        12,
        0,
        0,
        Math.PI*2
    );

    ctx.fill();


    /*
       Nhân vật robot mèo xanh
       thay cho việc nhúng hình ảnh
       có bản quyền trực tiếp.
    */

    ctx.fillStyle="#1e9fd0";

    ctx.beginPath();

    ctx.arc(
        x,
        y,
        37,
        0,
        Math.PI*2
    );

    ctx.fill();


    ctx.fillStyle="#f5fbff";

    ctx.beginPath();

    ctx.arc(
        x,
        y-2,
        29,
        0,
        Math.PI*2
    );

    ctx.fill();


    ctx.fillStyle="#1e9fd0";

    ctx.beginPath();

    ctx.arc(
        x-24,
        y-29,
        12,
        0,
        Math.PI*2
    );

    ctx.arc(
        x+24,
        y-29,
        12,
        0,
        Math.PI*2
    );

    ctx.fill();


    ctx.fillStyle="#111";

    ctx.beginPath();

    ctx.arc(
        x-9,
        y-8,
        4,
        0,
        Math.PI*2
    );

    ctx.arc(
        x+9,
        y-8,
        4,
        0,
        Math.PI*2
    );

    ctx.fill();


    ctx.fillStyle="#e63232";

    ctx.beginPath();

    ctx.arc(
        x,
        y+1,
        5,
        0,
        Math.PI*2
    );

    ctx.fill();


    if(
        player.hammerTimer>0
    ){

        ctx.save();

        ctx.translate(
            x+35,
            y-5
        );

        ctx.rotate(-.8);

        ctx.fillStyle="#8b562c";

        ctx.fillRect(
            0,
            0,
            8,
            58
        );

        ctx.fillStyle="#aaa";

        ctx.fillRect(
            -10,
            -8,
            28,
            18
        );

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


</script>

</body>
</html>
