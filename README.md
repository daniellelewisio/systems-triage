
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>The Systems Triage · CEO After Dark</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Newsreader:ital,opsz,wght@0,6..72,400;0,6..72,500;1,6..72,400;1,6..72,500;1,6..72,600&family=Inter:wght@400;500;600&family=Caveat:wght@500;600&display=swap" rel="stylesheet">
<style>
:root{
  --charcoal:#333031;
  --shiraz:#7a2435;
  --lipstick:#b8455a;
  --blush:#e2b5b0;
  --candlelight:#f3e9dc;
  --linen:#ffffff;
  --ink:#2a2728;
  --muted:#8a8083;
}
*{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth}
body{
  font-family:'Inter',sans-serif;
  background:var(--charcoal);
  color:var(--candlelight);
  line-height:1.55;
  letter-spacing:-0.01em;
  -webkit-font-smoothing:antialiased;
  overflow-x:hidden;
}
.wrap{max-width:740px;margin:0 auto;padding:0 24px}

/* atmosphere */
.glow{
  position:fixed;top:-30vh;left:50%;transform:translateX(-50%);
  width:120vw;height:80vh;pointer-events:none;z-index:0;
  background:radial-gradient(ellipse at center,rgba(122,36,53,0.55) 0%,rgba(122,36,53,0.18) 35%,transparent 65%);
  filter:blur(20px);
}
.grain{
  position:fixed;inset:0;pointer-events:none;z-index:1;opacity:0.04;
  background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='120' height='120'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='3'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
}
.stage{position:relative;z-index:2}

/* hero */
.hero{padding:50px 0 40px;text-align:center}
.eyebrow{
  font-size:11px;letter-spacing:0.34em;text-transform:uppercase;
  color:var(--blush);font-weight:500;margin-bottom:26px;
  display:flex;align-items:center;justify-content:center;gap:14px;
}
.eyebrow::before,.eyebrow::after{content:"";height:1px;width:34px;background:rgba(226,181,176,0.4)}
.hero h1{
  font-family:'Newsreader',serif;font-weight:400;
  font-size:clamp(46px,9vw,80px);line-height:0.98;letter-spacing:-0.025em;
  color:var(--linen);margin-bottom:22px;
}
.hero h1 em{font-style:italic;color:var(--blush)}
.hero .sub{font-size:17px;color:rgba(243,233,220,0.72);max-width:480px;margin:0 auto 8px}
.resume-note{margin-top:18px;font-size:13px;color:var(--muted)}
.resume-note button{background:none;border:none;color:var(--blush);text-decoration:underline;
  text-underline-offset:3px;cursor:pointer;font-family:inherit;font-size:13px}

/* card */
.card{
  background:rgba(243,233,220,0.04);
  border:1px solid rgba(243,233,220,0.1);
  border-radius:14px;padding:38px 34px;margin-bottom:22px;backdrop-filter:blur(4px);
}
.step-num{font-family:'Newsreader',serif;font-style:italic;font-size:14px;
  color:var(--lipstick);letter-spacing:0.04em;margin-bottom:6px}
.card h2{font-family:'Newsreader',serif;font-weight:400;font-size:clamp(26px,4.4vw,34px);
  line-height:1.1;letter-spacing:-0.02em;color:var(--linen);margin-bottom:10px}
.card h2 .hl{color:var(--blush);font-style:italic}
.card .lead{font-size:15px;color:rgba(243,233,220,0.68);margin-bottom:24px;max-width:560px}
.napkin{font-family:'Caveat',cursive;font-size:21px;color:var(--blush);
  transform:rotate(-1.2deg);display:inline-block;margin-bottom:22px;line-height:1.3}

/* dump */
.task-input-row{display:flex;gap:10px;margin-bottom:18px}
.task-input-row input{
  flex:1;background:rgba(0,0,0,0.22);border:1.5px solid rgba(243,233,220,0.16);
  border-radius:8px;padding:14px 16px;color:var(--candlelight);
  font-family:inherit;font-size:15px;transition:border-color .18s;
}
.task-input-row input::placeholder{color:var(--muted)}
.task-input-row input:focus{outline:none;border-color:var(--lipstick)}
.btn{
  background:var(--lipstick);color:var(--linen);border:none;border-radius:8px;
  font-family:inherit;font-size:14px;font-weight:500;letter-spacing:0.02em;
  padding:14px 26px;cursor:pointer;transition:background .18s,transform .12s;white-space:nowrap;
}
.btn:hover{background:var(--shiraz)}
.btn:active{transform:translateY(1px)}
.btn:disabled{opacity:.4;cursor:not-allowed}
.btn-ghost{background:none;border:1px solid rgba(243,233,220,0.22);color:var(--candlelight)}
.btn-ghost:hover{background:rgba(243,233,220,0.07)}

