<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Birthday Surprise 🎈</title>
<style>
  body{margin:0;font-family:Arial,Helvetica,sans-serif;background:#cfefff;text-align:center;overflow:hidden}
  .screen{display:none;min-height:100vh;padding:20px;box-sizing:border-box}
  .active{display:block}

  .balloon{
    margin:60px auto;
    width:140px;height:170px;
    background:radial-gradient(circle at 30% 30%, #ff9adf, #ff2f9a);
    border-radius:50% 50% 45% 45%;
    color:#fff;font-size:36px;
    display:flex;align-items:center;justify-content:center;
    box-shadow:0 15px 30px rgba(0,0,0,.2);
    cursor:pointer;transition:transform .2s;
  }
  .balloon:active{transform:scale(.9)}

  button{
    padding:12px 22px;border:none;border-radius:30px;
    background:#1e90ff;color:white;font-size:16px;margin-top:20px
  }

  .cake-area{margin-top:30px}
  .cake{font-size:100px}
  .plate{font-size:90px;margin-top:10px}
  .eat-note{font-size:18px;margin-top:10px}

  .final-text{
    font-size:44px;font-weight:bold;
    background:linear-gradient(90deg,red,orange,yellow,green,blue,indigo,violet);
    -webkit-background-clip:text;color:transparent
  }
</style>
</head>
<body>

<!-- BALLOON SCREEN -->
<div id="balloonScreen" class="screen active">
  <h2>Pop the Balloon 🎈</h2>
  <div id="balloon" class="balloon">1</div>
</div>

<!-- MESSAGE SCREEN -->
<div id="messageScreen" class="screen">
  <h2 id="messageText"></h2>
  <button onclick="nextStep()">Next 🎈</button>
</div>

<!-- CANDLES -->
<div id="candleScreen" class="screen">
  <h2>Blow the candles in 3…2…1 💨</h2>
  <div style="font-size:28px" id="candles">🕯️ 🕯️ 🕯️ 🕯️ 🕯️ 🕯️ 🕯️ 🕯️ 🕯️ 🕯️ 🕯️ 🕯️ 🕯️ 🕯️ 🕯️ 🕯️ 🕯️ 🕯️ 🕯️ 🕯️ 🕯️</div>
  <div class="cake">🎂</div>
  <button onclick="blowCandles()">Blow</button>
</div>

<!-- CUT CAKE -->
<div id="cutScreen" class="screen">
  <h2>Cut the Cake 🍰</h2>
  <div class="cake">🎂</div>
  <button onclick="cutCake()">Cut Cake</button>
</div>

<!-- EAT CAKE -->
<div id="eatScreen" class="screen">
  <h2>Tap the cake to eat 😋</h2>
  <div class="cake-area">
    <div id="plate" class="plate">🍽️</div>
    <div id="cakeSlice" class="cake">🍰</div>
    <div class="eat-note">Keep tapping to eat it...</div>
  </div>
</div>

<!-- FINAL -->
<div id="finalScreen" class="screen">
  <div class="final-text">HAPPY BIRTHDAY 🎉🎈</div>
  <p>Sorry I'm unable to give you a gift, but I hope this made you smile 💙</p>
</div>

<script>
const messages=[
"Happy Birthday 🎉",
"We met by accident but rn you're the most trustable person for me.",
"Funny how a random meeting turned into someone I trust the most.",
"Happy Birthday to my favorite unexpected person.",
"I didn’t plan you, but I’m so glad life did.",
"You’re proof that accidents can be beautiful.",
"Trust came easy with you—and that’s rare.",
"Happy Birthday to my calm in the chaos.",
"Happy Birthday to someone who genuinely matters to me.",
"Beshi beshi kore cake khan 🎂 Cake calories don’t count today—science says so.",
"Happy Birthday! Thanks for being the weird to my weirder.",
"Another year of you being ridiculously lovable, annoying, and hilarious. Don’t change 🧸💖",
"Happy Birthday, pookiest soul I know 🧸",
"Somehow you became my comfort person.",
"Happy Birthday—thank you for being you 🤍",
"You make ordinary days feel special.",
"I’m grateful for your existence.",
"You deserve all the happiness today.",
"May this year bring you peace and joy.",
"Keep shining like you always do.",
"Ready for the cake surprise? 🎂"
];

let index=0;
const balloon=document.getElementById('balloon');

balloon.onclick=()=>{
  showMessage();
};

function showMessage(){
  balloonScreen.classList.remove('active');
  messageScreen.classList.add('active');
  messageText.innerText=messages[index];
}

function nextStep(){
  messageScreen.classList.remove('active');
  index++;
  if(index<messages.length){
    balloon.innerText=index+1;
    balloonScreen.classList.add('active');
  }else{
    candleScreen.classList.add('active');
  }
}

function blowCandles(){
  candles.innerText='💨💨💨';
  setTimeout(()=>{
    candleScreen.classList.remove('active');
    cutScreen.classList.add('active');
  },1200);
}

function cutCake(){
  cutScreen.classList.remove('active');
  eatScreen.classList.add('active');
}

let eatCount=0;
const cakeSlice=document.getElementById('cakeSlice');

cakeSlice.onclick=()=>{
  eatCount++;
  if(eatCount===3) cakeSlice.innerText='🍰';
  if(eatCount===6) cakeSlice.innerText='🧁';
  if(eatCount===9) cakeSlice.innerText='🥄';
  if(eatCount>11){
    eatScreen.classList.remove('active');
    finalScreen.classList.add('active');
  }
};
</script>

</body>
</html>
