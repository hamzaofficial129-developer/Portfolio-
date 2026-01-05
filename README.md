<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Hamza - Web Developer & Graphics Designer</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;800&display=swap" rel="stylesheet">
  <style>
    :root {
      --bg1: linear-gradient(135deg,#0f172a 0%,#001219 50%,#0f172a 100%);
      --glass: rgba(255,255,255,0.06);
      --accent: #7c3aed;
      --accent-2: #06b6d4;
      --card: rgba(255,255,255,0.03);
      --text: #e6eef8;
    }
    *{box-sizing:border-box;margin:0;padding:0;}
    html,body{height:100%;}
    body{
      font-family:'Poppins',system-ui,Segoe UI,Roboto,Arial;
      background: radial-gradient(1200px 600px at 10% 10%, rgba(124,58,237,0.12), transparent),
                  radial-gradient(900px 400px at 90% 90%, rgba(6,182,212,0.08), transparent),
                  #001219;
      color:var(--text);
      -webkit-font-smoothing:antialiased;
      overflow-x:hidden;
      transition: background 0.3s ease, color 0.3s ease;
    }
    
    /* Light theme styles */
    body.light-theme {
      background: linear-gradient(135deg,#fdfbfb 0%,#ebedee 100%);
      color: #0b1220;
    }
    body.light-theme .card {
      background: rgba(0,0,0,0.04);
      color: #0b1220;
    }
    body.light-theme .link {
      color: #0b1220;
    }
    body.light-theme input,
    body.light-theme textarea {
      background: rgba(0,0,0,0.05);
      color: #0b1220;
      border: 1px solid rgba(0,0,0,0.1);
    }

    /* Navigation */
    .nav{display:flex;justify-content:space-between;align-items:center;padding:18px 28px;position:relative;z-index:10}
    .brand{display:flex;gap:12px;align-items:center}
    .logo{width:46px;height:46px;border-radius:10px;display:grid;place-items:center;background:linear-gradient(135deg,var(--accent),var(--accent-2));font-weight:800}
    .brand h1{font-size:18px}
    .links{display:flex;gap:14px;align-items:center;flex-wrap:wrap;}
    .link{padding:8px 12px;border-radius:8px;font-weight:600;cursor:pointer;opacity:0.9;transition:transform 0.2s;}
    .link:hover{transform:translateY(-3px)}

    /* Hero */
    .hero{min-height:72vh;display:grid;grid-template-columns:1fr 420px;gap:28px;align-items:center;padding:32px;position:relative}
    .hero-left{max-width:820px}
    .eyebrow{display:inline-block;padding:6px 10px;background:var(--glass);backdrop-filter:blur(6px);border-radius:999px;font-size:13px;margin-bottom:18px}
    .headline{font-size:46px;line-height:1.02;margin-bottom:12px}
    .lead{opacity:0.9;margin-bottom:18px}
    .actions{display:flex;gap:12px;flex-wrap:wrap;}
    .btn{background:linear-gradient(90deg,var(--accent),var(--accent-2));padding:12px 16px;border-radius:12px;border:0;font-weight:700;cursor:pointer;color:white}
    .ghost{padding:10px 14px;border-radius:12px;border:1px solid rgba(255,255,255,0.2);background:transparent;cursor:pointer;color:var(--text)}

    /* Right card */
    .card{background:rgba(255,255,255,0.04);padding:22px;border-radius:16px;backdrop-filter:blur(6px);box-shadow:0 6px 30px rgba(2,6,23,0.6)}
    .profile{display:flex;gap:14px;align-items:center}
    .avatar{width:68px;height:68px;border-radius:14px;background:linear-gradient(135deg,#ffd166,#ef476f);display:grid;place-items:center;font-weight:800;color:#041124}

    /* Projects */
    .projects{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:14px;margin-top:20px}
    .proj{padding:12px;border-radius:12px;background:rgba(255,255,255,0.03)}
    .proj h4{margin:6px 0 2px}
    .proj p{margin:0;font-size:13px;opacity:0.85}

    /* Features / Skills */
    .features{display:grid;grid-template-columns:1fr 1fr;gap:18px;padding:28px}
    .feature{padding:18px;border-radius:12px;background:var(--card);box-shadow:inset 0 1px 0 rgba(255,255,255,0.02)}

    footer{padding:24px;text-align:center;opacity:0.9;font-size:14px;}

    @media (max-width:880px){
      .hero{grid-template-columns:1fr;min-height:78vh}
      .hero-right{order:2}
    }

    .typing{font-weight:700;color:var(--accent)}

    /* Background Canvases */
    canvas#particles,canvas#confetti{position:fixed;inset:0;pointer-events:none;z-index:0}

    .badge{position:fixed;right:18px;bottom:18px;background:linear-gradient(90deg,var(--accent),var(--accent-2));padding:10px 14px;border-radius:999px;font-weight:700;cursor:pointer;z-index:15;color:white}

    .reveal{opacity:0;transform:translateY(10px);animation:reveal 700ms ease forwards}
    .reveal.delay{animation-delay:120ms}
    .reveal.late{animation-delay:240ms}
    @keyframes reveal{to{opacity:1;transform:none}}

    /* Skills section */
    .skills-container{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:16px;margin-top:20px;}
    .skill-item{padding:12px;border-radius:10px;background:rgba(255,255,255,0.03);text-align:center;}
    .skill-item h4{margin-bottom:8px;}
    .skill-bar{height:6px;background:rgba(255,255,255,0.1);border-radius:3px;overflow:hidden;}
    .skill-level{height:100%;background:linear-gradient(90deg,var(--accent),var(--accent-2));}
    
    /* Contact form improvements */
    #contact .card {
      max-width: 820px;
      margin: auto;
    }
    #contact form {
      display: grid;
      gap: 12px;
      margin-top: 20px;
    }
    #contact input,
    #contact textarea {
      padding: 12px;
      border-radius: 10px;
      border: 0;
      background: rgba(255,255,255,0.05);
      color: var(--text);
      font-family: 'Poppins', sans-serif;
    }
    #contact .form-actions {
      display: flex;
      gap: 12px;
      flex-wrap: wrap;
      margin-top: 10px;
    }
    
    /* Professional signature */
    .professional-signature {
      margin-top: 30px;
      padding-top: 20px;
      border-top: 1px solid rgba(255,255,255,0.1);
      text-align: center;
    }
    .professional-signature h4 {
      margin-bottom: 8px;
      font-weight: 600;
    }
    .professional-signature p {
      margin: 4px 0;
      opacity: 0.9;
    }
  </style>
