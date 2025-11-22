<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For My Love ❤️</title>
<style>
body, html{margin:0;height:100%;overflow:hidden;font-family:sans-serif;background:black;color:white;text-align:center;transition:background 0.8s;}
.wrap{height:100%;display:flex;align-items:center;justify-content:center;position:relative;}
.hearts{pointer-events:none;position:absolute;inset:0;}
.heart{position:absolute;font-size:20px;color:red;animation:float 5s linear infinite;}
@keyframes float{0%{transform:translateY(100vh);opacity:1}100%{transform:translateY(-10vh);opacity:0}}
.card{padding:20px;background:rgba(0,0,0,0.3);border-radius:15px;}
.title3d{font-size:36px;font-weight:bold;margin-top:40px;text-shadow: 3px 3px 10px #ff69b4, -3px -3px 10px #ff1493; cursor:pointer; user-select:none;}
.message{margin-top:20px;font-size:20px;opacity:0;transition:all 0.4s;line-height:1.5;text-align:center;}
.message.show{opacity:1;}
.progress{margin-top:10px;font-size:16px;color:#ffcc00;}
</style>
</head>
<body>
<div class="wrap" id="wrap">
  <div class="hearts" id="hearts"></div>
  <div class="card" id="card">
    <div id="title" class="title3d">Tap to Show Message ❤️</div>
    <div id="message" class="message"></div>
    <div class="progress" id="progress">1 / 10</div>
  </div>
</div>

<!-- Embedded Background Music -->
<audio id="bgMusic" autoplay loop>
  <source src="data:audio/mpeg;base64,//uQxAAAAAAAAAAAAAAAAAAAAAA..." type="audio/mpeg">
</audio>

<script>
const bgMusic = document.getElementById('bgMusic');
const title = document.getElementById('title');
const message = document.getElementById('message');
const progress = document.getElementById('progress');
const wrap = document.getElementById('wrap');
const hearts = document.getElementById('hearts');

const slides=[
{title:"❤️ 1. Why She’s Special to You", text:"You’re not just another person in my life… you’re the one who feels meant for me.<br>Something in you fits perfectly in places I didn’t even know were empty."},
{title:"❤️ 2. Why She’s Important", text:"You matter to me in ways I can’t replace.<br>My day feels incomplete if even a single moment passes without you in it."},
{title:"❤️ 3. Why Only She Stands Out", text:"Other people exist, but you stand out without trying.<br>Your presence has a purity and peace no one else carries."},
{title:"❤️ 4. Why You Love Only Her", text:"My heart chose you without hesitation, without confusion.<br>It’s not a decision… it’s a feeling that keeps pulling me back to you."},
{title:"❤️ 5. Why You Imagine a Life With Her", text:"When I think of the future, your name naturally appears in it.<br>Not because I forced it… but because loving you feels like the right place to stay."},
{title:"❤️ 6. Why She’s Your Everything", text:"I don’t need a thousand people around me — just you.<br>You’re the peace, the comfort, the smile, and the home my heart returns to."},
{title:"❤️ 7. Why Your Love Never Decreases", text:"My love for you doesn’t fade with time… it deepens.<br>The more I know you, the more reasons my heart finds to stay."},
{title:"❤️ 8. Why You Love Her As She Is", text:"I adore you exactly the way you are — every flaw, every softness.<br>You don’t need to change; you’re already everything I prayed for quietly."},
{title:"❤️ 9. Why You Feel Safe With Her", text:"You’re the only person who gets my silence, my chaos, and my softness.<br>With you, even my unspoken emotions feel understood."},
{title:"❤️ 10. Why She’s Enough for You", text:"I don’t look for anyone else because my heart doesn’t wander.<br>It has already found its place — and that place is you."}
];

let idx = 0;

// Show slide on tap
title.addEventListener('click', ()=>{
  showSlide(idx);
  idx++;
});

function showSlide(i){
  if(i>=slides.length){
    message.innerHTML="All lines read ❤️";
    message.classList.add('show');
    progress.innerHTML=slides.length+" / "+slides.length;
    return;
  }
  wrap.style.background = `linear-gradient(135deg, hsl(${i*36},70%,10%), hsl(${i*36},50%,20%))`;
  title.textContent = slides[i].title;
  message.innerHTML = slides[i].text;
  message.classList.add('show');
  progress.innerHTML=(i+1)+" / "+slides.length;
  createHearts();
}

function createHearts(){
  for(let j=0;j<12;j++){
    let h=document.createElement('div');
    h.className='heart';
    h.innerHTML='❤️';
    h.style.left=Math.random()*100+'vw';
    h.style.fontSize=(20+Math.random()*30)+'px';
    hearts.appendChild(h);
    setTimeout(()=>h.remove(),5000);
  }
}
</script>
</body>
</html>
