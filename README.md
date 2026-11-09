<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">
<meta name="theme-color" content="#030916">
<title>JARVIS 4.0 | STARK AI</title>

<style>
:root {
 --bg:#030916;
 --blue:#00bfff;
 --cyan:#43eaff;
 --white:#dffaff;
 --muted:#668ba8;
 --line:#12405b;
 --glass:rgba(8,30,52,.75);
}

* {
 box-sizing:border-box;
 margin:0;
 padding:0;
}

body {
 background:var(--bg);
 color:var(--white);
 font-family:Arial,sans-serif;
 min-height:100vh;
 overflow-x:hidden;
}

body:before {
 content:"";
 position:fixed;
 inset:0;
 pointer-events:none;
 background:
 linear-gradient(#00bfff09 1px,transparent 1px),
 linear-gradient(90deg,#00bfff09 1px,transparent 1px);
 background-size:35px 35px;
 z-index:-1;
}

body:after {
 content:"";
 position:fixed;
 inset:0;
 pointer-events:none;
 background:radial-gradient(ellipse at center,#07315b55,transparent 75%);
 z-index:-1;
}

header {
 height:65px;
 display:flex;
 align-items:center;
 justify-content:space-between;
 padding:0 22px;
 border-bottom:1px solid var(--line);
 background:#061222;
}

.logo {
 color:var(--cyan);
 font-size:19px;
 letter-spacing:5px;
 font-weight:bold;
 text-shadow:0 0 15px var(--blue);
}

.online {
 font-size:10px;
 color:#57ffc5;
 letter-spacing:2px;
}

.dot {
 display:inline-block;
 width:7px;
 height:7px;
 border-radius:50%;
 background:#57ffc5;
 box-shadow:0 0 10px #57ffc5;
 margin-right:7px;
}

.container {
 max-width:1050px;
 margin:auto;
 padding:20px;
}

.top {
 display:flex;
 justify-content:space-between;
 align-items:center;
 gap:10px;
}

.clock {
 font-size:29px;
 letter-spacing:3px;
 color:var(--cyan);
}

.date {
 color:var(--muted);
 font-size:10px;
 margin-top:6px;
 letter-spacing:2px;
}

.version {
 border:1px solid var(--line);
 padding:9px;
 font-size:9px;
 color:var(--cyan);
 letter-spacing:2px;
}

.hero {
 text-align:center;
 margin-top:25px;
}

.hero h1 {
 font-size:31px;
 letter-spacing:10px;
 color:var(--white);
 text-shadow:0 0 25px var(--blue);
}

.hero p {
 margin-top:9px;
 color:var(--muted);
 font-size:9px;
 letter-spacing:5px;
}

.reactor {
 width:260px;
 height:260px;
 max-width:75vw;
 max-height:75vw;
 position:relative;
 margin:35px auto 20px;
 display:grid;
 place-items:center;
}

.ring {
 position:absolute;
 border-radius:50%;
 border:1px solid var(--cyan);
 box-shadow:0 0 13px #00bfff55,inset 0 0 12px #00bfff22;
}

.r1 {
 width:100%;
 height:100%;
 border-left-color:transparent;
 border-bottom-color:transparent;
 animation:spin 9s linear infinite;
}

.r2 {
 width:87%;
 height:87%;
 border-right-color:transparent;
 border-top-color:transparent;
 animation:spin 7s linear infinite reverse;
}

.r3 {
 width:72%;
 height:72%;
 border-style:dashed;
 border-color:#008dff;
 animation:spin 18s linear infinite;
}

.r4 {
 width:58%;
 height:58%;
 border-width:3px;
 border-color:#00bfff66;
 animation:pulse 3s infinite;
}

.core {
 width:100px;
 height:100px;
 border-radius:50%;
 background:radial-gradient(circle,#fff 0%,#8bf5ff 12%,#00bfff 40%,#064caa 75%,#03152d);
 box-shadow:0 0 25px #00bfff,0 0 65px #007bff,0 0 100px #0066ff66;
 animation:core 3s ease-in-out infinite;
}

@keyframes spin {
 to {transform:rotate(360deg)}
}

@keyframes pulse {
 50% {transform:scale(1.07);opacity:.5}
}

@keyframes core {
 50% {transform:scale(1.09);filter:brightness(1.4)}
}

.reactor-label {
 color:var(--cyan);
 font-size:11px;
 letter-spacing:5px;
 text-align:center;
}

.wave {
 display:flex;
 justify-content:center;
 align-items:center;
 gap:5px;
 height:45px;
 margin:15px;
}

.wave span {
 height:5px;
 width:4px;
 border-radius:5px;
 background:var(--cyan);
 box-shadow:0 0 8px var(--blue);
}

.wave.active span {
 animation:wave .55s ease-in-out infinite alternate;
}

.wave span:nth-child(2n){animation-delay:.15s}
.wave span:nth-child(3n){animation-delay:.3s}

@keyframes wave {
 to {height:35px}
}

.status {
 text-align:center;
 color:var(--cyan);
 letter-spacing:4px;
 font-size:11px;
 margin:15px;
}

.panels {
 display:grid;
 grid-template-columns:repeat(3,1fr);
 gap:12px;
 margin-top:25px;
}

.panel {
 background:var(--glass);
 border:1px solid var(--line);
 padding:16px;
 border-radius:5px;
 box-shadow:inset 0 0 25px #008cff0a;
 min-width:0;
}

.panel-title {
 color:var(--muted);
 font-size:9px;
 letter-spacing:2px;
 margin-bottom:12px;
}

.panel-value {
 color:var(--cyan);
 font-size:13px;
 font-weight:bold;
}

.chat-panel {
 margin-top:15px;
}

.response {
 background:#020d1a;
 border:1px solid #123e5c;
 min-height:85px;
 padding:16px;
 font-size:13px;
 line-height:1.7;
 color:#c6edff;
 border-radius:4px;
 overflow-wrap:anywhere;
}

.controls {
 display:flex;
 justify-content:center;
 flex-wrap:wrap;
 gap:10px;
 margin:17px 0;
}

button {
 padding:14px 18px;
 background:#09213a;
 color:var(--cyan);
 border:1px solid #087eae;
 border-radius:4px;
 font-size:10px;
 letter-spacing:2px;
 cursor:pointer;
}

button.primary {
 background:linear-gradient(120deg,#07528b,#06305c);
 border-color:var(--cyan);
 box-shadow:0 0 18px #007bff44;
}

button.stop {
 color:#ff8787;
 border-color:#824c59;
}

button:active {
 background:#125080;
}

.voice-settings {
 margin-top:15px;
}

select,input {
 width:100%;
 padding:12px;
 background:#041426;
 color:var(--white);
 border:1px solid var(--line);
 border-radius:3px;
 font-size:12px;
}

.setting-label {
 color:var(--muted);
 font-size:9px;
 letter-spacing:2px;
 margin:16px 0 8px;
}

.terminal {
 background:#020c17;
 border:1px solid var(--line);
 padding:14px;
 height:125px;
 overflow-y:auto;
 color:#63caff;
 font-size:10px;
 line-height:2;
 margin-top:12px;
}

.terminal .user {
 color:#ffc56b;
}

.chat-input {
 display:flex;
 gap:8px;
 margin-top:12px;
}

.chat-input input {
 min-width:0;
}

.chat-input button {
 min-width:65px;
}

.footer {
 text-align:center;
 padding:30px 10px;
 color:#43647f;
 font-size:9px;
 letter-spacing:3px;
}

@media(max-width:600px) {
 .container{padding:13px}
 .panels{grid-template-columns:1fr 1fr}
 .hero h1{font-size:25px}
 .reactor{width:235px;height:235px}
 .clock{font-size:23px}
}
</style>
</head>

<body>

<header>
 <div class="logo">J.A.R.V.I.S.</div>
 <div class="online"><span class="dot"></span>ONLINE</div>
</header>

<div class="container">

 <div class="top">
  <div>
   <div class="clock" id="clock">00:00:00</div>
   <div class="date" id="date">INITIALIZING...</div>
  </div>
  <div class="version">STARK AI // 4.0</div>
 </div>

 <div class="hero">
  <h1>JARVIS</h1>
  <p>PERSONAL ARTIFICIAL INTELLIGENCE</p>
 </div>

 <div class="reactor">
  <div class="ring r1"></div>
  <div class="ring r2"></div>
  <div class="ring r3"></div>
  <div class="ring r4"></div>
  <div class="core"></div>
 </div>

 <div class="reactor-label">NEURAL CORE</div>

 <div class="wave" id="wave">
  <span></span><span></span><span></span>
  <span></span><span></span><span></span>
  <span></span><span></span><span></span>
  <span></span><span></span><span></span>
  <span></span><span></span><span></span>
  <span></span><span></span>
 </div>

 <div class="status" id="status">SYSTEM STANDBY</div>

 <div class="panels">
  <div class="panel">
   <div class="panel-title">AI CORE</div>
   <div class="panel-value">ONLINE</div>
  </div>

  <div class="panel">
   <div class="panel-title">VOICE MODULE</div>
   <div class="panel-value" id="voiceStatus">READY</div>
  </div>

  <div class="panel">
   <div class="panel-title">INTERFACE</div>
   <div class="panel-value">ACTIVE</div>
  </div>
 </div>

 <div class="panel chat-panel">
  <div class="panel-title">JARVIS COMMUNICATION TERMINAL</div>

  <div class="response" id="response">
   Good evening. JARVIS is online and awaiting your instructions.
  </div>

  <div class="controls">
   <button class="primary" onclick="listen()">🎙 ACTIVATE VOICE</button>
   <button class="stop" onclick="stopJarvis()">■ STOP</button>
  </div>

  <div class="voice-settings">
   <div class="setting-label">BRITISH VOICE SELECTION</div>
   <select id="voices">
    <option>Loading available voices...</option>
   </select>

   <div class="setting-label">SPEECH SPEED</div>
   <input type="range" id="rate" min=".7" max="1.1" value=".88" step=".05">

   <div class="setting-label">VOICE PITCH</div>
   <input type="range" id="pitch" min=".5" max="1.2" value=".8" step=".05">

   <button onclick="testVoice()" style="width:100%;margin-top:15px">
    TEST JARVIS VOICE
   </button>
  </div>
 </div>

 <div class="panel chat-panel">
  <div class="panel-title">SYSTEM COMMAND LOG</div>
  <div class="terminal" id="terminal">
   > JARVIS 4.0 INITIALIZED<br>
   > NEURAL INTERFACE ACTIVE<br>
   > VOICE ENGINE READY<br>
   > AWAITING COMMAND...
  </div>

  <div class="chat-input">
   <input id="command" placeholder="Enter a command...">
   <button onclick="sendCommand()">SEND</button>
  </div>
 </div>

 <div class="panels">
  <div class="panel">
   <div class="panel-title">RADAR</div>
   <div class="panel-value">SIMULATED</div>
  </div>
  <div class="panel">
   <div class="panel-title">NETWORK</div>
   <div class="panel-value">BROWSER</div>
  </div>
  <div class="panel">
   <div class="panel-title">VERSION</div>
   <div class="panel-value">4.0.0</div>
  </div>
 </div>

 <div class="footer">
  STARK INDUSTRIES // JARVIS PERSONAL SYSTEM<br><br>
  ALL SYSTEMS STANDING BY
 </div>

</div>

<script>

// CLOCK

function updateClock(){
 const d=new Date();
 document.getElementById("clock").textContent=
 d.toLocaleTimeString("en-IN");
 document.getElementById("date").textContent=
 d.toDateString().toUpperCase();
}
setInterval(updateClock,1000);
updateClock();

// VOICES

let selectedVoice=null;
let recognition=null;

const voiceBox=document.getElementById("voices");

function loadVoices(){
 const voices=speechSynthesis.getVoices();
 if(!voices.length)return;

 const previous=voiceBox.value;
 voiceBox.innerHTML="";

 const english=voices.filter(v=>
  v.lang.toLowerCase().startsWith("en")
 );

 const british=english.filter(v=>
  v.lang.toLowerCase()==="en-gb"
 );

 const available=british.length?british:english;

 available.forEach(v=>{
  const opt=document.createElement("option");
  opt.value=v.voiceURI;
  opt.textContent=v.name+" ("+v.lang+")";
  voiceBox.appendChild(opt);
 });

 const preferred=available.find(v=>
  /daniel|oliver|george|british/i.test(v.name)
 )||available[0];

 if(preferred){
  selectedVoice=preferred;
  voiceBox.value=preferred.voiceURI;
 }

 if(available.some(v=>v.voiceURI===previous)){
  voiceBox.value=previous;
  selectedVoice=available.find(v=>v.voiceURI===previous);
 }
}

speechSynthesis.onvoiceschanged=loadVoices;
loadVoices();

voiceBox.addEventListener("change",()=>{
 selectedVoice=speechSynthesis.getVoices().find(
  v=>v.voiceURI===voiceBox.value
 )||null;
});

// CLOCK / TERMINAL

function log(text,cls=""){
 const terminal=document.getElementById("terminal");
 const line=document.createElement("div");
 line.textContent="> "+text;
 line.className=cls;
 terminal.appendChild(line);
 terminal.scrollTop=terminal.scrollHeight;
}

// SPEAK

function speak(text){
 speechSynthesis.cancel();

 const msg=new SpeechSynthesisUtterance(text);
 msg.lang="en-GB";
 msg.rate=Number(document.getElementById("rate").value);
 msg.pitch=Number(document.getElementById("pitch").value);
 msg.volume=1;

 if(selectedVoice)msg.voice=selectedVoice;

 msg.onstart=()=>{
  document.getElementById("wave").classList.add("active");
  document.getElementById("status").textContent="JARVIS SPEAKING";
  document.getElementById("voiceStatus").textContent="SPEAKING";
 };

 msg.onend=()=>{
  document.getElementById("wave").classList.remove("active");
  document.getElementById("status").textContent="SYSTEM STANDBY";
  document.getElementById("voiceStatus").textContent="READY";
 };

 msg.onerror=()=>{
  document.getElementById("wave").classList.remove("active");
  document.getElementById("voiceStatus").textContent="READY";
 };

 speechSynthesis.speak(msg);
}

function reply(text){
 document.getElementById("response").textContent=text;
 log("JARVIS: "+text);
 speak(text);
}

// VOICE INPUT

function listen(){
 const API=window.SpeechRecognition||
 window.webkitSpeechRecognition;

 if(!API){
  reply("Voice recognition is not available. Please use Chrome.");
  return;
 }

 if(recognition){
  try{recognition.abort()}catch(e){}
 }

 speechSynthesis.cancel();

 recognition=new API();
 recognition.lang="en-GB";
 recognition.continuous=false;
 recognition.interimResults=false;

 document.getElementById("status").textContent="LISTENING";
 document.getElementById("voiceStatus").textContent="LISTENING";
 document.getElementById("wave").classList.add("active");

 recognition.onresult=e=>{
  const text=e.results[0][0].transcript;
  log("USER: "+text,"user");
  processCommand(text.toLowerCase());
 };

 recognition.onerror=e=>{
  log("VOICE ERROR: "+e.error);
  document.getElementById("status").textContent="VOICE ERROR";
  document.getElementById("voiceStatus").textContent="READY";
  document.getElementById("wave").classList.remove("active");
 };

 recognition.onend=()=>{
  document.getElementById("wave").classList.remove("active");
  if(document.getElementById("status").textContent==="LISTENING"){
   document.getElementById("status").textContent="SYSTEM STANDBY";
   document.getElementById("voiceStatus").textContent="READY";
  }
 };

 try{
  recognition.start();
 }catch(e){
  document.getElementById("status").textContent="RETRY";
 }
}

function stopJarvis(){
 if(recognition){
  try{recognition.abort()}catch(e){}
 }
 speechSynthesis.cancel();
 document.getElementById("wave").classList.remove("active");
 document.getElementById("status").textContent="SYSTEM STANDBY";
 document.getElementById("voiceStatus").textContent="READY";
 document.getElementById("response").textContent="Voice output stopped.";
 log("AUDIO STOPPED");
}

// COMMANDS

function processCommand(c){

 if(c.includes("hello")||c.includes("hey jarvis")){
  reply("Good evening. JARVIS is online. How may I assist you?");
 }

 else if(c.includes("time")){
  reply("The current time is "+new Date().toLocaleTimeString("en-GB"));
 }

 else if(c.includes("date")){
  reply("Today's date is "+new Date().toDateString());
 }

 else if(c.includes("system check")||c.includes("diagnostics")){
  reply("System diagnostic complete. Interface operational. Voice module ready. Advanced AI connection pending.");
 }

 else if(c.includes("who are you")){
  reply("I am JARVIS. Your personal artificial intelligence interface.");
 }

 else if(c.includes("how are you")){
  reply("All systems are functioning normally. Thank you for asking.");
 }

 else if(c.includes("status report")){
  reply("Neural interface online. Voice recognition ready. Visual systems operational. Awaiting instructions.");
 }

 else if(c.includes("goodbye")){
  reply("Until next time. JARVIS standing by.");
 }

 else{
  reply("I have received your command. My advanced AI connection is not yet configured.");
 }
}

// TEXT COMMANDS

function sendCommand(){
 const input=document.getElementById("command");
 const text=input.value.trim();
 if(!text)return;
 log("USER: "+text,"user");
 input.value="";
 processCommand(text.toLowerCase());
}

document.getElementById("command").addEventListener("keydown",e=>{
 if(e.key==="Enter")sendCommand();
});

// TEST VOICE

function testVoice(){
 reply("Good evening. I am JARVIS. Your personal artificial intelligence system. All primary systems are standing by. How may I assist you today?");
}

</script>
</body>
</html>
