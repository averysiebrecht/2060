# 2060


<!DOCTYPE html>
<html lang="en" >

<head>

  <meta charset="UTF-8">
  
<link rel="apple-touch-icon" type="image/png" href="https://static.codepen.io/assets/favicon/apple-touch-icon-5ae1a0698dcc2402e9712f7d01ed509a57814f994c660df9f7a952f3060705ee.png" />
<meta name="apple-mobile-web-app-title" content="CodePen">

<link rel="shortcut icon" type="image/x-icon" href="https://static.codepen.io/assets/favicon/favicon-aec34940fbc1a6e787974dcd360f2c6b63348d4b1f4e06c77743096d55480f33.ico" />

<link rel="mask-icon" type="" href="https://static.codepen.io/assets/favicon/logo-pin-8f3771b1072e3c38bd662872f6b673a722f4b3ca2421637d5596661b4e2132cc.svg" color="#111" />


  <title>CodePen - 2061-7</title>
  
  
  
  
<style>
#myCanvas{
  background:lightgrey;
  border-style:solid;
}

#score{
  font-size:150%;
}
</style>

  
  
  
  

</head>

<body translate="no" >
  <h2>Score: <span id="score">0</span></h2>
<canvas id="myCanvas" width="600" height="400">
  Your browser does not support canvas
</canvas>
  
  
  
      <script id="rendered-js" >
console.clear();

const canvas = document.getElementById("myCanvas");
const ctx = canvas.getContext("2d");

function makeBot(x, y, r) {
  let bot = {};
  bot.x = x;
  bot.y = y;
  bot.r = r;
  bot.dx = 1;
  bot.dy = -0.1;
  bot.theta = Math.atan2(bot.dy, bot.dx);
  return bot;
}

let myBot = makeBot(20, 30, 15);

function drawBot(bot) {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  ctx.beginPath();
  ctx.arc(bot.x, bot.y, bot.r, 0, 2 * Math.PI);
  ctx.stroke();
  ctx.moveTo(bot.x, bot.y);
  ctx.lineTo(
    bot.x + bot.r * Math.cos(bot.theta),
    bot.y + bot.r * Math.sin(bot.theta)
  );
  ctx.stroke();
}

function moveBot(bot) {
  bot.x = bot.x + bot.dx;
  bot.y = bot.y + bot.dy;
  drawBot(bot);
  bot.theta = Math.atan2(bot.dy, bot.dx);

  if (bot.y - bot.r < 0) {
    bot.dy = -bot.dy;
  }
  
  if(bot.x + bot.r >= canvas.width){
    bot.dx = -bot.dx;
  }
  
  
  
}

setInterval(moveBot, 10, myBot);
    </script>

  

</body>

</html>
 
