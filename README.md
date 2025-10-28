<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>For Rehan — A Gentle Reveal</title>
  <style>
    :root{
      --sun-1:#2b0a3a;
      --sun-2:#6d2671;
      --sun-3:#ff7eb6;
      --soft:#f6f7fb;
      --muted:#c7cbd6;
      --accent:#ffd6ea;
      --radius:16px;
    }
    *{box-sizing:border-box}
    html,body{
      height:100%;margin:0;
      background:linear-gradient(180deg,var(--sun-1),var(--sun-2),#ff9ab3);
      font-family:Inter,Segoe UI,Roboto;
      color:var(--soft);
    }

    .wrap{max-width:920px;margin:36px auto;padding:20px}
    .card{
      background:rgba(0,0,0,0.18);
      border-radius:var(--radius);
      padding:28px;
      backdrop-filter:blur(6px);
      box-shadow:0 10px 30px rgba(0,0,0,0.4);
    }

    .stage{
      min-height:60vh;
      padding:32px;margin:22px 0;
      border-radius:14px;
      opacity:0;transform:translateY(16px);
      transition:all .6s cubic-bezier(.2,.9,.2,1);
    }
    .stage.visible{opacity:1;transform:none}
    .soft{background:rgba(255,255,255,0.05)}
    .dark{background:rgba(0,0,0,0.12)}

    .revealBtn{
      padding:12px 18px;border-radius:12px;
      border:0;cursor:pointer;
      background:linear-gradient(90deg,#ffd6ea,#ffb3d1);
      color:#2b0a3a;font-weight:700;
    }
    .revealBtn.secondary{
      background:transparent;
      border:1px solid rgba(255,255,255,0.25);
      color:#fff;
    }

    .sanaLine{
      opacity:0;transform:translateY(10px);
      transition:all .4s;
      margin:6px 0;padding:10px 14px;
      border-radius:10px;
      background:rgba(255,255,255,0.05);
    }
    .sanaLine.visible{opacity:1;transform:none}

    #confetti{
      position:fixed;left:0;top:0;width:100vw;height:100vh;
      pointer-events:none;z-index:1000;
    }
  </style>
</head>

<body>

<audio id="bgAudio" src="lofi.mp3" loop></audio>
<canvas id="confetti"></canvas>

<div class="wrap">
<div class="card">

<h1>For Rehan — Take this slow</h1>
<p class="lead" style="color:var(--muted)">Scroll aaram se… sab ek-ek step me dikhunga.</p>

<div class="stage soft">
  <h2>Hey Rehan —</h2>
  <p>You gave love genuinely. That's powerful. ❤️</p>
</div>

<div class="stage dark">
  <h2>You were real.</h2>
  <p>Tera dil saccha tha. Tum galat nahi the.</p>
</div>

<div class="stage soft" id="stage-3">
  <h2>A small thing about Sana…</h2>
  <p>Only when you feel ready 👇</p>
  <button class="revealBtn" id="softReveal">I want to know</button>
  <br><br>
  <button class="revealBtn secondary" id="toggleAudio">Play Lo-fi</button>
</div>

<div class="stage dark" id="revealStage">
  <h2>A gentle truth</h2>
  <p>Ready? We’ll reveal her words slowly…</p>
  <button class="revealBtn" id="revealTruth">Reveal Sana’s words</button>
</div>

<div class="stage soft" id="sanaStage" style="display:none;">
  <h2>Exact lines Sana told me</h2>
  <div id="sanaList">
    <div class="sanaLine">Troyee ne unsai kabhi pyar kiya hi nhi tha</div>
    <div class="sanaLine">bass dikhawa tha</div>
    <div class="sanaLine">uske saath khel rahi thi</div>
    <div class="sanaLine">usne khud bola hai mujhe</div>
    <div class="sanaLine">Devdas ban kar koi fayda nahi</div>
  </div>
  <button class="revealBtn" id="revealNext">Next line</button>
  <button class="revealBtn secondary" id="revealAll">Reveal all</button>
</div>

<div class="stage dark" id="angerStage" style="display:none;">
  <h2>Anger is okay</h2>
  <p>Feel it — then use it to level up. Gym. Studies. Future. 🔥</p>
</div>

<div class="stage soft" id="surpriseStage" style="display:none;">
  <h2>A gift for you</h2>
  <div id="giftArea" style="display:none;">
    <strong>From Ali:</strong>  
    <p>Rehan, you're stronger than this moment. We got your back. ❤️</p>
  </div>
  <button class="revealBtn" id="openGift">Open</button>
</div>

<div class="stage dark" id="finalStage" style="display:none;">
  <h2>When you rise again…</h2>
  <ul>
    <li>The wound is where light enters.</li>
    <li>You deserve loyalty, always.</li>
  </ul>
  <button class="revealBtn" id="celebrate">Confetti 🎉</button>
</div>

<footer style="margin-top:20px;color:var(--muted);font-size:12px;">
Made with love by Ali ❤️
</footer>

</div>
</div>

<script>
// Reveal sections on scroll
const observer = new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(e.isIntersecting) e.target.classList.add("visible");
  });
},{threshold:.3});
document.querySelectorAll('.stage').forEach(s=>observer.observe(s));