.task-list{list-style:none;display:flex;flex-direction:column;gap:8px}
.task-list li{
  display:flex;align-items:center;gap:12px;background:rgba(0,0,0,0.18);
  border:1px solid rgba(243,233,220,0.08);border-radius:8px;padding:12px 14px;animation:slideIn .25s ease;
}
@keyframes slideIn{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:none}}
.task-list .tname{flex:1;font-size:15px}
.tag-example{font-size:10px;letter-spacing:0.1em;text-transform:uppercase;color:var(--blush);
  border:1px solid rgba(226,181,176,0.35);border-radius:100px;padding:3px 9px;flex-shrink:0}
.task-list .tdel{background:none;border:none;color:var(--muted);cursor:pointer;
  font-size:18px;line-height:1;padding:2px 6px;border-radius:4px;transition:color .15s}
.task-list .tdel:hover{color:var(--lipstick)}
.dump-count{font-size:12px;color:var(--muted);margin-top:16px;letter-spacing:0.04em}
.dump-count b{color:var(--blush)}

/* scoring */
.score-task{background:rgba(0,0,0,0.18);border:1px solid rgba(243,233,220,0.1);
  border-radius:10px;padding:20px;margin-bottom:14px}
.score-task .stitle{font-size:16px;font-weight:600;color:var(--linen);margin-bottom:16px}
.slider-block{margin-bottom:16px}
.slider-block:last-child{margin-bottom:0}
.slider-label{display:flex;justify-content:space-between;font-size:12px;
  letter-spacing:0.04em;color:rgba(243,233,220,0.7);margin-bottom:7px}
.slider-label .q{color:var(--blush);font-weight:500}
.slider-label .v{font-family:'Newsreader',serif;font-style:italic;color:var(--lipstick);font-size:15px}
input[type=range]{-webkit-appearance:none;width:100%;height:4px;border-radius:4px;
  background:rgba(243,233,220,0.16);outline:none}
input[type=range]::-webkit-slider-thumb{-webkit-appearance:none;width:20px;height:20px;
  border-radius:50%;background:var(--lipstick);cursor:pointer;border:3px solid var(--charcoal);
  box-shadow:0 0 0 1px var(--lipstick);transition:transform .12s}
input[type=range]::-webkit-slider-thumb:hover{transform:scale(1.15)}
input[type=range]::-moz-range-thumb{width:20px;height:20px;border-radius:50%;
  background:var(--lipstick);cursor:pointer;border:3px solid var(--charcoal)}

