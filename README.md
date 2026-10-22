<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>PRISON PHONE</title>

<style>
* {
  box-sizing: border-box;
}

[hidden] {
  display: none !important;
}

body {
  margin: 0;
  min-height: 100dvh;
  display: grid;
  place-items: center;
  background: #e8e7ec;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  color: #111;
}

button,
input {
  font: inherit;
}

button {
  cursor: pointer;
  -webkit-tap-highlight-color: transparent;
}

button:focus-visible {
  outline: 3px solid #007aff;
  outline-offset: 3px;
}

.phone {
  position: relative;
  width: min(390px, 100vw);
  height: min(820px, 100dvh);
  min-height: 460px;
  overflow: hidden;
  border: 7px solid #202024;
  border-radius: 48px;
  background: #a8a7be;
  box-shadow: 0 25px 70px #25203530;
}

.wallpaper {
  position: absolute;
  inset: 0;
  background: linear-gradient(155deg, #b4bfd6, #d5bfca 52%, #888cae);
  background-size: cover;
  background-position: center;
}

/* 상단 상태 표시줄 */
.status {
  position: absolute;
  top: 19px;
  left: 25px;
  right: 23px;
  z-index: 10;
  height: 23px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  color: #000;
  pointer-events: none;
}

.carrier {
  font-size: 16px;
  font-weight: 500;
  letter-spacing: -.4px;
}

.status-icons {
  /* 아이콘 크기 조절 */
  --wifi-width: 21px;
  --wifi-height: 17px;
  --battery-width: 30px;
  --battery-height: 18px;
  --battery-number-size: 13px;

  /* 배터리 빈 부분과 숫자 색상 */
  --battery-gray: #a3a3a8;

  position: relative;
  display: flex;
  align-items: center;
  gap: 7px;
  color: #000;
}

.status-icons svg {
  display: block;
  flex-shrink: 0;
}

.wifi-icon {
  width: var(--wifi-width);
  height: var(--wifi-height);
}

.battery {
  position: relative;
  width: var(--battery-width);
  height: var(--battery-height);
  flex-shrink: 0;
  border-radius: 5px;
  background: var(--battery-gray);
}

.battery-fill {
  position: absolute;
  inset: 0 auto 0 0;
  width: 74%;
  border-radius: 5px 0 0 5px;
  background: #000;
}

.battery-number {
  position: absolute;
  inset: 0;
  z-index: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0;
  padding: 0;
  font-family: Arial, sans-serif;
  font-size: var(--battery-number-size);
  font-weight: 400;
  line-height: 1;
  letter-spacing: 0;
  color: var(--battery-gray);
}

.battery::after {
  content: "";
  position: absolute;
  right: -3px;
  top: 50%;
  transform: translateY(-50%);
  width: 2px;
  height: 7px;
  border-radius: 0 2px 2px 0;
  background: var(--battery-gray);
}

.status-icons::after {
  content: "";
  position: absolute;
  right: 9px;
  bottom: -10px;
  width: 57px;
  height: 3px;
  border-radius: 5px;
  background: #000;
  opacity: .65;
}

.island {
  position: absolute;
  top: 10px;
  left: 50%;
  transform: translateX(-50%);
  width: 105px;
  height: 29px;
  border-radius: 30px;
  background: #090909;
  z-index: 11;
}

.screen {
  position: absolute;
  inset: 0;
  padding-top: 60px;
}

/* 잠금화면 */
.lock {
  padding-top: 110px;
  text-align: center;
  color: #fff;
}

.lock-date {
  font-size: 18px;
}

.lock-time {
  font-size: 82px;
  font-weight: 600;
  letter-spacing: -5px;
  line-height: 1.2;
}

.unlock {
  position: absolute;
  bottom: 65px;
  left: 50%;
  transform: translateX(-50%);
  border: 1px solid #ffffff60;
  border-radius: 30px;
  padding: 13px 24px;
  color: #fff;
  background: #ffffff20;
  backdrop-filter: blur(15px);
}

/* 홈 화면 */
.home {
  padding: 85px 25px 100px;
}

.widget {
  padding: 21px;
  margin-bottom: 32px;
  border-radius: 25px;
  color: #fff;
  background: #ffffff22;
  backdrop-filter: blur(15px);
}

.widget small {
  opacity: .8;
}

.widget p {
  margin: 10px 0 0;
  font-size: 24px;
}

.apps {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 24px 12px;
}

.app-icon {
  padding: 0;
  border: 0;
  background: transparent;
  color: #fff;
  font-size: 11px;
  text-align: center;
}

.icon-box {
  position: relative;
  width: 58px;
  height: 58px;
  margin: 0 auto 7px;
  display: grid;
  place-items: center;
  border-radius: 15px;
  font-size: 30px;
  box-shadow: 0 4px 12px #00000010;
}

.green {
  background: linear-gradient(#63ed79, #21bd43);
}

.black {
  background: #111;
}

.yellow {
  background: linear-gradient(#ffd75a 28%, #fff 28%);
}

.badge {
  position: absolute;
  top: -6px;
  right: -5px;
  min-width: 21px;
  padding: 3px 5px;
  border-radius: 20px;
  background: #ff3b30;
  color: #fff;
  font-size: 12px;
}

.dock {
  position: absolute;
  bottom: 35px;
  left: 15px;
  right: 15px;
  display: flex;
  justify-content: space-around;
  padding: 15px;
  border-radius: 30px;
  background: #ffffff30;
  backdrop-filter: blur(20px);
}

.dock .icon-box {
  margin: 0;
}

/* 앱 공통 */
.page {
  display: flex;
  flex-direction: column;
  padding-bottom: 35px;
  background: #fff;
}

.header {
  display: flex;
  align-items: center;
  min-height: 55px;
  padding: 8px 15px;
  border-bottom: 1px solid #eee;
  gap: 10px;
}

.header h2 {
  margin: 0;
  font-size: 17px;
}

.back {
  padding: 8px 0;
  border: 0;
  background: transparent;
  color: #007aff;
  font-size: 16px;
}

.scroll {
  flex: 1;
  min-height: 0;
  overflow-y: auto;
}

.title {
  margin: 15px 20px;
  font-size: 31px;
  letter-spacing: -1px;
}

.row {
  width: 100%;
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 17px 20px;
  border: 0;
  border-bottom: 1px solid #eee;
  background: #fff;
  text-align: left;
}

.avatar {
  flex-shrink: 0;
  width: 43px;
  height: 43px;
  display: grid;
  place-items: center;
  border-radius: 50%;
  background: #eeeef3;
  font-size: 23px;
}

.row-text {
  flex: 1;
  min-width: 0;
}

.row-text strong {
  display: block;
  font-size: 15px;
}

.preview {
  margin-top: 5px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  color: #888;
  font-size: 13px;
}

/* 문자 */
.chat-body {
  padding: 20px 15px;
}

.bubble {
  width: fit-content;
  max-width: 82%;
  padding: 10px 14px;
  margin: 0 0 10px;
  border-radius: 19px;
  background: #e9e9eb;
  font-size: 15px;
  line-height: 1.5;
  overflow-wrap: anywhere;
  white-space: pre-wrap;
}

.bubble.me {
  margin-left: auto;
  color: #fff;
  background: #007aff;
}

.composer {
  display: flex;
  padding: 10px 12px;
  gap: 8px;
  border-top: 1px solid #eee;
}

.composer input {
  flex: 1;
  width: 0;
  min-width: 0;
  border: 1px solid #ddd;
  border-radius: 25px;
  padding: 10px 13px;
  font-size: 16px;
}

.send {
  width: 38px;
  height: 38px;
  border: 0;
  border-radius: 50%;
  background: #007aff;
  color: #fff;
}

/* 타임라인 */
.post {
  padding: 18px;
  border-bottom: 1px solid #eee;
}

.post-head {
  display: flex;
  align-items: center;
  gap: 10px;
}

.handle {
  margin-top: 3px;
  color: #888;
  font-size: 12px;
}

.post p {
  font-size: 14px;
  line-height: 1.7;
  white-space: pre-wrap;
  overflow-wrap: anywhere;
}

.like {
  padding: 5px 0;
  border: 0;
  background: none;
  color: #777;
}

.like.active {
  color: #f04477;
}

/* 메모 */
.note {
  margin: 15px;
  padding: 18px;
  border-radius: 15px;
  background: #fff8db;
  white-space: pre-wrap;
  overflow-wrap: anywhere;
  line-height: 1.8;
}

/* 문자 알림 */
.banner {
  position: absolute;
  top: 60px;
  left: 10px;
  right: 10px;
  z-index: 20;
  padding: 15px;
  border: 0;
  border-radius: 22px;
  background: #f5f5f4ed;
  box-shadow: 0 8px 25px #0002;
  text-align: left;
  backdrop-filter: blur(20px);
}

.banner small {
  display: block;
  margin-bottom: 6px;
  color: #777;
}

.banner strong {
  display: block;
  margin-bottom: 4px;
}

/* 전화 */
.call {
  position: absolute;
  inset: 0;
  z-index: 30;
  padding: 135px 25px 55px;
  color: #fff;
  text-align: center;
  background: linear-gradient(160deg, #353a50, #171a27);
}

.call-name {
  margin-bottom: 12px;
  font-size: 32px;
}

.call-state {
  color: #c4c6d1;
}

.call-line {
  max-height: 35%;
  margin-top: 55px;
  overflow-y: auto;
  line-height: 1.8;
  white-space: pre-wrap;
}

.call-actions {
  position: absolute;
  bottom: 80px;
  left: 35px;
  right: 35px;
  display: flex;
  justify-content: space-around;
}

.call-actions button {
  width: 76px;
  height: 76px;
  border: 0;
  border-radius: 50%;
  color: #fff;
  font-size: 14px;
}

.reject {
  background: #ff453a;
}

.accept {
  background: #30d158;
}

/* 하단 홈 버튼 */
.home-bar {
  position: absolute;
  bottom: 8px;
  left: 50%;
  z-index: 15;
  transform: translateX(-50%);
  width: 125px;
  height: 18px;
  padding: 0;
  border: 0;
  background: transparent;
}

.home-bar::after {
  content: "";
  position: absolute;
  top: 7px;
  left: 0;
  width: 100%;
  height: 5px;
  border-radius: 10px;
  background: #111;
}

@media (max-width: 430px) {
  body {
    background: #000;
  }

  .phone {
    width: 100vw;
    height: 100dvh;
    border: 0;
    border-radius: 0;
  }
}
</style>
</head>

<body>
<div class="phone">

  <div class="wallpaper" id="wallpaper"></div>

  <div class="status">
    <span class="carrier">SKT</span>

    <div class="status-icons">
      <svg width="22" height="18" viewBox="0 0 22 18"
        role="img" aria-label="통신 신호">
        <rect x="0" y="12" width="4" height="6"
          rx="1.3" fill="currentColor"/>
        <rect x="6" y="8" width="4" height="10"
          rx="1.3" fill="currentColor"/>
        <rect x="12" y="4" width="4" height="14"
          rx="1.3" fill="currentColor"/>
        <rect x="18" y="0" width="4" height="18"
          rx="1.3" fill="currentColor" opacity=".3"/>
      </svg>

      <svg class="wifi-icon" viewBox="0 0 24 19"
        role="img" aria-label="와이파이">
        <path d="M2 5 Q12 -3 22 5"
          fill="none" stroke="currentColor" stroke-width="3.5"/>
        <path d="M5.5 10 Q12 4.5 18.5 10"
          fill="none" stroke="currentColor" stroke-width="3.5"/>
        <path d="M9 14 Q12 11.5 15 14 L12 18 Z"
          fill="currentColor"/>
      </svg>

      <div class="battery" role="img" aria-label="배터리 74퍼센트">
        <div class="battery-fill"></div>
        <span class="battery-number">74</span>
      </div>
    </div>
  </div>

  <div class="island"></div>

  <section class="screen lock" id="lock">
    <div class="lock-date" id="lockDate"></div>
    <div class="lock-time" id="lockTime"></div>
    <button class="unlock" id="unlock">탭하여 잠금 해제</button>
  </section>

  <section class="screen home" id="home" hidden>
    <div class="widget">
      <small id="ownerLabel"></small>
      <p>오늘도 좋은 하루.</p>
    </div>
    <div class="apps" id="appGrid"></div>
    <div class="dock" id="dock"></div>
  </section>

  <section class="screen page" id="messages" hidden>
    <div class="header">
      <button class="back" data-home>‹ 홈</button>
    </div>
    <div class="scroll">
      <h1 class="title">메시지</h1>
      <div id="chatList"></div>
    </div>
  </section>

  <section class="screen page" id="chat" hidden>
    <div class="header">
      <button class="back" id="chatBack">‹ 메시지</button>
      <h2 id="chatName"></h2>
    </div>
    <div class="scroll chat-body" id="chatBody"></div>
    <form class="composer" id="composer">
      <input id="messageInput" placeholder="메시지"
        autocomplete="off" aria-label="메시지 입력">
      <button class="send" type="submit" aria-label="보내기">↑</button>
    </form>
  </section>

  <section class="screen page" id="social" hidden>
    <div class="header">
      <button class="back" data-home>‹ 홈</button>
      <h2>타임라인</h2>
    </div>
    <div class="scroll" id="feed"></div>
  </section>

  <section class="screen page" id="contacts" hidden>
    <div class="header">
      <button class="back" data-home>‹ 홈</button>
      <h2>전화</h2>
    </div>
    <div class="scroll">
      <h1 class="title">연락처</h1>
      <div id="contactList"></div>
    </div>
  </section>

  <section class="screen page" id="notes" hidden>
    <div class="header">
      <button class="back" data-home>‹ 홈</button>
      <h2>메모</h2>
    </div>
    <div class="scroll" id="noteList"></div>
  </section>

  <button class="banner" id="banner" hidden></button>

  <section class="call" id="call" hidden
    role="dialog" aria-modal="true" aria-labelledby="callName">
    <div class="call-name" id="callName"></div>
    <div class="call-state" id="callState"></div>
    <div class="call-line" id="callLine"></div>
    <div class="call-actions">
      <button class="reject" id="hangup">거절</button>
      <button class="accept" id="answer">받기</button>
    </div>
  </section>

  <button class="home-bar" id="homeButton"
    aria-label="홈 화면으로 이동" hidden></button>
</div>

<script>
/* ==========================================
   이름 / 배경 / 자동 문자 / 전화 설정
========================================== */

const SETTINGS = {
  owner: "휴대폰 주인 이름",

  // 저장소에 올린 배경 사진의 정확한 파일 이름
  wallpaper: "다운로드 (9).jpg",

  // 잠금 해제 후 문자와 전화가 오는 시간: 초
  messageAfter: 12,
  callAfter: 28,

  incomingMessage: {
    from: "미오",
    text: "지금 어디야?"
  },

  incomingCall: {
    from: "미오",
    text: "통화가 연결됐어.\n여기에 통화 대사를 넣으면 돼."
  }
};

/* ==========================================
   기존 문자 기록
   me: false → 상대가 보낸 문자
   me: true  → 휴대폰 주인이 보낸 문자
========================================== */

const CHATS = [
  {
    name: "미오",
    emoji: "🦊",
    messages: [
      { me: false, text: "이건 받은 문자 예시야." },
      { me: true, text: "이건 내가 보낸 문자 예시야." }
    ]
  },
  {
    name: "유우",
    emoji: "🦔",
    messages: [
      { me: false, text: "여기에 이전 대화를 넣으면 돼." }
    ]
  },
  {
    name: "시즈카",
    emoji: "🦌",
    messages: []
  },
  {
    name: "세이나",
    emoji: "🐇",
    messages: []
  },
  {
    name: "이츠키",
    emoji: "🐺",
    messages: []
  },
  {
    name: "레아",
    emoji: "🐶",
    messages: []
  }
];

/* ==========================================
   타임라인 게시물
========================================== */

const POSTS = [
  {
    name: "PRISON Official",
    handle: "@PRISON_official",
    emoji: "🔒",
    text: "여기에 공식 계정 게시물 내용을 입력해.",
    likes: 1280
  },
  {
    name: "계정 이름",
    handle: "@account_id",
    emoji: "🤍",
    text: "여기에 팬이나 멤버의 게시물을 입력해.",
    likes: 24
  }
];

/* ==========================================
   메모
   \n → 줄바꿈
========================================== */

const NOTES = [
  "메모 제목\n\n여기에 메모 내용을 입력해.",
  "할 일\n\n• 첫 번째\n• 두 번째"
];

/* ==========================================
   화면과 기능
========================================== */

const $ = id => document.getElementById(id);

let unlocked = false;
let currentScreen = "lock";
let currentChat = null;
let bannerTimer;
let activeCall = null;
let callTimer;
let previousCallFocus = null;

function make(tag, className, text) {
  const element = document.createElement(tag);
  if (className) element.className = className;
  if (text !== undefined) element.textContent = text;
  return element;
}

function show(id) {
  document.querySelectorAll(".screen").forEach(element => {
    element.hidden = element.id !== id;
  });
  currentScreen = id;
}

function updateClock() {
  const now = new Date();

  $("lockTime").textContent = now.toLocaleTimeString("ko-KR", {
    hour: "2-digit",
    minute: "2-digit",
    hour12: false
  });

  $("lockDate").textContent = now.toLocaleDateString("ko-KR", {
    month: "long",
    day: "numeric",
    weekday: "long"
  });
}

updateClock();
setInterval(updateClock, 1000);

$("ownerLabel").textContent = SETTINGS.owner + "의 iPhone";

if (SETTINGS.wallpaper) {
  const imageURL = new URL(SETTINGS.wallpaper, document.baseURI);
  $("wallpaper").style.backgroundImage =
    "url(" + JSON.stringify(imageURL.href) + ")";
}

const APPS = [
  { id: "messages", name: "메시지", icon: "💬", color: "green" },
  { id: "social", name: "타임라인", icon: "𝕏", color: "black" },
  { id: "notes", name: "메모", icon: "📝", color: "yellow" },
  { id: "contacts", name: "전화", icon: "☎", color: "green" }
];

function appButton(app, dock = false) {
  const button = make("button", "app-icon");
  button.setAttribute("aria-label", app.name);

  const box = make("span", "icon-box " + app.color, app.icon);

  if (app.id === "messages" && !dock) {
    const badge = make("span", "badge", "1");
    badge.id = "messageBadge";
    badge.hidden = true;
    box.append(badge);
  }

  button.append(box);

  if (!dock) {
    button.append(make("span", "", app.name));
  }

  button.onclick = () => openApp(app.id);
  return button;
}

APPS.forEach(app => {
  $("appGrid").append(appButton(app));
});

[APPS[3], APPS[0]].forEach(app => {
  $("dock").append(appButton(app, true));
});

function openApp(id) {
  if (id === "messages") renderChats();
  show(id);
}

document.querySelectorAll("[data-home]").forEach(button => {
  button.onclick = () => show("home");
});

$("homeButton").onclick = () => show("home");
$("chatBack").onclick = () => openApp("messages");

$("unlock").onclick = () => {
  if (unlocked) return;

  unlocked = true;
  show("home");
  $("homeButton").hidden = false;

  setTimeout(() => {
    receiveMessage(
      SETTINGS.incomingMessage.from,
      SETTINGS.incomingMessage.text
    );
  }, SETTINGS.messageAfter * 1000);

  setTimeout(() => {
    startCall(SETTINGS.incomingCall.from, true);
  }, SETTINGS.callAfter * 1000);
};

function renderChats() {
  $("chatList").replaceChildren();

  CHATS.forEach((chat, index) => {
    const row = make("button", "row");
    const text = make("div", "row-text");
    const last = chat.messages.at(-1);

    text.append(
      make("strong", "", chat.name),
      make("div", "preview", last ? last.text : "대화 없음")
    );

    row.append(make("span", "avatar", chat.emoji), text);
    row.onclick = () => openChat(index);

    $("chatList").append(row);
  });
}

function openChat(index) {
  currentChat = index;
  $("chatName").textContent = CHATS[index].name;
  $("messageBadge").hidden = true;
  $("banner").hidden = true;
  $("messageInput").value = "";

  show("chat");
  renderChat();
}

function renderChat() {
  $("chatBody").replaceChildren();

  CHATS[currentChat].messages.forEach(message => {
    $("chatBody").append(
      make(
        "div",
        "bubble" + (message.me ? " me" : ""),
        message.text
      )
    );
  });

  $("chatBody").scrollTop = $("chatBody").scrollHeight;
}

$("composer").onsubmit = event => {
  event.preventDefault();

  const text = $("messageInput").value.trim();
  if (!text || currentChat === null) return;

  CHATS[currentChat].messages.push({ me: true, text });
  $("messageInput").value = "";
  renderChat();
};

function receiveMessage(from, text) {
  let index = CHATS.findIndex(chat => chat.name === from);

  if (index === -1) {
    CHATS.push({
      name: from,
      emoji: "👤",
      messages: []
    });
    index = CHATS.length - 1;
    renderContacts();
  }

  CHATS[index].messages.push({ me: false, text });

  if (currentScreen === "chat" && currentChat === index) {
    renderChat();
    return;
  }

  if (currentScreen === "messages") renderChats();

  $("messageBadge").hidden = false;

  const banner = $("banner");
  banner.replaceChildren(
    make("small", "", "메시지 · 지금"),
    make("strong", "", from),
    make("span", "", text)
  );

  banner.hidden = false;
  banner.onclick = () => openChat(index);

  clearTimeout(bannerTimer);
  bannerTimer = setTimeout(() => {
    banner.hidden = true;
  }, 6000);
}

POSTS.forEach(post => {
  const article = make("article", "post");
  const head = make("div", "post-head");
  const name = make("div");

  name.append(
    make("strong", "", post.name),
    make("div", "handle", post.handle)
  );

  head.append(make("span", "avatar", post.emoji), name);

  const like = make("button", "like", "♡ " + post.likes);
  let liked = false;

  like.setAttribute("aria-pressed", "false");

  like.onclick = () => {
    liked = !liked;
    like.classList.toggle("active", liked);
    like.setAttribute("aria-pressed", String(liked));
    like.textContent =
      (liked ? "♥ " : "♡ ") + (post.likes + (liked ? 1 : 0));
  };

  article.append(head, make("p", "", post.text), like);
  $("feed").append(article);
});

NOTES.forEach(note => {
  $("noteList").append(make("div", "note", note));
});

function renderContacts() {
  $("contactList").replaceChildren();

  CHATS.forEach(contact => {
    const row = make("button", "row");

    row.append(
      make("span", "avatar", contact.emoji),
      make("strong", "", contact.name)
    );

    row.onclick = () => startCall(contact.name, false);
    $("contactList").append(row);
  });
}

renderContacts();

function startCall(name, incoming) {
  if (activeCall) return;

  activeCall = { name, incoming };
  previousCallFocus = document.activeElement;

  $("callName").textContent = name;
  $("callState").textContent =
    incoming ? "전화 수신 중" : "전화 거는 중…";
  $("callLine").textContent = "";
  $("hangup").textContent = incoming ? "거절" : "종료";
  $("answer").hidden = !incoming;
  $("call").hidden = false;

  document.querySelectorAll(".screen").forEach(element => {
    element.inert = true;
  });
  $("banner").inert = true;
  $("homeButton").inert = true;
  $("hangup").focus();

  clearTimeout(callTimer);

  callTimer = setTimeout(() => {
    $("callState").textContent =
      incoming ? "부재중 전화" : "응답이 없습니다";
    $("answer").hidden = true;
    $("hangup").textContent = "닫기";
  }, incoming ? 25000 : 5000);
}

$("answer").onclick = () => {
  clearTimeout(callTimer);
  $("callState").textContent = "통화 중";
  $("callLine").textContent = SETTINGS.incomingCall.text;
  $("answer").hidden = true;
  $("hangup").textContent = "종료";
  $("hangup").focus();
};

$("hangup").onclick = () => {
  clearTimeout(callTimer);
  $("call").hidden = true;
  activeCall = null;

  document.querySelectorAll(".screen").forEach(element => {
    element.inert = false;
  });
  $("banner").inert = false;
  $("homeButton").inert = false;

  if (previousCallFocus && previousCallFocus.isConnected) {
    previousCallFocus.focus();
  }
};

$("call").addEventListener("keydown", event => {
  if (event.key !== "Tab") return;

  const buttons = [...$("call").querySelectorAll("button")]
    .filter(button => !button.hidden);

  const first = buttons[0];
  const last = buttons[buttons.length - 1];

  if (event.shiftKey && document.activeElement === first) {
    event.preventDefault();
    last.focus();
  } else if (!event.shiftKey && document.activeElement === last) {
    event.preventDefault();
    first.focus();
  }
});
</script>
</body>
</html>
