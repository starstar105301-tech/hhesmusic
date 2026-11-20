<!DOCTYPE html>
<html lang="zh-Hant">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>節奏白板</title>
<style>
:root{box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px);--bg:#eef3f8;--ink:#1f2937;--muted:#6b7280;--accent:#2563eb;--card:#fff;--line:#cbd5e1}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#111827;--ink:#e5e7eb;--muted:#9ca3af;--accent:#60a5fa}}
:root[data-theme="dark"]{--bg:#111827;--ink:#e5e7eb;--muted:#9ca3af;--accent:#60a5fa}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font-family:"Noto Sans TC","PingFang TC","Microsoft JhengHei",sans-serif;padding:16px}
h1{font-size:1.4rem;margin:0 0 4px}
p.hint{margin:0 0 14px;color:var(--muted);font-size:.95rem}
.wrap{max-width:980px;margin:0 auto}
.palette{display:flex;gap:14px;flex-wrap:wrap;margin-bottom:16px}
.pcard{background:var(--card);color:#111;border:2px solid var(--line);border-radius:12px;padding:8px 10px 6px;text-align:center;cursor:grab;touch-action:none;user-select:none;width:110px}
.pcard.sel{border-color:var(--accent);box-shadow:0 0 0 3px rgba(37,99,235,.3)}
.pcard span{display:block;font-size:.85rem;margin-top:2px}
.pcard svg{width:70px;height:80px}
.board{background:#fff;color:#111;border-radius:14px;padding:18px 14px;box-shadow:0 4px 18px rgba(0,0,0,.15);overflow-x:auto}
.row{display:flex;align-items:stretch;margin:10px 0;min-width:640px}
.ts{width:44px;display:flex;flex-direction:column;justify-content:center;align-items:center;font-weight:700;font-size:1.5rem;line-height:1.1;flex:none}
.ts.empty{visibility:hidden}
.measure{flex:1;display:flex;border-left:3px solid #111;position:relative}
.measure:last-child{border-right:3px double #111}
.slot{flex:1;min-height:110px;border-right:1px dashed #cbd5e1;display:flex;align-items:center;justify-content:center;position:relative;touch-action:none}
.slot:last-child{border-right:none}
.slot::after{content:attr(data-b);position:absolute;bottom:3px;left:0;right:0;text-align:center;font-size:.75rem;color:#94a3b8}
.slot.over{background:#dbeafe}
.slot svg{width:60px;height:72px;cursor:grab}
.row::before{content:"";}
.line{position:absolute;left:0;right:0;top:50%;border-top:1.5px solid #111;pointer-events:none}
.ghost{position:fixed;pointer-events:none;z-index:99;opacity:.85;transform:translate(-50%,-50%)}
.ghost svg{width:60px;height:72px}
.tools{margin-top:14px}
button{font:inherit;padding:8px 16px;border-radius:10px;border:1px solid var(--line);background:var(--card);color:#111;cursor:pointer}
</style>
</head>
<body>
<div class="wrap">
<h1>🥁 節奏白板</h1>
<p class="hint">把圖卡拖進白板的拍子格裡（也可以先點圖卡，再點格子）。點一下已放的圖卡可以拿掉。每格 = 一拍。</p>
<div class="palette" id="palette"></div>
<div class="board" id="board"></div>
<div class="tools"><button id="clear">全部清除</button></div>
</div>
<script>
const NOTE=(x,y)=>`<ellipse cx="${x}" cy="${y}" rx="10" ry="7.2" transform="rotate(-20 ${x} ${y})" fill="#111"/>`;
const ART={
 q:`<svg viewBox="0 0 70 80">${NOTE(28,62)}<line x1="37" y1="60" x2="37" y2="14" stroke="#111" stroke-width="3"/></svg>`,
 e:`<svg viewBox="0 0 70 80">${NOTE(15,62)}${NOTE(51,62)}<line x1="24" y1="60" x2="24" y2="16" stroke="#111" stroke-width="3"/><line x1="60" y1="60" x2="60" y2="16" stroke="#111" stroke-width="3"/><polygon points="22.5,14 61.5,14 61.5,24 22.5,24" fill="#111"/></svg>`,
 r:`<svg viewBox="0 0 70 80"><path d="M28 12 L44 30 L30 42 L44 58 C34 54 28 62 34 70 C38 74 42 72 44 70" fill="none" stroke="#111" stroke-width="5" stroke-linejoin="round" stroke-linecap="round"/></svg>`
};
const NAME={q:"四分音符",e:"八分音符（一組）",r:"四分休止符"};
const data=Array(32).fill(null);
let sel=null;
const $=s=>document.querySelector(s);
const pal=$("#palette");
for(const k of ["q","e","r"]){
  const d=document.createElement("div");d.className="pcard";d.dataset.k=k;
  d.innerHTML=ART[k]+`<span>${NAME[k]}</span>`;pal.appendChild(d);
}
const board=$("#board");
for(let r=0;r<2;r++){
  const row=document.createElement("div");row.className="row";
  row.innerHTML=`<div class="ts${r?" empty":""}"><div>4</div><div>4</div></div>`;
  for(let m=0;m<4;m++){
    const me=document.createElement("div");me.className="measure";
    for(let b=0;b<4;b++){
      const s=document.createElement("div");s.className="slot";s.dataset.i=r*16+m*4+b;s.dataset.b=b+1;me.appendChild(s);
    }
    row.appendChild(me);
  }
  board.appendChild(row);
}
const slots=[...document.querySelectorAll(".slot")];
function render(){
  slots.forEach((s,i)=>{s.innerHTML=data[i]?ART[data[i]]:"";});
  document.querySelectorAll(".pcard").forEach(c=>c.classList.toggle("sel",c.dataset.k===sel));
}
function slotAt(x,y){const el=document.elementFromPoint(x,y);return el&&el.closest(".slot");}
let drag=null;
document.addEventListener("pointerdown",e=>{
  const pc=e.target.closest(".pcard"),sl=e.target.closest(".slot");
  let k=null,from=null;
  if(pc){k=pc.dataset.k}
  else if(sl&&data[sl.dataset.i]){k=data[sl.dataset.i];from=+sl.dataset.i}
  else if(sl&&sel){data[sl.dataset.i]=sel;render();return}
  else return;
  drag={k,from,x:e.clientX,y:e.clientY,moved:false,ghost:null,pc:!!pc};
  e.preventDefault();
});
document.addEventListener("pointermove",e=>{
  if(!drag)return;
  if(!drag.moved&&Math.hypot(e.clientX-drag.x,e.clientY-drag.y)>6){
    drag.moved=true;
    const g=document.createElement("div");g.className="ghost";g.innerHTML=ART[drag.k];document.body.appendChild(g);drag.ghost=g;
  }
  if(drag.moved){
    drag.ghost.style.left=e.clientX+"px";drag.ghost.style.top=e.clientY+"px";
    const t=slotAt(e.clientX,e.clientY);
    slots.forEach(s=>s.classList.toggle("over",s===t));
  }
});
document.addEventListener("pointerup",e=>{
  if(!drag)return;
  const d=drag;drag=null;
  if(d.ghost)d.ghost.remove();
  slots.forEach(s=>s.classList.remove("over"));
  if(!d.moved){
    if(d.pc){sel=sel===d.k?null:d.k}
    else{data[d.from]=null}
    render();return;
  }
  const t=slotAt(e.clientX,e.clientY);
  if(t){
    const i=+t.dataset.i;
    if(d.from!==null){const old=data[i];data[i]=d.k;data[d.from]=old}
    else data[i]=d.k;
  }else if(d.from!==null){data[d.from]=null}
  render();
});
document.addEventListener("pointercancel",()=>{if(drag&&drag.ghost)drag.ghost.remove();drag=null;slots.forEach(s=>s.classList.remove("over"))});
$("#clear").onclick=()=>{data.fill(null);render()};
render();
</script>
</body>
</html>
