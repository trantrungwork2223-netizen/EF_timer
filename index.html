<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8" />
  <title>EF Tracker - 1 ngày làm việc</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #0f172a;
      color: #e5e7eb;
      padding: 20px;
    }

    h1 {
      margin-bottom: 10px;
    }

    .add-box {
      background: #1e293b;
      padding: 12px;
      border-radius: 10px;
      margin-bottom: 20px;
      display: flex;
      gap: 10px;
    }

    input {
      padding: 6px;
      border-radius: 6px;
      border: 1px solid #475569;
      background: #020617;
      color: white;
    }

    button {
      padding: 6px 12px;
      border-radius: 6px;
      background: #0284c7;
      border: none;
      cursor: pointer;
      color: white;
    }

    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 15px;
    }

    .card {
      background: #1e293b;
      padding: 12px;
      border-radius: 10px;
      border: 1px solid #334155;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .timer {
      background: #020617;
      padding: 8px;
      border-radius: 8px;
      text-align: center;
      font-size: 24px;
      font-family: monospace;
      border: 1px solid #0a0f23;
    }

    .controls {
      display: flex;
      gap: 10px;
    }

    .small {
      transform: scale(0.85);
      color: #f97316;
    }

    .overtime {
      color: #22c55e;
    }
  </style>
</head>
<body>

<h1>EF Tracker</h1>

<!-- UI thêm project -->
<div class="add-box">
  <input id="projName" placeholder="Tên dự án">
  <input id="projPercent" type="number" placeholder="% EF (vd: 30)">
  <button onclick="addProject()">Thêm / Cập nhật</button>
</div>

<div class="grid" id="projectArea"></div>

<script>
  const BASE_SECONDS = 8 * 60 * 60;
  let projects = [];

  function format(sec){
    sec = Math.max(0, Math.round(sec));
    let h = Math.floor(sec/3600);
    let m = Math.floor((sec%3600)/60);
    let s = sec%60;
    return `${String(h).padStart(2,"0")}:${String(m).padStart(2,"0")}:${String(s).padStart(2,"0")}`;
  }

  function render(){
    const container = document.getElementById("projectArea");
    container.innerHTML = "";

    if(projects.length===0) return;

    let min = Math.min(...projects.map(p=>p.remainingSeconds));

    projects.forEach(p=>{
      let card=document.createElement("div");
      card.className="card";

      let title=document.createElement("div");
      title.textContent = `${p.name} (${p.allocation}% của 8h)`;

      let timer=document.createElement("div");
      timer.className="timer";
      timer.textContent = format(p.remainingSeconds);

      if(p.remainingSeconds === min) timer.classList.add("small");
      if(p.totalSeconds > p.allocatedSeconds) timer.classList.add("overtime");

      let ctrls=document.createElement("div");
      ctrls.className="controls";

      let btnStart=document.createElement("button");
      btnStart.textContent = p.running ? "Pause" : "Start";
      btnStart.onclick = ()=>toggle(p.name);

      let btnOT=document.createElement("button");
      btnOT.textContent = "+ OT";
      btnOT.onclick = ()=>addOT(p.name);

      ctrls.appendChild(btnStart);
      ctrls.appendChild(btnOT);

      card.appendChild(title);
      card.appendChild(timer);
      card.appendChild(ctrls);

      container.appendChild(card);
    });
  }

  function addProject(){
    let name=document.getElementById("projName").value.trim();
    let percent=parseFloat(document.getElementById("projPercent").value);

    if(!name||isNaN(percent)||percent<=0){ alert("Nhập đúng tên & %"); return;}

    let sec = (percent/100)*BASE_SECONDS;

    let existing = projects.find(p=>p.name.toLowerCase()===name.toLowerCase());

    if(existing){
      existing.totalSeconds += sec;
      existing.remainingSeconds += sec;
      existing.allocatedSeconds += sec;
    } else {
      projects.push({
        name,
        allocation:percent,
        allocatedSeconds:sec,
        totalSeconds:sec,
        remainingSeconds:sec,
        running:false,
        lastTick:null
      });
    }

    document.getElementById("projName").value="";
    document.getElementById("projPercent").value="";
    render();
  }

  function toggle(name){
    let now=Date.now();
    projects.forEach(p=>{
      if(p.name===name){
        p.running=!p.running;
        p.lastTick=now;
      } else {
        p.running=false;
      }
    });
    render();
  }

  function addOT(name){
    let min=prompt("Cộng thêm bao nhiêu phút OT?", "30");
    if(min===null) return;
    min=parseFloat(min);
    if(isNaN(min)||min<=0) return;
    
    let add=min*60;
    let p=projects.find(p=>p.name===name);
    p.totalSeconds+=add;
    p.remainingSeconds+=add;
    render();
  }

  setInterval(()=>{
    let now=Date.now();
    let changed=false;

    projects.forEach(p=>{
      if(p.running && p.remainingSeconds>0){
        let delta=(now - (p.lastTick||now))/1000;
        if(delta>=0.5){
          p.remainingSeconds-=delta;
          p.lastTick=now;
          if(p.remainingSeconds<=0){
            alert(`Project ${p.name} đã hết giờ!`)
            p.remainingSeconds=0;
            p.running=false;
          }
          changed=true;
        }
      }
    });

    if(changed) render();
  },500);

</script>
</body>
</html>