/* verdict */
.verdict{background:linear-gradient(160deg,var(--shiraz) 0%,#5e1b29 100%);
  border:1px solid rgba(226,181,176,0.3);border-radius:14px;padding:42px 36px;
  margin-bottom:22px;text-align:center;box-shadow:0 30px 80px rgba(0,0,0,0.4)}
.verdict .v-eyebrow{font-size:11px;letter-spacing:0.28em;text-transform:uppercase;
  color:var(--blush);margin-bottom:18px}
.verdict h2{font-family:'Newsreader',serif;font-weight:400;font-size:clamp(28px,5vw,40px);
  line-height:1.08;color:var(--linen);margin-bottom:18px;letter-spacing:-0.02em}
.verdict h2 em{font-style:italic;color:var(--blush)}
.verdict .v-why{font-size:15px;color:rgba(243,233,220,0.85);max-width:480px;margin:0 auto 4px;font-style:italic}
.ranked{margin-top:8px}
.ranked h3{font-family:'Newsreader',serif;font-weight:400;font-size:20px;color:var(--linen);
  margin-bottom:16px;text-align:left}
.rank-row{display:flex;align-items:center;gap:14px;padding:13px 0;
  border-bottom:1px solid rgba(243,233,220,0.08);text-align:left}
.rank-row:last-child{border-bottom:none}
.rank-pos{font-family:'Newsreader',serif;font-style:italic;font-size:18px;color:var(--lipstick);width:28px;flex-shrink:0}
.rank-name{flex:1;font-size:15px}
.rank-bar{width:90px;height:6px;border-radius:6px;background:rgba(0,0,0,0.25);overflow:hidden;flex-shrink:0}
.rank-bar span{display:block;height:100%;background:var(--lipstick);border-radius:6px}
.rank-row.top .rank-name{color:var(--blush);font-weight:600}

/* SOP */
.field{margin-bottom:20px}
.field label{display:block;font-size:12px;letter-spacing:0.06em;text-transform:uppercase;
  color:var(--blush);margin-bottom:8px;font-weight:500}
.field input,.field textarea{width:100%;background:rgba(0,0,0,0.22);
  border:1.5px solid rgba(243,233,220,0.16);border-radius:8px;padding:13px 15px;
  color:var(--candlelight);font-family:inherit;font-size:15px;transition:border-color .18s;resize:vertical}
.field input:focus,.field textarea:focus{outline:none;border-color:var(--lipstick)}
.field input::placeholder,.field textarea::placeholder{color:var(--muted)}
.steps-list{list-style:none;display:flex;flex-direction:column;gap:10px;margin-bottom:14px}
.steps-list li{display:flex;gap:12px;align-items:flex-start}
.steps-list .snum{font-family:'Newsreader',serif;font-style:italic;color:var(--lipstick);
  font-size:16px;padding-top:11px;width:24px;flex-shrink:0}
.steps-list input{flex:1}
.steps-list .tdel{background:none;border:none;color:var(--muted);cursor:pointer;
  font-size:18px;padding:10px 6px;line-height:1}
.steps-list .tdel:hover{color:var(--lipstick)}

.actions{display:flex;gap:12px;margin-top:28px;flex-wrap:wrap}
.hidden{display:none}
.fade{animation:fadeUp .45s ease}
@keyframes fadeUp{from{opacity:0;transform:translateY(14px)}to{opacity:1;transform:none}}
.saved-flag{font-size:12px;color:var(--muted);margin-top:14px;letter-spacing:0.04em;opacity:0;transition:opacity .3s}
.saved-flag.show{opacity:1}
.saved-flag b{color:var(--blush);font-weight:500}

.closer{text-align:center;padding:30px 0 30px}
.closer .verb{font-family:'Newsreader',serif;font-style:italic;font-size:clamp(22px,4vw,30px);color:var(--blush)}
.closer .sub{font-size:14px;color:var(--muted);margin-top:14px}
.reset-row{text-align:center;padding:0 0 70px}
.reset-row button{background:none;border:none;color:var(--muted);text-decoration:underline;
  text-underline-offset:3px;cursor:pointer;font-family:inherit;font-size:12px;letter-spacing:0.04em}
.foot{text-align:center;font-size:11px;letter-spacing:0.2em;text-transform:uppercase;
  color:var(--muted);padding:30px 0 50px;border-top:1px solid rgba(243,233,220,0.07)}
.foot b{color:var(--blush);font-weight:500}

@media(max-width:560px){
  .card{padding:30px 22px}
  .verdict{padding:34px 24px}
  .task-input-row{flex-direction:column}
  .rank-bar{width:60px}
}
</style>
</head>
<body>
<div class="glow"></div>
<div class="grain"></div>

<div class="stage">
<div class="wrap">

  <header class="hero">
    <p class="sub">It's 9pm. You've got forty things you could systemise and you've frozen. Pour a Shiraz. Let's find the one that matters tonight.</p>
  </header>

  <!-- STEP 1 -->
  <section class="card" id="step1">
    <div class="step-num">Step one</div>
    <h2>Empty your <span class="hl">head</span> onto the table.</h2>
    <p class="lead">Every task you do more than once. The repeat offenders. Don't organise, don't judge, don't make it pretty, just get them out. The invoicing, the onboarding email, the thing you do every Monday and resent every time.</p>
    <div class="napkin">scrawled on a napkin, mostly ✎</div>
    <div class="task-input-row">
      <input type="text" id="taskInput" placeholder="e.g. Writing the same onboarding email" autocomplete="off">
      <button class="btn" id="addTask">Add it</button>
    </div>
    <ul class="task-list" id="taskList"></ul>
    <p class="dump-count" id="dumpCount">Nothing on the table yet. Start pouring.</p>
    <div class="actions">
      <button class="btn" id="toScore" disabled>Right. Now sort them</button>
    </div>
    <p class="saved-flag" id="saveFlag1">Saved as you go, so a stray click won't lose your pile.</p>
  </section>

  <!-- STEP 2 -->
  <section class="card hidden" id="step2">
    <div class="step-num">Step two</div>
    <h2>Be <span class="hl">honest</span> about each one.</h2>
    <p class="lead">Three sliders per task. How often it happens, how much you dread it, and whether you're the only person on earth who can do it. The dread matters. The task you avoid is usually the one bleeding you dry.</p>
    <div id="scoreContainer"></div>
    <div class="actions">
      <button class="btn-ghost btn" id="backTo1">Add more tasks</button>
      <button class="btn" id="toVerdict">Pour the verdict</button>
    </div>
  </section>

  <!-- STEP 3 -->
  <section class="hidden" id="step3">
    <div class="verdict">
      <div class="v-eyebrow">Your move tonight</div>
      <h2 id="verdictTitle">.</h2>
      <p class="v-why" id="verdictWhy"></p>
    </div>
    <div class="card">
      <div class="ranked">
        <h3>The rest, in order. Don't touch them yet.</h3>
        <div id="rankedList"></div>
      </div>
      <div class="actions">
        <button class="btn-ghost btn" id="backTo2">Re-score</button>
        <button class="btn" id="toBuild">Build the system</button>
      </div>
    </div>
  </section>

  <!-- STEP 4 -->
  <section class="card hidden" id="step4">
    <div class="step-num">Step three</div>
    <h2>Document it <span class="hl">once</span>. Improve it later.</h2>
    <p class="lead">Not pretty. Not perfect. Just written down so it's no longer living in your head. The first version exists to exist. You'll sharpen it next time you run it.</p>
    <div class="field">
      <label>The system</label>
      <input type="text" id="sopName" placeholder="System name">
    </div>
    <div class="field">
      <label>What does "done" look like?</label>
      <textarea id="sopOutcome" rows="2" placeholder="When this is finished, what's true? e.g. Client has everything they need and I've touched it zero extra times."></textarea>
    </div>
    <div class="field">
      <label>When does this happen, or what kicks it off?</label>
      <input type="text" id="sopTrigger" placeholder="e.g. Every time a new client signs  ·  or  ·  Every Monday morning">
    </div>
    <div class="field">
      <label>The steps</label>
      <ul class="steps-list" id="stepsList"></ul>
      <div class="task-input-row">
        <input type="text" id="stepInput" placeholder="One step. Plain words." autocomplete="off">
        <button class="btn" id="addStep">Add step</button>
      </div>
    </div>
    <div class="field">
      <label>Now let's get this off your plate, what could a robot or VA do later?</label>
      <textarea id="sopDelegate" rows="2" placeholder="Be honest. Which of these steps don't actually need you?"></textarea>
    </div>
    <div class="field">
      <label>Improvements & optimisations to think about later</label>
      <textarea id="sopImprove" rows="2" placeholder="Anything clunky, slow, or worth revisiting once it's running. Park it here, don't fix it tonight."></textarea>
    </div>
    <div class="actions">
      <button class="btn-ghost btn" id="backTo3">Back</button>
      <button class="btn" id="download">Export to spreadsheet</button>
    </div>
    <p class="saved-flag" id="saveFlag4">Saved as you go. The spreadsheet is yours to keep and build on.</p>
  </section>

  <!-- CLOSER -->
  <section class="closer hidden" id="closer">
    <p class="verb">One system down. Now close the laptop and finish your wine.</p>
    <p class="sub">Your spreadsheet downloaded. Come back next session, add new tasks, re-sort, and build the next one. Before you know it you'll have fully systemised your business and be ready to start freeing up your time.</p>
  </section>

  <div class="reset-row">
    <button id="resetAll">Clear everything and start a fresh triage</button>
  </div>

</div>
</div>

<script src="https://cdn.jsdelivr.net/npm/xlsx-js-style@1.2.0/dist/xlsx.bundle.js"></script>
<script>
(function(){
  const KEY='ceo_afterdark_systems_triage_v1';
  let state={tasks:[],sop:{name:'',outcome:'',trigger:'',delegate:'',improve:'',steps:[]},verdictName:''};
  let verdictTask=null;
  const $=id=>document.getElementById(id);

  /* persistence */
  function save(){ try{ localStorage.setItem(KEY,JSON.stringify(state)); flash(); }catch(e){} }
  let flashTimer;
  function flash(){
    ['saveFlag1','saveFlag4'].forEach(id=>{const el=$(id);if(el)el.classList.add('show');});
    clearTimeout(flashTimer);
    flashTimer=setTimeout(()=>{['saveFlag1','saveFlag4'].forEach(id=>{const el=$(id);if(el)el.classList.remove('show');});},2200);
  }
  function load(){
    try{ const raw=localStorage.getItem(KEY); if(raw){ state=Object.assign(state,JSON.parse(raw)); return true; } }catch(e){}
    return false;
  }

  /* STEP 1 */
  const taskInput=$('taskInput'), taskList=$('taskList'), dumpCount=$('dumpCount'), toScore=$('toScore');
  function renderTasks(){
    taskList.innerHTML='';
    state.tasks.forEach(t=>{
      const li=document.createElement('li');
      li.innerHTML=`<span class="tname"></span>${t.example?'<span class="tag-example">example</span>':''}<button class="tdel" aria-label="Remove">×</button>`;
      li.querySelector('.tname').textContent=t.name;
      li.querySelector('.tdel').onclick=()=>{ state.tasks=state.tasks.filter(x=>x.id!==t.id); renderTasks(); save(); };
      taskList.appendChild(li);
    });
    const n=state.tasks.length;
    const hasEx=state.tasks.some(t=>t.example);
    dumpCount.innerHTML = n===0 ? 'Nothing on the table yet. Start pouring.'
      : `<b>${n}</b> task${n>1?'s':''} on the table.` + (hasEx?' We\'ve put a few examples in to get you going, swap them for your own.':(n<3?' Keep going, get them all out.':' That\'s a real pile. Sort them when you\'re ready.'));
    toScore.disabled = n<1;
  }
  function addTask(){
    const v=taskInput.value.trim(); if(!v)return;
    state.tasks.push({id:Date.now()+Math.random(),name:v,freq:5,dread:5,onlyme:5});
    taskInput.value=''; taskInput.focus(); renderTasks(); save();
  }
  $('addTask').onclick=addTask;
  taskInput.addEventListener('keydown',e=>{if(e.key==='Enter')addTask();});

  /* STEP 2 */
  function renderScore(){
    const c=$('scoreContainer'); c.innerHTML='';
    state.tasks.forEach(t=>{
      const div=document.createElement('div'); div.className='score-task';
      div.innerHTML=`<div class="stitle"></div>
        ${sliderRow(t.id,'freq','How often?',t.freq)}
        ${sliderRow(t.id,'dread','How much dread?',t.dread)}
        ${sliderRow(t.id,'onlyme','Only you can do it?',t.onlyme)}`;
      div.querySelector('.stitle').textContent=t.name;
      c.appendChild(div);
    });
    c.querySelectorAll('input[type=range]').forEach(r=>{
      r.addEventListener('input',()=>{
        const t=state.tasks.find(x=>x.id==r.dataset.id);
        t[r.dataset.key]=+r.value;
        r.closest('.slider-block').querySelector('.v').textContent=labelFor(r.dataset.key,+r.value);
        save();
      });
    });
  }
  function sliderRow(id,key,q,val){
    return `<div class="slider-block">
      <div class="slider-label"><span class="q">${q}</span><span class="v">${labelFor(key,val)}</span></div>
      <input type="range" min="1" max="10" value="${val}" data-id="${id}" data-key="${key}"></div>`;
  }
  function labelFor(key,v){
    if(v<=3) return key==='dread'?'manageable':key==='onlyme'?'anyone':'now & then';
    if(v<=6) return key==='dread'?'annoying':key==='onlyme'?'sort of':'weekly-ish';
    if(v<=8) return key==='dread'?'heavy':key==='onlyme'?'mostly me':'often';
    return key==='dread'?'soul-crushing':key==='onlyme'?'only me':'constant';
  }

  /* STEP 3 */
  function score(t){ return t.freq*1.0 + t.dread*1.3 + t.onlyme*1.1; }
  function sortedTasks(){ return [...state.tasks].sort((a,b)=>score(b)-score(a)); }
  function renderVerdict(){
    const sorted=sortedTasks();
    verdictTask=sorted[0]; state.verdictName=verdictTask.name;
    $('verdictTitle').innerHTML=`Build the system for:<br><em>${esc(verdictTask.name)}</em>`;
    $('verdictWhy').textContent=whyLine(verdictTask);
    const max=score(sorted[0]); const rl=$('rankedList'); rl.innerHTML='';
    sorted.forEach((t,i)=>{
      const row=document.createElement('div');
      row.className='rank-row'+(i===0?' top':'');
      const pct=Math.round(score(t)/max*100);
      row.innerHTML=`<span class="rank-pos">${i+1}</span><span class="rank-name"></span>
        <span class="rank-bar"><span style="width:${pct}%"></span></span>`;
      row.querySelector('.rank-name').textContent=t.name;
      rl.appendChild(row);
    });
    save();
  }
  function whyLine(t){
    if(t.dread>=8&&t.onlyme>=7) return "High dread, all on you. This is the one quietly draining your energy. Systemise it and you get yourself back.";
    if(t.dread>=8) return "You dread this more than the rest. The avoidance is costing you more than the task ever would.";
    if(t.freq>=8) return "You do this constantly. Document it once and you stop re-thinking it every single time.";
    if(t.onlyme>=8) return "Right now only you can do this. Get it out of your head so the business isn't a single point of failure.";
    return "It scored highest on frequency, dread, and dependence combined. Start here.";
  }

  /* STEP 4 */
  const stepInput=$('stepInput'), stepsList=$('stepsList');
  function bindSop(){
    [['sopName','name'],['sopOutcome','outcome'],['sopTrigger','trigger'],['sopDelegate','delegate'],['sopImprove','improve']].forEach(([id,key])=>{
      const el=$(id); el.value=state.sop[key]||'';
      el.oninput=()=>{state.sop[key]=el.value;save();};
    });
  }
  function renderSteps(){
    stepsList.innerHTML='';
    state.sop.steps.forEach((s,i)=>{
      const li=document.createElement('li');
      li.innerHTML=`<span class="snum">${i+1}</span><input type="text"><button class="tdel">×</button>`;
      const inp=li.querySelector('input'); inp.value=s;
      inp.addEventListener('input',()=>{state.sop.steps[i]=inp.value;save();});
      li.querySelector('.tdel').onclick=()=>{state.sop.steps.splice(i,1);renderSteps();save();};
      stepsList.appendChild(li);
    });
  }
  function addStep(){
    const v=stepInput.value.trim(); if(!v)return;
    state.sop.steps.push(v); stepInput.value=''; stepInput.focus(); renderSteps(); save();
  }
  $('addStep').onclick=addStep;
  stepInput.addEventListener('keydown',e=>{if(e.key==='Enter')addStep();});

  /* NAV */
  function show(id){$(id).classList.remove('hidden');$(id).classList.add('fade');$(id).scrollIntoView({behavior:'smooth',block:'start'});}
  function hide(id){$(id).classList.add('hidden');}
  $('toScore').onclick=()=>{renderScore();hide('step1');show('step2');};
  $('backTo1').onclick=()=>{hide('step2');show('step1');};
  $('toVerdict').onclick=()=>{renderVerdict();hide('step2');show('step3');};
  $('backTo2').onclick=()=>{hide('step3');show('step2');};
  $('toBuild').onclick=()=>{ if(!state.sop.name){state.sop.name=verdictTask?verdictTask.name:'';} bindSop(); renderSteps(); hide('step3');show('step4');};
  $('backTo3').onclick=()=>{hide('step4');show('step3');};

  function esc(s){return (s||'').replace(/[&<>]/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;'}[c]));}

  /* XLSX EXPORT (styled) */
  $('download').onclick=()=>{
    if(typeof XLSX==='undefined'){
      alert("The spreadsheet engine didn't load (likely a connection hiccup). Refresh the page and try again.");
      return;
    }
    try{
    const P={charcoal:'333031',shiraz:'7A2435',lipstick:'B8455A',blush:'E2B5B0',
      candle:'F3E9DC',linen:'FFFFFF',ink:'2A2728',muted:'8A8083',rule:'E0D6C8'};
    const fill=c=>({patternType:'solid',fgColor:{rgb:c}});
    const SER='Georgia', SAN='Arial';
    const bottomRule={bottom:{style:'thin',color:{rgb:P.rule}}};

    const wb=XLSX.utils.book_new();
    const sorted=sortedTasks();

    /* ---- TRIAGE SHEET ---- */
    const t_aoa=[
      ['CEO After Dark   ·   The Systems Triage','','','','','',''],
      ['A SPARK product. Your tasks, ranked. Build them top to bottom.','','','','','',''],
      ['','','','','','',''],
      ['Rank','Task','How often','Dread','Only me','Score','Status'],
    ];
    sorted.forEach((t,i)=>t_aoa.push([i+1,t.name,t.freq,t.dread,t.onlyme,+score(t).toFixed(1),i===0?'BUILD THIS FIRST':'']));
    const noteRow=t_aoa.length+1;
    t_aoa.push(['','','','','','','']);
    t_aoa.push(['Scoring','','','','','','']);
    t_aoa.push(['Dread is weighted heaviest, then dependence, then frequency. The task you avoid is usually the one bleeding you dry.','','','','','','']);
    t_aoa.push(['','','','','','','']);
    t_aoa.push(['Add new tasks below as you think of them, then re-open the tool to re-rank.','','','','','','']);
    const ws1=XLSX.utils.aoa_to_sheet(t_aoa);
    ws1['!cols']=[{wch:8},{wch:40},{wch:12},{wch:9},{wch:10},{wch:9},{wch:18}];
    ws1['!merges']=[
      {s:{r:0,c:0},e:{r:0,c:6}},{s:{r:1,c:0},e:{r:1,c:6}},
      {s:{r:noteRow,c:0},e:{r:noteRow,c:6}},{s:{r:noteRow+1,c:0},e:{r:noteRow+1,c:6}},
      {s:{r:noteRow+3,c:0},e:{r:noteRow+3,c:6}},
    ];
    ws1['!rows']=[{hpt:46},{hpt:20},{hpt:8},{hpt:26}];

    const setC=(ws,addr,style)=>{ if(ws[addr]) ws[addr].s=style; };
    // title band
    setC(ws1,'A1',{fill:fill(P.charcoal),font:{name:SER,sz:18,italic:true,color:{rgb:P.candle}},alignment:{horizontal:'left',vertical:'center',indent:1}});
    setC(ws1,'A2',{font:{name:SAN,sz:9,italic:true,color:{rgb:P.muted}},alignment:{horizontal:'left',indent:1}});
    // header row (row 4 -> index 3)
    ['A4','B4','C4','D4','E4','F4','G4'].forEach((a,i)=>setC(ws1,a,{
      fill:fill(P.shiraz),font:{name:SAN,sz:9,bold:true,color:{rgb:P.linen}},
      alignment:{horizontal:i===1?'left':'center',vertical:'center',indent:i===1?1:0}}));
    // data rows
    sorted.forEach((t,i)=>{
      const r=5+i, first=(i===0);
      const base={alignment:{horizontal:'center',vertical:'center'},border:bottomRule,font:{name:SAN,sz:10,color:{rgb:P.ink}}};
      const rankS={alignment:{horizontal:'center',vertical:'center'},border:bottomRule,font:{name:SER,sz:11,italic:true,color:{rgb:P.lipstick}}};
      const taskS={alignment:{horizontal:'left',vertical:'center',indent:1},border:bottomRule,font:{name:SAN,sz:10,bold:first,color:{rgb:P.ink}}};
      const statusS={alignment:{horizontal:'center',vertical:'center'},border:bottomRule,font:{name:SAN,sz:8,bold:true,color:{rgb:first?P.linen:P.ink}}};
      const cells=[['A',rankS],['B',taskS],['C',base],['D',base],['E',base],['F',base],['G',statusS]];
      cells.forEach(([col,st])=>{
        const s=JSON.parse(JSON.stringify(st));
        if(first) s.fill=fill(col==='G'?P.lipstick:P.blush);
        setC(ws1,col+r,s);
      });
    });
    setC(ws1,'A'+(noteRow+1),{font:{name:SAN,sz:8,bold:true,color:{rgb:P.shiraz}}});
    setC(ws1,'A'+(noteRow+2),{font:{name:SAN,sz:9,italic:true,color:{rgb:P.muted}}});
    setC(ws1,'A'+(noteRow+4),{font:{name:SAN,sz:9,italic:true,color:{rgb:P.lipstick}}});

    /* ---- SOP SHEET ---- */
    const sop=state.sop;
    const steps=sop.steps.filter(x=>x.trim());
    const s_aoa=[
      ['CEO After Dark   ·   Your System',''],
      ['Documented once. Improve it later.',''],
      ['',''],
      ['The system',sop.name||state.verdictName||''],
      ['When it happens / what kicks it off',sop.trigger||''],
      ['What "done" looks like',sop.outcome||''],
      ['',''],
      ['THE STEPS',''],
    ];
    steps.forEach((st,i)=>s_aoa.push([i+1,st]));
    s_aoa.push(['','']);
    s_aoa.push(['Off your plate: what a robot or VA could do',sop.delegate||'']);
    s_aoa.push(['Improvements & optimisations for later',sop.improve||'']);
    s_aoa.push(['','']);
    s_aoa.push(['Now finish your wine.','']);
    const ws2=XLSX.utils.aoa_to_sheet(s_aoa);
    ws2['!cols']=[{wch:34},{wch:62}];
    const stepsHdr=8; // row index of 'THE STEPS' (0-based) = 7 -> excel row 8
    ws2['!merges']=[
      {s:{r:0,c:0},e:{r:0,c:1}},{s:{r:1,c:0},e:{r:1,c:1}},
      {s:{r:7,c:0},e:{r:7,c:1}},
    ];
    const lastRow=s_aoa.length;
    ws2['!merges'].push({s:{r:lastRow-1,c:0},e:{r:lastRow-1,c:1}});
    ws2['!rows']=[{hpt:46},{hpt:20}];

    setC(ws2,'A1',{fill:fill(P.charcoal),font:{name:SER,sz:18,italic:true,color:{rgb:P.candle}},alignment:{horizontal:'left',vertical:'center',indent:1}});
    setC(ws2,'A2',{font:{name:SAN,sz:9,italic:true,color:{rgb:P.muted}},alignment:{horizontal:'left',indent:1}});
    const labelS={fill:fill(P.candle),font:{name:SAN,sz:9,bold:true,color:{rgb:P.shiraz}},alignment:{horizontal:'left',vertical:'top',indent:1,wrapText:true}};
    const valS={font:{name:SAN,sz:10,color:{rgb:P.ink}},alignment:{horizontal:'left',vertical:'top',indent:1,wrapText:true}};
    [4,5,6].forEach(r=>{ setC(ws2,'A'+r,labelS); setC(ws2,'B'+r,valS); });
    // THE STEPS header
    setC(ws2,'A8',{fill:fill(P.shiraz),font:{name:SAN,sz:9,bold:true,color:{rgb:P.linen}},alignment:{horizontal:'left',vertical:'center',indent:1}});
    steps.forEach((st,i)=>{
      const r=9+i;
      setC(ws2,'A'+r,{font:{name:SER,sz:11,italic:true,color:{rgb:P.lipstick}},alignment:{horizontal:'center',vertical:'center'},border:bottomRule});
      setC(ws2,'B'+r,{font:{name:SAN,sz:10,color:{rgb:P.ink}},alignment:{horizontal:'left',vertical:'center',indent:1},border:bottomRule});
    });
    const dr=9+steps.length+1, ir=dr+1;
    setC(ws2,'A'+dr,labelS); setC(ws2,'B'+dr,valS);
    setC(ws2,'A'+ir,labelS); setC(ws2,'B'+ir,valS);
    setC(ws2,'A'+lastRow,{font:{name:SER,sz:13,italic:true,color:{rgb:P.shiraz}},alignment:{horizontal:'left',indent:1}});

    XLSX.utils.book_append_sheet(wb,ws1,'Triage');
    XLSX.utils.book_append_sheet(wb,ws2,'Your System');
    const fname=((sop.name||state.verdictName||'my-systems').replace(/[^a-z0-9]+/gi,'-').toLowerCase())+'-triage.xlsx';
    XLSX.writeFile(wb,fname);
    show('closer');
    }catch(err){
      alert("Something went wrong building your spreadsheet. Refresh and try again, your tasks are still saved.");
      console.error(err);
    }
  };

  /* RESET */
  $('resetAll').onclick=()=>{
    if(!confirm('Clear all your tasks, scores, and system notes? This can\'t be undone.'))return;
    localStorage.removeItem(KEY);
    state={tasks:[],sop:{name:'',outcome:'',trigger:'',delegate:'',improve:'',steps:[]},verdictName:''};
    ['step2','step3','step4','closer'].forEach(hide);
    show('step1'); renderTasks();
    ['sopName','sopOutcome','sopTrigger','sopDelegate','sopImprove'].forEach(id=>$(id).value='');
    stepsList.innerHTML='';
  };

  /* INIT */
  const hadSaved=load();
  if(!hadSaved && state.tasks.length===0){
    // gentle starting examples, only when there's no real work yet
    [['Writing the same onboarding email to every new client',8,6,8],
     ['Chasing overdue invoices',5,8,7],
     ['Batching a week of social content',7,5,6]].forEach(([name,freq,dread,onlyme])=>{
      state.tasks.push({id:Date.now()+Math.random(),name,freq,dread,onlyme,example:true});
    });
  }
  renderTasks(); bindSop(); renderSteps();
})();
</script>
</body>
</html>
