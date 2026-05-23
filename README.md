<!DOCTYPE html><html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Furniture Word Game</title>
<style>
body{
font-family:Arial,sans-serif;
background:linear-gradient(135deg,#87CEFA,#FFE082);
text-align:center;
padding:20px;
margin:0;
}
.game{
max-width:700px;
margin:auto;
background:white;
padding:20px;
border-radius:25px;
box-shadow:0 8px 20px rgba(0,0,0,.2);
}
h1{color:#ff6f00}
.card{
font-size:80px;
padding:20px;
}
.question{
font-size:28px;
margin:15px;
font-weight:bold;
}
button{
padding:12px 18px;
margin:8px;
border:none;
border-radius:15px;
font-size:18px;
cursor:pointer;
background:#4CAF50;
color:white;
}
button:hover{transform:scale(1.05)}
.score{font-size:22px;margin:15px;color:#1565c0}
#result{font-size:24px;font-weight:bold}
</style>
</head>
<body>
<div class="game">
<h1>🏠 Furniture Word Game</h1>
<div class="score">Score: <span id="score">0</span></div>
<div class="card" id="emoji">🪑</div>
<div class="question">What is this?</div>
<div id="options"></div>
<div id="result"></div>
<button onclick="nextGame()">Next</button>
</div>
<script>
const data=[
{name:'Chair',emoji:'🪑'},
{name:'Bed',emoji:'🛏️'},
{name:'Lamp',emoji:'💡'},
{name:'Sofa',emoji:'🛋️'},
{name:'Door',emoji:'🚪'},
{name:'Table',emoji:'🍽️'},
{name:'Clock',emoji:'🕒'},
{name:'Cupboard',emoji:'🗄️'}
];
let score=0;
let current;function shuffle(a){ return [...a].sort(()=>Math.random()-0.5) }

function nextGame(){ document.getElementById('result').innerHTML=''; current=data[Math.floor(Math.random()*data.length)]; document.getElementById('emoji').innerHTML=current.emoji;

let opts=[current.name]; while(opts.length<4){ let x=data[Math.floor(Math.random()*data.length)].name; if(!opts.includes(x))opts.push(x); } opts=shuffle(opts);

let html=''; opts.forEach(o=>{ html+=<button onclick="check('${o}')">${o}</button>; }); document.getElementById('options').innerHTML=html; }

function check(ans){ if(ans===current.name){ score++; document.getElementById('result').innerHTML='✅ Correct!'; }else{ document.getElementById('result').innerHTML='❌ Answer: '+current.name; } document.getElementById('score').innerHTML=score; } nextGame(); </script>

</body>
</html>
