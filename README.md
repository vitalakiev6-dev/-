index.html
<!DOCTYPE html>

<html lang="ru">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>Открой, если не боишься 😈</title>

<style>

*{box-sizing:border-box}

body{

 margin:0;min-height:100vh;display:grid;place-items:center;

 background:radial-gradient(circle at top,#3b6b9d,#11152e);

 color:white;font-family:Arial,sans-serif;text-align:center;

}

.card{

 padding:35px 20px;width:90%;max-width:500px;

 border:1px solid #ffffff55;border-radius:25px;

 background:#ffffff18;

}

h1{font-size:38px}

p{font-size:19px}

button{

 border:0;border-radius:30px;padding:16px 25px;

 font-size:18px;font-weight:bold;cursor:pointer;

 background:#ffd166;color:#222;

}

#scare{

 display:none;position:fixed;inset:0;

 background:#050000;place-items:center;

}

#scare.show{display:grid;animation:flash .15s steps(2) 5}

.face{font-size:min(65vw,350px);animation:shake .08s infinite}

@keyframes flash{50%{background:#850000}}

@keyframes shake{

 0%{transform:translate(5px,-4px)}

 50%{transform:translate(-5px,4px)}

 100%{transform:translate(3px,2px)}

}

#close{background:white;color:black;margin-top:20px}

</style>

</head>

<body>

<div class="card">

 <div style="font-size:60px">🎄🎁✨</div>

 <h1>Для тебя!</h1>

 <p>Тебя ждёт особенный сюрприз!</p>

 <button onclick="surprise()">Открыть поздравление 🎁</button>

</div>

<div id="scare">

 <div>

  <div class="face">😱</div>

  <h1>ААА! ПОПАЛСЯ!</h1>

  <button id="close" onclick="document.getElementById('scare').classList.remove('show')">Назад</button>

 </div>

</div>

<script>

function surprise(){

 document.getElementById('scare').classList.add('show');

 try{

  const ctx=new(window.AudioContext||window.webkitAudioContext)();

  const osc=ctx.createOscillator();

  const gain=ctx.createGain();

  osc.type='sawtooth';

  osc.frequency.setValueAtTime(180,ctx.currentTime);

  osc.frequency.exponentialRampToValueAtTime(880,ctx.currentTime+0.18);

  gain.gain.setValueAtTime(0.001,ctx.currentTime);

  gain.gain.linearRampToValueAtTime(0.18,ctx.currentTime+0.03);

  gain.gain.exponentialRampToValueAtTime(0.001,ctx.currentTime+0.65);

  osc.connect(gain);

  gain.connect(ctx.destination);

  osc.start();

  osc.stop(ctx.currentTime+0.67);

 }catch(e){}

}

</script>

</body>

</html>
