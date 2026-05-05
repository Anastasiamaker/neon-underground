<!DOCTYPE html>

<html>

<head>

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Neon Underground Arcade</title>

<style>

body{

  margin:0;

  background:#050008;

  color:#00f3ff;

  font-family:"Courier New",monospace;

  text-align:center;

}

h1{

  color:#bc13fe;

  text-shadow:0 0 20px #bc13fe;

  animation: glow 2s infinite alternate;

}

@keyframes glow{

  from{ text-shadow:0 0 10px #bc13fe;}

  to{ text-shadow:0 0 30px #ff00ff;}

}

.grid{

  display:grid;

  grid-template-columns:repeat(auto-fit,minmax(200px,1fr));

  gap:15px;

  padding:20px;

}

.card{

  border:2px solid #bc13fe;

  border-radius:15px;

  padding:15px;

  box-shadow:0 0 15px #bc13fe;

  background:#120018;

  transition:0.3s;

}

.card:hover{

  transform:scale(1.05);

  box-shadow:0 0 25px #ff00ff;

}

button{

  padding:10px;

  margin-top:10px;

  border-radius:8px;

  border:2px solid #00f3ff;

  background:black;

  color:#00f3ff;

  cursor:pointer;

}

button:hover{

  background:#bc13fe;

  color:white;

}

#game{

  margin:20px;

  padding:20px;

  border:2px solid #00f3ff;

  box-shadow:0 0 20px #00f3ff;

  border-radius:15px;

}

.topbar{

  display:flex;

  justify-content:space-around;

  padding:10px;

  font-size:14px;

}

</style>

</head>

<body>

<h1>NEON UNDERGROUND ARCADE</h1>

<div class="topbar">

  <div>👤 <span id="player">Player</span></div>

  <div>💰 Coins: <span id="coins">0</span></div>

  <div>⭐ High Score: <span id="high">0</span></div>

</div>

<input id="nameInput" placeholder="Enter your name">

<button onclick="saveName()">Save</button>

<div id="menu" class="grid"></div>

<div id="game"></div>

<script>

let coins=localStorage.getItem("coins")||0;

let high=localStorage.getItem("high")||0;

let player=localStorage.getItem("name")||"Player";

document.getElementById("coins").innerText=coins;

document.getElementById("high").innerText=high;

document.getElementById("player").innerText=player;

function saveName(){

  let n=nameInput.value;

  localStorage.setItem("name",n);

  player=n;

  document.getElementById("player").innerText=n;

}

function addCoins(n){

  coins=parseInt(coins)+n;

  localStorage.setItem("coins",coins);

  document.getElementById("coins").innerText=coins;

}

function setHigh(n){

  if(n>high){

    high=n;

    localStorage.setItem("high",n);

    document.getElementById("high").innerText=n;

  }

}

let games=[

["Tap Master",tap],

["Reaction",reaction],

["Math",math],

["Guess",guess],

["Aim",aim],

["Color",color],

["Spam Click",spam],

["Lucky Spin",spin],

["Fast Type",type],

["Mini Quiz",quiz]

];

let menu=document.getElementById("menu");

games.forEach((g,i)=>{

  menu.innerHTML+=`

  <div class="card">

    <h3>${g[0]}</h3>

    <button onclick="games[${i}][1]()">PLAY</button>

  </div>`;

});

function back(){

  game.innerHTML="";

}

function tap(){

  let s=0,t=10;

  game.innerHTML=`

  <h2>Tap!</h2>

  <p>${t}s</p>

  <button onclick="s++;this.innerText=s">TAP</button>

  <button onclick="back()">Back</button>`;

  let timer=setInterval(()=>{

    t--;

    if(t<=0){

      clearInterval(timer);

      addCoins(s);

      setHigh(s);

      alert("Score "+s);

    }

  },1000);

}

function reaction(){

  game.innerHTML=`<h2>Wait...</h2><button id="b">Wait</button>`;

  let start;

  setTimeout(()=>{

    b.innerText="CLICK!";

    start=Date.now();

    b.onclick=()=>{

      let r=Date.now()-start;

      addCoins(10);

      alert(r+"ms");

    };

  },2000);

}

function math(){

  let a=Math.floor(Math.random()*10);

  let b=Math.floor(Math.random()*10);

  game.innerHTML=`

  <h2>${a}+${b}</h2>

  <input id="m">

  <button onclick="check()">OK</button>`;

  window.check=()=>{

    if(Number(m.value)==a+b){

      addCoins(5);

      alert("Correct");

    }

  }

}

function guess(){

  let n=Math.floor(Math.random()*10);

  game.innerHTML=`<input id="g"><button onclick="play()">Guess</button>`;

  window.play=()=>{

    if(Number(g.value)==n){

      addCoins(10);

      alert("Win!");

    }

  }

}

function aim(){

  game.innerHTML=`<button onclick="hit()" style="position:absolute">🎯</button>`;

  window.hit=()=>{

    addCoins(2);

  }

}

function color(){

  let c=["red","blue","green"];

  let r=c[Math.floor(Math.random()*3)];

  game.innerHTML=`<h2 style="color:${r}">${r}</h2>`;

}

function spam(){

  let s=0;

  game.innerHTML=`<button onclick="s++;this.innerText=s">CLICK</button>`;

}

function spin(){

  let r=Math.floor(Math.random()*50);

  addCoins(r);

  alert("You won "+r);

}

function type(){

  game.innerHTML=`<input placeholder="type fast">`;

}

function quiz(){

  game.innerHTML=`<h2>2+2?</h2><input id="q"><button onclick="if(q.value==4)addCoins(5)">OK</button>`;

}

</script>

</body>

</html>
