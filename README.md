<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>For Rehan — A Gentle Reveal</title>
  <style>
    /* --- Sunset theme + soft styling --- */
    :root{
      --sun-1: #2b0a3a; /* deep purple */
      --sun-2: #6d2671; /* purple */
      --sun-3: #ff7eb6; /* pink */
      --card: rgba(255,255,255,0.03);
      --soft:#f6f7fb;
      --muted:#c7cbd6;
      --accent:#ffd6ea;
      --radius:16px;
    }
    *{box-sizing:border-box}
    html,body{height:100%;margin:0;background:linear-gradient(180deg,var(--sun-1) 0%, var(--sun-2) 45%, #ff9ab3 100%);color:var(--soft);font-family:Inter,ui-sans-serif,system-ui,Segoe UI,Roboto,'Helvetica Neue',Arial}
    a{color:var(--accent)}

    .wrap{max-width:920px;margin:36px auto;padding:28px}
    .card{background:linear-gradient(180deg, rgba(0,0,0,0.18), rgba(255,255,255,0.02));border-radius:var(--radius);padding:28px;box-shadow:0 10px 30px rgba(2,6,23,0.4);backdrop-filter:blur(6px);}

    h1{font-size:28px;margin:0 0 8px}
    p.lead{color:var(--muted);margin-top:6px}

    .stages{margin-top:22px}
    .stage{min-height:60vh;padding:32px;border-radius:14px;margin:22px 0;display:flex;flex-direction:column;justify-content:center;align-items:flex-start;gap:18px;opacity:0;transform:translateY(16px) scale(0.995);transition:all 620ms cubic-bezier(.2,.9,.2,1)}
    .stage.visible{opacity:1;transform:none}
    .stage .title{font-size:22px;letter-spacing:0.2px}
    .stage .text{font-size:16px;line-height:1.55;color:var(--soft);max-width:880px}

    .soft{background:linear-gradient(180deg, rgba(255,255,255,0.03), rgba(255,255,255,0.01));border:1px solid rgba(255,255,255,0.03)}
    .dark{background:linear-gradient(180deg, rgba(0,0,0,0.12), rgba(0,0,0,0.06));border:1px solid rgba(255,255,255,0.02)}

    .revealBtn{appearance:none;border:0;padding:12px 18px;border-radius:12px;background:linear-gradient(90deg,#ffd6ea,#ffb3d1);color:#2b0a3a;font-weight:800;cursor:pointer}
    .revealBtn.secondary{background:transparent;border:1px solid rgba(255,255,255,0.06);color:var(--soft)}

    .sanaList{display:flex;flex-direction:column;gap:12px;margin-top:10px}
    .sanaLine{opacity:0;transform:translateY(10px);transition:all 480ms ease-in-out;padding:12px 14px;border-radius:10px;background:linear-gradient(90deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));border:1px solid rgba(255,255,255,0.02)}
    .sanaLine.visible{opacity:1;transform:none}

    .audioControls{display:flex;gap:10px;align-items:center;margin-top:8px}
    .playBtn{appearance:none;border:0;padding:8px 12px;border-radius:10px;background:linear-gradient(90deg,#fff1f8,#ffd6ea);color:#2b0a3a;cursor:pointer;font-weight:700}

    footer{margin-top:18px;color:var(--muted);font-size:13px}

    canvas#confetti{position:fixed;left:0;top:0;pointer-events:none;z-index:999}

    @media (max-width:700px){.wrap{padding:18px}.card{padding:18px}h1{font-size:22px}}
  </style>
</head>
<body>
  <audio controls autoplay>
  <source src="Alag%20aasman%20-%20(Lo-Fi)%20%20Anuv%20jain%20%20Prod.%20By%20Flawed%20-%20Flawed.mp3" type="audio/mpeg">
  Your browser does not support the audio element.
</audio>
  <canvas id="confetti"></canvas>

  <div class="wrap">
    <div class="card">
      <h1>For Rehan — Take this slow</h1>
      <p class="lead">This space is for you. Scroll slowly — I’ll reveal things step by step. Everything here is true and honest. — Ali</p>

      <div class="stages">

        <section class="stage soft" data-stage="1">
          <div class="title">Hey Rehan —</div>
          <div class="text">I know the hurt is real. You gave your heart honestly. Hosteller memories make everything louder — the late-night plans, the small promises. Take a breath. We're with you.</div>
        </section>

        <section class="stage dark" data-stage="2">
          <div class="title">You were real.</div>
          <div class="text">Jo pyaar tune diya — woh saccha tha. Plans banana, future imagine karna — that honesty is rare. Tu galat nahi tha. Tumhara dil genuine tha.</div>
        </section>

        <section class="stage soft" data-stage="3">
          <div class="title">A small thing Sana told me</div>
          <div class="text">If you're ready I can share what Sana told me. No pressure — only when you want to know. Your peace comes first.</div>
          <div class="audioControls">
            <button class="playBtn" id="toggleAudio">Play Lo‑fi</button>
            <small style="color:var(--muted)"></small>
          </div>
          <button class="revealBtn" id="softReveal">I want to know (gently)</button>
        </section>

        <section class="stage dark" data-stage="4" id="revealStage">
          <div class="title">A gentle truth</div>
          <div class="text" id="revealText">When you're ready—press the button below. We'll reveal the words Sana spoke, one at a time. Nothing else added. Only her exact words.</div>
          <div style="display:flex;gap:12px;margin-top:12px;">
            <button class="revealBtn" id="revealTruth">Reveal Sana's words</button>
            <button class="revealBtn secondary" id="notNow">Not now</button>
          </div>
        </section>

        <!-- SANA WORDS: single column, reveal one-by-one -->
        <section class="stage soft" data-stage="5" id="sanaStage" style="display:none;">
          <div class="title">The words spoken by Sana</div>
          <div class="text">Below are the exact lines Sana told me. I have not added or changed any words — they appear one by one so you can take them in slowly.</div>
          <div class="sanaList" id="sanaList">
            <div class="sanaLine" data-idx="0">Troyee ne unsai kabhi pyar kiya hi nhi tha</div>
            <div class="sanaLine" data-idx="1">bss dikhawa tha</div>
            <div class="sanaLine" data-idx="2">unke sath khel rhi thi bss</div>
            <div class="sanaLine" data-idx="3">usne khud bola hai mujhe</div>
            <div class="sanaLine" data-idx="4">dev das ban kar koi feida nhi hai</div>
          </div>
          <div style="margin-top:12px;display:flex;gap:10px;align-items:center;">
            <button class="revealBtn" id="revealNext">Reveal next line</button>
            <button class="revealBtn secondary" id="autoReveal">Auto reveal</button>
            <button class="revealBtn secondary" id="skipReveal">Reveal all</button>
          </div>
        </section>

        <section class="stage dark" data-stage="6" style="display:none;" id="angerStage">
          <div class="title">It’s okay to be angry — and use it</div>
          <div class="text">Anger is valid. Koi tere saath khel raha tha — that hurts. Feel it for a bit, then channel it — gym, study, new goals. Think of your family and the effort they put in; use this energy to build yourself stronger.</div>
        </section>

        <section class="stage soft" data-stage="7" style="display:none;" id="surpriseStage">
          <div class="title">A small surprise</div>
          <div class="text">Open the gift from Ali — a short message to remind you that you're not alone.</div>
          <div style="margin-top:12px;display:flex;gap:10px;align-items:center;">
            <button class="revealBtn" id="openGift">Open the gift</button>
            <button class="revealBtn secondary" id="downloadNote">Download the note</button>
          </div>
          <div id="giftArea" class="secret" style="margin-top:12px;display:none;">
            <strong>From Ali:</strong>
            <p style="margin:8px 0">Rehan, you're braver than you feel today. You deserved honesty, not pretend. We see you. We got you. — Ali</p>
          </div>
        </section>

        <section class="stage dark" data-stage="8" style="display:none;" id="finalStage">
          <div class="title">For when you stand up again</div>
          <div class="text">A few lines to hold close:</div>
          <ul style="margin-top:10px;color:var(--muted);">
            <li>"The wound is where the light enters." — keep learning, keep shining.</li>
            <li>"You are not a mistake. You are a person with a big heart."</li>
            <li>"Chahe kuch bhi ho, tu deserve karta hai woh jo teri kadar kare."</li>
          </ul>
          <div style="margin-top:12px;display:flex;gap:10px;">
            <button class="revealBtn" id="celebrate">Show a little confetti</button>
            <button class="revealBtn secondary" id="shareBtn">Copy a supportive message</button>
          </div>
        </section>

      </div>

      <footer>>Made with love and care.. (bro jyada kuch nahin but apne bhai ke liye itna hi kar payaa.. mujhe direct sach batane se jyada achha ye hi laga.. im sorry if it hurt u but bro ek na ek din to tujhe ye pata lagna hi tha....</footer>
    </div>
  </div>

  <!-- Background audio: replace `lofi.mp3` with your file or put a file of that name in same folder -->
  <audio id="bgAudio" src="lofi.mp3" loop preload="none"></audio>

<script>
  // IntersectionObserver to reveal stages on scroll
  const stages = document.querySelectorAll('.stage');
  const io = new IntersectionObserver((entries)=>{
    entries.forEach(e=>{ if(e.isIntersecting) e.target.classList.add('visible'); });
  },{threshold:0.18});
  stages.forEach(s=>io.observe(s));

  // audio controls
  const bgAudio = document.getElementById('bgAudio');
  const toggleAudio = document.getElementById('toggleAudio');
  let audioPlaying = false;
  toggleAudio.addEventListener('click', ()=>{
    if(!audioPlaying){
      // try play
      bgAudio.play().then(()=>{
        audioPlaying = true; toggleAudio.textContent = 'Pause Lo‑fi';
      }).catch(()=>{
        // show small hint — file missing
        toggleAudio.textContent = 'Audio not found — add lofi.mp3';
        setTimeout(()=>toggleAudio.textContent='Play Lo‑fi',2500);
      });
    } else { bgAudio.pause(); audioPlaying=false; toggleAudio.textContent='Play Lo‑fi'; }
  });

  // gentle reveal flow
  const softReveal = document.getElementById('softReveal');
  const revealStage = document.getElementById('revealStage');
  const revealTruth = document.getElementById('revealTruth');
  const notNow = document.getElementById('notNow');
  const sanaStage = document.getElementById('sanaStage');
  const truthStage = document.getElementById('truthStage');
  const angerStage = document.getElementById('angerStage');
  const surpriseStage = document.getElementById('surpriseStage');
  const finalStage = document.getElementById('finalStage');

  softReveal?.addEventListener('click', ()=>{ revealStage.scrollIntoView({behavior:'smooth',block:'center'}); revealStage.classList.add('visible'); });

  revealTruth?.addEventListener('click', ()=>{
    // show sana stage and reveal lines one by one
    sanaStage.style.display='block';
    sanaStage.scrollIntoView({behavior:'smooth',block:'center'});
    // reveal first line immediately
    revealSanaLinesSequential(0);
    // show next stages with delays
    setTimeout(()=>{ angerStage.style.display='block'; angerStage.scrollIntoView({behavior:'smooth',block:'center'}); },1600);
    setTimeout(()=>{ surpriseStage.style.display='block'; },3000);
    setTimeout(()=>{ finalStage.style.display='block'; },4200);
  });

  notNow?.addEventListener('click', ()=>{ alert('No pressure. Take your time. We are here when you\'re ready.'); });

  // SANA lines logic
  const sanaLines = Array.from(document.querySelectorAll('.sanaLine'));
  let current = 0;
  const revealNextBtn = document.getElementById('revealNext');
  const autoRevealBtn = document.getElementById('autoReveal');
  const skipRevealBtn = document.getElementById('skipReveal');
  let autoTimer = null;

  function showLine(i){ if(i<0||i>=sanaLines.length) return; sanaLines[i].classList.add('visible'); }
  function revealSanaLinesSequential(startIndex=0){ current = startIndex; showLine(current); }

  revealNextBtn?.addEventListener('click', ()=>{ current++; if(current<sanaLines.length) showLine(current); else revealNextBtn.disabled=true; });

  autoRevealBtn?.addEventListener('click', ()=>{
    if(autoTimer) { clearInterval(autoTimer); autoTimer=null; autoRevealBtn.textContent='Auto reveal'; return; }
    autoRevealBtn.textContent='Stop auto';
    let i=0; showLine(0);
    autoTimer = setInterval(()=>{ i++; if(i>=sanaLines.length){ clearInterval(autoTimer); autoTimer=null; autoRevealBtn.textContent='Auto reveal'; } else showLine(i); },900);
  });

  skipRevealBtn?.addEventListener('click', ()=>{ sanaLines.forEach((ln)=>ln.classList.add('visible')); if(autoTimer){ clearInterval(autoTimer); autoTimer=null; autoRevealBtn.textContent='Auto reveal'; } });

  // gift open and download
  const openGift = document.getElementById('openGift');
  const giftArea = document.getElementById('giftArea');
  openGift?.addEventListener('click', ()=>{ giftArea.style.display='block'; giftArea.scrollIntoView({behavior:'smooth',block:'center'}); });

  const downloadNote = document.getElementById('downloadNote');
  downloadNote?.addEventListener('click', ()=>{
    const note = `Rehan —

You're brave. You were honest. The loss is theirs. We stand with you.

— Alisher`;
    const blob = new Blob([note],{type:'text/plain'});
    const url = URL.createObjectURL(blob);
    const a = document.createElement('a'); a.href = url; a.download = 'for-rehan-note.txt'; document.body.appendChild(a); a.click(); a.remove(); URL.revokeObjectURL(url);
  });

  // confetti
  const confettiCanvas = document.getElementById('confetti');
  const ctx = confettiCanvas.getContext('2d');
  function resize(){ confettiCanvas.width = innerWidth; confettiCanvas.height = innerHeight; }
  addEventListener('resize', resize); resize();
  function rand(min,max){ return Math.random()*(max-min)+min }
  function makeConfetti(){ const pieces=[]; for(let i=0;i<120;i++){ pieces.push({x:rand(0,innerWidth),y:rand(-innerHeight,0),vx:rand(-1,1),vy:rand(2,6),w:rand(6,12),h:rand(8,18),col:['#ffd6ea','#fff1f8','#ff9ab3','#ffd6a5'][Math.floor(rand(0,4))]}); }
    let t=0; function frame(){ ctx.clearRect(0,0,innerWidth,innerHeight); t+=1; for(const p of pieces){ p.x+=p.vx; p.y+=p.vy; p.vy+=0.06; ctx.fillStyle=p.col; ctx.fillRect(p.x,p.y,p.w,p.h); } if(t<300) requestAnimationFrame(frame); else ctx.clearRect(0,0,innerWidth,innerHeight); } frame(); }
  document.getElementById('celebrate')?.addEventListener('click', ()=>{ makeConfetti(); });

  // share supportive message copy
  document.getElementById('shareBtn')?.addEventListener('click', ()=>{ const msg = `Rehan, tu bahut strong hai. Jo tune diya woh saccha tha. Ab aage badh. Hum tere saath hain.`; navigator.clipboard?.writeText(msg).then(()=>alert('Message copied — paste it anywhere to share.')) });

  // keyboard accessibility
  document.addEventListener('keydown',(e)=>{ if(e.key==='Enter'){ const v = document.activeElement; if(v && v.classList && v.classList.contains('revealBtn')) v.click(); } });
</script>
</body>
</html>
