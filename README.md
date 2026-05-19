# obligacion
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no,viewport-fit=cover"/>
<meta name="apple-mobile-web-app-capable" content="yes"/>
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent"/>
<meta name="apple-mobile-web-app-title" content="Obligaciones"/>
<meta name="theme-color" content="#070B14"/>
<title>Mis Obligaciones</title>
<style>
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
html,body{height:100%;background:#070B14;color:#F8FAFC;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;overflow-x:hidden}
::-webkit-scrollbar{display:none}
button{font-family:inherit;cursor:pointer}
input,select{font-family:inherit;outline:none}
input[type=number]::-webkit-inner-spin-button{-webkit-appearance:none}

.page{min-height:100vh;background:#070B14;max-width:430px;margin:0 auto;position:relative}

/* HEADER */
.hdr{background:linear-gradient(160deg,#0F1A35,#0A1628);padding:calc(env(safe-area-inset-top,44px) + 12px) 20px 18px;border-bottom:1px solid rgba(255,255,255,0.06)}
.hdr-sup{font-size:11px;color:#64748B;letter-spacing:2px;text-transform:uppercase;text-align:center;margin-bottom:6px}
.month-nav{display:flex;align-items:center;justify-content:space-between;margin-bottom:3px}
.nav-btn{background:rgba(255,255,255,0.07);border:none;color:#94A3B8;width:34px;height:34px;border-radius:9px;font-size:22px;display:flex;align-items:center;justify-content:center}
.month-title{text-align:center}
.month-title h1{font-size:26px;font-weight:800;letter-spacing:-0.5px}
.current-badge{font-size:11px;color:#A78BFA;font-weight:700;letter-spacing:1.5px;margin-top:2px}
.cycle-range{text-align:center;font-size:12px;color:#475569;margin-bottom:14px}
.cycle-range span{color:#94A3B8;font-weight:600}
.kpis{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:12px}
.kpi{border-radius:12px;padding:11px 13px}
.kpi-lbl{font-size:10px;letter-spacing:1px;text-transform:uppercase;margin-bottom:4px;opacity:.9}
.kpi-val{font-size:16px;font-weight:800}
.prog-row{display:flex;justify-content:space-between;font-size:11px;color:#64748B;margin-bottom:4px}
.prog-row span:last-child{color:#A78BFA;font-weight:700}
.bar-bg{background:rgba(255,255,255,0.07);border-radius:6px;height:7px}
.bar-fill{height:100%;border-radius:6px;background:linear-gradient(90deg,#7C3AED,#10B981);transition:width .5s}

/* BANNER */
.banner{background:linear-gradient(135deg,rgba(124,58,237,0.18),rgba(79,70,229,0.12));border:1px solid rgba(124,58,237,0.3);border-radius:14px;padding:12px 14px;margin-bottom:14px;display:flex;gap:10px;align-items:flex-start}
.banner-icon{font-size:26px;flex-shrink:0}
.banner-txt{flex:1;font-size:12px;color:#94A3B8;line-height:1.5}
.banner-txt strong{color:#A78BFA}
.banner-close{background:none;border:none;color:#475569;font-size:20px;padding:0 2px;flex-shrink:0;line-height:1}

/* TABS */
.tabs{display:flex;gap:8px;padding:12px 20px 0}
.tab{flex:1;padding:9px 0;border-radius:10px;border:none;font-size:13px;transition:all .2s}
.tab.on{background:rgba(124,58,237,0.3);color:#A78BFA;font-weight:700}
.tab.off{background:rgba(255,255,255,0.05);color:#64748B;font-weight:400}

/* CONTENT */
.content{padding:16px 20px;padding-bottom:calc(90px + env(safe-area-inset-bottom,20px))}

/* DIVIDERS */
.div-row{display:flex;align-items:center;gap:8px;margin-bottom:10px}
.div-line{flex:1;height:1px;background:rgba(255,255,255,0.07)}
.div-lbl{font-size:11px;font-weight:700;letter-spacing:1.2px;text-transform:uppercase;white-space:nowrap;border-radius:20px;padding:3px 10px}
.lbl-p{color:#A78BFA;background:rgba(124,58,237,0.15);border:1px solid rgba(124,58,237,0.25)}
.lbl-a{color:#F59E0B;background:rgba(245,158,11,0.12);border:1px solid rgba(245,158,11,0.25)}
.info-box{background:rgba(245,158,11,0.06);border:1px solid rgba(245,158,11,0.18);border-radius:11px;padding:9px 12px;margin-bottom:10px;font-size:12px;color:#D97706;line-height:1.5}

/* PAYMENT ROW */
.prow{background:rgba(255,255,255,0.04);border:1px solid rgba(255,255,255,0.08);border-radius:14px;padding:12px 13px;margin-bottom:8px;display:flex;align-items:center;gap:11px;transition:all .18s;-webkit-user-select:none;user-select:none}
.prow:active{transform:scale(0.98);opacity:.8}
.prow.done{background:rgba(16,185,129,0.07);border-color:rgba(16,185,129,0.25)}
.prow.today{background:rgba(239,68,68,0.09);border-color:rgba(239,68,68,0.35)}
.cb{width:23px;height:23px;border-radius:50%;display:flex;align-items:center;justify-content:center;flex-shrink:0;font-size:12px;color:#fff;font-weight:700;transition:all .2s}
.prow-icon{font-size:19px;flex-shrink:0}
.prow-info{flex:1;min-width:0}
.prow-name{font-weight:600;font-size:14px;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.prow-name.done-txt{color:#64748B;text-decoration:line-through}
.prow-name.active-txt{color:#F8FAFC}
.prow-day{font-size:11px;color:#64748B;display:flex;gap:6px;align-items:center}
.badge-hot{color:#EF4444;font-weight:700;font-size:10px}
.prow-right{text-align:right;display:flex;flex-direction:column;align-items:flex-end;gap:3px}
.prow-amt{font-size:13px;font-weight:700}
.prow-meta{display:flex;gap:4px;align-items:center}
.days-tag{font-size:11px;font-weight:600}
.alarm-btn{background:rgba(255,255,255,0.08);border:none;border-radius:6px;width:26px;height:26px;font-size:13px;display:flex;align-items:center;justify-content:center;flex-shrink:0}
.alarm-btn:active{opacity:.6}

/* SUMMARY */
.summary-box{background:rgba(255,255,255,0.03);border:1px solid rgba(255,255,255,0.08);border-radius:14px;padding:14px 16px}
.summary-title{font-size:11px;color:#64748B;margin-bottom:10px;text-transform:uppercase;letter-spacing:1px}
.summary-row{display:flex;justify-content:space-between;margin-bottom:7px;font-size:13px}
.summary-row span:first-child{color:#94A3B8}

/* DEBT CARD */
.dcard{background:rgba(255,255,255,0.04);border:1px solid rgba(255,255,255,0.08);border-radius:16px;padding:15px;margin-bottom:12px}
.dcard-top{display:flex;align-items:flex-start;gap:12px}
.dcard-ico{width:44px;height:44px;border-radius:12px;display:flex;align-items:center;justify-content:center;font-size:22px;flex-shrink:0}
.dcard-info{flex:1;min-width:0}
.dcard-name{font-weight:700;font-size:15px;margin-bottom:2px}
.dcard-sub{font-size:12px;color:#64748B}
.dcard-actions{display:flex;gap:5px}
.dcard-btn{background:rgba(255,255,255,0.08);border:none;border-radius:8px;width:32px;height:32px;font-size:14px;display:flex;align-items:center;justify-content:center}
.dcard-btn:active{opacity:.6}
.bal-row{display:flex;justify-content:space-between;margin:10px 0 5px;font-size:12px}
.bal-row span:first-child{color:#64748B}
.bal-bar{background:rgba(255,255,255,0.06);border-radius:5px;height:5px}
.bal-fill{height:100%;border-radius:5px;max-width:100%}

/* ADD BTN */
.add-btn{width:100%;background:rgba(124,58,237,0.1);border:2px dashed rgba(124,58,237,0.35);border-radius:16px;padding:14px;color:#A78BFA;font-size:15px;font-weight:600;display:flex;align-items:center;justify-content:center;gap:8px}
.add-btn:active{opacity:.7}

/* UPCOMING */
.up-card{border-radius:14px;padding:14px 15px;margin-bottom:10px;display:flex;align-items:center;gap:12px}
.up-icon{font-size:26px}
.up-info{flex:1}
.up-name{font-weight:700;font-size:15px}
.up-sub{font-size:12px;color:#94A3B8}
.up-right{text-align:right;display:flex;flex-direction:column;align-items:flex-end;gap:5px}
.up-tag{font-size:12px;font-weight:700;border-radius:8px;padding:3px 8px}
.up-alarm{background:rgba(255,255,255,0.08);border:none;border-radius:6px;padding:4px 9px;color:#94A3B8;font-size:12px}
.up-alarm:active{opacity:.6}
.empty{text-align:center;color:#475569;padding:48px 0;font-size:15px}

/* FAB */
.fab{position:fixed;bottom:calc(28px + env(safe-area-inset-bottom,0px));right:20px;width:52px;height:52px;border-radius:50%;background:linear-gradient(135deg,#7C3AED,#4F46E5);border:none;color:#fff;font-size:26px;box-shadow:0 4px 20px rgba(124,58,237,.5);display:flex;align-items:center;justify-content:center;z-index:50;line-height:1}
.fab:active{transform:scale(0.9)}

/* TOAST */
.toast{position:fixed;top:calc(20px + env(safe-area-inset-top,44px));left:50%;transform:translateX(-50%);background:#1E293B;border:1px solid rgba(255,255,255,.15);border-radius:12px;padding:10px 18px;font-size:13px;color:#F8FAFC;z-index:3000;max-width:320px;text-align:center;box-shadow:0 8px 32px rgba(0,0,0,.4);pointer-events:none;white-space:nowrap}

/* MODAL */
.modal-bg{position:fixed;inset:0;background:rgba(0,0,0,0.78);z-index:2000;display:flex;align-items:flex-end}
.modal-sheet{background:#0F172A;border-radius:24px 24px 0 0;width:100%;max-height:88vh;overflow-y:auto;padding:24px 20px calc(40px + env(safe-area-inset-bottom,0px));border:1px solid rgba(255,255,255,0.1)}
.modal-head{display:flex;justify-content:space-between;align-items:center;margin-bottom:20px}
.modal-title{font-size:18px;font-weight:700}
.modal-close{background:rgba(255,255,255,0.1);border:none;color:#F8FAFC;width:32px;height:32px;border-radius:50%;font-size:18px;display:flex;align-items:center;justify-content:center}
.modal-close:active{opacity:.6}
.form{display:flex;flex-direction:column;gap:14px}
.field label{font-size:12px;color:#94A3B8;display:block;margin-bottom:6px}
.inp{width:100%;background:rgba(255,255,255,0.05);border:1px solid rgba(255,255,255,0.15);border-radius:10px;padding:10px 12px;color:#F8FAFC;font-size:15px}
.inp:focus{border-color:rgba(124,58,237,0.6);background:rgba(255,255,255,0.07)}
select.inp{background:#1E293B}
.grid2{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.icon-grid{display:flex;gap:8px;flex-wrap:wrap}
.ico-btn{width:40px;height:40px;border-radius:10px;border:1px solid rgba(255,255,255,0.1);background:rgba(255,255,255,0.05);font-size:20px;display:flex;align-items:center;justify-content:center}
.ico-btn.sel{border:2px solid #7C3AED;background:rgba(124,58,237,0.2)}
.ico-btn:active{opacity:.7}
.color-grid{display:flex;gap:8px;flex-wrap:wrap}
.col-btn{width:32px;height:32px;border-radius:50%;border:2px solid transparent}
.col-btn.sel{border-color:#F8FAFC!important;transform:scale(1.15)}
.col-btn:active{transform:scale(0.9)}
.save-btn{background:linear-gradient(135deg,#7C3AED,#4F46E5);border:none;border-radius:12px;padding:14px;color:#F8FAFC;font-size:16px;font-weight:700;margin-top:6px}
.save-btn:active{opacity:.8}
.del-btn{background:rgba(239,68,68,0.15);border:1px solid rgba(239,68,68,0.3);border-radius:12px;padding:12px;color:#EF4444;font-size:14px;font-weight:600}
.del-btn:active{opacity:.7}
</style>
</head>
<body>
<div class="page" id="root"></div>

<script>
// ═══════════════════════════════════════════════════════
//  CONSTANTS & DATA
// ═══════════════════════════════════════════════════════
const CYCLE = 16;
const MES = ["Enero","Febrero","Marzo","Abril","Mayo","Junio","Julio","Agosto","Septiembre","Octubre","Noviembre","Diciembre"];
const ICONS = ["💳","🚗","🏦","🏛️","🏠","🎒","⛳","👩‍💼","📱","📋","🌐","🏥","📚","💼","🏋️","🐶"];
const COLORS = ["#7C3AED","#0EA5E9","#10B981","#F59E0B","#EC4899","#1E40AF","#F97316","#EF4444","#14B8A6","#8B5CF6"];

const DEFAULT_DEBTS = [
  {id:1,name:"Tarjeta NU",type:"credit",balance:7850000,payment:420000,dueDay:1,dueDay2:null,payment2:null,color:"#7C3AED",icon:"💳"},
  {id:2,name:"Crédito Carro Coomeva",type:"loan",balance:157281352,payment:3040000,dueDay:27,dueDay2:null,payment2:null,color:"#0EA5E9",icon:"🚗"},
  {id:3,name:"Club Campestre Guaymaral",type:"service",balance:null,payment:3500000,dueDay:27,dueDay2:null,payment2:null,color:"#10B981",icon:"⛳"},
  {id:4,name:"Colegio Gregorio",type:"service",balance:null,payment:5052800,dueDay:5,dueDay2:null,payment2:null,color:"#F59E0B",icon:"🎒"},
  {id:5,name:"Salario MariaE",type:"salary",balance:null,payment:1719000,dueDay:15,dueDay2:30,payment2:1464000,color:"#EC4899",icon:"👩‍💼"},
  {id:6,name:"Crédito BBVA",type:"loan",balance:365445367,payment:10200000,dueDay:5,dueDay2:null,payment2:null,color:"#1E40AF",icon:"🏦"},
  {id:7,name:"Crédito AV Villas",type:"loan",balance:147603520,payment:3467272,dueDay:2,dueDay2:null,payment2:null,color:"#F97316",icon:"🏛️"},
  {id:8,name:"MiPlanilla",type:"service",balance:null,payment:1820000,dueDay:25,dueDay2:null,payment2:null,color:"#14B8A6",icon:"📋"},
];

// ═══════════════════════════════════════════════════════
//  STATE (simple reactive store)
// ═══════════════════════════════════════════════════════
function load(k,d){try{const v=localStorage.getItem(k);return v?JSON.parse(v):d;}catch(e){return d;}}
function save(k,v){try{localStorage.setItem(k,JSON.stringify(v));}catch(e){}}

const now = new Date();
const S = {
  debts: load("debts2", DEFAULT_DEBTS),
  paid: load("paid2", {}),
  salaryMonth: now.getMonth(),
  salaryYear: now.getFullYear(),
  tab: "month",
  projDebt: null,
  editDebt: null,
  addOpen: false,
  toast: "",
  toastTimer: null,
  bannerDismissed: load("bd", false),
};

function setState(patch){
  Object.assign(S, patch);
  render();
}
function saveDebts(d){S.debts=d;save("debts2",d);}
function savePaid(p){S.paid=p;save("paid2",p);}

// ═══════════════════════════════════════════════════════
//  HELPERS
// ═══════════════════════════════════════════════════════
function fmt(n){
  if(n==null)return "—";
  return "$"+Math.round(n).toString().replace(/\B(?=(\d{3})+(?!\d))/g,".");
}
function getCalMonth(day,sm,sy){
  if(day>=CYCLE)return{cm:sm,cy:sy};
  const d=new Date(sy,sm+1,1);
  return{cm:d.getMonth(),cy:d.getFullYear()};
}
function daysUntil(day,cy,cm){
  const t=new Date(cy,cm,day,23,59,0);
  return Math.ceil((t-new Date())/(86400000));
}
function sColor(d){
  if(d<=3)return"#EF4444";
  if(d<=7)return"#F59E0B";
  return"#10B981";
}
function buildCycle(debts,sm,sy){
  const items=[];
  debts.forEach(function(d){
    [[d.dueDay,d.payment,1],[d.dueDay2,d.payment2,2]].forEach(function(arr){
      var day=arr[0],amt=arr[1],slot=arr[2];
      if(!day||!amt)return;
      var c=getCalMonth(day,sm,sy);
      items.push({debt:d,day:day,amount:amt,slot:slot,cm:c.cm,cy:c.cy});
    });
  });
  items.sort(function(a,b){
    return(a.day>=CYCLE?a.day:a.day+100)-(b.day>=CYCLE?b.day:b.day+100);
  });
  return items;
}
function pKey(p){return p.debt.id+"-"+p.slot+"-"+p.cy+"-"+p.cm;}
function isPaid(p){return !!S.paid[pKey(p)];}
function togglePaid(p){
  var k=pKey(p);
  var np=Object.assign({},S.paid);
  np[k]=!np[k];
  savePaid(np);
  setState({paid:np});
}
function showToast(msg){
  if(S.toastTimer)clearTimeout(S.toastTimer);
  var t=setTimeout(function(){setState({toast:"",toastTimer:null});},4000);
  setState({toast:msg,toastTimer:t});
}
function scheduleAlarm(name,icon,amount,day,cm,cy){
  if(!("Notification" in window)){showToast("Navegador sin notificaciones.");return;}
  Notification.requestPermission().then(function(p){
    if(p==="granted"){
      var t=new Date(cy,cm,day,8,0,0);
      var delay=t-Date.now();
      var title=icon+" Pago hoy: "+name;
      var body="Cuota: "+fmt(amount)+" — Día "+day;
      if(delay>0){
        setTimeout(function(){new Notification(title,{body:body});},delay);
        showToast("🔔 Alarma: "+day+"/"+(cm+1)+"/"+cy+" 8:00 AM");
      } else {
        new Notification(title,{body:body});
        showToast("⚠️ Fecha pasada — enviado ahora");
      }
    } else {
      showToast("Permiso denegado.");
    }
  });
}

// ═══════════════════════════════════════════════════════
//  RENDER HELPERS
// ═══════════════════════════════════════════════════════
function el(tag,attrs,kids){
  var e=document.createElement(tag);
  if(attrs)Object.keys(attrs).forEach(function(k){
    if(k==="style"&&typeof attrs[k]==="object"){
      Object.assign(e.style,attrs[k]);
    } else if(k.startsWith("on")&&typeof attrs[k]==="function"){
      e.addEventListener(k.slice(2).toLowerCase(),attrs[k]);
    } else if(k==="className"){
      e.className=attrs[k];
    } else if(k==="htmlFor"){
      e.setAttribute("for",attrs[k]);
    } else {
      try{e.setAttribute(k,attrs[k]);}catch(err){}
    }
  });
  if(kids)kids.forEach(function(c){
    if(c==null||c===false||c===undefined)return;
    if(typeof c==="string"||typeof c==="number"){e.appendChild(document.createTextNode(c));}
    else{e.appendChild(c);}
  });
  return e;
}
function txt(s){return document.createTextNode(String(s));}
function div(cls,kids,extra){return el("div",Object.assign({className:cls},extra||{}),Array.isArray(kids)?kids:[kids]);}

// ═══════════════════════════════════════════════════════
//  COMPONENTS
// ═══════════════════════════════════════════════════════

function renderHeader(cycle){
  var sm=S.salaryMonth,sy=S.salaryYear;
  var totalMonthly=cycle.reduce(function(s,p){return s+(p.amount||0);},0);
  var paidTotal=cycle.filter(isPaid).reduce(function(s,p){return s+(p.amount||0);},0);
  var pending=totalMonthly-paidTotal;
  var totalBalance=S.debts.reduce(function(s,d){return s+(d.balance||0);},0);
  var isCurrent=(sm===now.getMonth()&&sy===now.getFullYear());
  var nextMon=MES[sm===11?0:sm+1];
  var cur3=MES[sm].slice(0,3);
  var nxt3=nextMon.slice(0,3);
  var pct=totalMonthly>0?Math.round((paidTotal/totalMonthly)*100):0;

  var banner=null;
  if(!S.bannerDismissed){
    banner=div("banner",[
      div("banner-icon",["📲"]),
      el("div",{className:"banner-txt"},[
        txt("Toca "),el("strong",null,[txt("Compartir (⎋)")]),
        txt(" → "),el("strong",null,[txt('"Agregar a pantalla de inicio"')]),
        txt(" para instalar como app.")
      ]),
      el("button",{className:"banner-close",onclick:function(){
        save("bd",true);setState({bannerDismissed:true});
      }},["×"])
    ]);
  }

  var kpis=[
    {l:"Gasto del mes",v:totalMonthly,c:"#EF4444",bg:"rgba(239,68,68,0.1)",bc:"rgba(239,68,68,0.2)"},
    {l:"Deuda total",  v:totalBalance, c:"#A78BFA",bg:"rgba(124,58,237,0.12)",bc:"rgba(124,58,237,0.22)"},
    {l:"Pagado",       v:paidTotal,    c:"#10B981",bg:"rgba(16,185,129,0.1)",bc:"rgba(16,185,129,0.2)"},
    {l:"Pendiente",    v:pending,      c:"#F59E0B",bg:"rgba(245,158,11,0.1)",bc:"rgba(245,158,11,0.2)"},
  ];

  return el("div",{className:"hdr"},[
    banner,
    div("hdr-sup",["Obligaciones del salario de"]),
    div("month-nav",[
      el("button",{className:"nav-btn",onclick:function(){
        if(sm===0){setState({salaryMonth:11,salaryYear:sy-1});}
        else setState({salaryMonth:sm-1});
      }},["‹"]),
      el("div",{className:"month-title"},[
        el("h1",null,[MES[sm]+" "+sy]),
        isCurrent?el("div",{className:"current-badge"},["● MES ACTUAL"]):null
      ]),
      el("button",{className:"nav-btn",onclick:function(){
        if(sm===11){setState({salaryMonth:0,salaryYear:sy+1});}
        else setState({salaryMonth:sm+1});
      }},["›"])
    ]),
    el("div",{className:"cycle-range"},[
      txt("Cubre del "),el("span",null,["16 "+cur3]),
      txt(" al "),el("span",null,["15 "+nxt3+(sm===11?" "+(sy+1):"")])
    ]),
    el("div",{className:"kpis"},kpis.map(function(k){
      return el("div",{className:"kpi",style:{background:k.bg,border:"1px solid "+k.bc}},[
        el("div",{className:"kpi-lbl",style:{color:k.c}},[k.l]),
        el("div",{className:"kpi-val"},[fmt(k.v)])
      ]);
    })),
    div("prog-row",[el("span",null,["Progreso"]),el("span",null,[pct+"%"])]),
    div("bar-bg",[el("div",{className:"bar-fill",style:{width:pct+"%"}})])
  ]);
}

function renderPayRow(p){
  var done=isPaid(p);
  var days=daysUntil(p.day,p.cy,p.cm);
  var isToday=days===0,isOD=days<0;
  var cbStyle=done
    ?{border:"none",background:"#10B981"}
    :{border:"2px solid "+p.debt.color,background:"transparent"};
  var cls="prow"+(done?" done":isToday?" today":"");

  var daysLabel="";
  if(!done){
    if(isToday)daysLabel="Hoy";
    else if(isOD)daysLabel=Math.abs(days)+"d venc.";
    else daysLabel=days+"d";
  }

  var row=el("div",{className:cls},[
    el("div",{className:"cb",style:cbStyle},[done?"✓":""]),
    el("div",{className:"prow-icon"},[p.debt.icon]),
    el("div",{className:"prow-info"},[
      el("div",{className:"prow-name "+(done?"done-txt":"active-txt")},[
        p.debt.name+(p.slot===2?" (2ª)":"")
      ]),
      el("div",{className:"prow-day"},[
        "Día "+p.day,
        (isToday&&!done)?el("span",{className:"badge-hot"},["• ¡HOY!"]):null,
        (isOD&&!done)?el("span",{className:"badge-hot"},["• VENCIDO"]):null
      ])
    ]),
    el("div",{className:"prow-right"},[
      el("div",{className:"prow-amt",style:{color:done?"#64748B":"#F8FAFC"}},[fmt(p.amount)]),
      el("div",{className:"prow-meta"},[
        !done?el("span",{className:"days-tag",style:{color:sColor(days)}},[daysLabel]):null,
        el("button",{
          className:"alarm-btn",
          onclick:function(e){
            e.stopPropagation();
            scheduleAlarm(p.debt.name,p.debt.icon,p.amount,p.day,p.cm,p.cy);
          }
        },["🔔"])
      ])
    ])
  ]);
  row.addEventListener("click",function(){togglePaid(p);});
  return row;
}

function renderDivider(txt2,cls){
  return el("div",{className:"div-row"},[
    div("div-line"),
    el("div",{className:"div-lbl "+cls},[txt2]),
    div("div-line")
  ]);
}

function renderChecklist(cycle){
  var sm=S.salaryMonth,sy=S.salaryYear;
  var g1=cycle.filter(function(p){return p.day>=CYCLE;});
  var g2=cycle.filter(function(p){return p.day<CYCLE;});
  var totalMonthly=cycle.reduce(function(s,p){return s+(p.amount||0);},0);
  var paidTotal=cycle.filter(isPaid).reduce(function(s,p){return s+(p.amount||0);},0);
  var pending=totalMonthly-paidTotal;
  var cur3=MES[sm].slice(0,3);
  var nextMon=MES[sm===11?0:sm+1];
  var nxt3=nextMon.slice(0,3);
  var frag=document.createDocumentFragment();

  if(g1.length>0){
    var sec1=document.createElement("div");
    sec1.style.marginBottom="20px";
    sec1.appendChild(renderDivider("💰 "+cur3+" · días 16–31","lbl-p"));
    g1.forEach(function(p){sec1.appendChild(renderPayRow(p));});
    frag.appendChild(sec1);
  }
  if(g2.length>0){
    var sec2=document.createElement("div");
    sec2.style.marginBottom="20px";
    sec2.appendChild(renderDivider("💰 "+cur3+" → "+nxt3+" · días 1–15","lbl-a"));
    sec2.appendChild(el("div",{className:"info-box"},[
      "ℹ️ Vencen en "+nextMon+" pero se pagan con el salario de "+MES[sm]+"."
    ]));
    g2.forEach(function(p){sec2.appendChild(renderPayRow(p));});
    frag.appendChild(sec2);
  }

  var sumBox=div("summary-box",[
    el("div",{className:"summary-title"},["Resumen · Salario "+MES[sm]]),
    ...[
      {l:"Total comprometido",v:totalMonthly,c:"#F8FAFC"},
      {l:"Pagado",            v:paidTotal,   c:"#10B981"},
      {l:"Pendiente",         v:pending,     c:"#F59E0B"},
    ].map(function(r){
      return el("div",{className:"summary-row"},[
        el("span",null,[r.l]),
        el("span",{style:{fontWeight:700,color:r.c}},[fmt(r.v)])
      ]);
    })
  ]);
  frag.appendChild(sumBox);
  return frag;
}

function renderCredits(){
  var sm=S.salaryMonth,sy=S.salaryYear;
  var frag=document.createDocumentFragment();
  frag.appendChild(el("div",{style:{fontSize:"13px",color:"#64748B",marginBottom:"12px"}},["Todas las obligaciones"]));

  S.debts.forEach(function(d){
    var c=getCalMonth(d.dueDay,sm,sy);
    var card=div("dcard",[
      el("div",{className:"dcard-top",style:{marginBottom:d.balance?"0":"0"}},[
        el("div",{className:"dcard-ico",style:{background:d.color+"22",border:"1px solid "+d.color+"44"}},[d.icon]),
        el("div",{className:"dcard-info"},[
          el("div",{className:"dcard-name"},[d.name]),
          el("div",{className:"dcard-sub"},[
            d.dueDay2
              ?"Días "+d.dueDay+" y "+d.dueDay2+" · "+fmt(d.payment)+" + "+fmt(d.payment2)
              :"Día "+d.dueDay+" · "+fmt(d.payment)
          ])
        ]),
        el("div",{className:"dcard-actions"},[
          el("button",{className:"dcard-btn",onclick:function(){setState({editDebt:d});}},["✏️"]),
          d.balance?el("button",{className:"dcard-btn",onclick:function(){setState({projDebt:d});}},["📈"]):null,
          el("button",{className:"dcard-btn",onclick:function(){scheduleAlarm(d.name,d.icon,d.payment,d.dueDay,c.cm,c.cy);}},["🔔"])
        ])
      ]),
      d.balance?el("div",null,[
        el("div",{className:"bal-row"},[
          el("span",null,["Saldo: "+fmt(d.balance)]),
          el("span",{style:{color:d.color}},["~"+Math.ceil(d.balance/d.payment)+" meses"])
        ]),
        div("bal-bar",[el("div",{className:"bal-fill",style:{
          width:Math.min(100,(d.payment/(d.balance||1))*100*5)+"%",
          background:"linear-gradient(90deg,"+d.color+","+d.color+"66)"
        }})])
      ]):null
    ]);
    frag.appendChild(card);
  });

  var addBtn=el("button",{className:"add-btn",onclick:function(){setState({addOpen:true});}},["+ Agregar obligación"]);
  frag.appendChild(addBtn);
  return frag;
}

function renderUpcoming(cycle){
  var upc=cycle.map(function(p){
    return Object.assign({},p,{days:daysUntil(p.day,p.cy,p.cm)});
  }).filter(function(p){return p.days>=0&&p.days<=7;})
    .sort(function(a,b){return a.days-b.days;});

  var frag=document.createDocumentFragment();
  frag.appendChild(el("div",{style:{fontSize:"13px",color:"#64748B",marginBottom:"12px"}},["Próximos 7 días"]));

  if(upc.length===0){
    frag.appendChild(el("div",{className:"empty"},["🎉 Sin pagos urgentes esta semana"]));
    return frag;
  }
  upc.forEach(function(p){
    var sc=sColor(p.days);
    var card=el("div",{
      className:"up-card",
      style:{
        background:p.days===0?"rgba(239,68,68,0.1)":"rgba(255,255,255,0.04)",
        border:"1px solid "+(p.days===0?"rgba(239,68,68,0.3)":"rgba(255,255,255,0.08)")
      }
    },[
      el("div",{className:"up-icon"},[p.debt.icon]),
      el("div",{className:"up-info"},[
        el("div",{className:"up-name"},[p.debt.name+(p.slot===2?" (2ª)":"")]),
        el("div",{className:"up-sub"},[fmt(p.amount)+" · Día "+p.day])
      ]),
      el("div",{className:"up-right"},[
        el("div",{className:"up-tag",style:{color:sc,background:sc+"22"}},[p.days===0?"¡HOY!":p.days+"d"]),
        el("button",{
          className:"up-alarm",
          onclick:function(){scheduleAlarm(p.debt.name,p.debt.icon,p.amount,p.day,p.cm,p.cy);}
        },["🔔 Alarma"])
      ])
    ]);
    frag.appendChild(card);
  });
  return frag;
}

function renderProjection(){
  var debt=S.projDebt;
  if(!debt||!debt.balance)return null;
  var months=[],bal=debt.balance,maxBal=debt.balance;
  for(var i=1;i<=36;i++){
    bal=Math.max(0,bal-debt.payment);
    var d=new Date(now.getFullYear(),now.getMonth()+i,1);
    months.push({label:d.toLocaleDateString("es-CO",{month:"short",year:"2-digit"}),balance:bal});
    if(bal===0)break;
  }
  var bg=el("div",{className:"modal-bg"});
  bg.addEventListener("click",function(){setState({projDebt:null});});
  var sheet=el("div",{className:"modal-sheet"});
  sheet.addEventListener("click",function(e){e.stopPropagation();});
  var head=el("div",{className:"modal-head"},[
    el("div",null,[
      el("div",{style:{fontSize:"18px",fontWeight:"700"}},[debt.icon+" "+debt.name]),
      el("div",{style:{fontSize:"13px",color:"#94A3B8",marginTop:"2px"}},["Proyección de saldo"])
    ]),
    el("button",{className:"modal-close",onclick:function(){setState({projDebt:null});}},["×"])
  ]);
  sheet.appendChild(head);
  months.forEach(function(m){
    var pct=((maxBal-m.balance)/maxBal*100).toFixed(1);
    var row=el("div",{style:{marginBottom:"10px"}},[
      el("div",{style:{display:"flex",justifyContent:"space-between",fontSize:"13px",color:"#94A3B8",marginBottom:"4px"}},[
        el("span",null,[m.label]),
        el("span",{style:{color:m.balance===0?"#10B981":"#F8FAFC",fontWeight:"600"}},[m.balance===0?"✅ Pagado":fmt(m.balance)])
      ]),
      div("bar-bg",[el("div",{style:{width:pct+"%",height:"100%",borderRadius:"6px",background:"linear-gradient(90deg,"+debt.color+","+debt.color+"66)"}})])
    ]);
    sheet.appendChild(row);
  });
  if(months[months.length-1]&&months[months.length-1].balance===0){
    sheet.appendChild(el("div",{style:{background:"rgba(16,185,129,0.15)",border:"1px solid rgba(16,185,129,0.3)",borderRadius:"12px",padding:"12px 16px",textAlign:"center",color:"#10B981",fontSize:"14px",fontWeight:"600",marginTop:"12px"}},
      ["🎉 Libre de deuda en "+months.length+" meses"]
    ));
  }
  bg.appendChild(sheet);
  return bg;
}

function renderDebtModal(){
  var debt=S.editDebt;
  var isNew=!debt&&S.addOpen;
  if(!debt&&!isNew)return null;

  var f={
    name:debt?debt.name:"",
    type:debt?debt.type:"service",
    balance:debt&&debt.balance?debt.balance:"",
    payment:debt?debt.payment:"",
    dueDay:debt?debt.dueDay:"",
    dueDay2:debt&&debt.dueDay2?debt.dueDay2:"",
    payment2:debt&&debt.payment2?debt.payment2:"",
    color:debt?debt.color:"#7C3AED",
    icon:debt?debt.icon:"💳",
    id:debt?debt.id:null
  };

  var bg=el("div",{className:"modal-bg"});
  bg.addEventListener("click",function(){setState({editDebt:null,addOpen:false});});
  var sheet=el("div",{className:"modal-sheet"});
  sheet.addEventListener("click",function(e){e.stopPropagation();});

  sheet.appendChild(el("div",{className:"modal-head"},[
    el("div",{className:"modal-title"},[debt?"Editar obligación":"Nueva obligación"]),
    el("button",{className:"modal-close",onclick:function(){setState({editDebt:null,addOpen:false});}},["×"])
  ]));

  var form=div("form");

  // Name
  var nameInp=el("input",{className:"inp",type:"text",value:f.name,placeholder:"Ej: Tarjeta Visa"});
  nameInp.addEventListener("input",function(){f.name=this.value;});
  form.appendChild(el("div",{className:"field"},[el("label",null,["Nombre"]),nameInp]));

  // Type
  var typeInp=el("select",{className:"inp"});
  ["loan","credit","service","salary"].forEach(function(v){
    var o=el("option",{value:v},[v==="loan"?"Crédito":v==="credit"?"Tarjeta de crédito":v==="service"?"Servicio":"Salario"]);
    if(v===f.type)o.selected=true;
    typeInp.appendChild(o);
  });
  typeInp.addEventListener("change",function(){f.type=this.value;});
  form.appendChild(el("div",{className:"field"},[el("label",null,["Tipo"]),typeInp]));

  // Balance
  var balInp=el("input",{className:"inp",type:"number",value:f.balance,placeholder:"0"});
  balInp.addEventListener("input",function(){f.balance=this.value;});
  form.appendChild(el("div",{className:"field"},[el("label",null,["Saldo actual (si aplica)"]),balInp]));

  // Payment + day row
  var p1=el("input",{className:"inp",type:"number",value:f.payment,placeholder:"0"});
  p1.addEventListener("input",function(){f.payment=this.value;});
  var d1=el("input",{className:"inp",type:"number",value:f.dueDay,placeholder:"1-31",min:"1",max:"31"});
  d1.addEventListener("input",function(){f.dueDay=this.value;});
  form.appendChild(el("div",{className:"grid2"},[
    el("div",{className:"field"},[el("label",null,["Cuota / Pago 1"]),p1]),
    el("div",{className:"field"},[el("label",null,["Día de pago 1"]),d1])
  ]));

  // Payment2 + day2
  var p2=el("input",{className:"inp",type:"number",value:f.payment2,placeholder:"0 (opcional)"});
  p2.addEventListener("input",function(){f.payment2=this.value;});
  var d2=el("input",{className:"inp",type:"number",value:f.dueDay2,placeholder:"opcional",min:"1",max:"31"});
  d2.addEventListener("input",function(){f.dueDay2=this.value;});
  form.appendChild(el("div",{className:"grid2"},[
    el("div",{className:"field"},[el("label",null,["Pago 2 (opcional)"]),p2]),
    el("div",{className:"field"},[el("label",null,["Día de pago 2"]),d2])
  ]));

  // Icons
  var iconGrid=div("icon-grid");
  ICONS.forEach(function(ic){
    var btn=el("button",{className:"ico-btn"+(f.icon===ic?" sel":"")},ic.split(""));
    btn.addEventListener("click",function(){
      f.icon=ic;
      iconGrid.querySelectorAll(".ico-btn").forEach(function(b){b.classList.remove("sel");});
      this.classList.add("sel");
    });
    iconGrid.appendChild(btn);
  });
  form.appendChild(el("div",{className:"field"},[el("label",null,["Ícono"]),iconGrid]));

  // Colors
  var colorGrid=div("color-grid");
  COLORS.forEach(function(c){
    var btn=el("button",{className:"col-btn"+(f.color===c?" sel":""),style:{background:c}});
    btn.addEventListener("click",function(){
      f.color=c;
      colorGrid.querySelectorAll(".col-btn").forEach(function(b){b.classList.remove("sel");});
      this.classList.add("sel");
    });
    colorGrid.appendChild(btn);
  });
  form.appendChild(el("div",{className:"field"},[el("label",null,["Color"]),colorGrid]));

  // Save
  var saveBtn=el("button",{className:"save-btn"},[ debt?"Guardar cambios":"Agregar obligación"]);
  saveBtn.addEventListener("click",function(){
    if(!f.name||!f.payment||!f.dueDay)return;
    var saved={
      id:f.id||Date.now(),
      name:f.name, type:f.type,
      balance:f.balance?parseFloat(f.balance):null,
      payment:parseFloat(f.payment),
      payment2:f.payment2?parseFloat(f.payment2):null,
      dueDay:parseInt(f.dueDay),
      dueDay2:f.dueDay2?parseInt(f.dueDay2):null,
      color:f.color, icon:f.icon
    };
    var nd;
    if(debt){nd=S.debts.map(function(d){return d.id===saved.id?saved:d;});}
    else{nd=S.debts.concat([saved]);}
    saveDebts(nd);
    setState({debts:nd,editDebt:null,addOpen:false});
  });
  form.appendChild(saveBtn);

  // Delete (edit only)
  if(debt){
    var delBtn=el("button",{className:"del-btn"},["🗑️ Eliminar obligación"]);
    delBtn.addEventListener("click",function(){
      if(!confirm("¿Eliminar "+debt.name+"?"))return;
      var nd=S.debts.filter(function(d){return d.id!==debt.id;});
      saveDebts(nd);
      setState({debts:nd,editDebt:null,addOpen:false});
    });
    form.appendChild(delBtn);
  }

  sheet.appendChild(form);
  bg.appendChild(sheet);
  return bg;
}

// ═══════════════════════════════════════════════════════
//  MAIN RENDER
// ═══════════════════════════════════════════════════════
function render(){
  var root=document.getElementById("root");
  root.innerHTML="";

  var cycle=buildCycle(S.debts,S.salaryMonth,S.salaryYear);
  var page=div("page");

  page.appendChild(renderHeader(cycle));

  // Tabs
  var tabs=div("tabs");
  [["month","Checklist"],["all","Créditos"],["upcoming","Próximos"]].forEach(function(arr){
    var id=arr[0],label=arr[1];
    var btn=el("button",{className:"tab "+(S.tab===id?"on":"off")},[label]);
    btn.addEventListener("click",function(){setState({tab:id});});
    tabs.appendChild(btn);
  });
  page.appendChild(tabs);

  // Content
  var content=div("content");
  if(S.tab==="month") content.appendChild(renderChecklist(cycle));
  else if(S.tab==="all") content.appendChild(renderCredits());
  else content.appendChild(renderUpcoming(cycle));
  page.appendChild(content);

  // FAB
  if(S.tab!=="all"){
    var fab=el("button",{className:"fab"},["+"]);
    fab.addEventListener("click",function(){setState({addOpen:true});});
    page.appendChild(fab);
  }

  // Toast
  if(S.toast){
    page.appendChild(el("div",{className:"toast"},[S.toast]));
  }

  // Modals
  var proj=renderProjection();
  if(proj) page.appendChild(proj);
  var debtModal=renderDebtModal();
  if(debtModal) page.appendChild(debtModal);

  root.appendChild(page);
}

// ═══════════════════════════════════════════════════════
//  BOOT
// ═══════════════════════════════════════════════════════
render();
</script>
</body>
</html>