// Audio control
const audio=document.getElementById("bgAudio");
document.getElementById("toggleAudio").onclick=()=>{
  if(audio.paused){audio.play();toggleAudio.textContent="Pause Lo-fi";}
  else {audio.pause();toggleAudio.textContent="Play Lo-fi";}
};

// Sana words logic
const sanaStage=document.getElementById("sanaStage");
const sanaLines=[...document.querySelectorAll(".sanaLine")];
let idx=0;

document.getElementById("softReveal").onclick=()=>{
  document.getElementById("revealStage").scrollIntoView({behavior:"smooth"});
};

document.getElementById("revealTruth").onclick=()=>{
  sanaStage.style.display="block";
  sanaStage.scrollIntoView({behavior:"smooth"});
  revealNext();
  setTimeout(()=>document.getElementById("angerStage").style.display="block",1500);
  setTimeout(()=>document.getElementById("surpriseStage").style.display="block",2700);
  setTimeout(()=>document.getElementById("finalStage").style.display="block",3900);
};

function revealNext(){
  if(idx<sanaLines.length){
    sanaLines[idx].classList.add("visible");
    idx++;
  }
}

document.getElementById("revealNext").onclick=revealNext;
document.getElementById("revealAll").onclick=()=>{
  sanaLines.forEach(l=>l.classList.add("visible"));
  idx=sanaLines.length;
};

document.getElementById("openGift").onclick=()=>{
  document.getElementById("giftArea").style.display="block";
};

// Confetti Celebration 🎉
const confettiCanvas=document.getElementById("confetti");
const ctx=confettiCanvas.getContext("2d");
confettiCanvas.width=innerWidth;
confettiCanvas.height=innerHeight;

function shootConfetti(){
  const colors=["#ffb3d1","#ffd6ea","#ffffff"];
  let particles=[];
  for(let i=0;i<150;i++){
    particles.push({
      x:Math.random()*innerWidth,
      y:Math.random()*innerHeight-innerHeight,
      r:Math.random()*6+2,
      c:colors[Math.floor(Math.random()*colors.length)],
      v:Math.random()*3+2
    });
  }
  function draw(){
    ctx.clearRect(0,0,innerWidth,innerHeight);
    particles.forEach(p=>{
      ctx.beginPath();
      ctx.arc(p.x,p.y,p.r,0,Math.PI*2);
      ctx.fillStyle=p.c;ctx.fill();
      p.y+=p.v;
    });
    requestAnimationFrame(draw);
  }
  draw();
}
document.getElementById("celebrate").onclick=shootConfetti;
</script>

</body>
</html>
