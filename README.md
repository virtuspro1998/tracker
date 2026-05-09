<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">
<title>Финансы</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.min.js"></script>
<style>
*{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent}
:root{--bg:#0a0a0a;--s1:#141414;--s2:#1c1c1c;--s3:#242424;--br:#2c2c2c;--tx:#f0f0f0;--mu:#737373;--dm:#404040;--g:#22c55e;--gb:#052e16;--r:#ef4444;--rb:#450a0a;--o:#f97316;--ob:#431407;--p:#a855f7;--y:#eab308}
body{background:var(--bg);color:var(--tx);font-family:'Segoe UI',system-ui,sans-serif;min-height:100vh;overflow-x:hidden}
.tb{background:var(--s1);border-bottom:1px solid var(--br);padding:12px 16px;display:flex;justify-content:space-between;align-items:center;position:sticky;top:0;z-index:50}
.logo{font-size:18px;font-weight:800;color:var(--g)}
.tbr{display:flex;align-items:center;gap:10px}
.td{font-size:11px;color:var(--mu)}
.pb{background:none;border:none;color:var(--dm);font-size:15px;cursor:pointer}
.tabs{display:flex;background:var(--s1);border-bottom:1px solid var(--br);overflow-x:auto;scrollbar-width:none;position:sticky;top:49px;z-index:49}
.tabs::-webkit-scrollbar{display:none}
.tab{flex:1;min-width:58px;padding:9px 5px;text-align:center;font-size:10px;font-weight:700;color:var(--dm);border-bottom:2px solid transparent;cursor:pointer;text-transform:uppercase;letter-spacing:.4px;white-space:nowrap}
.tab.on{color:var(--g);border-bottom-color:var(--g)}
.pg{display:none;padding:13px;padding-bottom:80px}
.pg.on{display:block}
.card{background:var(--s1);border:1px solid var(--br);border-radius:10px;padding:13px;margin-bottom:9px}
.cl{font-size:10px;color:var(--mu);text-transform:uppercase;letter-spacing:.7px;margin-bottom:4px}
.cv{font-size:26px;font-weight:800;line-height:1}
.cs{font-size:11px;color:var(--mu);margin-top:4px}
.g2{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:9px}
.mn{background:var(--s1);border:1px solid var(--br);border-radius:9px;padding:11px}
.ml{font-size:9px;color:var(--mu);text-transform:uppercase;letter-spacing:.7px;margin-bottom:3px}
.mv{font-size:20px;font-weight:800}
.cg{color:var(--g)}.cr{color:var(--r)}.co{color:var(--o)}.cp{color:var(--p)}
.sec{font-size:10px;font-weight:700;color:var(--mu);text-transform:uppercase;letter-spacing:.9px;margin:15px 0 7px;display:flex;align-items:center;gap:7px}
.sec::after{content:'';flex:1;height:1px;background:var(--br)}
.it{display:flex;align-items:center;justify-content:space-between;padding:10px 12px;background:var(--s1);border:1px solid var(--br);border-radius:9px;margin-bottom:6px;cursor:pointer}
.itl{flex:1;min-width:0}
.itn{font-size:13px;font-weight:600;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.its{font-size:11px;color:var(--mu);margin-top:2px}
.itr{text-align:right;flex-shrink:0;margin-left:9px}
.ita{font-size:17px;font-weight:800}
.bk{display:inline-block;font-size:9px;font-weight:700;padding:2px 6px;border-radius:18px;margin-top:2px}
.bg{background:var(--gb);color:var(--g)}.br2{background:var(--rb);color:var(--r)}.bo{background:var(--ob);color:var(--o)}.bp{background:#2e1065;color:var(--p)}
.dc{background:var(--s1);border:1px solid var(--br);border-radius:10px;padding:12px;margin-bottom:7px;cursor:pointer}
.dh{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:7px}
.dn{font-size:13px;font-weight:700}
.da{font-size:19px;font-weight:800}
.dp{font-size:10px;color:var(--mu)}
.db{height:5px;background:var(--s3);border-radius:3px;overflow:hidden;margin-bottom:4px}
.dbf{height:100%;border-radius:3px}
.df{display:flex;justify-content:space-between;font-size:10px;color:var(--mu)}
.mts{display:flex;gap:6px;overflow-x:auto;scrollbar-width:none;margin-bottom:11px}
.mts::-webkit-scrollbar{display:none}
.mc{flex-shrink:0;padding:4px 11px;border-radius:18px;border:1px solid var(--br);background:none;color:var(--mu);font-size:11px;font-weight:600;cursor:pointer;white-space:nowrap}
.mc.on{background:var(--g);border-color:var(--g);color:#000}
.s3{display:grid;grid-template-columns:repeat(3,1fr);gap:7px;margin-bottom:11px}
.sb{background:var(--s1);border:1px solid var(--br);border-radius:9px;padding:9px;text-align:center}
.sbv{font-size:15px;font-weight:800}
.sbl{font-size:9px;color:var(--mu);text-transform:uppercase;margin-top:2px}
.cc{background:var(--s1);border:1px solid var(--br);border-radius:10px;padding:13px;margin-bottom:9px}
.ct{font-size:10px;color:var(--mu);text-transform:uppercase;letter-spacing:.7px;margin-bottom:11px}
.cw{position:relative;height:190px}
.cws{position:relative;height:160px}
.lg{display:flex;flex-wrap:wrap;gap:5px;margin-top:7px}
.li{display:flex;align-items:center;gap:4px;font-size:10px;color:var(--mu)}
.ld{width:7px;height:7px;border-radius:50%;flex-shrink:0}
.al{padding:8px 12px;border-radius:9px;font-size:11px;margin-bottom:7px}
.aw{background:rgba(234,179,8,.1);border:1px solid rgba(234,179,8,.2);color:var(--y)}
.aok{background:var(--gb);border:1px solid rgba(34,197,94,.2);color:var(--g)}
.fab{position:fixed;bottom:20px;right:16px;width:50px;height:50px;background:var(--g);border-radius:50%;border:none;font-size:24px;color:#000;cursor:pointer;display:flex;align-items:center;justify-content:center;box-shadow:0 4px 14px rgba(34,197,94,.3);z-index:200;font-weight:700}
.ov{display:none;position:fixed;inset:0;background:rgba(0,0,0,.6);z-index:300;align-items:flex-end}
.ov.on{display:flex}
.mo{background:var(--s1);border-radius:15px 15px 0 0;padding:18px 16px 34px;width:100%;max-height:87vh;overflow-y:auto;border-top:1px solid var(--br)}
.mh{display:flex;justify-content:space-between;align-items:center;margin-bottom:14px}
.mt{font-size:15px;font-weight:800;color:var(--g)}
.mx{background:var(--s2);border:none;color:var(--mu);font-size:15px;width:26px;height:26px;border-radius:50%;cursor:pointer}
.tr{display:grid;grid-template-columns:1fr 1fr;gap:7px;margin-bottom:13px}
.tt{padding:10px;border:2px solid var(--br);border-radius:9px;background:none;color:var(--mu);font-size:12px;font-weight:700;cursor:pointer}
.ti{border-color:var(--g);background:var(--gb);color:var(--g)}
.te{border-color:var(--r);background:var(--rb);color:var(--r)}
.fg{margin-bottom:11px}
.fl{font-size:10px;color:var(--mu);text-transform:uppercase;letter-spacing:.7px;margin-bottom:4px;display:block}
.fi,.fs{width:100%;background:var(--s2);border:1px solid var(--br);border-radius:9px;padding:10px 12px;color:var(--tx);font-size:13px;outline:none;font-family:inherit}
.fs option{background:var(--s2)}
.bs{width:100%;padding:12px;background:var(--g);color:#000;font-size:14px;font-weight:800;border:none;border-radius:9px;cursor:pointer;margin-top:5px}
.em{text-align:center;padding:28px 16px;color:var(--dm);font-size:12px}
</style>
</head>
<body>
<div class="tb">
  <div class="logo">&#128176; ФИНАНСЫ</div>
  <div class="tbr">
    <button class="pb" onclick="chPin()">&#128273;</button>
    <div class="td" id="tday"></div>
  </div>
</div>
<div class="tabs">
  <div class="tab on" onclick="go('d')">&#128202; Сводка</div>
  <div class="tab" onclick="go('i')">&#128200; Доходы</div>
  <div class="tab" onclick="go('e')">&#128201; Расходы</div>
  <div class="tab" onclick="go('t')">&#128179; Долги</div>
  <div class="tab" onclick="go('r')">&#129309; Должники</div>
</div>
<div class="pg on" id="pg-d">
  <div class="card"><div class="cl">Свободно в мае</div><div class="cv cg" id="vfr">&#8211;</div><div class="cs" id="vfrs"></div></div>
  <div class="g2">
    <div class="mn"><div class="ml">Получено</div><div class="mv cg" id="vg">&#8211;</div></div>
    <div class="mn"><div class="ml">Потрачено</div><div class="mv cr" id="vs">&#8211;</div></div>
  </div>
  <div class="g2">
    <div class="mn"><div class="ml">Долги</div><div class="mv co" id="vd">&#8211;</div></div>
    <div class="mn"><div class="ml">Ждём</div><div class="mv cp" id="vdr">&#8211;</div></div>
  </div>
  <div id="val"></div>
  <div class="sec">Аналитика</div>
  <div class="cc"><div class="ct">Расходы (май)</div><div class="cws"><canvas id="cE"></canvas></div><div class="lg" id="lE"></div></div>
  <div class="cc"><div class="ct">Долги — остатки</div><div class="cw"><canvas id="cD"></canvas></div></div>
  <div class="cc"><div class="ct">Доходы vs Расходы</div><div class="cws"><canvas id="cM"></canvas></div></div>
  <div class="sec">Ожидаем платежей</div><div id="vpd"></div>
  <div class="sec">Последние операции</div><div id="vrc"></div>
</div>
<div class="pg" id="pg-i">
  <div class="mts" id="im"></div>
  <div class="s3">
    <div class="sb"><div class="sbv cg" id="ig">0</div><div class="sbl">Получено</div></div>
    <div class="sb"><div class="sbv co" id="iw">0</div><div class="sbl">Ожидается</div></div>
    <div class="sb"><div class="sbv cr" id="il">0</div><div class="sbl">Просрочено</div></div>
  </div>
  <div id="il2"></div>
</div>
<div class="pg" id="pg-e">
  <div class="mts" id="em"></div>
  <div class="s3">
    <div class="sb"><div class="sbv cr" id="et">0</div><div class="sbl">Итого</div></div>
    <div class="sb"><div class="sbv co" id="ef">0</div><div class="sbl">Постоян.</div></div>
    <div class="sb"><div class="sbv cp" id="ep">0</div><div class="sbl">Личные</div></div>
  </div>
  <div id="el2"></div>
</div>
<div class="pg" id="pg-t">
  <div class="card"><div class="cl">Всего долгов</div><div class="cv cr" id="dt">&#8211;</div><div class="cs" id="di"></div></div>
  <div class="sec">Личные долги</div><div id="dp"></div>
  <div class="sec">Карты</div><div id="dc2"></div>
</div>
<div class="pg" id="pg-r">
  <div class="card"><div class="cl">Ожидаем</div><div class="cv cp" id="dr">&#8211;</div></div>
  <div class="sec">Кто должен мне</div><div id="drl"></div>
</div>
<button class="fab" onclick="opM()">+</button>
<div class="ov" id="ov" onclick="if(event.target===this)clM()">
  <div class="mo">
    <div class="mh"><div class="mt">Новая запись</div><button class="mx" onclick="clM()">&#10005;</button></div>
    <div class="tr">
      <button class="tt ti" id="bi" onclick="sT('i')">Доход</button>
      <button class="tt" id="be" onclick="sT('e')">Расход</button>
    </div>
    <div class="fg"><label class="fl">Дата</label><input type="date" class="fi" id="fd"></div>
    <div class="fg"><label class="fl">Категория</label><select class="fs" id="fc"></select></div>
    <div class="fg"><label class="fl">Описание</label><input type="text" class="fi" id="fds" placeholder="Квартира №41"></div>
    <div class="fg"><label class="fl">Сумма</label><input type="number" class="fi" id="fa" placeholder="0" inputmode="numeric"></div>
    <div id="ie">
      <div class="fg"><label class="fl">Статус</label><select class="fs" id="fs2" onchange="tR()"><option value="received">Получено</option><option value="pending">Ожидается</option><option value="late">Задержка</option></select></div>
      <div class="fg" id="rg"><label class="fl">Дата получения</label><input type="date" class="fi" id="frd"></div>
    </div>
    <button class="bs" onclick="sv()">Сохранить</button>
  </div>
</div>
<script>
var DB={g:function(k){try{return JSON.parse(localStorage.getItem(k));}catch(e){return null;}},s:function(k,v){localStorage.setItem(k,JSON.stringify(v));}};
function uid(){return Date.now().toString(36)+Math.random().toString(36).slice(2,5);}
function rub(n){return Math.round(n||0).toLocaleString('ru-RU')+' ₽';}
function rubK(n){n=Math.round(n||0);if(n>=1000000){return(n/1000000).toFixed(1)+'М';}if(n>=1000){return Math.round(n/1000)+'К';}return String(n);}
function fd(s){if(!s){return '';}var p=s.split('-');return p[2]+'.'+p[1]+'.'+p[0];}
function mn(s){var m=['','Янв','Фев','Мар','Апр','Май','Июн','Июл','Авг','Сен','Окт','Ноя','Дек'];return m[parseInt(s.split('-')[1])]||s;}

function seed(){
  if(DB.g('_ok')){return;}
  DB.s('inc',[
    {id:'i1',date:'2026-05-01',cat:'Помещения',amt:110000,desc:'Бийская Михайлев',st:'pending',rd:null,ra:null,mo:'2026-05'},
    {id:'i2',date:'2026-05-01',cat:'Помещения',amt:150000,desc:'Бийская Горохов',st:'pending',rd:null,ra:null,mo:'2026-05'},
    {id:'i3',date:'2026-05-01',cat:'Помещения',amt:150000,desc:'Бийская Ткаченко',st:'pending',rd:null,ra:null,mo:'2026-05'},
    {id:'i4',date:'2026-05-01',cat:'Помещения',amt:200000,desc:'УАЗ',st:'pending',rd:null,ra:null,mo:'2026-05'},
    {id:'i5',date:'2026-05-01',cat:'Земля',amt:20000,desc:'Обручева',st:'pending',rd:null,ra:null,mo:'2026-05'},
    {id:'i6',date:'2026-05-01',cat:'Земля',amt:35000,desc:'Вышки МТС',st:'pending',rd:null,ra:null,mo:'2026-05'},
    {id:'i7',date:'2026-04-01',cat:'Квартиры',amt:25000,desc:'Квартира 6',st:'received',rd:'2026-04-25',ra:25000,mo:'2026-04'},
    {id:'i8',date:'2026-05-01',cat:'Квартиры',amt:25000,desc:'Квартира 41',st:'received',rd:'2026-05-06',ra:25000,mo:'2026-05'},
    {id:'i9',date:'2026-05-01',cat:'Квартиры',amt:30000,desc:'Квартира 55',st:'received',rd:'2026-05-06',ra:30000,mo:'2026-05'},
    {id:'i10',date:'2026-04-01',cat:'Квартиры',amt:21500,desc:'Квартира 62',st:'received',rd:'2026-04-29',ra:21500,mo:'2026-04'},
    {id:'i11',date:'2026-05-01',cat:'Гаражи',amt:12000,desc:'Гараж 31',st:'pending',rd:null,ra:null,mo:'2026-05'},
    {id:'i12',date:'2026-05-01',cat:'Гаражи',amt:5500,desc:'Гараж 33',st:'pending',rd:null,ra:null,mo:'2026-05'},
    {id:'i13',date:'2026-05-01',cat:'Гаражи',amt:12000,desc:'Гараж 9',st:'pending',rd:null,ra:null,mo:'2026-05'},
    {id:'i14',date:'2026-04-25',cat:'Гаражи',amt:10000,desc:'Контейнер май',st:'received',rd:'2026-04-25',ra:10000,mo:'2026-05'},
    {id:'i15',date:'2026-04-25',cat:'Гаражи',amt:10000,desc:'Контейнер июнь',st:'received',rd:'2026-04-25',ra:10000,mo:'2026-06'},
    {id:'i16',date:'2026-05-01',cat:'Зарплата',amt:20000,desc:'Зарплата',st:'pending',rd:null,ra:null,mo:'2026-05'},
    {id:'i17',date:'2026-05-01',cat:'Зарплата',amt:130000,desc:'Премия',st:'pending',rd:null,ra:null,mo:'2026-05'}
  ]);
  DB.s('exp',[
    {id:'e1',date:'2026-05-01',cat:'Персонал',amt:110000,desc:'Татьяна',mo:'2026-05'},
    {id:'e2',date:'2026-05-01',cat:'Семья',amt:65000,desc:'Брат квартира',mo:'2026-05'},
    {id:'e3',date:'2026-05-01',cat:'Реклама',amt:20000,desc:'Kids Hockey',mo:'2026-05'},
    {id:'e4',date:'2026-05-06',cat:'Кредит',amt:400000,desc:'Тинькофф погашение',mo:'2026-05'},
    {id:'e5',date:'2026-05-06',cat:'Личные',amt:30000,desc:'Заначка Тинькофф',mo:'2026-05'},
    {id:'e6',date:'2026-05-06',cat:'Долг',amt:30000,desc:'Оплата Рустаму',mo:'2026-05'}
  ]);
  DB.s('dbt',[
    {id:'d1',name:'Рустам',orig:1851700,paid:30000,tp:'p'},
    {id:'d2',name:'Никишкин',orig:520000,paid:0,tp:'p'},
    {id:'d3',name:'Рита',orig:300000,paid:0,tp:'p'},
    {id:'d4',name:'Никитин',orig:300000,paid:163800,tp:'p'},
    {id:'d5',name:'Коммуналка',orig:250000,paid:0,tp:'p'},
    {id:'d6',name:'Михайлев',orig:20000,paid:0,tp:'p'},
    {id:'d7',name:'Алексей',orig:30000,paid:0,tp:'p'},
    {id:'d8',name:'Тинькофф',orig:470000,paid:430000,tp:'c'},
    {id:'d9',name:'Сбербанк',orig:470000,paid:0,tp:'c'}
  ]);
  DB.s('dtr',[
    {id:'t1',name:'Ольга Ч.',amt:160000,got:0,note:'Возврат долга'},
    {id:'t2',name:'Сергей Г.',amt:90000,got:0,note:'Возврат долга'}
  ]);
  DB.s('_ok',1);
}

function chkPin(){
  var s=DB.g('_s');
  if(s&&(Date.now()-s)<28800000){return;}
  var pin=localStorage.getItem('_p')||'1998';
  var t=0;
  while(t<5){
    var v=prompt('PIN-код для входа:');
    if(v===null){document.body.innerHTML='<div style="height:100vh;display:flex;align-items:center;justify-content:center;background:#0a0a0a;color:#ef4444">Закрыто</div>';return;}
    if(v===pin){DB.s('_s',Date.now());return;}
    t++;
    if(t<5){alert('Неверно. Осталось: '+(5-t));}
  }
  document.body.innerHTML='<div style="height:100vh;display:flex;align-items:center;justify-content:center;background:#0a0a0a;color:#ef4444">Заблокировано</div>';
}
function chPin(){
  var o=prompt('Текущий PIN:');
  if(o!==(localStorage.getItem('_p')||'1998')){alert('Неверно');return;}
  var n=prompt('Новый PIN (4 цифры):');
  if(!n||!/^\d{4}$/.test(n)){alert('4 цифры');return;}
  if(n!==prompt('Повтори:')){alert('Не совпадает');return;}
  localStorage.setItem('_p',n);
  alert('PIN изменён');
}

var cur='d',iMo='2026-05',eMo='2026-05';
var PG={d:'pg-d',i:'pg-i',e:'pg-e',t:'pg-t',r:'pg-r'};
var PK=Object.keys(PG);

function go(n){
  document.querySelectorAll('.pg').forEach(function(p){p.classList.remove('on');});
  document.querySelectorAll('.tab').forEach(function(t){t.classList.remove('on');});
  document.getElementById(PG[n]).classList.add('on');
  document.querySelectorAll('.tab')[PK.indexOf(n)].classList.add('on');
  cur=n;
  ren(n);
}
function ren(n){
  if(n==='d'){rD();}
  else if(n==='i'){rI();}
  else if(n==='e'){rE();}
  else if(n==='t'){rT();}
  else if(n==='r'){rR();}
}

var cE,cD,cM;
function dk(c){try{if(c){c.destroy();}}catch(x){}}
var EC=['#ef4444','#f97316','#eab308','#a855f7','#3b82f6','#06b6d4','#22c55e'];

function rD(){
  var inc=DB.g('inc')||[];
  var exp=DB.g('exp')||[];
  var dbt=DB.g('dbt')||[];
  var dtr=DB.g('dtr')||[];
  var m='2026-05';
  var got=0;
  for(var a=0;a<inc.length;a++){if(inc[a].mo===m&&inc[a].st==='received'){got+=(inc[a].ra||inc[a].amt);}}
  var sp=0;
  for(var b=0;b<exp.length;b++){if(exp[b].mo===m){sp+=exp[b].amt;}}
  var free=got-sp;
  var td=0;
  for(var c=0;c<dbt.length;c++){td+=Math.max(0,dbt[c].orig-dbt[c].paid);}
  var tr=0;
  for(var d=0;d<dtr.length;d++){tr+=Math.max(0,dtr[d].amt-dtr[d].got);}
  document.getElementById('vg').textContent=rubK(got);
  document.getElementById('vs').textContent=rubK(sp);
  document.getElementById('vfr').textContent=rub(free);
  document.getElementById('vfr').className='cv '+(free>=0?'cg':'cr');
  document.getElementById('vfrs').textContent=free>=0?'После всех расходов':'Расходы превышают доходы!';
  document.getElementById('vd').textContent=rubK(td);
  document.getElementById('vdr').textContent=rubK(tr);
  var ah='';
  var ci=0;
  for(var e2=0;e2<dbt.length;e2++){if(dbt[e2].tp==='c'){ci+=Math.max(0,dbt[e2].orig-dbt[e2].paid)*0.2/12;}}
  if(ci>0){ah+='<div class="al aw">Проценты по картам: ~'+rub(Math.round(ci))+'/мес</div>';}
  var pnd=[];
  for(var f=0;f<inc.length;f++){if(inc[f].mo===m&&inc[f].st!=='received'){pnd.push(inc[f]);}}
  if(pnd.length>0){ah+='<div class="al aw">'+pnd.length+' платежей ожидается до 10 мая</div>';}
  document.getElementById('val').innerHTML=ah;
  Chart.defaults.color='#737373';
  Chart.defaults.font.family='Segoe UI,system-ui,sans-serif';
  Chart.defaults.font.size=10;
  var eMap={};
  for(var g=0;g<exp.length;g++){if(exp[g].mo===m){eMap[exp[g].cat]=(eMap[exp[g].cat]||0)+exp[g].amt;}}
  dk(cE);
  var c1=document.getElementById('cE');
  var eK=Object.keys(eMap);
  if(c1&&eK.length>0){
    cE=new Chart(c1,{type:'doughnut',data:{labels:eK,datasets:[{data:eK.map(function(k){return eMap[k];}),backgroundColor:EC,borderWidth:0,hoverOffset:3}]},options:{responsive:true,maintainAspectRatio:false,cutout:'60%',plugins:{legend:{display:false},tooltip:{callbacks:{label:function(x){return ' '+x.label+': '+rub(x.raw);}}}}}});
    var leg='';
    for(var h=0;h<eK.length;h++){leg+='<div class="li"><div class="ld" style="background:'+EC[h%7]+'"></div>'+eK[h]+': '+rubK(eMap[eK[h]])+'</div>';}
    document.getElementById('lE').innerHTML=leg;
  }
  dk(cD);
  var c2=document.getElementById('cD');
  if(c2){
    cD=new Chart(c2,{type:'bar',data:{labels:dbt.map(function(x){return x.name;}),datasets:[{label:'Остаток',data:dbt.map(function(x){return Math.max(0,x.orig-x.paid);}),backgroundColor:'rgba(239,68,68,0.75)',borderRadius:3},{label:'Оплачено',data:dbt.map(function(x){return x.paid;}),backgroundColor:'rgba(34,197,94,0.75)',borderRadius:3}]},options:{indexAxis:'y',responsive:true,maintainAspectRatio:false,scales:{x:{stacked:true,grid:{color:'#242424'},ticks:{callback:function(v){return rubK(v);}}},y:{stacked:true,grid:{display:false},ticks:{font:{size:9}}}},plugins:{legend:{position:'bottom',labels:{boxWidth:9,padding:7}},tooltip:{callbacks:{label:function(x){return ' '+x.dataset.label+': '+rub(x.raw);}}}}}});
  }
  var aM={};
  for(var i2=0;i2<inc.length;i2++){aM[inc[i2].mo]=1;}
  for(var j=0;j<exp.length;j++){aM[exp[j].mo]=1;}
  var allM=Object.keys(aM).sort();
  dk(cM);
  var c3=document.getElementById('cM');
  if(c3&&allM.length>0){
    cM=new Chart(c3,{type:'bar',data:{labels:allM.map(mn),datasets:[{label:'Доходы',data:allM.map(function(mo){var s=0;for(var k=0;k<inc.length;k++){if(inc[k].mo===mo&&inc[k].st==='received'){s+=(inc[k].ra||inc[k].amt);}}return s;}),backgroundColor:'rgba(34,197,94,0.75)',borderRadius:3},{label:'Расходы',data:allM.map(function(mo){var s=0;for(var k=0;k<exp.length;k++){if(exp[k].mo===mo){s+=exp[k].amt;}}return s;}),backgroundColor:'rgba(239,68,68,0.75)',borderRadius:3}]},options:{responsive:true,maintainAspectRatio:false,scales:{x:{grid:{color:'#242424'}},y:{grid:{color:'#242424'},ticks:{callback:function(v){return rubK(v);}}}},plugins:{legend:{position:'bottom',labels:{boxWidth:9,padding:7}},tooltip:{callbacks:{label:function(x){return ' '+x.dataset.label+': '+rub(x.raw);}}}}}});
  }
  var pe=document.getElementById('vpd');
  if(pnd.length===0){pe.innerHTML='<div class="al aok">Все майские платежи получены!</div>';}
  else{var ph='';for(var l=0;l<Math.min(pnd.length,5);l++){ph+='<div class="it"><div class="itl"><div class="itn">'+pnd[l].desc+'</div><div class="its">'+pnd[l].cat+'</div></div><div class="itr"><div class="ita co">'+rubK(pnd[l].amt)+'</div><span class="bk bo">Ждём</span></div></div>';}pe.innerHTML=ph;}
  var all=[];
  for(var n2=0;n2<inc.length;n2++){if(inc[n2].st==='received'){all.push({desc:inc[n2].desc,cat:inc[n2].cat,amt:inc[n2].ra||inc[n2].amt,d:inc[n2].rd||inc[n2].date,tp:'i'});}}
  for(var o=0;o<exp.length;o++){all.push({desc:exp[o].desc,cat:exp[o].cat,amt:exp[o].amt,d:exp[o].date,tp:'e'});}
  all.sort(function(a,b){return b.d.localeCompare(a.d);});
  all=all.slice(0,6);
  var re=document.getElementById('vrc');
  if(all.length===0){re.innerHTML='<div class="em">Нет операций</div>';}
  else{var rh='';for(var p2=0;p2<all.length;p2++){rh+='<div class="it"><div class="itl"><div class="itn">'+all[p2].desc+'</div><div class="its">'+all[p2].cat+' · '+fd(all[p2].d)+'</div></div><div class="itr"><div class="ita '+(all[p2].tp==='i'?'cg':'cr')+'">'+(all[p2].tp==='i'?'+':'-')+rubK(all[p2].amt)+'</div></div></div>';}re.innerHTML=rh;}
}

function rI(){
  var inc=DB.g('inc')||[];
  var mo={};
  for(var a=0;a<inc.length;a++){mo[inc[a].mo]=1;}
  var mths=Object.keys(mo).sort().reverse();
  if(mths.indexOf(iMo)<0){iMo=mths[0]||'2026-05';}
  var mh='';
  for(var b=0;b<mths.length;b++){mh+='<button class="mc '+(mths[b]===iMo?'on':'')+'" onclick="siM(\''+mths[b]+'\')">'+mn(mths[b])+' '+mths[b].split('-')[0]+'</button>';}
  document.getElementById('im').innerHTML=mh;
  var items=[];
  for(var c=0;c<inc.length;c++){if(inc[c].mo===iMo){items.push(inc[c]);}}
  var g=0,w=0,l=0;
  for(var d=0;d<items.length;d++){
    if(items[d].st==='received'){g+=(items[d].ra||items[d].amt);}
    else if(items[d].st==='pending'){w+=items[d].amt;}
    else{l+=items[d].amt;}
  }
  document.getElementById('ig').textContent=rubK(g);
  document.getElementById('iw').textContent=rubK(w);
  document.getElementById('il').textContent=rubK(l);
  var cats={};
  for(var e=0;e<items.length;e++){if(!cats[items[e].cat]){cats[items[e].cat]=[];}cats[items[e].cat].push(items[e]);}
  var el=document.getElementById('il2');
  if(items.length===0){el.innerHTML='<div class="em">Нет данных</div>';return;}
  var h='';
  var ck=Object.keys(cats);
  for(var f=0;f<ck.length;f++){
    h+='<div class="sec">'+ck[f]+'</div>';
    var ci=cats[ck[f]];
    for(var g2=0;g2<ci.length;g2++){
      var bk=ci[g2].st==='received'?'<span class="bk bg">OK '+fd(ci[g2].rd)+'</span>':ci[g2].st==='late'?'<span class="bk br2">Задержка</span>':'<span class="bk bo">до 10-го</span>';
      var cl=ci[g2].st==='received'?'cg':ci[g2].st==='late'?'cr':'co';
      h+='<div class="it" onclick="edI(\''+ci[g2].id+'\')"><div class="itl"><div class="itn">'+ci[g2].desc+'</div><div style="margin-top:3px">'+bk+'</div></div><div class="itr"><div class="ita '+cl+'">'+rub(ci[g2].ra||ci[g2].amt)+'</div></div></div>';
    }
  }
  el.innerHTML=h;
}
function siM(m){iMo=m;rI();}

function rE(){
  var exp=DB.g('exp')||[];
  var mo={};
  for(var a=0;a<exp.length;a++){mo[exp[a].mo]=1;}
  var mths=Object.keys(mo).sort().reverse();
  if(mths.indexOf(eMo)<0){eMo=mths[0]||'2026-05';}
  var mh='';
  for(var b=0;b<mths.length;b++){mh+='<button class="mc '+(mths[b]===eMo?'on':'')+'" onclick="seM(\''+mths[b]+'\')">'+mn(mths[b])+' '+mths[b].split('-')[0]+'</button>';}
  document.getElementById('em').innerHTML=mh;
  var items=[];
  for(var c=0;c<exp.length;c++){if(exp[c].mo===eMo){items.push(exp[c]);}}
  var tot=0,fix=0,per=0;
  var FX=['Персонал','Семья','Реклама'],PR=['Личные','Прочие'];
  for(var d=0;d<items.length;d++){
    tot+=items[d].amt;
    if(FX.indexOf(items[d].cat)>=0){fix+=items[d].amt;}
    if(PR.indexOf(items[d].cat)>=0){per+=items[d].amt;}
  }
  document.getElementById('et').textContent=rubK(tot);
  document.getElementById('ef').textContent=rubK(fix);
  document.getElementById('ep').textContent=rubK(per);
  var cats={};
  for(var e=0;e<items.length;e++){if(!cats[items[e].cat]){cats[items[e].cat]=[];}cats[items[e].cat].push(items[e]);}
  var el=document.getElementById('el2');
  if(items.length===0){el.innerHTML='<div class="em">Нет расходов</div>';return;}
  var h='';
  var ck=Object.keys(cats);
  for(var f=0;f<ck.length;f++){
    var ct=0;for(var g2=0;g2<cats[ck[f]].length;g2++){ct+=cats[ck[f]][g2].amt;}
    h+='<div class="sec">'+ck[f]+' <span style="color:var(--mu);font-size:11px;text-transform:none;font-weight:400">'+rub(ct)+'</span></div>';
    for(var h2=0;h2<cats[ck[f]].length;h2++){h+='<div class="it"><div class="itl"><div class="itn">'+cats[ck[f]][h2].desc+'</div><div class="its">'+fd(cats[ck[f]][h2].date)+'</div></div><div class="itr"><div class="ita cr">-'+rub(cats[ck[f]][h2].amt)+'</div></div></div>';}
  }
  el.innerHTML=h;
}
function seM(m){eMo=m;rE();}

function rT(){
  var dbt=DB.g('dbt')||[];
  var tot=0;
  for(var a=0;a<dbt.length;a++){tot+=Math.max(0,dbt[a].orig-dbt[a].paid);}
  var ci=0;
  for(var b=0;b<dbt.length;b++){if(dbt[b].tp==='c'){ci+=Math.max(0,dbt[b].orig-dbt[b].paid)*0.2/12;}}
  document.getElementById('dt').textContent=rub(tot);
  document.getElementById('di').textContent=ci>0?'Проценты по картам: ~'+rub(Math.round(ci))+'/мес':'';
  function mk(x){
    var l=Math.max(0,x.orig-x.paid);
    var pc=x.orig>0?Math.round(x.paid/x.orig*100):0;
    var col=pc>=80?'var(--g)':pc>=40?'var(--o)':'var(--r)';
    var ex=x.tp==='c'?'<div style="font-size:10px;color:var(--o)">~'+rub(Math.round(l*0.2/12))+'/мес</div>':'';
    return '<div class="dc" onclick="pyD(\''+x.id+'\')"><div class="dh"><div><div class="dn">'+x.name+'</div><div class="dp">'+rub(x.orig)+'</div></div><div style="text-align:right"><div class="da cr">'+rub(l)+'</div>'+ex+'</div></div><div class="db"><div class="dbf" style="width:'+pc+'%;background:'+col+'"></div></div><div class="df"><span>Оплачено '+rub(x.paid)+'</span><span>'+pc+'%</span></div></div>';
  }
  var p='',c='';
  for(var e=0;e<dbt.length;e++){if(dbt[e].tp==='p'){p+=mk(dbt[e]);}else{c+=mk(dbt[e]);}}
  document.getElementById('dp').innerHTML=p||'<div class="em">Нет</div>';
  document.getElementById('dc2').innerHTML=c||'<div class="em">Нет</div>';
}
function pyD(id){
  var dbt=DB.g('dbt')||[];
  var d=null;
  for(var i=0;i<dbt.length;i++){if(dbt[i].id===id){d=dbt[i];break;}}
  if(!d){return;}
  var v=prompt(d.name+' — остаток: '+rub(Math.max(0,d.orig-d.paid))+'. Сумма оплаты:');
  if(!v){return;}
  var a=parseFloat(v);
  if(a>0){d.paid=Math.min(d.orig,d.paid+a);DB.s('dbt',dbt);rT();if(cur==='d'){rD();}}
}

function rR(){
  var dtr=DB.g('dtr')||[];
  var tot=0;
  for(var a=0;a<dtr.length;a++){tot+=Math.max(0,dtr[a].amt-dtr[a].got);}
  document.getElementById('dr').textContent=rub(tot);
  var el=document.getElementById('drl');
  if(dtr.length===0){el.innerHTML='<div class="em">Все вернули!</div>';return;}
  var h='';
  for(var b=0;b<dtr.length;b++){
    var l=Math.max(0,dtr[b].amt-dtr[b].got);
    var pc=dtr[b].amt>0?Math.round(dtr[b].got/dtr[b].amt*100):0;
    h+='<div class="dc" onclick="gtD(\''+dtr[b].id+'\')"><div class="dh"><div><div class="dn">'+dtr[b].name+'</div><div class="dp">'+(dtr[b].note||'')+'</div></div><div style="text-align:right"><div class="da cp">'+rub(l)+'</div><span class="bk bp">Ожидаю</span></div></div><div class="db"><div class="dbf" style="width:'+pc+'%;background:var(--g)"></div></div><div class="df"><span>Получено '+rub(dtr[b].got)+'</span><span>'+pc+'%</span></div></div>';
  }
  el.innerHTML=h;
}
function gtD(id){
  var dtr=DB.g('dtr')||[];
  var d=null;
  for(var i=0;i<dtr.length;i++){if(dtr[i].id===id){d=dtr[i];break;}}
  if(!d){return;}
  var v=prompt(d.name+' — осталось: '+rub(Math.max(0,d.amt-d.got))+'. Получено:');
  if(!v){return;}
  var a=parseFloat(v);
  if(a>0){d.got=Math.min(d.amt,d.got+a);DB.s('dtr',dtr);rR();if(cur==='d'){rD();}}
}

function edI(id){
  var inc=DB.g('inc')||[];
  var it=null;
  for(var i=0;i<inc.length;i++){if(inc[i].id===id){it=inc[i];break;}}
  if(!it){return;}
  var s=prompt(it.desc+' — статус (received/pending/late):',it.st);
  if(!s){return;}
  if(['received','pending','late'].indexOf(s)<0){return;}
  it.st=s;
  if(s==='received'){
    var dv=prompt('Дата (ГГГГ-ММ-ДД):',it.rd||'2026-05-09');
    var av=prompt('Сумма:',it.ra||it.amt);
    if(dv){it.rd=dv;}
    if(av){it.ra=parseFloat(av);}
  }
  DB.s('inc',inc);rI();if(cur==='d'){rD();}
}

var mT='i';
var IC=['Помещения','Земля','Квартиры','Гаражи','Зарплата','Разовые'];
var EC2=['Персонал','Семья','Реклама','Кредит','Долг','Личные','Еда','Одежда','Транспорт','Отдых','Прочие'];

function opM(){
  mT='i';
  document.getElementById('bi').className='tt ti';
  document.getElementById('be').className='tt';
  document.getElementById('ie').style.display='block';
  var h='';for(var i=0;i<IC.length;i++){h+='<option>'+IC[i]+'</option>';}
  document.getElementById('fc').innerHTML=h;
  document.getElementById('fd').value='2026-05-09';
  document.getElementById('frd').value='2026-05-09';
  document.getElementById('fds').value='';
  document.getElementById('fa').value='';
  document.getElementById('fs2').value='received';
  document.getElementById('rg').style.display='block';
  document.getElementById('ov').classList.add('on');
}
function clM(){document.getElementById('ov').classList.remove('on');}
function sT(t){
  mT=t;
  document.getElementById('bi').className='tt'+(t==='i'?' ti':'');
  document.getElementById('be').className='tt'+(t==='e'?' te':'');
  document.getElementById('ie').style.display=t==='i'?'block':'none';
  var c=t==='i'?IC:EC2;
  var h='';for(var i=0;i<c.length;i++){h+='<option>'+c[i]+'</option>';}
  document.getElementById('fc').innerHTML=h;
}
function tR(){
  var s=document.getElementById('fs2').value;
  document.getElementById('rg').style.display=s==='received'?'block':'none';
}
function sv(){
  var dt=document.getElementById('fd').value;
  var ct=document.getElementById('fc').value;
  var ds=document.getElementById('fds').value.trim();
  var am=parseFloat(document.getElementById('fa').value);
  if(!dt||!ds||!am||am<=0){alert('Заполни все поля');return;}
  var mo=dt.slice(0,7);
  if(mT==='i'){
    var st=document.getElementById('fs2').value;
    var rd=st==='received'?document.getElementById('frd').value:null;
    var inc=DB.g('inc')||[];
    inc.push({id:uid(),date:dt,cat:ct,amt:am,desc:ds,st:st,rd:rd,ra:st==='received'?am:null,mo:mo});
    DB.s('inc',inc);
  } else {
    var exp=DB.g('exp')||[];
    exp.push({id:uid(),date:dt,cat:ct,amt:am,desc:ds,mo:mo});
    DB.s('exp',exp);
  }
  clM();ren(cur);
}

chkPin();
seed();
var tEl=document.getElementById('tday');
if(tEl){tEl.textContent=new Date('2026-05-09').toLocaleDateString('ru-RU',{day:'numeric',month:'long'});}
rD();
</script>
</body>
</html>
