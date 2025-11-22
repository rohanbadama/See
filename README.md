

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Romantic Page</title>
<style>
  body {
    margin: 0;
    padding: 0;
    background: linear-gradient(120deg, #ffdde1, #ee9ca7);
    font-family: 'Arial', sans-serif;
    overflow: hidden;
    perspective: 1000px;
  }
  #message {
    position: absolute;
    top: 40%;
    width: 100%;
    text-align: center;
    font-size: 2rem;
    color: #ff4d6d;
    text-shadow: 2px 2px 10px #fff, -2px -2px 10px #ffb6c1;
    transform: rotateY(0deg);
    transition: transform 0.5s;
    cursor: pointer;
  }
  .hearts {
    position: absolute;
    width: 20px;
    height: 20px;
    background: url('https://i.imgur.com/O6U7K6H.png') no-repeat center center / cover;
    pointer-events: none;
    animation: floatUp linear infinite;
  }
  @keyframes floatUp {
    0% {transform: translateY(100vh) scale(0.5); opacity:1;}
    100% {transform: translateY(-10vh) scale(1); opacity:0;}
  }
  .cartoon {
    position: absolute;
    width: 80px;
    animation: floatCartoon linear infinite;
  }
  @keyframes floatCartoon {
    0% {left:-100px; transform: rotate(0deg);}
    50% {left:50vw; transform: rotate(360deg);}
    100% {left:110vw; transform: rotate(720deg);}
  }
</style>
</head>
<body>

<audio id="bgMusic" loop>
  <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
</audio>

<div id="message">Tap me sweetheart 💖</div>

<script>
const messages = [
"Tap me sweetheart 💖",
"❤️ 1. Why She’s Special to You: “You’re not just another person in my life… you’re the one who feels meant for me. Something in you fits perfectly in places I didn’t even know were empty.”",
"❤️ 2. Why She’s Important: “You matter to me in ways I can’t replace. My day feels incomplete if even a single moment passes without you in it.”",
"❤️ 3. Why Only She Stands Out: “Other people exist, but you stand out without trying. Your presence has a purity and peace no one else carries.”",
"❤️ 4. Why You Love Only Her: “My heart chose you without hesitation, without confusion. It’s not a decision… it’s a feeling that keeps pulling me back to you.”",
"❤️ 5. Why You Imagine a Life With Her: “When I think of the future, your name naturally appears in it. Not because I forced it… but because loving you feels like the right place to stay.”",
"❤️ 6. Why She’s Your Everything: “I don’t need a thousand people around me — just you. You’re the peace, the comfort, the smile, and the home my heart returns to.”",
"❤️ 7. Why Your Love Never Decreases: “My love for you doesn’t fade with time… it deepens. The more I know you, the more reasons my heart finds to stay.”",
"❤️ 8. Why You Love Her As She Is: “I adore you exactly the way you are — every flaw, every softness. You don’t need to change; you’re already everything I prayed for quietly.”",
"❤️ 9. Why You Feel Safe With Her: “You’re the only person who gets my silence, my chaos, and my softness. With you, even my unspoken emotions feel understood.”",
"❤️ 10. Why She’s Enough for You: “I don’t look for anyone else because my heart doesn’t wander. It has already found its place — and that place is you.”",
"So I love you 💖"
];

let index = 0;
const messageDiv = document.getElementById('message');
const bgMusic = document.getElementById('bgMusic');

function nextMessage() {
  if(index === 0) { bgMusic.play().catch(()=>{}); } // Play music on first tap
  if(index < messages.length - 1){
    index++;
    messageDiv.textContent = messages[index];
    messageDiv.style.transform = `rotateY(${Math.random()*20-10}deg)`;
  }
}
document.body.addEventListener('click', nextMessage);

// Hearts particles
function createHeart() {
  const heart = document.createElement('div');
  heart.className = 'hearts';
  heart.style.left = Math.random()*100 + 'vw';
  heart.style.animationDuration = (Math.random()*5 + 5) + 's';
  document.body.appendChild(heart);
  setTimeout(()=>heart.remove(), 6000);
}
setInterval(createHeart, 300);

// Cartoon animations
const cartoonImages = [
  "https://i.imgur.com/Jd8TtXb.png", // Doramon
  "https://i.imgur.com/fpFTnsH.png"  // Ninja Hattori
];
function createCartoon() {
  const c = document.createElement('img');
  c.src = cartoonImages[Math.floor(Math.random()*cartoonImages.length)];
  c.className = 'cartoon';
  c.style.top = (Math.random()*70 + 10) + 'vh';
  c.style.animationDuration = (Math.random()*10 + 10)+'s';
  document.body.appendChild(c);
  setTimeout(()=>c.remove(), 12000);
}
setInterval(createCartoon, 5000);
</script>

</body>
</html>
