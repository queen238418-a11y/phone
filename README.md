# Phone
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>PRISON PHONE</title>

<style>
* { box-sizing: border-box; }
body {
  margin: 0;
  min-height: 100dvh;
  display: grid;
  place-items: center;
  background: #e8e7ec;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  color: #111;
}
button, input { font: inherit; }
button { cursor: pointer; }
button:focus-visible { outline: 3px solid #007aff; outline-offset: 3px; }
[hidden] { display: none !important; }

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
.status {
  position: absolute;
  top: 16px;
  left: 25px;
  right: 22px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 23px;
  font-size: 13px;
  font-weight: 600;
  z-index: 10;
  pointer-events: none;
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
.lock {
  color: white;
  text-align: center;
  padding-top: 110px;
}
.lock-date { font-size: 18px; }
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
  color: white;
  background: #ffffff20;
  backdrop-filter: blur(15px);
}
.home { padding: 85px 25px 100px; }
.widget {
  color: white;
  padding: 21px;
  border-radius: 25px;
  background: #ffffff22;
  backdrop-filter: blur(15px);
  margin-bottom: 32px;
}
.widget small { opacity: .8; }
.widget p { margin: 10px 0 0; font-size: 24px; }
.apps {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 24px 12px;
}
.app-icon {
  border: 0;
  background: transparent;
  padding: 0;
  color: white;
  font-size: 11px;
  text-align: center;
}
.icon-box {
  position: relative;
  width: 58px;
  height: 58px;
  border-radius: 15px;
  margin: 0 auto 7px;
  display: grid;
  place-items: center;
  font-size: 30px;
  box-shadow: 0 4px 12px #00000010;
}
.green { background: linear-gradient(#63ed79, #21bd43); }
.black { background: #111; }
.yellow { background: linear-gradient(#ffd75a 28%, #fff 28%); }
.badge {
  position: absolute;
  top: -6px;
  right: -5px;
  min-width: 21px;
  padding: 3px 5px;
  border-radius: 20px;
  background: #ff3b30;
  color: white;
  font-size: 12px;
}
.dock {
  position: absolute;
  bottom: 35px;
  left: 15px;
  right: 15px;
  padding: 15px;
  border-radius: 30px;
  background: #ffffff30;
  backdrop-filter: blur(20px);
  display: flex;
  justify-content: space-around;
}
.dock .icon-box { margin: 0; }
.page {
  background: #fff;
  padding-bottom: 35px;
  display: flex;
  flex-direction: column;
}
.header {
  display: flex;
  align-items: center;
  min-height: 55px;
  padding: 8px 15px;
  border-bottom: 1px solid #eee;
  gap: 10px;
}
.header h2 { font-size: 17px; margin: 0; }
.back {
  border: 0;
  background: transparent;
  color: #007aff;
  font-size: 16px;
  padding: 8px 0;
}
.scroll { overflow-y: auto; flex: 1; min-height: 0; }
.title { font-size: 31px; margin: 15px 20px; letter-spacing: -1px; }
.row {
  width: 100%;
  display: flex;
  gap: 12px;
  padding: 17px 20px;
  border: 0;
  border-bottom: 1px solid #eee;
  background: #fff;
  text-align: left;
  align-items: center;
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
.row-text { min-width: 0; flex: 1; }
.row-text strong { display: block; font-size: 15px; }
.preview {
  margin-top: 5px;
  color: #888;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  font-size: 13px;
}
.chat-body { padding: 20px 15px; }
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
  color: white;
  background: #007aff;
}
.composer {
  display: flex;
  padding: 10px 12px;
  gap: 8px;
  border-top: 1px solid #eee;
}
.composer input {
  width: 0;
  flex: 1;
  min-width: 0;
  border: 1px solid #ddd;
  border-radius: 25px;
  padding: 10px 13px;
}
.send {
  border: 0;
  border-radius: 50%;
  width: 38px;
  height: 38px;
  background: #007aff;
  color: white;
}
.post { padding: 18px; border-bottom: 1px solid #eee; }
.post-head { display: flex; gap: 10px; align-items: center; }
.handle { color: #888; font-size: 12px; margin-top: 3px; }
.post p { font-size: 14px; line-height: 1.7; white-space: pre-wrap; }
.like { border: 0; background: none; color: #777; padding: 5px 0; }
.like.active { color: #f04477; }
.note {
  margin: 15px;
  padding: 18px;
  background: #fff8db;
  border-radius: 15px;
  white-space: pre-wrap;
  line-height: 1.8;
}
.banner {
  position: absolute;
  top: 55px;
  left: 10px;
  right: 10px;
  z-index: 20;
  border: 0;
  border-radius: 22px;
  background: #f5f5f4ed;
  box-shadow: 0 8px 25px #0002;
  padding: 15px;
  text-align: left;
  backdrop-filter: blur(20px);
}
.banner small { display: block; color: #777; margin-bottom: 6px; }
.banner strong { display: block; margin-bottom: 4px; }
.call {
  position: absolute;
  inset: 0;
  z-index: 30;
  color: white;
  text-align: center;
  background: linear-gradient(160deg, #353a50, #171a27);
  padding: 135px 25px 55px;
}
.call-name { font-size: 32px; margin-bottom: 12px; }
.call-state { color: #c4c6d1; }
.call-line {
  margin-top: 55px;
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
  border: 0;
  width: 76px;
  height: 76px;
  border-radius: 50%;
  color: white;
  font-size: 14px;
}
.reject { background: #ff453a; }
.accept { background: #30d158; }
.home-bar {
  position: absolute;
  z-index: 15;
  bottom: 8px;
  left: 50%;
  transform: translateX(-50%);
  width: 125px;
  height: 5px;
  padding: 0;
  border: 0;
  border-radius: 10px;
  background: #111;
}
@media(max-width: 430px) {
  body { background: #000; }
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
    <span id="statusTime"></span>
    <span>▮▮▮ &nbsp; 5G &nbsp; ▰</span>
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
      <input id="messageInput" placeholder="메시지" autocomplete="off"
        aria-label="메시지 입력">
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

  <section class="call" id="call" hidden>
    <div class="call-name" id="callName"></div>
    <div class="call-state" id="callState">전화 수신 중</div>
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
   여기가 네가 내용을 바꾸는 곳!
   따옴표와 쉼표는 남겨두고 글자만 바꾸면 돼.
   아래 대사는 작동 확인을 위한 예시야.
========================================== */

const SETTINGS = {
  owner: "휴대폰 주인 이름",

  // 배경 이미지를 올린 뒤 "wallpaper.jpg"처럼 입력
  wallpaper: "다운로드 (9).jpg",

  // 잠금 해제 후 몇 초 뒤에 문자가 올지
  messageAfter: 12,

  // 잠금 해제 후 몇 초 뒤에 전화가 올지
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

const NOTES = [
  "메모 제목\n\n여기에 메모 내용을 입력해.",
  "할 일\n\n• 첫 번째\n• 두 번째"
];

/* ==========================================
   아래부터는 화면과 기능을 작동시키는 코드
========================================== */

const $ = id => document.getElementById(id);
let unlocked = false;
let currentScreen = "lock";
let currentChat = null;
let bannerTimer;
let activeCall = null;
let callTimer;

function make(tag, className, text) {
  const el = document.createElement(tag);
  if (className) el.className = className;
  if (text !== undefined) el.textContent = text;
  return el;
}

function show(id) {
  document.querySelectorAll(".screen").forEach(el => {
    el.hidden = el.id !== id;
  });
  currentScreen = id;
}

function updateClock() {
  const now = new Date();
  const time = now.toLocaleTimeString("ko-KR", {
    hour: "2-digit",
    minute: "2-digit",
    hour12: false
  });
  $("statusTime").textContent = time;
  $("lockTime").textContent = time;
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
  $("wallpaper").style.backgroundImage =
    'url(' + JSON.stringify(SETTINGS.wallpaper) + ')';
}

const appData = [
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
  if (!dock) button.append(make("span", "", app.name));
  button.onclick = () => openApp(app.id);
  return button;
}

appData.forEach(app => $("appGrid").append(appButton(app)));
[appData[3], appData[0]].forEach(app => {
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
    text.append(make("strong", "", chat.name));
    const last = chat.messages.at(-1);
    text.append(make("div", "preview", last ? last.text : "대화 없음"));
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
      make("div", "bubble" + (message.me ? " me" : ""), message.text)
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
    CHATS.push({ name: from, emoji: "👤", messages: [] });
    index = CHATS.length - 1;
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
  bannerTimer = setTimeout(() => banner.hidden = true, 6000);
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

CHATS.forEach(contact => {
  const row = make("button", "row");
  row.append(
    make("span", "avatar", contact.emoji),
    make("strong", "", contact.name)
  );
  row.onclick = () => startCall(contact.name, false);
  $("contactList").append(row);
});

function startCall(name, incoming) {
  // 이미 통화 화면이 열려 있으면 새 전화는 생략
  if (activeCall) return;
  activeCall = { name, incoming };
  $("callName").textContent = name;
  $("callState").textContent =
    incoming ? "전화 수신 중" : "전화 거는 중…";
  $("callLine").textContent = "";
  $("hangup").textContent = incoming ? "거절" : "종료";
  $("answer").hidden = !incoming;
  $("call").hidden = false;

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
};

$("hangup").onclick = () => {
  clearTimeout(callTimer);
  $("call").hidden = true;
  activeCall = null;
};
</script>
</body>
</html>
