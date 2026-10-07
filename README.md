[Квадратные уравнения.html](https://github.com/user-attachments/files/33160318/default.html)
<!doctype html><html><head><meta charset=utf8><meta name=viewport content="width=device-width,initial-scale=1,viewport-fit=cover"><style>:root{color-scheme:light;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}html{scroll-padding-top:env(safe-area-inset-top,0px)}body{margin:0;padding:0;font:14px -apple-system,BlinkMacSystemFont,sans-serif;background:#faf9f5;color:#141413}img{max-width:100%}[hidden]:not([hidden=until-found i]){display:none!important}</style></head><body>
<title>Квадратные уравнения</title>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Marck+Script&family=PT+Sans:wght@400;700&family=PT+Serif:ital,wght@0,400;0,700;1,400&display=swap">
<style>
:root{
  /* Страница школьной тетради в клетку с красными полями. Сверху шапка с прогрессом, ниже четыре вкладки. Красная ручка учителя: поля, оценка, ошибки. */
  --bg:#DDE3EE;
  --paper:#FAFBFE;
  --card:#FFFFFF;
  --grid:rgba(60,90,170,.14);
  --line:#C5CEE2;
  --ink:#16244F;
  --ink-soft:#4B5886;
  --accent:#2346C8;
  --on-accent:#FFFFFF;
  --accent-wash:#E6ECFB;
  --red:#C23B38;
  --ok:#1B7A4B;
  --on-ok:#FFFFFF;
  --warn:#9A6A12;
  --f-display:'Marck Script','Segoe Script','Bradley Hand',cursive;
  --f-body:'PT Sans',system-ui,-apple-system,'Segoe UI',sans-serif;
  --f-math:'PT Serif',Georgia,'Times New Roman',serif;
}
@media (prefers-color-scheme:dark){
  :root:not([data-theme="light"]){
    --bg:#0B0E14; --paper:#141925; --card:#1B2130; --grid:rgba(140,170,255,.09); --line:#2B3550;
    --ink:#E7ECF8; --ink-soft:#9DA9C9; --accent:#8FAEFF; --on-accent:#0B0E14; --accent-wash:#222C4A;
    --red:#FF7B76; --ok:#5CCB93; --on-ok:#0B0E14; --warn:#E3B45A;
    color-scheme:dark;
  }
}
:root[data-theme="dark"]{
  --bg:#0B0E14; --paper:#141925; --card:#1B2130; --grid:rgba(140,170,255,.09); --line:#2B3550;
  --ink:#E7ECF8; --ink-soft:#9DA9C9; --accent:#8FAEFF; --on-accent:#0B0E14; --accent-wash:#222C4A;
  --red:#FF7B76; --ok:#5CCB93; --on-ok:#0B0E14; --warn:#E3B45A;
  color-scheme:dark;
}

*,*::before,*::after{box-sizing:border-box}
body{background:var(--bg);color:var(--ink);font-family:var(--f-body);font-size:16px;line-height:1.55}
button,input{font:inherit;color:inherit}
:focus-visible{outline:2.5px solid var(--accent);outline-offset:2px}

.sheet{
  position:relative;max-width:820px;margin:0 auto;min-height:100vh;
  padding-block:22px 56px;padding-inline:34px 16px;
  background-color:var(--paper);
  background-image:linear-gradient(var(--grid) 1px,transparent 1px),linear-gradient(90deg,var(--grid) 1px,transparent 1px);
  background-size:24px 24px;
  border-inline:1px solid var(--line);
}
.sheet::before{content:"";position:absolute;inset-block:0;left:18px;width:2px;background:var(--red);opacity:.6}
@media (min-width:700px){
  .sheet{padding-inline:64px 36px}
  .sheet::before{left:42px}
}

/* шапка */
.eyebrow{margin:0;font-size:.8rem;letter-spacing:.12em;text-transform:uppercase;color:var(--ink-soft);font-weight:700}
h1{font-family:var(--f-display);font-weight:400;font-size:clamp(2.2rem,8vw,3.2rem);line-height:1.1;margin:4px 0 14px;color:var(--accent);text-wrap:balance}
h1::after{content:"";display:block;width:3.2em;height:3px;margin-top:6px;background:var(--red);border-radius:2px;transform:rotate(-.6deg)}
.status{background:var(--card);border:1px solid var(--line);padding:12px 14px}
.rank-row{display:flex;flex-wrap:wrap;justify-content:space-between;align-items:baseline;gap:6px 16px}
.lbl{display:block;font-size:.72rem;letter-spacing:.1em;text-transform:uppercase;color:var(--ink-soft);font-weight:700}
.rank{font-family:var(--f-display);font-size:1.7rem;line-height:1.15;color:var(--ink)}
.stats{display:flex;flex-wrap:wrap;gap:4px 16px;font-size:.92rem;color:var(--ink-soft);font-variant-numeric:tabular-nums}
.stats b{color:var(--ink)}
.xpbar{height:8px;margin-top:8px;background:var(--line);border-radius:4px;overflow:hidden}
.xpfill{height:100%;width:0;background:var(--accent);transition:width .4s ease}
.next{margin:6px 0 0;font-size:.85rem;color:var(--ink-soft)}

/* вкладки */
.tabs{
  position:sticky;top:env(safe-area-inset-top,0px);z-index:5;
  display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:4px;
  margin-block:18px 22px;padding-block:8px 0;background:var(--paper);border-bottom:1px solid var(--line);
}
.tabs button{background:transparent;border:0;border-bottom:3px solid transparent;padding:10px 2px 9px;font-weight:700;font-size:1rem;color:var(--ink-soft);cursor:pointer}
.tabs button[aria-selected="true"]{color:var(--accent);border-bottom-color:var(--accent)}
.tabs button:hover{color:var(--ink)}

h2{font-family:var(--f-display);font-weight:400;font-size:1.9rem;line-height:1.2;margin:34px 0 10px;color:var(--accent);text-wrap:balance}
h2:first-child{margin-top:0}
h3{font-size:1.1rem;margin:0 0 6px}
p{margin:0 0 12px;max-width:68ch}
.small{font-size:.9rem;color:var(--ink-soft)}

/* математика */
.m,.expr{font-family:var(--f-math)}
.big{font-size:1.25rem}
i{font-style:italic}
sub,sup{font-size:.7em;line-height:0}
.fr{display:inline-flex;flex-direction:column;vertical-align:middle;text-align:center;margin:0 .15em;font-size:.92em;line-height:1.2}
.fr .n{border-bottom:1.5px solid currentColor;padding:0 .25em .06em}
.fr .d{padding:.06em .25em 0}
.rad .rr{border-top:1.5px solid currentColor;padding:0 .12em}

/* лекция */
.types{display:grid;gap:0;margin:8px 0 14px;border-top:1px solid var(--line)}
.type{display:grid;grid-template-columns:minmax(0,1fr);gap:4px 18px;padding:10px 0;border-bottom:1px solid var(--line)}
.type>*{min-width:0}
@media (min-width:620px){.type{grid-template-columns:minmax(0,210px) minmax(0,1fr);align-items:baseline}}
.rule{padding:10px 14px;background:var(--accent-wash);max-width:none}
.cases{display:grid;grid-template-columns:repeat(auto-fit,minmax(170px,1fr));gap:10px;margin:10px 0 18px}
.case{background:var(--card);border:1px solid var(--line);padding:10px 12px}
.case p{margin:4px 0 0;font-size:.95rem}
.plain{margin:6px 0 14px;padding-left:20px}
.plain li{margin-bottom:6px}
.card{background:var(--card);border:1px solid var(--line);padding:16px;border-radius:4px}
.card+.card{margin-top:14px}

/* лаборатория */
.lab{display:grid;gap:16px;grid-template-columns:minmax(0,1fr)}
@media (min-width:700px){.lab{grid-template-columns:minmax(0,230px) minmax(0,1fr)}}
.sl{display:grid;grid-template-columns:auto 1fr;align-items:center;gap:4px 12px;margin-bottom:10px}
.sl label{font-family:var(--f-math);font-style:italic;font-size:1.1rem;min-width:4.2em;font-variant-numeric:tabular-nums}
.sl input[type=range]{width:100%;accent-color:var(--accent);min-width:0}
.plot{width:100%;height:auto;display:block;background:var(--paper);border:1px solid var(--line)}
.plot .gr{stroke:var(--grid);stroke-width:1}
.plot .gr5{stroke:var(--line);stroke-width:1}
.plot .ax{stroke:var(--ink-soft);stroke-width:1.4}
.plot .curve{stroke:var(--accent);stroke-width:2.6;fill:none}
.plot .rt{fill:var(--red);stroke:var(--card);stroke-width:1.5}
.plot text{fill:var(--ink-soft);font-family:var(--f-body);font-size:10px}
.labout{font-size:.98rem;min-height:5.6em}
.labout p{margin:0 0 6px}
.verdict{font-weight:700}

/* примеры */
.exh{font-family:var(--f-display);font-size:1.35rem;margin:0 0 4px;color:var(--ink)}
.steps{margin:10px 0 12px;padding-left:22px}
.steps li{margin-bottom:8px;font-family:var(--f-math)}

/* кнопки */
.btn{display:inline-flex;align-items:center;justify-content:center;gap:6px;min-height:42px;padding:8px 16px;border:1.5px solid var(--line);background:var(--card);color:var(--ink);font-weight:700;border-radius:4px;cursor:pointer}
.btn:hover{border-color:var(--accent)}
.btn.primary{background:var(--accent);border-color:var(--accent);color:var(--on-accent)}
.btn.primary:hover{filter:brightness(1.08)}

/* практика */
.chips{display:flex;flex-wrap:wrap;gap:6px;margin-bottom:14px}
.chip{min-height:38px;padding:6px 12px;border:1.5px solid var(--line);background:var(--card);border-radius:4px;font-weight:700;font-size:.92rem;cursor:pointer;font-variant-numeric:tabular-nums}
.chip[aria-pressed="true"]{background:var(--accent-wash);border-color:var(--accent);color:var(--accent)}
.ph{display:flex;flex-wrap:wrap;justify-content:space-between;gap:2px 12px;margin-bottom:8px;font-size:.88rem;color:var(--ink-soft)}
.pn{font-family:var(--f-display);font-size:1.5rem;line-height:1.1;color:var(--ink)}
.lead{margin:0 0 2px;font-size:.92rem;color:var(--ink-soft)}
.expr{margin:0 0 14px;font-size:1.45rem;line-height:1.9;overflow-wrap:anywhere}
.inrow{display:flex;gap:8px}
.inrow input{flex:1;min-width:0;min-height:46px;padding:8px 12px;font-size:1.1rem;font-family:var(--f-math);background:var(--paper);border:1.5px solid var(--line);border-radius:4px}
.inrow input:focus{border-color:var(--accent)}
.keys{display:flex;flex-wrap:wrap;gap:6px;margin:8px 0 6px}
.keys button{min-width:42px;min-height:38px;padding:4px 10px;border:1px solid var(--line);background:var(--paper);border-radius:4px;font-family:var(--f-math);font-size:1.05rem;cursor:pointer}
.keys button:hover{border-color:var(--accent)}
.fmtnote{margin:4px 0 10px;font-size:.88rem;color:var(--ink-soft)}
.fb{min-height:1.6em;margin:2px 0 10px;font-weight:700}
.fb.ok{color:var(--ok)}
.fb.bad{color:var(--red)}
.fb.warn,.fb.rev{color:var(--warn)}
.fb .ic{margin-right:6px}
.ans-line{display:block;margin-top:2px;font-weight:400;color:var(--ink)}
.hintbox{margin:0 0 12px;padding:10px 12px;background:var(--accent-wash);font-size:.95rem}
.actions,.nav{display:flex;flex-wrap:wrap;gap:8px;margin-top:8px}
.nav{justify-content:space-between;margin-top:14px;padding-top:14px;border-top:1px dashed var(--line)}
.map-h{margin:22px 0 8px;font-size:.8rem;letter-spacing:.1em;text-transform:uppercase;font-weight:700;color:var(--ink-soft)}
.dots{display:flex;flex-wrap:wrap;gap:6px}
.dot{width:40px;height:40px;border:1.5px solid var(--line);background:var(--card);border-radius:4px;font-weight:700;font-size:.88rem;cursor:pointer;font-variant-numeric:tabular-nums}
.dot.ok{background:var(--ok);border-color:var(--ok);color:var(--on-ok)}
.dot.rev{border-style:dashed;border-color:var(--warn);color:var(--warn)}
.dot.bad{border-color:var(--red);color:var(--red)}
.dot.cur{outline:2.5px solid var(--accent);outline-offset:2px}
.legend{display:flex;flex-wrap:wrap;gap:4px 14px;margin-top:10px;font-size:.85rem;color:var(--ink-soft)}
.legend span::before{content:"";display:inline-block;width:11px;height:11px;margin-right:6px;vertical-align:-1px;border:1.5px solid var(--line);border-radius:2px}
.legend .l-ok::before{background:var(--ok);border-color:var(--ok)}
.legend .l-rev::before{border-style:dashed;border-color:var(--warn)}
.legend .l-bad::before{border-color:var(--red)}

/* ответы */
details.blk{border-top:1px solid var(--line)}
details.blk:last-of-type{border-bottom:1px solid var(--line)}
details.blk summary{padding:12px 0;font-weight:700;cursor:pointer}
.alist{display:grid;grid-template-columns:repeat(auto-fill,minmax(150px,1fr));gap:6px 14px;padding:2px 0 14px}
.ai{display:flex;gap:8px;align-items:baseline;padding:4px 0;border-bottom:1px dotted var(--line)}
.an{min-width:1.8em;font-weight:700;color:var(--ink-soft);font-variant-numeric:tabular-nums}

/* тест */
.seg{display:flex;gap:4px;margin:0 0 12px}
.seg span{flex:1;height:6px;background:var(--line);border-radius:3px}
.seg span.done{background:var(--accent)}
.seg span.now{background:var(--ink-soft)}
.res-top{display:flex;flex-wrap:wrap;align-items:center;gap:16px 24px;margin-bottom:14px}
.mark{flex:none;width:5.6rem;height:5.6rem;display:grid;place-items:center;border:3px solid var(--red);border-radius:50%;font-family:var(--f-display);font-size:4.2rem;line-height:1;color:var(--red);transform:rotate(-7deg)}
.rv{display:grid;gap:0;margin:10px 0 14px;border-top:1px solid var(--line)}
.rv-i{display:grid;grid-template-columns:2.2rem minmax(0,1fr);gap:2px 10px;padding:10px 0;border-bottom:1px solid var(--line)}
.rv-i .s{font-weight:700;font-size:1.1rem}
.rv-i.ok .s{color:var(--ok)}
.rv-i.no .s{color:var(--red)}
.rv-i .meta{font-size:.9rem;color:var(--ink-soft)}
.rv-i .expr{font-size:1.1rem;line-height:1.7;margin:0}

footer{margin-top:44px;padding-top:14px;border-top:1px solid var(--line);display:flex;flex-wrap:wrap;justify-content:space-between;align-items:center;gap:10px}
footer p{margin:0;font-size:.85rem;color:var(--ink-soft)}

@media (prefers-reduced-motion:reduce){*{transition:none!important;animation:none!important}}
</style>

<div class="sheet">
  <header>
    <p class="eyebrow">Тема 8 · Алгебра</p>
    <h1>Квадратные уравнения</h1>
    <div class="status" id="status"></div>
  </header>

  <nav class="tabs" role="tablist" aria-label="Разделы урока">
    <button role="tab" id="t-lecture" data-tab="lecture" aria-selected="true" aria-controls="tab-lecture">Лекция</button>
    <button role="tab" id="t-practice" data-tab="practice" aria-selected="false" aria-controls="tab-practice">Практика</button>
    <button role="tab" id="t-answers" data-tab="answers" aria-selected="false" aria-controls="tab-answers">Ответы</button>
    <button role="tab" id="t-test" data-tab="test" aria-selected="false" aria-controls="tab-test">Тест</button>
  </nav>

  <main>
    <!-- ЛЕКЦИЯ -->
    <section id="tab-lecture" role="tabpanel" aria-labelledby="t-lecture">
      <h2>Виды квадратных уравнений</h2>
      <p>Квадратное уравнение имеет вид <span class="m" data-m>ax^2 + bx + c = 0</span>, где <span class="m" data-m>a ≠ 0</span>. Если <span class="m" data-m>b</span> или <span class="m" data-m>c</span> равно нулю, уравнение неполное.</p>
      <div class="types">
        <div class="type"><div class="m big" data-m>ax^2 + bx + c = 0</div><div><b>Полное.</b> Решается через дискриминант.</div></div>
        <div class="type"><div class="m big" data-m>ax^2 + bx = 0</div><div><b>Нет свободного члена.</b> Выносим <span class="m" data-m>x</span> за скобки: <span class="m" data-m>x(ax + b) = 0</span>. Корни: <span class="m" data-m>0</span> и <span class="m" data-m>−{b|a}</span>.</div></div>
        <div class="type"><div class="m big" data-m>ax^2 + c = 0</div><div><b>Нет члена с x.</b> Получаем <span class="m" data-m>x^2 = −{c|a}</span>. Если справа положительное число, корней два: <span class="m" data-m>±√[−{c|a}]</span>. Если отрицательное, корней нет.</div></div>
        <div class="type"><div class="m big" data-m>ax^2 = 0</div><div><b>Только x².</b> Единственный корень <span class="m" data-m>x = 0</span>.</div></div>
      </div>
      <p class="rule"><b>Произведение равно нулю</b>, когда равен нулю хотя бы один множитель: <span class="m" data-m>a·b·c = 0 ⟺ a = 0 или b = 0 или c = 0</span>.</p>

      <h2>Дискриминант и формула корней</h2>
      <p class="m big" data-m>D = b^2 − 4ac,    x = {−b ± √[D]|2a}</p>
      <div class="cases">
        <div class="case"><div class="m big" data-m>D > 0</div><p>два различных корня</p></div>
        <div class="case"><div class="m big" data-m>D = 0</div><p>один корень <span class="m" data-m>x = −{b|2a}</span></p></div>
        <div class="case"><div class="m big" data-m>D < 0</div><p>действительных корней нет</p></div>
      </div>

      <h3>Лаборатория дискриминанта</h3>
      <p class="small">Двигайте ползунки: смотрите, как коэффициенты меняют параболу и число корней.</p>
      <div class="card lab">
        <div>
          <div class="sl"><label for="la" id="lal"></label><input type="range" id="la" min="-4" max="4" step="0.5" value="1"></div>
          <div class="sl"><label for="lb" id="lbl"></label><input type="range" id="lb" min="-10" max="10" step="1" value="-6"></div>
          <div class="sl"><label for="lc" id="lcl"></label><input type="range" id="lc" min="-10" max="10" step="1" value="5"></div>
          <div class="labout" id="labout" aria-live="polite"></div>
        </div>
        <svg class="plot" id="plot" viewBox="0 0 400 280" role="img" aria-label="График параболы y = ax² + bx + c">
          <defs><clipPath id="pclip"><rect width="400" height="280"/></clipPath></defs>
          <g id="pgrid"></g>
          <g id="paxes"></g>
          <polyline id="pcurve" class="curve" clip-path="url(#pclip)" points=""/>
          <g id="proots"></g>
        </svg>
      </div>

      <h2>Теорема Виета</h2>
      <div class="types">
        <div class="type"><div class="m big" data-m>ax^2 + bx + c = 0</div><div class="m big" data-m>x_1 + x_2 = −{b|a},    x_1x_2 = {c|a}</div></div>
        <div class="type"><div class="m big" data-m>x^2 + px + q = 0</div><div class="m big" data-m>x_1 + x_2 = −p,    x_1x_2 = q</div></div>
      </div>
      <p>Полезные выражения для задач блока C:</p>
      <ul class="plain">
        <li class="m" data-m>x_1^2 + x_2^2 = (x_1 + x_2)^2 − 2x_1x_2</li>
        <li class="m" data-m>x_1^3 + x_2^3 = (x_1 + x_2)^3 − 3x_1x_2(x_1 + x_2)</li>
        <li class="m" data-m>{1|x_1} + {1|x_2} = {x_1 + x_2|x_1x_2}</li>
      </ul>

      <h2>Разложение трёхчлена</h2>
      <p class="m big" data-m>ax^2 + bx + c = a(x − x_1)(x − x_2)</p>
      <p>Здесь <span class="m" data-m>x_1, x_2</span> — корни уравнения. Так сокращают алгебраические дроби: раскладываем числитель и знаменатель на множители и убираем общий.</p>

      <h2>Разбор типовых задач</h2>
      <div class="card ex" id="ex1"></div>
      <div class="card ex" id="ex2"></div>

      <p style="margin-top:22px"><button class="btn primary" data-tab="practice">Перейти к задачам</button></p>
    </section>

    <!-- ПРАКТИКА -->
    <section id="tab-practice" role="tabpanel" aria-labelledby="t-practice" hidden>
      <h2>Практика</h2>
      <div class="chips" id="chips" role="group" aria-label="Блок задач"></div>
      <div class="card" id="pcard"></div>
      <p class="map-h">Карта задач</p>
      <div class="dots" id="dots"></div>
      <div class="legend"><span class="l-ok">решена</span><span class="l-rev">показан ответ</span><span class="l-bad">были ошибки</span></div>
    </section>

    <!-- ОТВЕТЫ -->
    <section id="tab-answers" role="tabpanel" aria-labelledby="t-answers" hidden>
      <h2>Ответы</h2>
      <p class="small">Сначала решите сами. Ответы из этого списка не засчитываются в прогресс.</p>
      <div id="alist"></div>
    </section>

    <!-- ТЕСТ -->
    <section id="tab-test" role="tabpanel" aria-labelledby="t-test" hidden>
      <h2>Тест</h2>
      <div id="tbox"></div>
    </section>
  </main>

  <footer>
    <p>Прогресс хранится на этом устройстве, если браузер это позволяет.</p>
    <button class="btn" data-act="reset" id="resetbtn">Сбросить прогресс</button>
  </footer>
</div>

<script>
(function(){
'use strict';

/* ---------- Разметка формул ---------- */
function fx(s){
  return s.replace(/√\[([^\]]*)\]|\{([^{}|]*)\|([^{}]*)\}|_(\d)|\^(\d)|([A-Za-z])|([&<>])/g,
    function(m,rad,n,d,sub,sup,v,ent){
      if(rad!==undefined) return '<span class="rad">√<span class="rr">'+fx(rad)+'</span></span>';
      if(n!==undefined) return '<span class="fr"><span class="n">'+fx(n)+'</span><span class="d">'+fx(d)+'</span></span>';
      if(sub!==undefined) return '<sub>'+sub+'</sub>';
      if(sup!==undefined) return '<sup>'+sup+'</sup>';
      if(v!==undefined) return '<i>'+v+'</i>';
      return ent==='&'?'&amp;':ent==='<'?'&lt;':'&gt;';
    });
}
var fmt=fx;

/* ---------- Разбор ответа ученика ---------- */
function compile(src){
  var s=String(src).replace(/\s+/g,''), i=0;
  function peek(){return s.charAt(i);}
  function isStart(c){return c!==''&&(/[0-9.x(]/.test(c)||s.substr(i,4)==='sqrt');}
  function expr(){
    var f=term();
    while(peek()==='+'||peek()==='-'){
      var op=s.charAt(i++), g=term(), a=f;
      f=(op==='+')?(function(a,g){return function(x){return a(x)+g(x);};})(a,g):(function(a,g){return function(x){return a(x)-g(x);};})(a,g);
    }
    return f;
  }
  function term(){
    var f=unary();
    for(;;){
      var c=peek(), g, a=f;
      if(c==='*'){i++; g=unary(); f=(function(a,g){return function(x){return a(x)*g(x);};})(a,g);}
      else if(c==='/'){i++; g=unary(); f=(function(a,g){return function(x){return a(x)/g(x);};})(a,g);}
      else if(isStart(c)){g=power(); f=(function(a,g){return function(x){return a(x)*g(x);};})(a,g);}
      else break;
    }
    return f;
  }
  function unary(){
    if(peek()==='-'){i++; var g=unary(); return function(x){return -g(x);};}
    if(peek()==='+'){i++; return unary();}
    return power();
  }
  function power(){
    var b=atom();
    if(peek()==='^'){i++; var e=unary(); return function(x){return Math.pow(b(x),e(x));};}
    return b;
  }
  function atom(){
    var c=peek();
    if(c==='('){i++; var f=expr(); if(peek()!==')') throw 0; i++; return f;}
    if(c==='x'){i++; return function(x){return x;};}
    if(s.substr(i,4)==='sqrt'){i+=4; var g=atom(); return function(x){return Math.sqrt(g(x));};}
    if(c!==''&&/[0-9.]/.test(c)){
      var j=i; while(i<s.length&&/[0-9.]/.test(s.charAt(i))) i++;
      var v=parseFloat(s.slice(j,i)); if(isNaN(v)) throw 0;
      return function(){return v;};
    }
    throw 0;
  }
  try{var f=expr(); if(i!==s.length) return null; return f;}catch(e){return null;}
}
function norm(s){
  return String(s).toLowerCase()
    .replace(/х/g,'x').replace(/[−–—]/g,'-').replace(/[×·∙⋅]/g,'*').replace(/÷/g,'/')
    .replace(/²/g,'^2').replace(/³/g,'^3').replace(/√/g,'sqrt');
}
function ev(k){var f=compile(k); return f?f(0):NaN;}
function close(a,b){return isFinite(a)&&isFinite(b)&&Math.abs(a-b)<=1e-6*Math.max(1,Math.abs(b));}
function dedupe(a){
  var r=[]; a=a.slice().sort(function(p,q){return p-q;});
  a.forEach(function(v){if(!r.length||Math.abs(v-r[r.length-1])>1e-7) r.push(v);});
  return r;
}
function splitItems(raw){
  var s=norm(raw);
  s=s.replace(/\b[xyt]\s*_?\d?\s*=/g,'').replace(/(сумма|произведение|ответ)\s*:?/g,'');
  s=s.replace(/\s*([+\-*\/^()±])\s*/g,'$1');
  return s.split(/;|или|и|\band\b|,(?=\D|$)|\s+/).map(function(t){return t.replace(/^,+|,+$/g,'').replace(/,/g,'.');}).filter(Boolean);
}
function expandPM(items){
  var out=[];
  items.forEach(function(t){
    var i=t.indexOf('±');
    if(i>=0){out.push(t.slice(0,i)+'+'+t.slice(i+1), t.slice(0,i)+'-'+t.slice(i+1));}
    else out.push(t);
  });
  return out;
}
var PTS=[0.37,1.91,-2.63,3.17,5.43,-0.71];
function same(f,g){
  for(var i=0;i<PTS.length;i++){
    var a=f(PTS[i]), b=g(PTS[i]);
    if(!isFinite(a)||!isFinite(b)) return false;
    if(Math.abs(a-b)>1e-7*Math.max(1,Math.abs(b))) return false;
  }
  return true;
}
var BAD_READ='Не удалось прочитать ответ. Проверьте скобки и знаки.';

function chkRoots(p,raw){
  var exp=dedupe(p.key.map(ev));
  var n=norm(raw);
  if(/нет|∅|пуст|no ?root|none/.test(n)){
    return exp.length===0?{ok:true}:{ok:false,msg:'У этого уравнения есть корни.'};
  }
  var items=expandPM(splitItems(raw)), vals=[];
  for(var i=0;i<items.length;i++){
    var f=compile(items[i]); if(!f) return {ok:false,msg:'Не удалось прочитать ответ. Корни разделяйте точкой с запятой, например 1; 5.'};
    var v=f(0); if(!isFinite(v)) return {ok:false,msg:BAD_READ};
    vals.push(v);
  }
  if(!vals.length) return {ok:false,msg:'Введите ответ.'};
  var got=dedupe(vals);
  if(exp.length===0) return {ok:false,msg:'Проверьте, есть ли у уравнения действительные корни.'};
  if(got.length===exp.length&&got.every(function(v,k){return close(v,exp[k]);})) return {ok:true};
  if(got.length<exp.length&&got.every(function(v){return exp.some(function(e){return close(e,v);});})) return {ok:false,msg:'Эти корни верные, но найдены не все.'};
  return {ok:false,msg:'Неверно. Проверьте вычисления.'};
}
function check(p,raw){
  var f,g,items,vals,i;
  if(p.type==='roots') return chkRoots(p,raw);
  if(p.type==='num'){
    var s=norm(raw).replace(/,/g,'.').replace(/^[a-z]\d?\s*=/,'');
    f=compile(s); var v=f?f(0):NaN;
    if(!isFinite(v)) return {ok:false,msg:'Не удалось прочитать ответ. Введите число или дробь, например −8/5.'};
    return close(v,ev(p.key))?{ok:true}:{ok:false,msg:'Неверно. Проверьте вычисления.'};
  }
  if(p.type==='pair'){
    items=splitItems(raw);
    if(items.length!==2) return {ok:false,msg:'Нужны два числа через точку с запятой: сумма; произведение.'};
    vals=[]; for(i=0;i<2;i++){f=compile(items[i]); if(!f) return {ok:false,msg:BAD_READ}; vals.push(f(0));}
    var e0=ev(p.key[0]), e1=ev(p.key[1]);
    if(close(vals[0],e0)&&close(vals[1],e1)) return {ok:true};
    if(close(vals[0],e1)&&close(vals[1],e0)) return {ok:false,msg:'Сначала сумма, потом произведение.'};
    return {ok:false,msg:'Неверно. Проверьте сумму и произведение по теореме Виета.'};
  }
  if(p.type==='eq'){
    var parts=norm(raw).split('=');
    if(parts.length!==2) return {ok:false,msg:'Запишите уравнение целиком, со знаком равно.'};
    var L=compile(parts[0]), R=compile(parts[1]), T=compile(p.key);
    if(!L||!R) return {ok:false,msg:BAD_READ};
    var r0=null;
    for(i=0;i<PTS.length;i++){
      var d=L(PTS[i])-R(PTS[i]), t=T(PTS[i]);
      if(!isFinite(d)||Math.abs(t)<1e-9) return {ok:false,msg:BAD_READ};
      var r=d/t;
      if(r0===null){ if(Math.abs(r)<1e-9) return {ok:false,msg:'Неверно. Проверьте уравнение.'}; r0=r; }
      else if(Math.abs(r-r0)>1e-7*Math.max(1,Math.abs(r0))) return {ok:false,msg:'Неверно. Проверьте знаки коэффициентов.'};
    }
    return {ok:true};
  }
  if(p.type==='fac'||p.type==='frac'){
    var sx=norm(raw).replace(/\s+/g,'');
    f=compile(sx); g=compile(p.key);
    if(!f) return {ok:false,msg:BAD_READ};
    if(!same(f,g)) return {ok:false,msg:'Неверно. Проверьте корни и знаки.'};
    if(p.type==='fac'){
      if((sx.match(/\(/g)||[]).length<2||sx.indexOf('^')>=0||sx.indexOf('x*x')>=0) return {ok:false,msg:'Значение верное, но нужно разложить на множители: запишите произведение скобок.'};
    } else if(sx.indexOf('^')>=0||sx.indexOf('x*x')>=0){
      return {ok:false,msg:'Значение верное, но дробь не сокращена: в ответе не должно остаться x².'};
    }
    return {ok:true};
  }
  return {ok:false,msg:BAD_READ};
}

/* ---------- Задачи ---------- */
var BL={A:'Неполные уравнения',B:'Полные уравнения и дискриминант',C:'Теорема Виета',D:'Разложение и дроби'};
var P=[];
function add(b,lead,e,type,key,ans,hint){P.push({n:P.length+1,b:b,lead:lead,e:e,type:type,key:key,ans:ans,hint:hint});}
var LR='Решите уравнение:', FAC='Разложите на множители:', RED='Сократите дробь:';
/* Блок A */
add('A',LR,'8x^2 − 16x = 0','roots',['0','2'],'0; 2','bx');
add('A',LR,'5x^2 + 15x = 0','roots',['0','-3'],'0; −3','bx');
add('A',LR,'11x^2 = 14x','roots',['0','14/11'],'0; {14|11}','bx3');
add('A',LR,'3x^2 + 2x = 0','roots',['0','-2/3'],'0; −{2|3}','bx');
add('A',LR,'5x^2 − 7 = 0','roots',['sqrt(7/5)','-sqrt(7/5)'],'±√[{7|5}]','cc');
add('A',LR,'5x^2 + 125 = 0','roots',[],'Нет корней','cc');
add('A',LR,'12x^2 − 48 = 0','roots',['2','-2'],'±2','cc');
add('A',LR,'{2y^2|3} − 6 = 0','roots',['3','-3'],'±3','cc');
add('A',LR,'0,5x^2 − 8 = 0','roots',['4','-4'],'±4','cc');
add('A',LR,'{5|2}t^2 − 90 = 0','roots',['6','-6'],'±6','cc');
add('A',LR,'x^2 + 81 = 0','roots',[],'Нет корней','cc');
add('A',LR,'(x − 5)^2 = 25 − 10x − 2x^2','roots',['0'],'0','br');
add('A',LR,'4x^2 − 36 = 0','roots',['3','-3'],'±3','cc');
add('A',LR,'7x^2 + 21x = 0','roots',['0','-3'],'0; −3','bx');
add('A',LR,'(x + 2)^2 = 4 + 4x + 5x^2','roots',['0'],'0','br');
/* Блок B */
add('B',LR,'x^2 + 4x + 3 = 0','roots',['-3','-1'],'−3; −1','full');
add('B',LR,'x^2 + 8x = 9','roots',['-9','1'],'−9; 1','full');
add('B',LR,'y^2 + 5 = 6y','roots',['1','5'],'1; 5','full');
add('B',LR,'4x^2 + x − 4 = x^2 − 3x','roots',['-2','2/3'],'−2; {2|3}','full');
add('B',LR,'5y^2 − 10y = 6 + 3y','roots',['3','-0.4'],'3; −0,4','full');
add('B',LR,'−6x^2 − 3 = 11x','roots',['-3/2','-1/3'],'−{3|2}; −{1|3}','full');
add('B',LR,'−t^2 − t + 2 = 0','roots',['-2','1'],'−2; 1','neg');
add('B',LR,'0,7x^2 + {x|2} − 0,2 = 0','roots',['-1','2/7'],'−1; {2|7}','dec');
add('B',LR,'x^2 − 6x + 7 = 0','roots',['3+sqrt(2)','3-sqrt(2)'],'3 ± √[2]','full');
add('B',LR,'2y^2 + 3y + 7 = 0','roots',[],'Нет корней','full');
add('B',LR,'x^2 − 8x + 15 = 0','roots',['3','5'],'3; 5','full');
add('B',LR,'2x^2 − 5x + 2 = 0','roots',['2','0.5'],'2; 0,5','full');
add('B',LR,'3x^2 − 7x + 2 = 0','roots',['2','1/3'],'2; {1|3}','full');
add('B',LR,'x^2 − 4x + 5 = 0','roots',[],'Нет корней','full');
add('B',LR,'x^2 + 2x − 8 = 0','roots',['-4','2'],'−4; 2','full');
/* Блок C */
add('C','','Найдите сумму корней уравнения: x^2 − 9x + 4 = 0.','num','9','9','vi');
add('C','','Найдите произведение корней: 5x^2 + 4x − 8 = 0.','num','-8/5','−1,6','vi');
add('C','','Найдите произведение корней: 2x^2 + 7x − 10 = 0.','num','-5','−5','vi');
add('C','','Если корни x^2 − 10x + q = 0 равны x_1, x_2, и x_1 = 4x_2, найдите q.','num','16','16','v34');
add('C','','Если x_1, x_2 — корни x^2 + 7x + 3 = 0, найдите x_1^2 + x_2^2.','num','43','43','sq');
add('C','','Если x_1, x_2 — корни x^2 − 10x + 3 = 0, найдите x_1^3 + x_2^3.','num','910','910','cube');
add('C','','Найдите сумму корней уравнения: x^2 − 11x + 6 = 0.','num','11','11','vi');
add('C','','Если корни x^2 − 12x + q = 0 равны x_1, x_2, и x_1 = 3x_2, найдите q.','num','27','27','v38');
add('C','','Если x_1, x_2 — корни x^2 + 5x + 2 = 0, найдите x_1^2 + x_2^2.','num','21','21','sq');
add('C','','Если x_1, x_2 — корни x^2 − 6x + 2 = 0, найдите x_1^3 + x_2^3.','num','180','180','cube');
add('C','','Составьте квадратное уравнение с корнями x_1 = 3, x_2 = −7.','eq','x^2+4x-21','x^2 + 4x − 21 = 0','make');
add('C','','Найдите сумму и произведение корней уравнения 3x^2 − 12x + 5 = 0.','pair',['4','5/3'],'Сумма: 4, произведение: {5|3}','vi');
add('C','','Если x_1, x_2 — корни x^2 − 8x + 5 = 0, найдите {1|x_1} + {1|x_2}.','num','1.6','1,6','inv');
add('C','','Если x_1, x_2 — корни x^2 − 4x − 2 = 0, найдите x_1^2x_2 + x_1x_2^2.','num','-8','−8','sym');
add('C','','Найдите значение p, если один из корней уравнения x^2 + px − 15 = 0 равен 3.','num','2','2','sub');
/* Блок D */
add('D',FAC,'5x^2 − 7x + 2','fac','5x^2-7x+2','(x − 1)(5x − 2)','fac');
add('D',FAC,'x^2 + 6x + 8','fac','x^2+6x+8','(x + 2)(x + 4)','fac');
add('D',FAC,'−4x^2 + 8x − 3','fac','-4x^2+8x-3','(1 − 2x)(2x − 3)','fac');
add('D',RED,'{x^2 + x − 12|x^2 + 2x − 8}','frac','(x-3)/(x-2)','{x − 3|x − 2}','red');
add('D',RED,'{2x^2 − x − 6|−3x^2 + 10x − 8}','frac','(2x+3)/(4-3x)','{2x + 3|4 − 3x}','red');
add('D',FAC,'3x^2 − 5x + 2','fac','3x^2-5x+2','(x − 1)(3x − 2)','fac');
add('D',FAC,'x^2 + 7x + 10','fac','x^2+7x+10','(x + 2)(x + 5)','fac');
add('D',FAC,'−3x^2 + 7x − 2','fac','-3x^2+7x-2','(2 − x)(3x − 1)','fac');
add('D',RED,'{x^2 + 2x − 15|x^2 + 3x − 10}','frac','(x-3)/(x-2)','{x − 3|x − 2}','red');
add('D',RED,'{3x^2 + 2x − 8|−2x^2 − x + 6}','frac','(3x-4)/(3-2x)','{3x − 4|3 − 2x}','red');
add('D',RED,'{x^2 − 9|x^2 − 5x + 6}','frac','(x+3)/(x-2)','{x + 3|x − 2}','red');
add('D',RED,'{2x^2 + 5x − 3|x^2 − 9}','frac','(2x-1)/(x-3)','{2x − 1|x − 3}','red');
add('D',FAC,'2x^2 − 9x + 10','fac','2x^2-9x+10','(x − 2)(2x − 5)','fac');
add('D',RED,'{x^2 − 4x + 4|x^2 − 3x + 2}','frac','(x-2)/(x-1)','{x − 2|x − 1}','red');
add('D',RED,'{4x^2 − 1|2x^2 + 5x − 3}','frac','(2x+1)/(x+3)','{2x + 1|x + 3}','red');

var HINT={
  bx:'Вынесите x за скобки: x(ax + b) = 0. Произведение равно нулю, когда один из множителей равен нулю.',
  bx3:'Перенесите 14x влево: 11x^2 − 14x = 0, затем вынесите x за скобки.',
  cc:'Перенесите свободный член вправо и найдите x^2. Если справа получилось отрицательное число, корней нет.',
  br:'Раскройте скобки и перенесите всё в левую часть. Посмотрите, какие слагаемые сократятся.',
  full:'Приведите уравнение к виду ax^2 + bx + c = 0, найдите D = b^2 − 4ac, затем x = {−b ± √[D]|2a}.',
  neg:'Умножьте обе части на −1, чтобы старший коэффициент стал положительным, затем найдите D.',
  dec:'Умножьте обе части на 10, чтобы избавиться от дробей, затем найдите D.',
  vi:'По теореме Виета: x_1 + x_2 = −{b|a}, x_1x_2 = {c|a}.',
  v34:'x_1 + x_2 = 10 и x_1 = 4x_2, значит 5x_2 = 10. Найдите x_2, потом x_1 и q = x_1x_2.',
  v38:'x_1 + x_2 = 12 и x_1 = 3x_2, значит 4x_2 = 12. Найдите x_2, потом x_1 и q = x_1x_2.',
  sq:'x_1^2 + x_2^2 = (x_1 + x_2)^2 − 2x_1x_2. Посмотрите пример 1 в лекции.',
  cube:'x_1^3 + x_2^3 = (x_1 + x_2)^3 − 3x_1x_2(x_1 + x_2).',
  make:'Уравнение с корнями x_1 и x_2: x^2 − (x_1 + x_2)x + x_1x_2 = 0.',
  inv:'{1|x_1} + {1|x_2} = {x_1 + x_2|x_1x_2}.',
  sym:'Вынесите x_1x_2 за скобки: x_1x_2(x_1 + x_2).',
  sub:'Подставьте x = 3 в уравнение и найдите p.',
  fac:'Найдите корни x_1, x_2 через D. Тогда ax^2 + bx + c = a(x − x_1)(x − x_2).',
  red:'Разложите числитель и знаменатель на множители через корни, затем сократите общий множитель. Посмотрите пример 2 в лекции.'
};
var FMT={
  roots:'Несколько корней разделяйте точкой с запятой, например 1; 5. Если корней нет, напишите «нет корней».',
  num:'Ответ: число или дробь, например 16 или −8/5.',
  pair:'Сначала сумма, затем произведение, например 4; 5/3.',
  eq:'Запишите уравнение целиком, например x^2 + 4x − 21 = 0.',
  fac:'Запишите произведение скобок, например (x − 1)(5x − 2).',
  frac:'Запишите сокращённую дробь, например (x − 3)/(x − 2).'
};

if(typeof module!=='undefined') module.exports={P:P,check:check,compile:compile,fx:fx};

/* ---------- Интерфейс ---------- */
function init(){
  var $=function(s,r){return (r||document).querySelector(s);};
  var $$=function(s,r){return Array.prototype.slice.call((r||document).querySelectorAll(s));};
  var LS='kvadratnye-uravneniya-8';
  var S={p:{},bestTest:0,bestStreak:0,tests:0};
  try{var raw=localStorage.getItem(LS); if(raw){var o=JSON.parse(raw); if(o&&typeof o==='object') for(var k in o) S[k]=o[k];}}catch(e){}
  function save(){try{localStorage.setItem(LS,JSON.stringify(S));}catch(e){}}
  var cur=1, filter='all', streak=0, revealArm=false, T=null, resetArm=false;
  var KEYS=[['x','x'],['x²','^2'],['√','√('],['±','±'],['/','/'],['(','('],[')',')'],[';','; ']];

  $$('[data-m]').forEach(function(el){el.innerHTML=fmt(el.textContent);});

  /* статус */
  var RANKS=[[0,'Переменная'],[80,'Коэффициент'],[200,'Дискриминант'],[350,'Корень'],[520,'Теорема Виета']];
  function xpTotal(){var t=0; for(var k in S.p) t+=S.p[k].xp||0; return t+(S.bestTest||0)*10;}
  function solvedCount(){var c=0; for(var k in S.p) if(S.p[k].st==='ok') c++; return c;}
  function renderStatus(){
    var xp=xpTotal(), ri=0;
    RANKS.forEach(function(r,i){if(xp>=r[0]) ri=i;});
    var nx=RANKS[ri+1], pct=nx?(xp-RANKS[ri][0])/(nx[0]-RANKS[ri][0])*100:100;
    $('#status').innerHTML=
      '<div class="rank-row"><div><span class="lbl">Звание</span><span class="rank">'+RANKS[ri][1]+'</span></div>'+
      '<div class="stats"><span><b>'+xp+'</b> XP</span><span><b>'+solvedCount()+'</b> из '+P.length+' решено</span><span>серия <b>'+streak+'</b></span></div></div>'+
      '<div class="xpbar" role="progressbar" aria-label="Прогресс до следующего звания" aria-valuemin="0" aria-valuemax="100" aria-valuenow="'+Math.round(pct)+'"><div class="xpfill"></div></div>'+
      '<p class="next">'+(nx?'До звания «'+nx[1]+'»: '+(nx[0]-xp)+' XP':'Высшее звание достигнуто')+'</p>';
    $('.xpfill').style.width=pct+'%';
  }

  /* вкладки */
  function showTab(name){
    $$('.tabs [data-tab]').forEach(function(b){var on=b.dataset.tab===name; b.setAttribute('aria-selected',on?'true':'false');});
    ['lecture','practice','answers','test'].forEach(function(t){$('#tab-'+t).hidden=(t!==name);});
    if(name==='practice') showProblem();
    if(name==='test') renderTest();
    window.scrollTo(0,0);
  }

  function esc(s){return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');}
  function stmt(p){
    return (p.lead?'<p class="lead">'+fmt(p.lead)+'</p>':'')+'<p class="expr">'+fmt(p.e)+'</p>';
  }
  function keysHtml(){
    return '<div class="keys" aria-label="Вставка символов">'+KEYS.map(function(k){return '<button type="button" data-ins="'+k[1]+'" aria-label="Вставить '+esc(k[0])+'">'+fmt(k[0]==='x²'?'x^2':k[0])+'</button>';}).join('')+'</div>';
  }
  function insertAt(id,text){
    var inp=$('#'+id); if(!inp) return;
    var a=inp.selectionStart, b=inp.selectionEnd;
    if(a==null){a=b=inp.value.length;}
    inp.value=inp.value.slice(0,a)+text+inp.value.slice(b);
    inp.focus(); var pos=a+text.length; inp.setSelectionRange(pos,pos);
  }

  /* практика */
  function inFilter(p){return filter==='all'||p.b===filter;}
  function renderChips(){
    var html='', all=P.filter(function(p){return (S.p[p.n]||{}).st==='ok';}).length;
    html+='<button class="chip" data-chip="all" aria-pressed="'+(filter==='all')+'">Все · '+all+'/'+P.length+'</button>';
    ['A','B','C','D'].forEach(function(b){
      var list=P.filter(function(p){return p.b===b;}), d=list.filter(function(p){return (S.p[p.n]||{}).st==='ok';}).length;
      html+='<button class="chip" data-chip="'+b+'" aria-pressed="'+(filter===b)+'" title="'+esc(BL[b])+'">Блок '+b+' · '+d+'/'+list.length+'</button>';
    });
    $('#chips').innerHTML=html;
  }
  function renderDots(){
    $('#dots').innerHTML=P.filter(inFilter).map(function(p){
      var st=(S.p[p.n]||{}).st||'';
      var lbl='Задача '+p.n+(st==='ok'?', решена':st==='rev'?', показан ответ':st==='bad'?', были ошибки':'');
      return '<button class="dot '+st+(p.n===cur?' cur':'')+'" data-n="'+p.n+'" aria-label="'+lbl+'">'+p.n+'</button>';
    }).join('');
  }
  function setFb(cls,html){var f=$('#fb'); if(!f) return; f.className='fb '+cls; f.innerHTML=html;}
  function ansLine(p){return '<span class="ans-line">Ответ: <span class="m">'+fmt(p.ans)+'</span></span>';}
  function showProblem(){
    var p=P[cur-1], st=S.p[cur]||{};
    revealArm=false;
    $('#pcard').innerHTML=
      '<div class="ph"><span class="pn">Задача '+p.n+'</span><span>Блок '+p.b+' · '+esc(BL[p.b])+'</span></div>'+
      stmt(p)+
      '<div class="inrow"><input id="ans" type="text" autocomplete="off" autocapitalize="off" autocorrect="off" spellcheck="false" aria-label="Ваш ответ" placeholder="Ваш ответ"><button class="btn primary" data-act="check">Проверить</button></div>'+
      keysHtml()+
      '<p class="fmtnote">'+fmt(FMT[p.type])+'</p>'+
      '<div id="fb" class="fb" role="status" aria-live="polite"></div>'+
      '<div id="hintbox" class="hintbox" hidden></div>'+
      '<div class="actions"><button class="btn" data-act="hint">Подсказка</button><button class="btn" data-act="reveal" id="revbtn">Показать ответ</button></div>'+
      '<div class="nav"><button class="btn" data-act="prev">← Назад</button><button class="btn" data-act="next" id="nextbtn">Далее →</button></div>';
    if(st.st==='ok') setFb('ok','<span class="ic">✓</span>Решено.'+ansLine(p));
    else if(st.st==='rev') setFb('rev','Ответ был показан.'+ansLine(p));
    renderDots(); renderChips();
  }
  function step(d){
    var list=P.filter(inFilter), i=-1;
    list.forEach(function(p,k){if(p.n===cur) i=k;});
    if(i<0) i=0; else i=(i+d+list.length)%list.length;
    cur=list[i].n; showProblem();
  }
  function doCheck(){
    var inp=$('#ans'); if(!inp) return;
    var raw=inp.value.trim();
    if(!raw){setFb('warn','Введите ответ.'); return;}
    var p=P[cur-1], st=S.p[cur]=S.p[cur]||{tries:0};
    var r=check(p,raw);
    if(r.ok){
      var msg;
      if(st.st==='ok') msg='Верно. Эта задача уже засчитана.';
      else{
        var gain=st.st==='rev'?0:(((st.tries||0)===0&&!st.hint)?10:5);
        st.xp=gain; st.st='ok';
        msg='Верно!'+(gain?' +'+gain+' XP':' Ответ был показан, XP не начислен.');
      }
      streak++; if(streak>(S.bestStreak||0)) S.bestStreak=streak;
      setFb('ok','<span class="ic">✓</span>'+esc(msg)+ansLine(p));
      $('#nextbtn').classList.add('primary');
    }else{
      st.tries=(st.tries||0)+1;
      if(st.st!=='ok'&&st.st!=='rev') st.st='bad';
      streak=0;
      setFb('bad','<span class="ic">✗</span>'+esc(r.msg));
    }
    save(); renderStatus(); renderDots(); renderChips();
  }
  function doHint(){
    var p=P[cur-1], st=S.p[cur]=S.p[cur]||{tries:0};
    if(st.st!=='ok') st.hint=true;
    var hb=$('#hintbox'); hb.hidden=false; hb.innerHTML='<b>Подсказка.</b> '+fmt(HINT[p.hint]);
    save();
  }
  function doReveal(){
    var btn=$('#revbtn');
    if(!revealArm){revealArm=true; btn.textContent='Точно показать? XP не начислится'; return;}
    var p=P[cur-1], st=S.p[cur]=S.p[cur]||{tries:0};
    if(st.st!=='ok'){st.st='rev'; st.xp=0; streak=0;}
    revealArm=false; btn.textContent='Показать ответ';
    setFb(st.st==='ok'?'ok':'rev', (st.st==='ok'?'<span class="ic">✓</span>Решено.':'Ответ показан.')+ansLine(p));
    save(); renderStatus(); renderDots(); renderChips();
  }

  /* ответы */
  function renderAnswers(){
    var html='';
    ['A','B','C','D'].forEach(function(b){
      var list=P.filter(function(p){return p.b===b;});
      html+='<details class="blk"><summary>Блок '+b+' · '+esc(BL[b])+' ('+list[0].n+'–'+list[list.length-1].n+')</summary><div class="alist">'+
        list.map(function(p){return '<div class="ai"><span class="an">'+p.n+'</span><span class="m">'+fmt(p.ans)+'</span></div>';}).join('')+'</div></details>';
    });
    $('#alist').innerHTML=html;
  }

  /* тест */
  function shuffle(a){a=a.slice(); for(var i=a.length-1;i>0;i--){var j=Math.floor(Math.random()*(i+1)); var t=a[i]; a[i]=a[j]; a[j]=t;} return a;}
  function startTest(){
    var qs=[];
    [['A',3],['B',3],['C',2],['D',2]].forEach(function(x){
      qs=qs.concat(shuffle(P.filter(function(p){return p.b===x[0];})).slice(0,x[1]));
    });
    T={qs:shuffle(qs),i:0,ans:[],res:[]};
    renderTest();
  }
  function seg(){
    var h='<div class="seg" aria-hidden="true">';
    for(var i=0;i<T.qs.length;i++) h+='<span class="'+(i<T.i?'done':i===T.i?'now':'')+'"></span>';
    return h+'</div>';
  }
  function renderTest(){
    var box=$('#tbox');
    if(!T){
      box.innerHTML='<div class="card"><h3>Контрольная работа</h3>'+
        '<p>10 задач из банка: по 3 из блоков A и B, по 2 из блоков C и D. Подсказок нет, результат появится в конце. Каждый новый тест собирается заново.</p>'+
        '<p class="small">'+(S.tests?'Лучший результат: '+S.bestTest+' из 10. Пройдено раз: '+S.tests+'.':'Вы ещё не проходили тест.')+'</p>'+
        '<button class="btn primary" data-act="tstart">Начать тест</button></div>';
      return;
    }
    if(T.i<T.qs.length){
      var p=T.qs[T.i];
      box.innerHTML='<div class="card">'+seg()+
        '<div class="ph"><span class="pn">Вопрос '+(T.i+1)+' из '+T.qs.length+'</span></div>'+stmt(p)+
        '<div class="inrow"><input id="tans" type="text" autocomplete="off" autocapitalize="off" autocorrect="off" spellcheck="false" aria-label="Ваш ответ" placeholder="Ваш ответ"><button class="btn primary" data-act="tsubmit">Ответить</button></div>'+
        keysHtml().replace(/data-ins/g,'data-tins')+
        '<p class="fmtnote">'+fmt(FMT[p.type])+'</p>'+
        '<div class="actions"><button class="btn" data-act="tskip">Пропустить</button></div></div>';
      var inp=$('#tans'); if(inp) inp.focus();
      return;
    }
    var score=T.res.filter(Boolean).length;
    var mk=score>=9?['5','Отлично']:score>=7?['4','Хорошо']:score>=5?['3','Удовлетворительно']:['2','Нужно повторить'];
    var weak={}; T.qs.forEach(function(p,i){if(!T.res[i]) weak[p.b]=1;});
    var wk=Object.keys(weak).sort();
    var h='<div class="card"><div class="res-top"><div class="mark" aria-label="Оценка '+mk[0]+'">'+mk[0]+'</div><div><h3>'+mk[1]+'</h3><p style="margin:0">Верно: <b>'+score+'</b> из '+T.qs.length+'</p>'+
      '<p class="small" style="margin:4px 0 0">'+(wk.length?'Повторите: '+wk.map(function(b){return 'блок '+b+' ('+esc(BL[b])+')';}).join(', ')+'.':'Ошибок нет.')+'</p></div></div>'+
      '<div class="rv">';
    T.qs.forEach(function(q,i){
      var ok=T.res[i];
      h+='<div class="rv-i '+(ok?'ok':'no')+'"><span class="s" aria-label="'+(ok?'верно':'неверно')+'">'+(ok?'✓':'✗')+'</span><div>'+
        '<div class="meta">Задача '+q.n+' · блок '+q.b+'</div>'+(q.lead?'<div class="meta">'+fmt(q.lead)+'</div>':'')+'<p class="expr">'+fmt(q.e)+'</p>'+
        '<div class="meta">Ваш ответ: '+(T.ans[i]?esc(T.ans[i]):'—')+(ok?'':' · правильный: <span class="m">'+fmt(q.ans)+'</span>')+'</div></div></div>';
    });
    h+='</div><div class="actions"><button class="btn primary" data-act="tstart">Пройти ещё раз</button><button class="btn" data-tab="practice">К практике</button></div></div>';
    box.innerHTML=h;
  }
  function testAnswer(skip){
    if(!T||T.i>=T.qs.length) return;
    var inp=$('#tans'), raw=skip?'':(inp?inp.value.trim():'');
    if(!skip&&!raw){inp&&inp.focus(); return;}
    var p=T.qs[T.i];
    T.ans.push(raw); T.res.push(raw?check(p,raw).ok:false); T.i++;
    if(T.i>=T.qs.length){
      var sc=T.res.filter(Boolean).length;
      S.tests=(S.tests||0)+1; if(sc>(S.bestTest||0)) S.bestTest=sc;
      save(); renderStatus();
    }
    renderTest();
    window.scrollTo(0,0);
  }

  /* лаборатория */
  function initLab(){
    var g='', k, px, py;
    for(k=-11;k<=11;k++){px=200+k*18; g+='<line class="'+(k%5===0?'gr5':'gr')+'" x1="'+px+'" y1="0" x2="'+px+'" y2="280"/>';}
    for(k=-15;k<=15;k++){py=140-k*9; g+='<line class="'+(k%5===0?'gr5':'gr')+'" x1="0" y1="'+py+'" x2="400" y2="'+py+'"/>';}
    $('#pgrid').innerHTML=g;
    var ax='<line class="ax" x1="0" y1="140" x2="400" y2="140"/><line class="ax" x1="200" y1="0" x2="200" y2="280"/>';
    [-10,-5,5,10].forEach(function(v){
      ax+='<text x="'+(200+v*18)+'" y="153" text-anchor="middle">'+String(v).replace('-','−')+'</text>';
      ax+='<text x="194" y="'+(140-v*9+3)+'" text-anchor="end">'+String(v).replace('-','−')+'</text>';
    });
    ax+='<text x="392" y="134" text-anchor="end">x</text><text x="206" y="11">y</text>';
    $('#paxes').innerHTML=ax;
    ['la','lb','lc'].forEach(function(id){$('#'+id).addEventListener('input',labUpdate);});
    labUpdate();
  }
  function nf(v){return String(Math.round(v*1000)/1000).replace('-','−');}
  function coef(v,first){var s=v<0?'−':(first?'':'+'); var a=Math.abs(v); return {sg:s,a:a};}
  function labUpdate(){
    var a=+$('#la').value, b=+$('#lb').value, c=+$('#lc').value;
    $('#lal').innerHTML=fmt('a = '+nf(a)); $('#lbl').innerHTML=fmt('b = '+nf(b)); $('#lcl').innerHTML=fmt('c = '+nf(c));
    var out=$('#labout');
    if(a===0){
      $('#pcurve').setAttribute('points',''); $('#proots').innerHTML='';
      out.innerHTML='<p class="verdict">Коэффициент a не может быть равен нулю.</p><p>При <span class="m">'+fmt('a = 0')+'</span> уравнение перестаёт быть квадратным.</p>';
      return;
    }
    var pts=[], x, y, i;
    for(i=-110;i<=110;i++){x=i/10; y=a*x*x+b*x+c; pts.push((200+x*18).toFixed(1)+','+(140-y*9).toFixed(1));}
    $('#pcurve').setAttribute('points',pts.join(' '));
    var D=b*b-4*a*c, rts=[], rh='';
    if(D>=0){var sq=Math.sqrt(D); rts=D===0?[-b/(2*a)]:[(-b-sq)/(2*a),(-b+sq)/(2*a)];}
    rts.forEach(function(r){if(Math.abs(r)<=11) rh+='<circle class="rt" cx="'+(200+r*18).toFixed(1)+'" cy="140" r="5"/>';});
    $('#proots').innerHTML=rh;
    var eq='y = '+(a===1?'':a===-1?'−':nf(a))+'x^2 '+(b<0?'− ':'+ ')+(Math.abs(b)===1?'':nf(Math.abs(b)))+'x '+(c<0?'− ':'+ ')+nf(Math.abs(c));
    var h='<p class="m">'+fmt(eq)+'</p>'+
      '<p class="m">'+fmt('D = b^2 − 4ac = ('+nf(b)+')^2 − 4·('+nf(a)+')·('+nf(c)+') = ')+'<b>'+nf(D)+'</b></p>';
    if(D>0) h+='<p class="verdict">D &gt; 0: два корня</p><p class="m">'+fmt('x_1 = '+nf(rts[0])+',   x_2 = '+nf(rts[1]))+'</p>';
    else if(D===0) h+='<p class="verdict">D = 0: один корень</p><p class="m">'+fmt('x = '+nf(rts[0]))+'</p>';
    else h+='<p class="verdict">D &lt; 0: корней нет</p><p>Парабола не пересекает ось <span class="m">'+fmt('x')+'</span>.</p>';
    out.innerHTML=h;
  }

  /* примеры */
  function stepper(el,title,task,steps){
    el.innerHTML='<p class="exh">'+title+'</p><p class="m" style="margin-bottom:6px">'+fmt(task)+'</p>'+
      '<ol class="steps">'+steps.map(function(s){return '<li hidden>'+fmt(s)+'</li>';}).join('')+'</ol>'+
      '<button class="btn" type="button">Показать шаг</button>';
    var lis=$$('li',el), btn=$('button',el), shown=0;
    btn.addEventListener('click',function(){
      if(shown>=lis.length){lis.forEach(function(l){l.hidden=true;}); shown=0; btn.textContent='Показать шаг'; return;}
      lis[shown].hidden=false; shown++;
      btn.textContent=shown>=lis.length?'Скрыть решение':'Показать следующий шаг';
    });
  }
  stepper($('#ex1'),'Пример 1 · Теорема Виета и выразимые свойства','Если x_1, x_2 — корни уравнения x^2 − 10x + 3 = 0, найдите x_1^2 + x_2^2.',[
    'По теореме Виета: x_1 + x_2 = 10, x_1x_2 = 3.',
    'Выразим сумму квадратов: x_1^2 + x_2^2 = (x_1 + x_2)^2 − 2x_1x_2.',
    'Подставим: 10^2 − 2·3 = 100 − 6.',
    'Ответ: 94.'
  ]);
  stepper($('#ex2'),'Пример 2 · Сокращение алгебраической дроби','Сократите дробь: {2x^2 − x − 6|−3x^2 + 10x − 8}.',[
    'Корни числителя 2x^2 − x − 6 = 0: D = 1 + 48 = 49, x_1 = 2, x_2 = −{3|2}.',
    'Разложим числитель: 2(x − 2)(x + {3|2}) = (x − 2)(2x + 3).',
    'Корни знаменателя −3x^2 + 10x − 8 = 0: D = 100 − 96 = 4, x_1 = 2, x_2 = {4|3}.',
    'Разложим знаменатель: −3(x − 2)(x − {4|3}) = −(x − 2)(3x − 4).',
    'Сократим на (x − 2). Ответ: {2x + 3|4 − 3x}.'
  ]);

  /* события */
  document.addEventListener('click',function(e){
    var t=e.target.closest('[data-tab],[data-act],[data-ins],[data-tins],[data-n],[data-chip]');
    if(!t) return;
    if(t.dataset.tab){showTab(t.dataset.tab); return;}
    if(t.dataset.ins!==undefined){insertAt('ans',t.dataset.ins); return;}
    if(t.dataset.tins!==undefined){insertAt('tans',t.dataset.tins); return;}
    if(t.dataset.n){cur=+t.dataset.n; showProblem(); return;}
    if(t.dataset.chip){
      filter=t.dataset.chip;
      var list=P.filter(inFilter), un=list.filter(function(p){return (S.p[p.n]||{}).st!=='ok';})[0];
      cur=(un||list[0]).n; showProblem(); return;
    }
    switch(t.dataset.act){
      case 'check': doCheck(); break;
      case 'hint': doHint(); break;
      case 'reveal': doReveal(); break;
      case 'prev': step(-1); break;
      case 'next': step(1); break;
      case 'tstart': startTest(); break;
      case 'tsubmit': testAnswer(false); break;
      case 'tskip': testAnswer(true); break;
      case 'reset':
        if(!resetArm){resetArm=true; t.textContent='Точно сбросить?'; setTimeout(function(){resetArm=false; t.textContent='Сбросить прогресс';},4000); break;}
        resetArm=false; t.textContent='Сбросить прогресс';
        S={p:{},bestTest:0,bestStreak:0,tests:0}; streak=0; T=null; cur=1; filter='all'; save();
        renderStatus(); showProblem(); renderTest();
        break;
    }
  });
  document.addEventListener('keydown',function(e){
    if(e.key!=='Enter') return;
    if(e.target&&e.target.id==='ans'){e.preventDefault(); doCheck();}
    else if(e.target&&e.target.id==='tans'){e.preventDefault(); testAnswer(false);}
  });

  /* старт */
  renderStatus(); renderAnswers(); initLab();
  var first=P.filter(function(p){return (S.p[p.n]||{}).st!=='ok';})[0];
  cur=first?first.n:1;
  showProblem(); renderTest();
}
if(typeof document!=='undefined') init();
})();
</script>

</body></html>