</head>
<body>
  <canvas id="particles"></canvas>
  <canvas id="confetti"></canvas>
  
  <nav class="nav">
    <div class="brand">
      <div class="logo">HZ</div>
      <div>
        <h1>Hamza</h1>
        <div style="font-size:12px;opacity:0.7">Web Developer & Graphics Designer</div>
      </div>
    </div>
    <div class="links">
      <div class="link" onclick="scrollToSection('projects')">Projects</div>
      <div class="link" onclick="scrollToSection('skills')">Skills</div>
      <div class="link" onclick="scrollToSection('contact')">Contact</div>
      <div class="link" id="themeToggle">🌙</div>
    </div>
  </nav>

  <main>
    <section class="hero">
      <div class="hero-left">
        <span class="eyebrow reveal">Professional Portfolio</span>
        <h2 class="headline reveal delay">Hi, I'm <span class="typing" id="typed">Hamza</span></h2>
        <p class="lead reveal delay">
          A passionate Web Developer and Graphics Designer creating stunning digital experiences. 
          I specialize in responsive web design, UI/UX, and creative visuals.
        </p>
        <div class="actions reveal late">
          <button class="btn" onclick="scrollToSection('projects')">View My Work</button>
          <button class="ghost" onclick="scrollToSection('contact')">Contact Me</button>
        </div>
      </div>
      
      <aside class="hero-right card reveal">
        <div class="profile">
          <div class="avatar">H</div>
          <div>
            <div style="font-weight:700">Hamza Official</div>
            <div style="font-size:13px;opacity:0.9">Web Developer · Graphics Designer</div>
          </div>
        </div>
        
        <div class="projects" id="projects">
          <div class="proj">
            <small style="opacity:0.8">Web Development</small>
            <h4>E-Commerce Platform</h4>
            <p>Responsive online store with modern UI and smooth animations.</p>
          </div>
          <div class="proj">
            <small style="opacity:0.8">Graphics Design</small>
            <h4>Brand Identity Package</h4>
            <p>Complete branding including logo, color palette, and typography.</p>
          </div>
          <div class="proj">
            <small style="opacity:0.8">UI/UX Design</small>
            <h4>Financial Dashboard UI</h4>
            <p>Modern financial dashboard with data visualization, analytics, and user-friendly interface for tracking expenses and investments.</p>
          </div>
        </div>
      </aside>
    </section>
    
    <section class="features" id="skills">
      <div class="feature reveal">
        <h3>Web Development</h3>
        <p>Building responsive, modern, and high-performance websites.</p>
        <div class="skills-container">
          <div class="skill-item"><h4>HTML/CSS</h4><div class="skill-bar"><div class="skill-level" style="width:95%"></div></div></div>
          <div class="skill-item"><h4>JavaScript</h4><div class="skill-bar"><div class="skill-level" style="width:90%"></div></div></div>
          <div class="skill-item"><h4>React</h4><div class="skill-bar"><div class="skill-level" style="width:85%"></div></div></div>
        </div>
      </div>
      <div class="feature reveal delay">
        <h3>Graphics Design</h3>
        <p>Designing powerful visuals to communicate ideas effectively.</p>
        <div class="skills-container">
          <div class="skill-item"><h4>Photoshop</h4><div class="skill-bar"><div class="skill-level" style="width:90%"></div></div></div>
          <div class="skill-item"><h4>Illustrator</h4><div class="skill-bar"><div class="skill-level" style="width:85%"></div></div></div>
          <div class="skill-item"><h4>Figma</h4><div class="skill-bar"><div class="skill-level" style="width:80%"></div></div></div>
        </div>
      </div>
    </section>
    
    <section style="padding:28px;" id="contact">
      <div class="card">
        <h3>Get in touch</h3>
        <p style="opacity:0.9">Have a project in mind? Let's create something great together.</p>
        <form onsubmit="fakeSend(event)">
          <input id="name" placeholder="Your name" required>
          <input id="email" placeholder="Email" type="email" required>
          <input id="phone" placeholder="Phone number" type="tel">
          <textarea id="message" placeholder="Message" rows="4"></textarea>
          <div class="form-actions">
            <button class="btn" type="submit">Send Message</button>
            <button type="button" class="ghost" onclick="celebrate()">Let's Go!</button>
          </div>
        </form>
        
        <div class="professional-signature">
          <h4>Yours sincerely,</h4>
          <p><strong>Hamza Ahmad</strong></p>
          <p>Web Developer & Graphics Designer</p>
          <p>Phone: 0309-6241193</p>
        </div>
      </div>
    </section>
  </main>

  <div class="badge" onclick="celebrate()">Let's Go! 🚀</div>

  <footer>© 2025 Hamza - Web Developer & Graphics Designer. All rights reserved.</footer>

  <script>
    // Typing Effect
    const words = ['Hamza', 'Web Developer', 'Graphics Designer', 'Creative Professional'];
    let i=0, j=0, dir=1;
    const typingEl = document.getElementById('typed');
    function tick(){
      const word = words[i];
      j += dir;
      typingEl.textContent = word.slice(0,j);
      if(j===word.length){dir=-1;setTimeout(tick,1200);return}
      if(j===0){dir=1;i=(i+1)%words.length}
      setTimeout(tick,80);
    }
    tick();

    // Particle Background
    const canvas = document.getElementById('particles');
    const ctx = canvas.getContext('2d');
    function resize(){
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    }
    window.addEventListener('resize', resize); resize();
    const particles=[];
    function spawn(x,y,burst=false){
      for(let k=0;k<(burst?12:1);k++){
        particles.push({x:x||Math.random()*innerWidth,y:y||Math.random()*innerHeight,vx:(Math.random()-0.5)*1.4,vy:(Math.random()-0.5)*1.4,size:Math.random()*2.2+0.6,life:Math.random()*120+40});
      }
    }
    for(let p=0;p<60;p++)spawn();
    canvas.addEventListener('mousemove',e=>spawn(e.clientX,e.clientY));
    function updateParticles(){
      ctx.clearRect(0,0,innerWidth,innerHeight);
      for(let i=particles.length-1;i>=0;i--){
        const p=particles[i];
        p.x+=p.vx;p.y+=p.vy;p.life--;
        const a=Math.max(0,p.life/140);
        ctx.fillStyle=`rgba(124,58,237,${0.08+0.6*a})`;
        ctx.beginPath();ctx.arc(p.x,p.y,p.size,0,Math.PI*2);ctx.fill();
        if(p.life<=0)particles.splice(i,1);
      }
      if(particles.length<80)spawn();
      requestAnimationFrame(updateParticles);
    }
    updateParticles();

    // Confetti
    const confettiCanvas=document.getElementById('confetti');
    const cctx=confettiCanvas.getContext('2d');
    function resizeConf(){confettiCanvas.width=innerWidth;confettiCanvas.height=innerHeight;}
    window.addEventListener('resize',resizeConf);resizeConf();
    function celebrate(){
      const pieces=[];
      const colors=['#ffb700','#ff3d7f','#7c3aed','#06b6d4','#34d399'];
      for(let i=0;i<120;i++){
        pieces.push({x:innerWidth/2+(Math.random()-0.5)*300,y:innerHeight/2+(Math.random()-0.9)*200,vx:(Math.random()-0.5)*6,vy:Math.random()*-8-2,size:Math.random()*6+4,rot:Math.random()*360,color:colors[i%colors.length],life:Math.random()*80+60});
      }
      (function frame(){
        cctx.clearRect(0,0,innerWidth,innerHeight);
        for(let i=pieces.length-1;i>=0;i--){
          const p=pieces[i];
          p.x+=p.vx;p.y+=p.vy;p.vy+=0.35;p.life--;
          cctx.save();
          cctx.translate(p.x,p.y);cctx.rotate(p.rot*Math.PI/180);
          cctx.fillStyle=p.color;cctx.fillRect(-p.size/2,-p.size/2,p.size,p.size*0.6);
          cctx.restore();
          if(p.life<=0||p.y>innerHeight+50)pieces.splice(i,1);
        }
        if(pieces.length>0)requestAnimationFrame(frame);
      })();
    }

    // Form fake send
    function fakeSend(e){
      e.preventDefault();
      celebrate();
      const btn=e.target.querySelector('button[type=submit]');
      const old=btn.textContent;
      btn.textContent='Message Sent!';
      setTimeout(()=>btn.textContent=old,1800);
      e.target.reset();
    }

    // Smooth scroll
    function scrollToSection(id){
      document.getElementById(id).scrollIntoView({behavior:'smooth',block:'start'});
    }

    // Theme toggle
    const themeToggle=document.getElementById('themeToggle');
    let dark=true;
    themeToggle.addEventListener('click',()=>{
      dark=!dark;
      if(!dark){
        document.body.classList.add('light-theme');
        themeToggle.textContent='☀️';
      }else{
        document.body.classList.remove('light-theme');
        themeToggle.textContent='🌙';
      }
    });
  </script>
</body>
</html>
