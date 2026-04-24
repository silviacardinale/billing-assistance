<!DOCTYPE html>
# billing-assistance

<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AiFonso · Billing Assistant · Doofinder</title>
<style>
*{box-sizing:border-box;margin:0;padding:0}
:root{
  --bg:#fff;--bg2:#faf9f8;--bg3:#f2f0ee;
  --text:#181816;--text2:#585854;--text3:#98988e;
  --border:rgba(0,0,0,.09);--border2:rgba(0,0,0,.15);
  --ink:#1a1a2e;
  --mg:#c0006e;--mg-bg:#fce8f3;--mg-b:#f0a0d0;
  --bl:#1255a4;--bl-bg:#e8f0fc;--bl-b:#90b8f0;
  --am:#8c5a00;--am-bg:#fff4d6;--am-b:#f0c840;
  --tl:#0a6060;--tl-bg:#e0f4f4;--tl-b:#70c8c8;
  --rd:#b02020;--rd-bg:#fdeaea;--rd-b:#f09090;
  --r:11px;--rs:8px;
}
body{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;background:var(--bg3);min-height:100vh;display:flex;align-items:flex-start;justify-content:center;padding:2rem 1rem}
.app{background:var(--bg);border-radius:20px;border:.5px solid var(--border2);width:100%;max-width:740px;box-shadow:0 6px 40px rgba(0,0,0,.10)}
.hdr{background:linear-gradient(135deg,var(--ink) 0%,#2a1845 100%);padding:1.4rem 2rem;display:flex;align-items:center;gap:16px;border-radius:20px 20px 0 0}
.hdr-logo{flex-shrink:0}.hdr-logo svg{display:block}
.hdr-title{flex:1}
.hdr-title h1{font-size:18px;font-weight:700;color:#fff;letter-spacing:-.2px}
.hdr-title p{font-size:12px;color:rgba(255,255,255,.5);margin-top:3px}
.hdr-badge{background:var(--mg);color:#fff;font-size:10px;font-weight:700;padding:3px 10px;border-radius:20px;letter-spacing:.04em;text-transform:uppercase;flex-shrink:0}
/* tab nav inside header */

.body{padding:1.75rem 2rem}

.prog{display:flex;align-items:center;margin-bottom:1.75rem}
.pstep{display:flex;align-items:center;flex:1}.pstep:last-child{flex:0}
.pc{width:30px;height:30px;border-radius:50%;border:2px solid var(--border2);display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:700;color:var(--text3);background:var(--bg);flex-shrink:0;transition:all .25s}
.pl{flex:1;height:2px;background:var(--border2);transition:background .25s;margin:0 3px}
.pstep.done .pc{background:var(--mg);border-color:var(--mg);color:#fff}
.pstep.done .pl{background:var(--mg)}
.pstep.on .pc{background:var(--ink);border-color:var(--ink);color:#fff;box-shadow:0 0 0 4px rgba(26,26,46,.1)}
.slbl{font-size:10px;font-weight:800;color:var(--text3);text-transform:uppercase;letter-spacing:.08em;margin-bottom:12px;display:flex;align-items:center;gap:8px}
.slbl::after{content:'';flex:1;height:.5px;background:var(--border)}
.scr{display:none}.scr.on{display:block}
.case-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:4px}
.case-card{background:var(--bg);border:1.5px solid var(--border2);border-radius:var(--rs);padding:13px 15px 13px 18px;text-align:left;cursor:pointer;transition:all .18s;width:100%;font-family:inherit;position:relative;overflow:hidden}
.case-card::before{content:'';position:absolute;left:0;top:0;bottom:0;width:4px}
.case-card:hover{border-color:var(--ink);transform:translateY(-1px);box-shadow:0 4px 14px rgba(0,0,0,.09)}
.case-card.sel{border-color:var(--ink);background:var(--bg2)}
.case-card .ct{font-size:13px;font-weight:700;color:var(--text);display:block;margin-bottom:3px}
.case-card .cd{font-size:11px;color:var(--text2);display:block;line-height:1.4}
.case-card .ctag{display:inline-block;font-size:10px;font-weight:700;padding:2px 8px;border-radius:20px;margin-top:6px}
.c-mg::before{background:var(--mg)}.c-bl::before{background:var(--bl)}.c-am::before{background:var(--am)}.c-tl::before{background:var(--tl)}.c-rd::before{background:var(--rd)}
.t-mg{background:var(--mg-bg);color:var(--mg)}.t-bl{background:var(--bl-bg);color:var(--bl)}.t-am{background:var(--am-bg);color:var(--am)}.t-tl{background:var(--tl-bg);color:var(--tl)}.t-rd{background:var(--rd-bg);color:var(--rd)}
input,textarea,select{width:100%;border:1.5px solid var(--border2);border-radius:var(--rs);padding:9px 12px;font-size:13px;font-family:inherit;background:var(--bg);color:var(--text);resize:none;outline:none;transition:border-color .15s}
input:focus,textarea:focus,select:focus{border-color:var(--mg);box-shadow:0 0 0 3px var(--mg-bg)}
input[type=range]{padding:0;border:none;background:transparent;accent-color:var(--mg);box-shadow:none}
input[type=number]{-moz-appearance:textfield}
.fl{font-size:11px;font-weight:700;color:var(--text2);margin-bottom:5px;text-transform:uppercase;letter-spacing:.04em}
.gf2{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:10px}
.gf3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px;margin-bottom:10px}
.card{background:var(--bg);border:1px solid var(--border);border-radius:var(--r);padding:1rem 1.25rem;margin-bottom:12px}
.al{border-radius:var(--rs);padding:12px 16px;font-size:12px;line-height:1.65;margin-bottom:12px;display:flex;gap:12px;align-items:flex-start}
.al-icon{font-size:15px;flex-shrink:0;margin-top:.1em}
.al-body{flex:1;min-width:0}
.al-body strong{font-weight:700;display:block;margin-bottom:4px;font-size:12px;line-height:1.4}
.a-bl{background:var(--bl-bg);border:.5px solid var(--bl-b);color:var(--bl)}
.a-mg{background:var(--mg-bg);border:.5px solid var(--mg-b);color:var(--mg)}
.a-am{background:var(--am-bg);border:.5px solid var(--am-b);color:var(--am)}
.a-tl{background:var(--tl-bg);border:.5px solid var(--tl-b);color:var(--tl)}
.a-rd{background:var(--rd-bg);border:.5px solid var(--rd-b);color:var(--rd)}
.policy{background:var(--bg2);border:.5px solid var(--border);border-radius:var(--rs);padding:11px 16px;font-size:12px;color:var(--text2);line-height:1.6;margin-bottom:16px}
.policy strong{color:var(--text);font-weight:700}
.result-box{border-radius:var(--rs);padding:11px 14px;font-size:13px;font-weight:700;margin-top:4px}
#annResult{background:var(--am-bg);border:.5px solid var(--am-b);color:var(--am)}
#clRefResult{background:var(--rd-bg);border:.5px solid var(--rd-b);color:var(--rd)}
.tog-row{display:flex;gap:6px;margin-bottom:14px}
.tog{flex:1;padding:9px 12px;background:var(--bg);border:1.5px solid var(--border2);border-radius:var(--rs);font-size:13px;font-weight:600;color:var(--text2);cursor:pointer;transition:all .15s;font-family:inherit;text-align:center}
.tog:hover{border-color:var(--mg);color:var(--text)}.tog.sel{border-color:var(--mg);background:var(--mg);color:#fff}
.opt-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:7px;margin-bottom:12px}
.opt{background:var(--bg);border:1.5px solid var(--border2);border-radius:var(--rs);padding:10px 12px;text-align:left;cursor:pointer;transition:all .15s;width:100%;font-family:inherit}
.opt:hover{border-color:var(--mg)}.opt.sel{border-color:var(--mg);background:var(--mg-bg)}
.opt .ot{font-size:12px;font-weight:700;color:var(--text);display:block}
.opt .od{font-size:10px;color:var(--text2);margin-top:2px;display:block}
.bp{background:var(--mg);color:#fff;border:none;border-radius:var(--rs);padding:11px 24px;font-size:13px;font-weight:700;cursor:pointer;font-family:inherit;transition:opacity .15s}
.bp:hover{opacity:.85}
.bs{background:var(--bg);border:1.5px solid var(--border2);border-radius:var(--rs);padding:11px 18px;font-size:13px;font-weight:600;cursor:pointer;color:var(--text);font-family:inherit;transition:all .15s}
.bs:hover{border-color:var(--ink)}
.brow{display:flex;gap:8px;justify-content:space-between;margin-top:1.5rem}
.step-list{display:flex;flex-direction:column;gap:0}
.step-item{display:flex;gap:14px;position:relative;padding-bottom:16px}
.step-item:last-child{padding-bottom:0}
.step-item:not(:last-child)::after{content:'';position:absolute;left:14px;top:32px;bottom:0;width:2px;background:var(--mg-bg)}
.step-num{width:30px;height:30px;min-width:30px;border-radius:50%;background:var(--mg);color:#fff;display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:800;flex-shrink:0;z-index:1}
.step-body{font-size:13px;color:var(--text);line-height:1.65;padding-top:5px}
.step-body strong{font-weight:700;color:var(--ink)}
.atag{display:inline-block;background:var(--bg2);border:1px solid var(--border2);border-radius:4px;padding:1px 7px;font-size:11px;font-weight:700;color:var(--text2)}
.calc-section{background:var(--bg2);border:1px solid var(--border);border-radius:var(--r);padding:1.25rem;margin:12px 0}
.calc-section h3{font-size:11px;font-weight:800;color:var(--mg);text-transform:uppercase;letter-spacing:.07em;margin-bottom:14px}
.rr{display:flex;align-items:center;gap:10px;margin-bottom:12px}
.rl{font-size:12px;color:var(--text2);width:200px;flex-shrink:0;font-weight:600}
.rv{font-size:15px;font-weight:800;color:var(--mg);min-width:44px;text-align:right}
.metrics{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin:12px 0}
.met{background:var(--bg);border:1px solid var(--border);border-radius:var(--rs);padding:11px;text-align:center}
.met .mv{font-size:17px;font-weight:800;color:var(--text)}
.met .ml{font-size:10px;color:var(--text3);margin-top:3px;line-height:1.3}
.met.hi{background:var(--mg);border-color:var(--mg)}
.met.hi .mv,.met.hi .ml{color:#fff}.met.hi .ml{opacity:.7}
.met.acc{background:var(--mg-bg);border-color:var(--mg-b)}
.met.acc .mv{color:var(--mg)}.met.acc .ml{color:var(--mg);opacity:.8}
.cb{border:1.5px solid var(--border);border-radius:var(--r);overflow:hidden;margin-bottom:12px}
.cb-hdr{display:flex;align-items:center;justify-content:space-between;padding:8px 14px;background:var(--bg2);border-bottom:1px solid var(--border)}
.cb-hdr .cbl{font-size:10px;font-weight:800;color:var(--text2);text-transform:uppercase;letter-spacing:.06em}
.cb-hdr button{font-size:11px;padding:4px 10px;background:var(--bg);border:1.5px solid var(--border2);border-radius:5px;cursor:pointer;font-family:inherit;color:var(--text);font-weight:600;transition:all .15s}
.cb-hdr button:hover{border-color:var(--mg);color:var(--mg)}
.cb-body{padding:13px 16px;font-size:13px;line-height:1.75;color:var(--text);white-space:pre-wrap}
.cb-body.mono{font-family:'SF Mono','Fira Mono',monospace;font-size:12px;line-height:1.7}
.cl{list-style:none}
.cl li{display:flex;gap:12px;align-items:flex-start;font-size:13px;padding:10px 0;border-bottom:.5px solid var(--border);color:var(--text);line-height:1.45}
.cl li:last-child{border-bottom:none}
.ci{width:20px;height:20px;min-width:20px;border-radius:50%;border:2px solid var(--border2);margin-top:1px;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:all .18s;flex-shrink:0}
.ci:hover{border-color:var(--mg)}.ci.ck{background:var(--mg);border-color:var(--mg)}
.ci.ck::after{content:'';width:8px;height:4.5px;border-left:2.5px solid #fff;border-bottom:2.5px solid #fff;transform:rotate(-45deg) translate(0,-1px);display:block}
.fin-badge{display:inline-flex;align-items:center;gap:5px;background:var(--am-bg);border:.5px solid var(--am-b);border-radius:20px;padding:4px 12px;font-size:11px;font-weight:700;color:var(--am);margin-bottom:12px}
.nofin-badge{display:inline-flex;align-items:center;gap:5px;background:var(--tl-bg);border:.5px solid var(--tl-b);border-radius:20px;padding:4px 12px;font-size:11px;font-weight:700;color:var(--tl);margin-bottom:12px}
.email-edit{width:100%;border:none;border-radius:0;padding:14px 16px;font-size:12px;font-family:'SF Mono','Fira Mono',monospace;line-height:1.7;color:var(--text);background:var(--bg);resize:vertical;min-height:260px;outline:none}
.email-edit:focus{background:#fdfcff}
.send-btn{background:#1a73e8;color:#fff;border:none;border-radius:var(--rs);padding:11px 22px;font-size:13px;font-weight:700;cursor:pointer;font-family:inherit;display:flex;align-items:center;gap:7px;transition:opacity .15s}
.send-btn:hover{opacity:.88}
/* ── guide tab ── */
.guide-body{padding:1.75rem 2rem;background:var(--bg);min-height:200px}
.g-section{margin-bottom:1.75rem}
.g-title{font-size:10px;font-weight:800;color:var(--mg);text-transform:uppercase;letter-spacing:.09em;margin-bottom:12px;display:flex;align-items:center;gap:8px}
.g-title::after{content:'';flex:1;height:1.5px;background:var(--mg-bg)}
.g-intro{font-size:13px;line-height:1.75;color:var(--text2);margin-bottom:12px}
.g-intro strong{color:var(--text);font-weight:700}
.g-flow{display:flex;flex-direction:column;gap:0}
.g-step{display:flex;gap:14px;position:relative;padding-bottom:16px}
.g-step:last-child{padding-bottom:0}
.g-step:not(:last-child)::after{content:'';position:absolute;left:13px;top:30px;bottom:0;width:2px;background:var(--mg-bg)}
.g-num{width:28px;height:28px;min-width:28px;border-radius:50%;background:var(--mg);color:#fff;display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:800;flex-shrink:0;z-index:1}
.g-body{padding-top:4px}
.g-body h3{font-size:13px;font-weight:700;color:var(--text);margin-bottom:3px}
.g-body p{font-size:12px;color:var(--text2);line-height:1.6}
.g-body p strong{color:var(--text);font-weight:600}
.g-case-grid{display:grid;grid-template-columns:1fr 1fr;gap:8px}
.g-case{background:var(--bg2);border:1px solid var(--border2);border-radius:var(--rs);padding:11px 14px 11px 17px;position:relative;overflow:hidden}
.g-case::before{content:'';position:absolute;left:0;top:0;bottom:0;width:4px}
.g-case.c-bl::before{background:var(--bl)}.g-case.c-am::before{background:var(--am)}
.g-case.c-rd::before{background:var(--rd)}.g-case.c-mg::before{background:var(--mg)}.g-case.c-tl::before{background:var(--tl)}
.g-case h4{font-size:12px;font-weight:700;color:var(--text);margin-bottom:3px}
.g-case p{font-size:11px;color:var(--text2);line-height:1.45;margin-bottom:5px}
.g-policy-list{display:flex;flex-direction:column;gap:8px}
.g-policy{background:var(--bg2);border:.5px solid var(--border);border-radius:var(--rs);padding:11px 14px;font-size:12px;color:var(--text2);line-height:1.6}
.g-policy strong{color:var(--text);font-weight:700}
.g-actors{display:flex;flex-direction:column;gap:8px}
.g-actor{display:flex;gap:12px;align-items:flex-start;background:var(--bg2);border:1px solid var(--border);border-radius:var(--rs);padding:11px 14px}
.g-actor-icon{font-size:18px;flex-shrink:0;margin-top:1px}
.g-actor-name{font-size:13px;font-weight:700;color:var(--text);margin-bottom:2px}
.g-actor-role{font-size:12px;color:var(--text2);line-height:1.5}
.g-ref{display:flex;flex-direction:column;gap:0;border:1px solid var(--border);border-radius:var(--r);overflow:hidden}
.g-ref-item{display:flex;gap:12px;align-items:flex-start;padding:10px 14px;font-size:12px;color:var(--text);line-height:1.5;border-bottom:.5px solid var(--border)}
.g-ref-item:last-child{border-bottom:none}
.g-ref-item:nth-child(odd){background:var(--bg2)}
.g-ref-icon{width:20px;height:20px;min-width:20px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:800;flex-shrink:0;margin-top:1px}
.g-ref-icon.yes{background:var(--tl-bg);color:var(--tl)}
.g-ref-icon.no{background:var(--rd-bg);color:var(--rd)}
.g-tips{display:grid;grid-template-columns:1fr 1fr;gap:8px}
.g-tip{background:var(--bg2);border:1px solid var(--border);border-radius:var(--rs);padding:12px 14px}
.g-tip-icon{font-size:18px;margin-bottom:6px}
.g-tip h4{font-size:12px;font-weight:700;color:var(--text);margin-bottom:4px}
.g-tip p{font-size:11px;color:var(--text2);line-height:1.55}
.g-footer{text-align:center;font-size:11px;color:var(--text3);margin-top:1.5rem;padding-top:1rem;border-top:.5px solid var(--border)}
.g-footer span{color:var(--mg);font-weight:700}
/* ── guide toggle ── */
.guide-toggle{display:flex;align-items:center;justify-content:space-between;margin-top:14px;padding:11px 16px;background:var(--ink);border-radius:var(--rs);cursor:pointer;font-size:13px;font-weight:700;color:rgba(255,255,255,.85);transition:background .15s;user-select:none}
.guide-toggle:hover{background:#2a1845}
#guideArrow{font-size:16px;transition:transform .25s}
#guideContent{margin-top:2px;border:1.5px solid var(--border2);border-radius:var(--rs);overflow:hidden}
.g-block{padding:1rem 1.25rem;border-bottom:1px solid var(--border)}
.g-block:last-child{border-bottom:none}
.g-label{font-size:10px;font-weight:800;color:var(--mg);text-transform:uppercase;letter-spacing:.08em;margin-bottom:10px;display:flex;align-items:center;gap:6px}
.g-label::after{content:'';flex:1;height:1px;background:var(--mg-bg)}
.g-flow{display:flex;flex-direction:column;gap:10px}
.g-step{display:flex;gap:10px;align-items:flex-start;font-size:12px;color:var(--text2);line-height:1.55}
.g-step .g-num{width:22px;height:22px;min-width:22px;border-radius:50%;background:var(--mg);color:#fff;display:flex;align-items:center;justify-content:center;font-size:10px;font-weight:800;flex-shrink:0;margin-top:1px}
.g-step .g-text strong{color:var(--text);font-weight:700}
.g-ref{display:flex;flex-direction:column;gap:0}
.g-ref-item{display:flex;gap:10px;align-items:flex-start;font-size:12px;color:var(--text2);padding:6px 0;border-bottom:.5px solid var(--border);line-height:1.5}
.g-ref-item:last-child{border-bottom:none}
.g-ref-item strong{color:var(--text);font-weight:700}
.g-yes{width:20px;height:20px;min-width:20px;border-radius:50%;background:var(--tl-bg);color:var(--tl);display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:800;flex-shrink:0;margin-top:1px}
.g-no{width:20px;height:20px;min-width:20px;border-radius:50%;background:var(--rd-bg);color:var(--rd);display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:800;flex-shrink:0;margin-top:1px}
.g-actors{display:flex;flex-direction:column;gap:8px}
.g-actor{display:flex;gap:10px;align-items:flex-start;font-size:12px;color:var(--text2);line-height:1.5}
.g-icon{font-size:16px;flex-shrink:0}
.g-actor strong{color:var(--text);font-weight:700}
.g-tips{display:grid;grid-template-columns:1fr 1fr;gap:8px}
.g-tip{display:flex;gap:8px;align-items:flex-start;font-size:12px;color:var(--text2);line-height:1.5;background:var(--bg2);border-radius:var(--rs);padding:9px 11px}
.g-tip strong{color:var(--text);font-weight:700}
</style>
</head>
<body>
<div class="app">

<div class="hdr">
  <div class="hdr-logo">
    <svg width="44" height="44" viewBox="0 0 44 44" fill="none">
      <rect width="44" height="44" rx="10" fill="rgba(255,255,255,0.12)"/>
      <circle cx="20" cy="20" r="10" stroke="#e040a0" stroke-width="3" fill="none"/>
      <line x1="27.5" y1="27.5" x2="35" y2="35" stroke="#e040a0" stroke-width="3" stroke-linecap="round"/>
      <path d="M16 17 Q20 14 24 17 Q28 20 24 23 Q20 26 16 23 Z" fill="#e040a0" opacity=".25"/>
      <circle cx="20" cy="20" r="4" fill="#e040a0"/>
    </svg>
  </div>
  <div class="hdr-title">
    <h1>AiFonso</h1>
    <p>Billing Assistant · Doofinder CX</p>
  </div>
  <div class="hdr-badge">Billing AI</div>
</div>



<!-- ══ ASISTENTE ══ -->
<div class="body">
<!-- progress -->
<div class="prog" id="PROG">
  <div class="pstep on" id="p0"><div class="pc">1</div><div class="pl"></div></div>
  <div class="pstep" id="p1"><div class="pc">2</div><div class="pl"></div></div>
  <div class="pstep" id="p2"><div class="pc">3</div><div class="pl"></div></div>
  <div class="pstep" id="p3"><div class="pc">4</div><div class="pl"></div></div>
  <div class="pstep" id="p4"><div class="pc">5</div></div>
</div>

<!-- ══ S0: TIPO DE CASO ══ -->
<div class="scr on" id="s0">
  <div class="slbl">¿Cuál es el caso?</div>
  <div class="policy"><strong>Política general:</strong> La suscripción se cancela al final del periodo de facturación actual (mensual o anual). No se realizan reembolsos por periodos no utilizados salvo excepción aprobada internamente.</div>
  <div class="case-grid">
    <button class="case-card c-bl" onclick="selectCase('discount_new')">
      <span class="ct">Descuento nuevo</span>
      <span class="cd">Acordado con el cliente, hay que crearlo y aplicarlo en el Admin Panel</span>
      <span class="ctag t-tl">Sin Finance</span>
    </button>
    <button class="case-card c-am" onclick="selectCase('cobro_exceso')">
      <span class="ct">Cobro en exceso</span>
      <span class="cd">Coupon ended, plan change o subida de precio — se cobró de más</span>
      <span class="ctag t-am">Mensual o anual</span>
    </button>
    <button class="case-card c-rd" onclick="selectCase('cancel_late')">
      <span class="ct">Cancelación tardía</span>
      <span class="cd">Se olvidó cancelar, intentó cancelar, quitó la app...</span>
      <span class="ctag t-rd">Evaluar compensación</span>
    </button>
    <button class="case-card c-mg" onclick="selectCase('billing_data')">
      <span class="ct">Cambio de datos de facturación</span>
      <span class="cd">El cliente quiere corregir datos en una factura ya emitida</span>
      <span class="ctag t-mg">Finance emite rectificativa</span>
    </button>
    <button class="case-card c-tl" onclick="selectCase('shopify_billing')">
      <span class="ct">Shopify Billing</span>
      <span class="cd">Desconectar Shopify Billing para aplicar descuentos o cambiar método de pago</span>
      <span class="ctag t-tl">Sin Finance</span>
    </button>
  </div>

  <!-- ══ GUÍA COLAPSABLE ══ -->
  <div class="guide-toggle" onclick="toggleGuide()">
    <span>📖 Guía de uso</span>
    <span id="guideArrow">▾</span>
  </div>
  <div id="guideContent" style="display:none">

    <div class="g-block">
      <div class="g-label">Los 5 pasos</div>
      <div class="g-flow">
        <div class="g-step"><div class="g-num">1</div><div class="g-text"><strong>Elige el tipo de caso</strong> — cada tarjeta indica si el caso requiere o no email a Finance.</div></div>
        <div class="g-step"><div class="g-num">2</div><div class="g-text"><strong>Rellena los datos del cliente</strong> — nombre, Account Code, email y factura. En cobro en exceso mensual aparece la calculadora con el texto listo para el cliente.</div></div>
        <div class="g-step"><div class="g-num">3</div><div class="g-text"><strong>Lee el proceso paso a paso</strong> — qué hacer, en qué orden y quién actúa.</div></div>
        <div class="g-step"><div class="g-num">4</div><div class="g-text"><strong>Completa el checklist</strong> — obligatorio antes de enviar a Finance. Evita errores en el correo.</div></div>
        <div class="g-step"><div class="g-num">5</div><div class="g-text"><strong>Revisa y envía el email</strong> — editable antes de enviar. "Enviar a Finance" lo abre en Gmail listo.</div></div>
      </div>
    </div>

    <div class="g-block">
      <div class="g-label">¿Cuándo envío email a Finance?</div>
      <div class="g-ref">
        <div class="g-ref-item"><span class="g-yes">✓</span><div><strong>Cobro en exceso anual</strong> — rectificativa + crédito + devolución de diferencia</div></div>
        <div class="g-ref-item"><span class="g-no">✗</span><div><strong>Cobro en exceso mensual</strong> — descuento escalonado, sin Finance</div></div>
        <div class="g-ref-item"><span class="g-yes">✓</span><div><strong>Cancelación tardía con compensación</strong> — rectificativa + devolución</div></div>
        <div class="g-ref-item"><span class="g-no">✗</span><div><strong>Cancelación tardía sin compensación</strong> — solo cancelar en Admin Panel</div></div>
        <div class="g-ref-item"><span class="g-yes">✓</span><div><strong>Cambio de datos de facturación</strong> — rectificativa + nueva factura</div></div>
        <div class="g-ref-item"><span class="g-no">✗</span><div><strong>Descuento nuevo</strong> — solo Admin Panel</div></div>
        <div class="g-ref-item"><span class="g-no">✗</span><div><strong>Shopify Billing</strong> — solo conseguir que el cliente acepte la nueva oferta</div></div>
      </div>
    </div>

    <div class="g-block">
      <div class="g-label">Quién hace qué</div>
      <div class="g-actors">
        <div class="g-actor"><span class="g-icon">👤</span><div><strong>Tú (CX)</strong> — gestionas el caso, comunicas al cliente, ejecutas en Admin Panel, envías a Finance.</div></div>
        <div class="g-actor"><span class="g-icon">💼</span><div><strong>Finance</strong> — emite rectificativas y ejecuta devoluciones solo con los datos que tú le mandas.</div></div>
        <div class="g-actor"><span class="g-icon">🛠</span><div><strong>Admin Panel</strong> — creas ofertas, cancelas suscripciones, activas trials. La mayoría de acciones las haces tú directamente.</div></div>
        <div class="g-actor"><span class="g-icon">📊</span><div><strong>Silvia/Carmen → Rafa (Data)</strong> — solo en descuentos no aplicados a tiempo, para corregir el MRR.</div></div>
      </div>
    </div>

    <div class="g-block">
      <div class="g-label">Consejos rápidos</div>
      <div class="g-tips">
        <div class="g-tip"><span class="g-icon">✅</span><div><strong>Checklist siempre</strong> — el email a Finance no puede tener errores.</div></div>
        <div class="g-tip"><span class="g-icon">✏️</span><div><strong>El email es editable</strong> — añade detalles antes de enviarlo.</div></div>
        <div class="g-tip"><span class="g-icon">🔄</span><div><strong>Nuevo caso al terminar</strong> — pulsa ↺ para limpiar todos los campos.</div></div>
        <div class="g-tip"><span class="g-icon">📎</span><div><strong>Direct Debit</strong> — el cliente debe enviar certificado de titularidad bancaria.</div></div>
        <div class="g-tip"><span class="g-icon">🏦</span><div><strong>Shopify</strong> — verifica siempre que la moneda esté en EUR en Account Settings.</div></div>
        <div class="g-tip"><span class="g-icon">🚫</span><div><strong>Descuento escalonado</strong> — badge verde = sin Finance, no hay email que enviar.</div></div>
      </div>
    </div>

  </div><!-- /guideContent -->
</div>

<!-- ══ S1: DATOS + CALCULADORA ══ -->
<div class="scr" id="s1">
  <div class="slbl" id="s1Label">Datos del caso</div>

  <!-- datos base siempre -->
  <div class="card">
    <div class="gf3">
      <div><div class="fl">Cliente</div><input id="cn" placeholder="Acme Corp"></div>
      <div><div class="fl">Account Code</div><input id="accCode" placeholder="8e9441c6-..."></div>
      <div><div class="fl">Email cliente</div><input id="emailClient" placeholder="cliente@empresa.com" type="email"></div>
    </div>
    <div class="gf2">
      <div><div class="fl">Nº de factura</div><input id="inv" placeholder="INV-0000"></div>
      <div><div class="fl">Notas internas (opcional)</div></div>
    </div>
    <textarea id="nt" rows="2" placeholder="Contexto adicional..."></textarea>
  </div>

  <!-- ── DESCUENTO NUEVO ── -->
  <div id="blk_discount_new" style="display:none">
    <div class="al a-bl"><span class="al-icon">ℹ</span><div class="al-body"><strong>Dos pasos en el Admin Panel</strong>Primero crear la oferta, luego aceptarla de inmediato para que no caduque.</div></div>
  </div>

  <!-- ── COBRO EN EXCESO ── -->
  <div id="blk_cobro_exceso" style="display:none">
    <div class="slbl">Motivo del cobro en exceso</div>
    <div class="case-grid" style="margin-bottom:14px">
      <button class="case-card c-am" id="ex_coupon" onclick="setExcessReason('coupon')"><span class="ct">Coupon ended</span><span class="cd">El descuento caducó y se cobró el precio completo</span></button>
      <button class="case-card c-bl" id="ex_plan" onclick="setExcessReason('plan')"><span class="ct">Plan change / subida de precio</span><span class="cd">Doofinder cambió los planes y el cliente se queja del nuevo precio</span></button>
    </div>
    <div class="slbl">Tipo de suscripción</div>
    <div class="tog-row">
      <button class="tog" id="tbM" onclick="setPeriod('monthly')">📅 Mensual</button>
      <button class="tog" id="tbA" onclick="setPeriod('annual')">📆 Anual</button>
    </div>

    <!-- MENSUAL -->
    <div id="blk_monthly" style="display:none">
      <div class="al a-bl"><span class="al-icon">ℹ</span><div class="al-body"><strong>Compensación con descuento escalonado — sin factura rectificativa</strong>Negocia el precio final para los próximos 12 meses. La suma de los meses de compensación + meses al descuento final debe cubrir los 12 meses del año.</div></div>
      <div class="calc-section">
        <h3>🧮 Calculadora de compensación</h3>
        <div class="gf3" style="margin-bottom:14px">
          <div><div class="fl">Plan</div>
            <select id="cPlan" onchange="onPlanChange()">
              <option value="49">Basic — 49 €/mes</option>
              <option value="149" selected>Pro — 149 €/mes</option>
              <option value="349">Advanced — 349 €/mes</option>
              <option value="custom">Precio personalizado</option>
            </select>
          </div>
          <div id="custWrap" style="display:none"><div class="fl">Precio tarifa (€/mes)</div><input type="number" id="custPrice" placeholder="154.85" oninput="cUpd()"></div>
          <div><div class="fl">Meses cobrados de más</div><input type="number" id="ninv" value="1" min="1" oninput="cUpd()"></div>
        </div>
        <div class="rr"><span class="rl">Descuento final acordado</span><input type="range" id="cDisc" min="0" max="95" value="30" step="1" oninput="cUpd()"><span class="rv" id="dVal">30%</span></div>
        <div class="rr"><span class="rl">Meses de compensación</span><input type="range" id="cMon" min="1" max="12" value="3" step="1" oninput="cUpd()"><span class="rv" id="mVal">3</span></div>
        <div class="metrics">
          <div class="met"><div class="mv" id="mPr">—</div><div class="ml">Precio tarifa</div></div>
          <div class="met"><div class="mv" id="mFp">—</div><div class="ml">Precio final acordado</div></div>
          <div class="met hi"><div class="mv" id="mRef">—</div><div class="ml">Importe a compensar</div></div>
        </div>
        <div class="metrics">
          <div class="met acc"><div class="mv" id="mFm">—</div><div class="ml">Precio primeros <span id="mMonLbl">3</span> meses</div></div>
          <div class="met acc"><div class="mv" id="mFd">—</div><div class="ml">Dto. primeros meses</div></div>
          <div class="met"><div class="mv" id="mRm">—</div><div class="ml">Meses después al dto. final</div></div>
        </div>
      </div>
      <div id="clientTextWrap" style="display:none">
        <div class="slbl">Texto para el cliente</div>
        <div class="cb">
          <div class="cb-hdr"><span class="cbl">✉ Copiar y enviar al cliente</span><button onclick="copyBlock('clientText',this)">Copiar</button></div>
          <div class="cb-body" id="clientText"></div>
        </div>
      </div>
    </div>

    <!-- ANUAL -->
    <div id="blk_annual" style="display:none">
      <div class="al a-am"><span class="al-icon">⚠</span><div class="al-body"><strong>Plan anual — proceso de renegociación</strong>Finance emite factura rectificativa por el importe total cobrado. El importe acordado se añade como crédito en la cuenta del cliente para la nueva oferta. La diferencia se devuelve al cliente.</div></div>
      <div class="card">
        <div class="gf2" style="margin-bottom:10px">
          <div><div class="fl">Importe anual cobrado (€)</div><input id="annCharged" type="number" placeholder="4800" oninput="annUpd()"></div>
          <div><div class="fl">Importe anual acordado (€)</div><input id="annCorrect" type="number" placeholder="2880" oninput="annUpd()"></div>
        </div>
        <div id="annResult" style="display:none" class="result-box"></div>
        <div style="margin-bottom:10px">
          <div class="fl">Método de pago del cliente</div>
          <select id="annPm" onchange="annPmChange()">
            <option value="">— Seleccionar —</option>
            <option value="card">Credit Card</option>
            <option value="paypal">PayPal</option>
            <option value="direct_debit">Direct Debit</option>
          </select>
        </div>
        <div id="annDdWrap" style="display:none">
          <div class="al a-am" style="margin-bottom:8px"><span class="al-icon">⚠</span><div class="al-body"><strong>Direct Debit — certificado requerido</strong>Solicitar al cliente el certificado de titularidad bancaria y adjuntarlo al email a Finance (PDF o imagen).</div></div>
          <div class="fl" style="margin-bottom:5px">Certificado de titularidad bancaria</div>
          <input type="file" id="annCert" accept=".pdf,.jpg,.jpeg,.png" style="font-size:12px;padding:7px 10px;background:var(--bg2)">
          <div id="annCertName" style="font-size:11px;color:var(--mg);margin-top:4px;font-weight:600"></div>
        </div>
      </div>
    </div>
  </div>

  <!-- ── CANCELACIÓN TARDÍA ── -->
  <div id="blk_cancel_late" style="display:none">
    <div class="slbl">Motivo de la cancelación tardía</div>
    <div class="case-grid" style="margin-bottom:14px">
      <button class="case-card c-rd" id="clF" onclick="setCancelReason('forgot')"><span class="ct">Se le olvidó cancelar</span><span class="cd">O no sabía cuándo vencía</span></button>
      <button class="case-card c-am" id="clE" onclick="setCancelReason('failed')"><span class="ct">Intentó cancelar y no funcionó</span><span class="cd">Error técnico o confusión</span></button>
      <button class="case-card c-bl" id="clA" onclick="setCancelReason('app')"><span class="ct">Quitó la app y pensó que era suficiente</span><span class="cd">No sabía que la suscripción seguía activa</span></button>
    </div>
    <div class="slbl">¿Se aprueba compensación?</div>
    <div class="tog-row">
      <button class="tog" id="clNo" onclick="setCancelComp('no')">✕ No — política estándar</button>
      <button class="tog" id="clYes" onclick="setCancelComp('yes')">✓ Sí — excepción aprobada</button>
    </div>
    <div id="blk_cancel_refund" style="display:none">
      <div class="al a-rd"><span class="al-icon">⚠</span><div class="al-body"><strong>Devolución de dinero aprobada</strong>Finance necesita el método de pago para ejecutar la devolución.</div></div>
      <div class="slbl">Método de pago</div>
      <div class="opt-grid">
        <button class="opt" onclick="pickPm('card',this)"><span class="ot">Tarjeta</span><span class="od">Stripe / crédito</span></button>
        <button class="opt" onclick="pickPm('paypal',this)"><span class="ot">PayPal</span></button>
        <button class="opt" onclick="pickPm('direct_debit',this)"><span class="ot">Direct Debit</span><span class="od">GoCardless</span></button>
        <button class="opt" onclick="pickPm('transfer',this)"><span class="ot">Transferencia</span><span class="od">Santander</span></button>
        <button class="opt" onclick="pickPm('shopify',this)"><span class="ot">Shopify Billing</span></button>
      </div>
      <div id="ddNote" style="display:none" class="al a-am"><span class="al-icon">⚠</span><div class="al-body"><strong>Direct Debit</strong>Solicitar al cliente un <strong>certificado de titularidad bancaria</strong> antes de proceder.</div></div>
      <div class="card">
        <div class="gf2">
          <div><div class="fl">Importe cobrado (€)</div><input id="clAc" type="number" placeholder="349" oninput="clRefUpd()"></div>
          <div><div class="fl">Importe a devolver (€)</div><input id="clAr" type="number" placeholder="349" oninput="clRefUpd()"></div>
        </div>
        <div id="clRefResult" style="display:none" class="result-box"></div>
      </div>
    </div>
  </div>

  <!-- ── BILLING DATA ── -->
  <div id="blk_billing_data" style="display:none">
    <div class="al a-mg"><span class="al-icon">ℹ</span><div class="al-body"><strong>Proceso</strong>El cliente actualiza los datos en el Admin Panel. CX solicita a Finance la factura rectificativa y la emisión de la nueva factura con los datos actualizados.</div></div>
    <div class="card">
      <div class="gf2" style="margin-bottom:10px">
        <div>
          <div class="fl">¿Cuántas facturas hay que rectificar?</div>
          <select id="bdCount" onchange="buildBdInvoices()">
            <option value="0">— Seleccionar —</option>
            <option value="1">1 factura</option>
            <option value="2">2 facturas</option>
            <option value="3">3 facturas</option>
            <option value="4">4 facturas</option>
            <option value="5">5 facturas</option>
          </select>
        </div>
      </div>
      <div id="bdInvoiceFields"></div>
    </div>
    <div class="card">
      <div class="fl" style="margin-bottom:10px">Nuevos datos de facturación (tal y como aparecen en el admin)</div>
      <div class="gf2">
        <div><div class="fl">Company Name</div><input id="bdCompany" placeholder="Acme Corp S.L."></div>
        <div><div class="fl">VAT ID</div><input id="bdVat" placeholder="ESB12345678"></div>
      </div>
      <div class="gf2">
        <div><div class="fl">Contact Person</div><input id="bdContact" placeholder="Juan García"></div>
        <div><div class="fl">Email</div><input id="bdEmail" placeholder="facturacion@empresa.com"></div>
      </div>
      <div><div class="fl">Invoicing Address</div><input id="bdAddress" placeholder="Calle Mayor 1, 28001 Madrid, España"></div>
    </div>
  </div>

  <!-- ── SHOPIFY BILLING ── -->
  <div id="blk_shopify_billing" style="display:none">
    <div class="al a-tl"><span class="al-icon">ℹ</span><div class="al-body"><strong>Solo cambio de medio de pago — sin más acciones requeridas</strong>Desconectar Shopify Billing desde el Admin Panel y hacer una oferta personalizada. El cliente la acepta con su nuevo medio de pago.<br><br>⚠ Verificar que la moneda del cliente en Account Settings esté en <strong>EUR</strong> (Shopify suele facturar en USD).</div></div>
  </div>

  <div class="brow">
    <button class="bs" onclick="go(0)">← Atrás</button>
    <button class="bp" onclick="goProc()">Ver proceso →</button>
  </div>
</div>

<!-- ══ S2: PROCESO ══ -->
<div class="scr" id="s2">
  <div id="finBadge" style="margin-bottom:12px"></div>
  <div class="slbl">Proceso a seguir</div>
  <div id="proc"></div>
  <div class="brow">
    <button class="bs" onclick="go(1)">← Atrás</button>
    <button class="bp" onclick="goChecklist()">Ir al checklist de verificación →</button>
  </div>
</div>

<!-- ══ S3: CHECKLIST ══ -->
<div class="scr" id="s3">
  <div class="slbl">Checklist de verificación</div>
  <div class="al a-am"><span class="al-icon">⚠</span><div class="al-body"><strong>Verifica todo antes de enviar a Finance</strong>No puede haber errores en el correo. Completa todos los puntos antes de continuar.</div></div>
  <div class="card"><ul class="cl" id="ck"></ul></div>
  <div class="brow">
    <button class="bs" onclick="go(2)">← Atrás</button>
    <button class="bp" id="toFinanceBtn" onclick="goEmail()" style="display:none">Generar email para Finance →</button>
    <button class="bp" id="doneBtn" onclick="restart()" style="display:none">Caso completado ✓</button>
  </div>
</div>

<!-- ══ S4: FINANCE EMAIL ══ -->
<div class="scr" id="s4">
  <div class="slbl">Email para Finance</div>
  <div class="al a-bl" style="margin-bottom:14px">
    <span class="al-icon">✏️</span>
    <div class="al-body"><strong>Revisa y edita antes de enviar</strong>Puedes modificar el texto directamente en el recuadro. Cuando esté listo, pulsa "Enviar a Finance".</div>
  </div>
  <div class="cb" style="overflow:visible">
    <div class="cb-hdr">
      <span class="cbl">📨 finance@doofinder.com</span>
      <button onclick="copyEditedEmail(this)">Copiar</button>
    </div>
    <textarea class="email-edit" id="financeEmailEdit" spellcheck="false"></textarea>
  </div>
  <div id="certAttachReminder" style="display:none;margin-bottom:12px" class="al a-am">
    <span class="al-icon">📎</span>
    <div class="al-body"><strong>Adjunto requerido al enviar</strong><span id="certFileName" style="font-size:12px;display:block;margin-top:2px"></span></div>
  </div>
  <div class="brow">
    <button class="bs" onclick="go(3)">← Atrás</button>
    <div style="display:flex;gap:8px">
      <button class="bp" onclick="restart()">Nuevo caso ↺</button>
      <button class="send-btn" onclick="sendEmail()">
        <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><line x1="22" y1="2" x2="11" y2="13"/><polygon points="22 2 15 22 11 13 2 9 22 2"/></svg>
        Enviar a Finance
      </button>
    </div>
</div>
</div>

</div><!-- /body -->
</div><!-- /app -->

<script>

function toggleGuide(){
  var c=document.getElementById('guideContent');
  var a=document.getElementById('guideArrow');
  var open=c.style.display==='none'||c.style.display==='';
  c.style.display=open?'block':'none';
  a.style.transform=open?'rotate(180deg)':'rotate(0deg)';
}

window.ST={ct:'',pm:'',period:'',cancelReason:'',cancelComp:'',excessReason:''};
window.C={price:0,disc:0,months:0,inv:1,fp:0,toRef:0,fmp:0,fmd:0,rem:0};

var PL={card:'Tarjeta de crédito',paypal:'PayPal',direct_debit:'Direct Debit (GoCardless)',shopify:'Shopify Billing',transfer:'Transferencia bancaria (Santander ES63 0049 5109 4720 1619 7279)'};
var CANCEL_REASON_LABEL={forgot:'El cliente se olvidó cancelar.',failed:'El cliente intentó cancelar y no le funcionó (error técnico o confusión en el proceso).',app:'El cliente quitó la app pensando que era suficiente para cancelar.'};
var EXCESS_REASON_LABEL={coupon:'Coupon ended — el descuento del cliente caducó y se le cobró el precio completo.',plan:'Plan change / subida de precio — Doofinder cambió los planes y el cliente fue cobrado con el nuevo precio sin haberlo acordado.'};

function setProg(n){
  for(var i=0;i<5;i++){
    var el=document.getElementById('p'+i);if(!el)return;
    el.className='pstep'+(i<n?' done':i===n?' on':'');
  }
}
function go(n){
  document.querySelectorAll('.scr').forEach(function(s){s.classList.remove('on');});
  document.getElementById('s'+n).classList.add('on');
  setProg(n);window.scrollTo(0,0);
}

var ALL_BLKS=['blk_discount_new','blk_cobro_exceso','blk_cancel_late','blk_billing_data','blk_shopify_billing'];
function selectCase(ct){
  ST.ct=ct;
  ALL_BLKS.forEach(function(id){document.getElementById(id).style.display='none';});
  document.getElementById('blk_'+ct).style.display='block';
  go(1);
}

function setExcessReason(r){
  ST.excessReason=r;
  ['ex_coupon','ex_plan'].forEach(function(id){document.getElementById(id).classList.remove('sel');});
  document.getElementById('ex_'+r).classList.add('sel');
}

function setPeriod(p){
  ST.period=p;
  document.getElementById('tbM').classList.toggle('sel',p==='monthly');
  document.getElementById('tbA').classList.toggle('sel',p==='annual');
  document.getElementById('blk_monthly').style.display=p==='monthly'?'block':'none';
  document.getElementById('blk_annual').style.display=p==='annual'?'block':'none';
  if(p==='monthly')cUpd();
}
function setCancelReason(r){
  ST.cancelReason=r;
  ['clF','clE','clA'].forEach(function(id){document.getElementById(id).classList.remove('sel');});
  var m={forgot:'clF',failed:'clE',app:'clA'};
  document.getElementById(m[r]).classList.add('sel');
}
function setCancelComp(v){
  ST.cancelComp=v;
  document.getElementById('clNo').classList.toggle('sel',v==='no');
  document.getElementById('clYes').classList.toggle('sel',v==='yes');
  document.getElementById('blk_cancel_refund').style.display=v==='yes'?'block':'none';
}
function pickPm(val,el){
  ST.pm=val;
  document.querySelectorAll('#blk_cancel_refund .opt').forEach(function(b){b.classList.remove('sel');});
  el.classList.add('sel');
  document.getElementById('ddNote').style.display=val==='direct_debit'?'flex':'none';
}
function clRefUpd(){
  var ac=parseFloat(document.getElementById('clAc').value)||0;
  var ar=parseFloat(document.getElementById('clAr').value)||0;
  var box=document.getElementById('clRefResult');
  if(ac>0&&ar>0){box.style.display='block';box.innerHTML='Importe a devolver: '+ar.toFixed(2)+' €';}
  else box.style.display='none';
}
function annUpd(){
  var ac=parseFloat(document.getElementById('annCharged').value)||0;
  var co=parseFloat(document.getElementById('annCorrect').value)||0;
  var d=ac-co;
  var box=document.getElementById('annResult');
  if(ac>0&&co>0&&d>0){
    box.style.display='block';
    box.innerHTML='<strong>Importe cobrado:</strong> '+ac.toFixed(2)+' € &nbsp;|&nbsp; <strong>Importe acordado (crédito):</strong> '+co.toFixed(2)+' € &nbsp;|&nbsp; <strong>A devolver al cliente:</strong> '+d.toFixed(2)+' €';
  } else box.style.display='none';
}
function annPmChange(){
  var val=document.getElementById('annPm').value;
  ST.annPm=val;
  document.getElementById('annDdWrap').style.display=val==='direct_debit'?'block':'none';
  document.getElementById('annCertName').textContent='';
}
document.addEventListener('change',function(e){
  if(e.target&&e.target.id==='annCert'){
    var f=e.target.files[0];
    document.getElementById('annCertName').textContent=f?'📎 '+f.name:'';
  }
});

function buildBdInvoices(){
  var n=parseInt(document.getElementById('bdCount').value)||0;
  var c=document.getElementById('bdInvoiceFields');
  c.innerHTML='';
  for(var i=1;i<=n;i++){
    var d=document.createElement('div');
    d.style.marginBottom='8px';
    d.innerHTML='<div class="fl">Factura '+i+'</div><input id="bdInv'+i+'" placeholder="INV-000'+i+'">';
    c.appendChild(d);
  }
}

function onPlanChange(){
  document.getElementById('custWrap').style.display=document.getElementById('cPlan').value==='custom'?'block':'none';
  cUpd();
}
function cUpd(){
  var pv=document.getElementById('cPlan').value;
  var price=pv==='custom'?(parseFloat(document.getElementById('custPrice').value)||0):parseFloat(pv);
  var disc=parseInt(document.getElementById('cDisc').value)/100;
  var months=parseInt(document.getElementById('cMon').value);
  var inv=parseInt(document.getElementById('ninv').value)||1;
  document.getElementById('dVal').textContent=Math.round(disc*100)+'%';
  document.getElementById('mVal').textContent=months;
  document.getElementById('mMonLbl').textContent=months;
  if(!price||price<=0){document.getElementById('clientTextWrap').style.display='none';return;}
  var fp=price*(1-disc);
  var toRef=(price-fp)*inv;
  var fmp=fp-(toRef/months);
  var fmd=fmp>0?1-(fmp/price):1;
  var rem=12-inv-months;if(rem<0)rem=0;
  C={price:price,disc:disc,months:months,inv:inv,fp:fp,toRef:toRef,fmp:fmp,fmd:fmd,rem:rem};
  document.getElementById('mPr').textContent=price.toFixed(2)+' €';
  document.getElementById('mFp').textContent=fp.toFixed(2)+' €';
  document.getElementById('mRef').textContent=toRef.toFixed(2)+' €';
  document.getElementById('mFm').textContent=fmp>0?fmp.toFixed(2)+' €':'0 €';
  document.getElementById('mFd').textContent=fmp>0?Math.round(fmd*100)+'%':'100%';
  document.getElementById('mRm').textContent=rem+' meses';
  var fd=fmp>0?Math.round(fmd*100):100;var d=Math.round(disc*100);
  var txt='Hemos detectado un error en tu '+(inv===1?'última factura':'últimas '+inv+' facturas')+' y queremos compensarte de la siguiente manera:\n\n'
    +'Durante los próximos '+months+' meses aplicaremos un descuento del '+fd+'% sobre tu plan, lo que equivale a '+fmp.toFixed(2)+' €/mes.\n\n'
    +'A partir del mes '+(months+1)+', el descuento quedará en el '+d+'% ('+fp.toFixed(2)+' €/mes)'+(rem>0?', que se mantendrá durante los siguientes '+rem+' meses.':'.')+'\n\n'
    +'De esta manera compensamos los '+toRef.toFixed(2)+' € cobrados de más.\n\n'
    +'Disculpa las molestias. Quedo a tu disposición para cualquier duda.';
  var el=document.getElementById('clientText');el.textContent=txt;el.dataset.txt=txt;
  document.getElementById('clientTextWrap').style.display='block';
}

function needsFinance(){
  var c=ST.ct;
  if(c==='discount_new')return false;
  if(c==='shopify_billing')return false;
  if(c==='cobro_exceso'&&ST.period==='monthly')return false;
  if(c==='cancel_late'&&ST.cancelComp==='no')return false;
  return true;
}

function act(n){return '<span class="atag">'+n+'</span>';}
function mkSteps(arr){
  var f=arr.filter(function(x){return x;});
  return '<div class="step-list">'+f.map(function(s,i){
    return '<div class="step-item"><div class="step-num">'+(i+1)+'</div><div class="step-body">'+s+'</div></div>';
  }).join('')+'</div>';
}

function goProc(){
  var c=ST.ct,h='';
  var nf=needsFinance();
  document.getElementById('finBadge').innerHTML=nf
    ?'<span class="fin-badge">📨 Este caso requiere email a Finance</span>'
    :'<span class="nofin-badge">✓ Este caso no requiere email a Finance</span>';

  if(c==='discount_new'){
    h+=mkSteps([
      '<strong>Crear la nueva oferta</strong> en el '+act('Admin Panel')+' con el precio y descuento acordados con el cliente.',
      '<strong>Aceptar la oferta inmediatamente</strong> — no esperar, puede caducar.',
      'Confirmar al cliente que el descuento está aplicado correctamente.',
    ]);
  }
  if(c==='cobro_exceso'){
    if(ST.period==='monthly'){
      h+='<div class="al a-bl" style="margin-bottom:12px"><span class="al-icon">ℹ</span><div class="al-body"><strong>Sin factura rectificativa</strong>La compensación es mediante descuento escalonado. No se requiere acción de Finance.</div></div>';
      h+=mkSteps([
        'Verificar el importe cobrado de más y las facturas afectadas.',
        'Negociar con el cliente el precio final para los próximos 12 meses.',
        'Calcular el descuento escalonado en la calculadora del paso anterior.',
        'Copiar el texto de compensación generado y enviarlo al cliente.',
        '<strong>Crear la nueva oferta</strong> en el '+act('Admin Panel')+' con el descuento acordado y <strong>aceptarla inmediatamente</strong>.',
        'Verificar que el cliente está suscrito correctamente al nuevo plan.',
      ]);
    } else {
      h+=mkSteps([
        'Verificar el importe anual cobrado y el importe acordado con el cliente.',
        'Avisar al cliente: se cancelará la suscripción actual y se creará una nueva con el precio correcto. Se pondrá un trial de 2-3 días para no perder el servicio.',
        'Cancelar la suscripción actual desde el '+act('Admin Panel')+'.',
        'Activar trial de 2-3 días.',
        'Crear la nueva oferta anual en el '+act('Admin Panel')+' con el precio acordado y solicitar al cliente que la acepte.',
        '<strong>Verificar que el cliente ha aceptado la nueva oferta.</strong>',
        'Enviar email a Finance: emite <strong>factura rectificativa por el importe total</strong> del exceso. No se emite factura nueva.',
      ]);
    }
  }
  if(c==='cancel_late'){
    if(ST.cancelComp==='no'){
      h+='<div class="al a-bl" style="margin-bottom:12px"><span class="al-icon">ℹ</span><div class="al-body"><strong>Sin compensación — sin email a Finance</strong>No hay factura rectificativa que emitir.</div></div>';
      h+=mkSteps([
        'Comunicar al cliente la política: la suscripción se cancela al final del periodo actual, sin reembolso por tiempo no utilizado.',
        'Cancelar la suscripción desde el '+act('Admin Panel')+' para que no se renueve.',
        'Confirmar al cliente la fecha efectiva de cancelación.',
      ]);
    } else {
      var ddS=ST.pm==='direct_debit'?'<strong>Direct Debit:</strong> el cliente debe aportar un <strong>certificado de titularidad bancaria</strong> antes de que Finance ejecute la devolución.':'';
      h+=mkSteps([
        'Cancelar la suscripción desde el '+act('Admin Panel')+'.',
        ddS,
        'Enviar email a Finance con el importe a devolver y el método de pago.',
        'Finance emite factura rectificativa y ejecuta la devolución al cliente.',
      ]);
    }
  }
  if(c==='billing_data'){
    h+=mkSteps([
      'Pedir al cliente que acceda a '+act('Admin Panel')+' → Account → Billing Information y actualice los datos correctos.',
      'Confirmar con el cliente que los datos han sido actualizados.',
      'Enviar email a Finance para que emitan la factura rectificativa y la nueva factura con los datos actualizados.',
    ]);
  }
  if(c==='shopify_billing'){
    h+='<div class="al a-tl" style="margin-bottom:12px"><span class="al-icon">✓</span><div class="al-body"><strong>Sin más acciones requeridas</strong>Solo hay que conseguir que el cliente acepte la nueva oferta con el medio de pago correcto.</div></div>';
    h+=mkSteps([
      '<strong>Desconectar Shopify Billing</strong> desde el '+act('Admin Panel')+'.',
      'Revisar la moneda del cliente en '+act('Account Settings')+' — asegurarse de que está en <strong>EUR</strong>.',
      'Preparar la oferta personalizada y enviarla al cliente.',
      'Pedir al cliente que <strong>acepte la oferta</strong> e introduzca su nuevo medio de pago.',
      '<strong>Verificar que el cliente ha aceptado correctamente.</strong>',
    ]);
  }
  document.getElementById('proc').innerHTML=h;
  go(2);
}

function goChecklist(){
  var c=ST.ct;
  var checks=[];
  if(c==='discount_new') checks=['Oferta creada en el Admin Panel','Oferta aceptada inmediatamente','Cliente notificado del descuento'];
  if(c==='cobro_exceso'){
    if(ST.period==='monthly') checks=['Importe cobrado de más verificado','Precio final negociado','Descuento escalonado calculado','Texto de compensación enviado al cliente','Nueva oferta creada y aceptada en Admin Panel','Cliente suscrito correctamente al nuevo plan'];
    else{
      checks=['Importes verificados (cobrado vs acordado)','Método de pago seleccionado'];
      var annPmNow=document.getElementById('annPm').value;
      if(annPmNow==='direct_debit')checks.push('Certificado de titularidad bancaria adjuntado');
      checks=checks.concat(['Cliente avisado del proceso','Suscripción cancelada en Admin Panel','Trial activado (2-3 días)','Nueva oferta anual aceptada por el cliente','Datos listos para el email a Finance']);
    }
  }
  if(c==='cancel_late'){
    if(ST.cancelComp==='no') checks=['Política comunicada al cliente','Suscripción cancelada en Admin Panel','Cliente confirmado de la fecha de cancelación'];
    else{
      checks=['Suscripción cancelada en Admin Panel'];
      if(ST.pm==='direct_debit')checks.push('Certificado de titularidad bancaria solicitado al cliente');
      checks=checks.concat(['Importe a devolver confirmado','Método de pago confirmado','Datos listos para el email a Finance']);
    }
  }
  if(c==='billing_data') checks=['Cliente ha actualizado datos en Admin Panel','Datos de facturación verificados por CX','Facturas a rectificar identificadas','Datos listos para el email a Finance'];
  if(c==='shopify_billing') checks=['Shopify Billing desconectado en Admin Panel','Moneda verificada (EUR) en Account Settings','Oferta personalizada preparada y enviada','Cliente ha aceptado la nueva oferta','Medio de pago del cliente verificado'];

  document.getElementById('ck').innerHTML=checks.map(function(x,i){
    return '<li><div class="ci" id="ci'+i+'" onclick="tck('+i+')"></div><span>'+x+'</span></li>';
  }).join('');

  var nf=needsFinance();
  document.getElementById('toFinanceBtn').style.display=nf?'block':'none';
  document.getElementById('doneBtn').style.display=nf?'none':'block';
  go(3);
}

function tck(i){document.getElementById('ci'+i).classList.toggle('ck');}

function goEmail(){
  var cn=document.getElementById('cn').value||'[Nombre cliente]';
  var emailCl=document.getElementById('emailClient').value||'[email cliente]';
  var accCode=document.getElementById('accCode').value||'[Account Code]';
  var inv=document.getElementById('inv').value||'[Nº factura]';
  var nt=document.getElementById('nt').value||'';
  var c=ST.ct;
  var body='';

  if(c==='cobro_exceso'&&ST.period==='annual'){
    var charged=parseFloat(document.getElementById('annCharged').value)||0;
    var correct=parseFloat(document.getElementById('annCorrect').value)||0;
    var diff=charged-correct;
    var annPmVal=document.getElementById('annPm').value;
    var annPmLabels={card:'Credit Card',paypal:'PayPal',direct_debit:'Direct Debit'};
    var pmLine=annPmVal?'Método de pago: '+(annPmLabels[annPmVal]||annPmVal)+'\n':'Método de pago: [por confirmar]\n';
    var certLine=annPmVal==='direct_debit'?'\n⚠ Adjunto: Certificado de titularidad bancaria del cliente.\n':'';
    var reasonLine=ST.excessReason?'Motivo: '+EXCESS_REASON_LABEL[ST.excessReason]+'\n':'';
    body='Asunto: Factura rectificativa — '+cn+'\n\n'
      +'Hola Finance,\n\n'
      +'Os escribimos desde CX en relación al siguiente caso:\n\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'DATOS DEL CLIENTE\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'Cliente:        '+cn+'\n'
      +'Email:          '+emailCl+'\n'
      +'Account Code:   '+accCode+'\n'
      +'Factura:        '+inv+'\n'
      +pmLine
      +'\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'MOTIVO\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +(reasonLine||'[Sin motivo especificado]\n')
      +'\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'IMPORTES\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'Importe cobrado:              '+charged.toFixed(2)+' €\n'
      +'Importe acordado (crédito):   '+correct.toFixed(2)+' €\n'
      +'Diferencia a devolver:        '+diff.toFixed(2)+' €\n'
      +'\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'ACCIÓN REQUERIDA\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'1. Emitir factura rectificativa por el importe cobrado: '+charged.toFixed(2)+' €.\n'
      +'   (El cliente se suscribe a la nueva oferta — no emitir factura nueva.)\n\n'
      +'2. Añadir crédito a la cuenta del cliente: '+correct.toFixed(2)+' €\n'
      +'   Este crédito se aplicará como pago de la nueva oferta.\n\n'
      +'3. Devolver al cliente la diferencia: '+diff.toFixed(2)+' €\n'
      +'   Vía: '+(annPmVal?annPmLabels[annPmVal]||annPmVal:'[método de pago]')+'.'
      +certLine
      +(nt?'\n\n━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\nNOTAS\n━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'+nt:'')
      +'\n\nQuedamos a vuestra disposición para cualquier duda.\n\nUn saludo,\nCX Team – Doofinder';
  }
  if(c==='cancel_late'&&ST.cancelComp==='yes'){
    var ar=parseFloat(document.getElementById('clAr').value)||0;
    var acCl=parseFloat(document.getElementById('clAc').value)||0;
    var reasonCancelLine=ST.cancelReason?(CANCEL_REASON_LABEL[ST.cancelReason]):'[Sin motivo especificado]';
    body='Asunto: Factura rectificativa + devolución — '+cn+'\n\n'
      +'Hola Finance,\n\n'
      +'Os escribimos desde CX en relación al siguiente caso:\n\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'DATOS DEL CLIENTE\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'Cliente:        '+cn+'\n'
      +'Email:          '+emailCl+'\n'
      +'Account Code:   '+accCode+'\n'
      +'Factura:        '+inv+'\n'
      +'Método de pago: '+(PL[ST.pm]||'[método]')+'\n'
      +'\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'MOTIVO\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'Cancelación tardía — '+reasonCancelLine+'\n'
      +'\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'IMPORTES\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'Importe cobrado:    '+(acCl>0?acCl.toFixed(2)+' €':'[por confirmar]')+'\n'
      +'Importe a devolver: '+ar.toFixed(2)+' €\n'
      +'\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'ACCIÓN REQUERIDA\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'1. Emitir factura rectificativa por '+ar.toFixed(2)+' €.\n'
      +'2. Devolver '+ar.toFixed(2)+' € al cliente vía '+(PL[ST.pm]||'[método]')+'.'
      +(ST.pm==='direct_debit'?'\n   ⚠ El cliente aportará certificado de titularidad bancaria.':'')
      +(nt?'\n\n━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\nNOTAS\n━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'+nt:'')
      +'\n\nQuedamos a vuestra disposición para cualquier duda.\n\nUn saludo,\nCX Team – Doofinder';
  }
  if(c==='billing_data'){
    var n=parseInt(document.getElementById('bdCount').value)||0;
    var invoicesList='';
    for(var i=1;i<=n;i++){
      var el=document.getElementById('bdInv'+i);
      if(el&&el.value)invoicesList+=(i>1?', ':'')+el.value;
    }
    if(!invoicesList)invoicesList=inv;
    var company=document.getElementById('bdCompany').value||'[Company Name]';
    var vat=document.getElementById('bdVat').value||'[VAT ID]';
    var contact=document.getElementById('bdContact').value||'[Contact Person]';
    var bdEmail=document.getElementById('bdEmail').value||'[Email]';
    var bdAddr=document.getElementById('bdAddress').value||'[Invoicing Address]';
    body='Asunto: Corrección de datos de facturación — '+cn+'\n\n'
      +'Hola Finance,\n\n'
      +'Os escribimos desde CX en relación al cliente '+cn+' ('+emailCl+').\n\n'
      +'El cliente ha actualizado sus datos de facturación en el admin de Doofinder\n'
      +'(Billing Information) y solicita que se corrijan en la última factura emitida.\n\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'DATOS DEL CLIENTE\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'Cliente:        '+cn+'\n'
      +'Email:          '+emailCl+'\n'
      +'Account Code:   '+accCode+'\n'
      +'\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'FACTURA A RECTIFICAR\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +invoicesList+'\n'
      +'\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'NUEVOS DATOS DE FACTURACIÓN\n'
      +'(tal y como figuran ahora en el admin)\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'Company Name:      '+company+'\n'
      +'VAT ID:            '+vat+'\n'
      +'Contact Person:    '+contact+'\n'
      +'Invoicing Address: '+bdAddr+'\n'
      +'Email:             '+bdEmail+'\n'
      +'\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'ACCIÓN REQUERIDA\n'
      +'━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'
      +'1. Emisión de factura rectificativa de la factura '+invoicesList+'.\n'
      +'2. Emisión de nueva factura con los datos de facturación actualizados\n'
      +'   (tal como figuran ahora en el admin).'
      +(nt?'\n\n━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\nNOTAS\n━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\n'+nt:'')
      +'\n\nQuedamos a vuestra disposición para cualquier duda.\n\nUn saludo,\nCX Team – Doofinder';
  }

  if(!body)body='[Este caso no genera email a Finance]';

  // Write to editable textarea
  var ta=document.getElementById('financeEmailEdit');
  ta.value=body;
  // auto-size height
  ta.style.height='auto';
  setTimeout(function(){ta.style.height=(ta.scrollHeight+4)+'px';},50);

  // Show cert attachment reminder if applicable
  var certWrap=document.getElementById('certAttachReminder');
  if(certWrap){
    var certFile=document.getElementById('annCert');
    var hasCert=certFile&&certFile.files&&certFile.files.length>0;
    var isAnnualDD=c==='cobro_exceso'&&ST.period==='annual'&&document.getElementById('annPm').value==='direct_debit';
    certWrap.style.display=isAnnualDD?'flex':'none';
    if(isAnnualDD){
      document.getElementById('certFileName').textContent=hasCert
        ?'Adjuntar: '+certFile.files[0].name
        :'Recuerda adjuntar el certificado de titularidad bancaria al enviar este email.';
    }
  }
  go(4);
}

function sendEmail(){
  var body=document.getElementById('financeEmailEdit').value;
  // Extract subject from first line "Asunto: ..."
  var subject='Billing — AiFonso';
  var firstLine=body.split('\n')[0];
  if(firstLine.toLowerCase().startsWith('asunto:')){
    subject=firstLine.replace(/^asunto:\s*/i,'').trim();
    body=body.split('\n').slice(1).join('\n').replace(/^\n+/,'');
  }
  var mailto='mailto:finance@doofinder.com'
    +'?subject='+encodeURIComponent(subject)
    +'&body='+encodeURIComponent(body);
  window.location.href=mailto;
}

function copyEditedEmail(btn){
  var txt=document.getElementById('financeEmailEdit').value;
  if(navigator.clipboard)navigator.clipboard.writeText(txt).then(function(){
    var o=btn.textContent;btn.textContent='✓ Copiado';
    setTimeout(function(){btn.textContent=o;},2000);
  });
}

function copyBlock(id,btn){
  var el=document.getElementById(id);
  var txt=el.dataset&&el.dataset.txt?el.dataset.txt:el.textContent;
  if(navigator.clipboard)navigator.clipboard.writeText(txt).then(function(){
    var o=btn.textContent;btn.textContent='✓ Copiado';setTimeout(function(){btn.textContent=o;},2000);
  });
}

function restart(){
  window.ST={ct:'',pm:'',period:'',cancelReason:'',cancelComp:'',excessReason:''};
  window.C={price:0,disc:0,months:0,inv:1,fp:0,toRef:0,fmp:0,fmd:0,rem:0};
  document.querySelectorAll('.case-card,.opt,.tog').forEach(function(b){b.classList.remove('sel');});
  ['cn','accCode','emailClient','inv','nt','clAc','clAr','annCharged','annCorrect','bdCompany','bdVat','bdContact','bdEmail','bdAddress'].forEach(function(id){
    var el=document.getElementById(id);if(el)el.value='';
  });
  document.getElementById('ninv').value='1';
  document.getElementById('bdCount').value='0';
  document.getElementById('bdInvoiceFields').innerHTML='';
  document.getElementById('annPm').value='';
  document.getElementById('annDdWrap').style.display='none';
  document.getElementById('annCertName').textContent='';
  var ta=document.getElementById('financeEmailEdit');if(ta){ta.value='';ta.style.height='';}
  var cr=document.getElementById('certAttachReminder');if(cr)cr.style.display='none';
  ALL_BLKS.forEach(function(id){document.getElementById(id).style.display='none';});
  ['blk_monthly','blk_annual','blk_cancel_refund','clientTextWrap','clRefResult','annResult','ddNote'].forEach(function(id){
    var el=document.getElementById(id);if(el)el.style.display='none';
  });
  go(0);
}

</script>
</body>
</html>
