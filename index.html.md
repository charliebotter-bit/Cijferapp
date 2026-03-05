<!DOCTYPE html>

<html lang="nl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CijferApp</title>
<link href="https://fonts.googleapis.com/css2?family=Clash+Display:wght@500;600;700&family=Cabinet+Grotesk:wght@400;500;700;800&display=swap" rel="stylesheet">
<style>
:root{--bg:#080b12;--s1:#0f1320;--s2:#151b2c;--s3:#1c2438;--border:#222a3e;--border2:#2d3651;--blue:#3d7eff;--blue2:#6a9eff;--purple:#8b5cf6;--green:#10d982;--orange:#f59e0b;--red:#f43f5e;--text:#e2e8f8;--text2:#8a94b0;--text3:#4f5a78;--r:16px;--r2:10px}
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:'Cabinet Grotesk',sans-serif;background:var(--bg);color:var(--text);min-height:100vh;overflow-x:hidden}
header{position:sticky;top:0;z-index:200;background:rgba(8,11,18,0.93);backdrop-filter:blur(20px);border-bottom:1px solid var(--border);padding:0 24px}
.hi{max-width:1000px;margin:0 auto;display:flex;align-items:center;justify-content:space-between;height:60px;gap:10px}
.logo{font-family:'Clash Display',sans-serif;font-size:22px;font-weight:700;background:linear-gradient(110deg,#3d7eff,#8b5cf6,#10d982);-webkit-background-clip:text;-webkit-text-fill-color:transparent;flex-shrink:0}
.hr{display:flex;align-items:center;gap:8px;flex-wrap:wrap;justify-content:flex-end}
.chip{font-size:11px;font-weight:700;letter-spacing:.5px;padding:5px 12px;border-radius:20px;background:rgba(61,126,255,.1);color:var(--blue2);border:1px solid rgba(61,126,255,.2)}
.hbtn{background:var(--s2);border:1px solid var(--border);color:var(--text2);font-family:'Cabinet Grotesk',sans-serif;font-size:12px;font-weight:700;padding:5px 11px;border-radius:8px;cursor:pointer;transition:all .2s;white-space:nowrap}
.hbtn:hover{border-color:var(--blue);color:var(--blue)}
.hbtn:disabled{opacity:.3;cursor:default;border-color:var(--border);color:var(--text3)}
.si{display:flex;align-items:center;gap:5px;font-size:11px;color:var(--text3);transition:all .4s}
.si-dot{width:6px;height:6px;border-radius:50%;background:var(--text3);transition:background .3s}
.si.saved .si-dot{background:var(--green)}
.si.saved{color:var(--green)}
.wrap{max-width:1000px;margin:0 auto;padding:28px 20px 100px;position:relative;z-index:1}
.sg{display:grid;grid-template-columns:1.3fr 1fr 1fr 1fr;gap:12px;margin-bottom:28px}
.sc{background:var(--s1);border:1px solid var(--border);border-radius:var(--r);padding:18px 20px;position:relative;overflow:hidden;transition:border-color .2s,transform .2s;animation:fadeUp .4s ease both}
.sc:hover{border-color:var(--border2);transform:translateY(-2px)}
.sc-glow{position:absolute;top:-50px;right:-50px;width:140px;height:140px;border-radius:50%;filter:blur(50px);opacity:.12;pointer-events:none}
.sc-label{font-size:10px;font-weight:700;text-transform:uppercase;letter-spacing:1.5px;color:var(--text3);margin-bottom:10px}
.sc-val{font-family:'Clash Display',sans-serif;font-size:42px;font-weight:700;line-height:1;transition:color .3s}
.sc-sub{font-size:12px;color:var(--text2);margin-top:6px}
.cb{color:var(--blue2)}.cg{color:var(--green)}.co{color:var(--orange)}.cr{color:var(--red)}.cm{color:var(--text3)}
.tabs{display:flex;gap:5px;background:var(--s1);border:1px solid var(--border);border-radius:var(--r);padding:5px;margin-bottom:24px}
.tb{flex:1;padding:10px 8px;background:transparent;border:none;color:var(--text2);font-family:'Cabinet Grotesk',sans-serif;font-size:13px;font-weight:700;border-radius:11px;cursor:pointer;transition:all .2s;display:flex;align-items:center;justify-content:center;gap:6px}
.tb.active{background:linear-gradient(135deg,var(--blue),var(--purple));color:#fff;box-shadow:0 4px 20px rgba(61,126,255,.3)}
.tb:not(.active):hover{color:var(--text);background:var(--s2)}
.tv{display:none}.tv.active{display:block}
.sh{display:flex;align-items:center;justify-content:space-between;margin-bottom:16px}
.st{font-family:'Clash Display',sans-serif;font-size:18px;font-weight:600}
.bp{background:linear-gradient(135deg,var(--blue),var(--purple));border:none;color:#fff;font-family:'Cabinet Grotesk',sans-serif;font-size:13px;font-weight:700;padding:10px 18px;border-radius:var(--r2);cursor:pointer;transition:opacity .2s,transform .15s;display:inline-flex;align-items:center;gap:6px}
.bp:hover{opacity:.9;transform:translateY(-1px)}
.vc{background:var(--s1);border:1px solid var(--border);border-radius:var(--r);margin-bottom:14px;overflow:hidden;transition:border-color .2s;animation:fadeUp .35s ease both}
.vc:hover{border-color:var(--border2)}
.vh{display:flex;align-items:center;padding:14px 18px;gap:14px;cursor:pointer;user-select:none}
.vs{width:4px;height:44px;border-radius:4px;flex-shrink:0}
.vn{flex:1;min-width:0}
.vni{background:transparent;border:none;color:var(--text);font-family:'Clash Display',sans-serif;font-size:16px;font-weight:600;outline:none;width:100%;cursor:text}
.vni::placeholder{color:var(--text3)}
.vsl{font-size:11px;color:var(--text3);margin-top:2px}
.va{font-family:'Clash Display',sans-serif;font-size:28px;font-weight:700;min-width:56px;text-align:right;flex-shrink:0;transition:color .3s}
.vch{color:var(--text3);font-size:14px;transition:transform .25s;flex-shrink:0}
.vch.open{transform:rotate(180deg)}
.vb{display:none;padding:0 18px 18px}
.vb.open{display:block}
.gh{display:grid;grid-template-columns:1fr 90px 82px 54px 36px;gap:8px;padding:8px 10px;border-bottom:1px solid var(--border);margin-bottom:4px}
.gh span{font-size:10px;font-weight:700;text-transform:uppercase;letter-spacing:1.2px;color:var(--text3)}
.gh span:nth-child(n+2){text-align:center}
.gr{display:grid;grid-template-columns:1fr 90px 82px 54px 36px;gap:8px;align-items:center;padding:5px 10px;border-radius:var(--r2);transition:background .15s}
.gr:hover{background:var(--s2)}
.gin{background:var(--s2);border:1px solid var(--border);border-radius:8px;color:var(--text);font-family:'Cabinet Grotesk',sans-serif;font-size:14px;font-weight:500;padding:8px 10px;outline:none;transition:border-color .2s;width:100%}
.gin:focus{border-color:var(--blue)}
.gin.num{text-align:center;font-weight:700;font-family:'Clash Display',sans-serif}
.gp{border-radius:20px;font-size:12px;font-weight:700;padding:4px 8px;text-align:center;font-family:'Clash Display',sans-serif;white-space:nowrap;transition:all .3s}
.db{background:none;border:none;color:var(--text3);font-size:15px;cursor:pointer;padding:5px;border-radius:6px;transition:color .15s,background .15s;display:flex;align-items:center;justify-content:center}
.db:hover{color:var(--red);background:rgba(244,63,94,.1)}
.agb{display:flex;align-items:center;justify-content:center;gap:6px;width:100%;padding:10px;background:var(--s2);border:1px dashed var(--border2);border-radius:var(--r2);color:var(--text3);font-family:'Cabinet Grotesk',sans-serif;font-size:13px;font-weight:600;cursor:pointer;transition:all .2s;margin:8px 0}
.agb:hover{border-color:var(--blue);color:var(--blue)}
.vsr{display:grid;grid-template-columns:repeat(4,1fr);gap:8px;margin-bottom:12px;padding:12px;background:var(--s2);border-radius:var(--r2);border:1px solid var(--border)}
.vst{text-align:center}
.vsv{font-family:'Clash Display',sans-serif;font-size:20px;font-weight:700;line-height:1}
.vsl2{font-size:10px;color:var(--text3);text-transform:uppercase;letter-spacing:1px;margin-top:3px}
.vct{margin-top:14px}
.vct-title{font-size:10px;font-weight:700;text-transform:uppercase;letter-spacing:1.2px;color:var(--text3);margin-bottom:10px}
.crs{display:flex;flex-direction:column;gap:7px}
.cr2{display:flex;align-items:center;gap:10px}
.cl{font-size:12px;color:var(--text2);width:110px;flex-shrink:0;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.ct{flex:1;height:24px;background:var(--s3);border-radius:6px;overflow:hidden;position:relative}
.cf{height:100%;border-radius:6px;transition:width .5s cubic-bezier(.22,1,.36,1);display:flex;align-items:center;padding-left:8px;font-family:'Clash Display',sans-serif;font-size:12px;font-weight:700;color:#fff;white-space:nowrap;min-width:40px}
.cpl{position:absolute;top:0;bottom:0;left:55%;width:2px;background:rgba(255,255,255,.2);border-radius:2px}
.vf{display:flex;align-items:center;justify-content:space-between;padding-top:12px;border-top:1px solid var(--border);gap:12px;margin-top:4px}
.vfi{font-size:13px;color:var(--text2)}
.vfi strong{color:var(--text)}
.dvb{background:none;border:1px solid var(--border);color:var(--text3);font-family:'Cabinet Grotesk',sans-serif;font-size:12px;font-weight:600;padding:6px 12px;border-radius:8px;cursor:pointer;transition:all .2s;white-space:nowrap}
.dvb:hover{border-color:var(--red);color:var(--red)}
.avb{width:100%;padding:14px;background:transparent;border:2px dashed var(--border);border-radius:var(--r);color:var(--text3);font-family:'Cabinet Grotesk',sans-serif;font-size:14px;font-weight:700;cursor:pointer;transition:all .2s;display:flex;align-items:center;justify-content:center;gap:8px;margin-bottom:30px}
.avb:hover{border-color:var(--blue);color:var(--blue)}
.pc{background:var(--s1);border:1px solid var(--border);border-radius:var(--r);padding:22px;margin-bottom:16px}
.pt{font-family:'Clash Display',sans-serif;font-size:16px;font-weight:600;margin-bottom:6px}
.pd{font-size:13px;color:var(--text2);margin-bottom:20px;line-height:1.5}
.fl{margin-bottom:14px}
.fll{font-size:12px;font-weight:700;color:var(--text2);margin-bottom:6px}
.rb{background:var(--s2);border-radius:var(--r2);padding:16px 18px;margin-top:16px;border:1px solid var(--border);display:none}
.rb.show{display:block}
.rn{font-family:'Clash Display',sans-serif;font-size:38px;font-weight:700;line-height:1;margin-bottom:6px}
.rd{font-size:13px;color:var(--text2);line-height:1.5}
.pt2{height:6px;background:var(--border);border-radius:10px;overflow:hidden;margin-top:12px}
.pf{height:100%;border-radius:10px;transition:width .5s cubic-bezier(.22,1,.36,1)}
.svc{background:var(--s1);border:1px solid var(--border);border-radius:var(--r);padding:18px;margin-bottom:12px}
.svh{display:flex;align-items:center;gap:12px;margin-bottom:14px}
.svd{width:10px;height:10px;border-radius:50%;flex-shrink:0}
.svn{font-family:'Clash Display',sans-serif;font-size:15px;font-weight:600;flex:1}
.svc2{font-size:13px;color:var(--text2)}
.svc2 b{font-family:'Clash Display',sans-serif;font-size:18px;font-weight:700}
.sff{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:10px}
.sfl label{font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:1px;color:var(--text3);margin-bottom:6px;display:block}
.sr2{display:flex;align-items:center;gap:12px;padding:10px 14px;background:var(--s2);border-radius:10px;border:1px solid var(--border)}
.srl{font-size:12px;color:var(--text2);flex:1}
.srn{font-family:'Clash Display',sans-serif;font-size:22px;font-weight:700;transition:color .3s}
.fcc{background:var(--s1);border:1px solid var(--border);border-radius:var(--r);padding:22px;margin-bottom:16px}
.fct{font-family:'Clash Display',sans-serif;font-size:16px;font-weight:600;margin-bottom:20px}
.fcb{display:flex;align-items:flex-end;gap:14px;height:200px}
.fcw{flex:1;display:flex;flex-direction:column;align-items:center;height:100%;gap:6px}
.fck{flex:1;width:100%;background:var(--s3);border-radius:8px 8px 0 0;position:relative;overflow:visible;display:flex;align-items:flex-end}
.fcf{width:100%;border-radius:8px 8px 0 0;transition:height .7s cubic-bezier(.22,1,.36,1);position:relative}
.fcfl{position:absolute;top:-22px;left:50%;transform:translateX(-50%);font-family:'Clash Display',sans-serif;font-size:13px;font-weight:700;white-space:nowrap}
.fcpl{position:absolute;left:0;right:0;bottom:55%;height:2px;background:rgba(255,255,255,.2);border-radius:2px}
.fcl{font-size:11px;color:var(--text2);text-align:center;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;max-width:100%}
.og{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.oc{background:var(--s1);border:1px solid var(--border);border-radius:var(--r);padding:18px;transition:border-color .2s;animation:fadeUp .35s ease both}
.oc:hover{border-color:var(--border2)}
.ot{display:flex;align-items:flex-start;gap:12px;margin-bottom:10px}
.od{width:12px;height:12px;border-radius:3px;margin-top:4px;flex-shrink:0}
.on{flex:1;font-family:'Clash Display',sans-serif;font-size:16px;font-weight:600;line-height:1.3}
.oa{font-family:'Clash Display',sans-serif;font-size:32px;font-weight:700;line-height:1}
.ob{height:8px;background:var(--s3);border-radius:8px;overflow:hidden;position:relative;margin:10px 0 8px}
.obf{height:100%;border-radius:8px;transition:width .7s cubic-bezier(.22,1,.36,1)}
.opl{position:absolute;top:0;bottom:0;left:55%;width:2px;background:rgba(255,255,255,.2);border-radius:2px}
.op{display:inline-flex;align-items:center;padding:3px 10px;border-radius:20px;font-size:11px;font-weight:700;letter-spacing:.4px}
.ogr{display:flex;justify-content:space-between;align-items:center;font-size:12px;padding:4px 0;border-bottom:1px solid var(--border)}
.ogr:last-child{border-bottom:none}
.modal-bg{position:fixed;inset:0;background:rgba(0,0,0,.7);backdrop-filter:blur(4px);z-index:500;display:none;align-items:center;justify-content:center;padding:20px}
.modal-bg.show{display:flex}
.modal{background:var(--s1);border:1px solid var(--border2);border-radius:var(--r);padding:28px;max-width:480px;width:100%;animation:fadeUp .2s ease}
.mt{font-family:'Clash Display',sans-serif;font-size:20px;font-weight:700;margin-bottom:8px}
.md{font-size:14px;color:var(--text2);margin-bottom:20px;line-height:1.6}
.ma{display:flex;gap:10px;flex-wrap:wrap}
.modal textarea{width:100%;background:var(--s2);border:1px solid var(--border);border-radius:var(--r2);color:var(--text);font-family:monospace;font-size:12px;padding:12px;outline:none;resize:vertical;min-height:120px;margin-bottom:16px}
.modal textarea:focus{border-color:var(--blue)}
.bs{background:var(--s2);border:1px solid var(--border2);color:var(--text);font-family:'Cabinet Grotesk',sans-serif;font-size:13px;font-weight:700;padding:10px 16px;border-radius:var(--r2);cursor:pointer;transition:all .2s}
.bs:hover{border-color:var(--blue);color:var(--blue)}
.bd{background:rgba(244,63,94,.1);border:1px solid rgba(244,63,94,.3);color:var(--red);font-family:'Cabinet Grotesk',sans-serif;font-size:13px;font-weight:700;padding:10px 16px;border-radius:var(--r2);cursor:pointer;transition:all .2s}
.bd:hover{background:rgba(244,63,94,.2)}
.toast{position:fixed;bottom:24px;left:50%;transform:translateX(-50%) translateY(80px);background:var(--s2);border:1px solid var(--border2);border-radius:12px;padding:12px 20px;font-size:13px;font-weight:600;color:var(--text);box-shadow:0 8px 32px rgba(0,0,0,.4);z-index:999;transition:transform .3s cubic-bezier(.22,1,.36,1),opacity .3s;opacity:0;pointer-events:none}
.toast.show{transform:translateX(-50%) translateY(0);opacity:1}
.es{text-align:center;padding:60px 20px}
.ei{font-size:48px;margin-bottom:12px}
.ett{font-family:'Clash Display',sans-serif;font-size:20px;font-weight:600;color:var(--text2);margin-bottom:8px}
.es2{font-size:14px;color:var(--text3);margin-bottom:24px}
@keyframes fadeUp{from{opacity:0;transform:translateY(10px)}to{opacity:1;transform:translateY(0)}}
@media(max-width:650px){.sg{grid-template-columns:1fr 1fr}.sg .sc:first-child{grid-column:1/-1}.gh,.gr{grid-template-columns:1fr 80px 72px 44px 32px}.og{grid-template-columns:1fr}.sff{grid-template-columns:1fr}.fcb{gap:6px}.chip{display:none}.vsr{grid-template-columns:1fr 1fr}}
</style>
</head>
<body>
<header>
  <div class="hi">
    <div class="logo">CijferApp</div>
    <div class="hr">
      <div class="si" id="si"><div class="si-dot"></div><span id="sl">—</span></div>
      <button class="hbtn" id="undoBtn" onclick="undo()" disabled>↩ Ongedaan</button>
      <button class="hbtn" onclick="openBackup()">💾 Back-up</button>
      <div class="chip">Grens: 5,5</div>
    </div>
  </div>
</header>
<div class="wrap">
  <div class="sg">
    <div class="sc" style="animation-delay:.05s"><div class="sc-glow" style="background:var(--blue)"></div><div class="sc-label">Totaalgemiddelde</div><div class="sc-val cb" id="sAvg">—</div><div class="sc-sub" id="sSub">Voeg vakken toe</div></div>
    <div class="sc" style="animation-delay:.1s"><div class="sc-glow" style="background:var(--green)"></div><div class="sc-label">Voldoendes</div><div class="sc-val cg" id="sPass">0</div><div class="sc-sub">van <span id="sTotal">0</span> vakken</div></div>
    <div class="sc" style="animation-delay:.15s"><div class="sc-glow" style="background:var(--red)"></div><div class="sc-label">Onvoldoendes</div><div class="sc-val cr" id="sFail">0</div><div class="sc-sub">vakken</div></div>
    <div class="sc" style="animation-delay:.2s"><div class="sc-glow" style="background:var(--orange)"></div><div class="sc-label">Hoogste cijfer</div><div class="sc-val co" id="sHigh">—</div><div class="sc-sub" id="sHighSub">—</div></div>
  </div>
  <div class="tabs">
    <button class="tb active" onclick="switchTab('vakken',this)">📚 Mijn vakken</button>
    <button class="tb" onclick="switchTab('predict',this)">🔮 Wat ga ik staan?</button>
    <button class="tb" onclick="switchTab('overview',this)">📊 Overzicht</button>
  </div>
  <div class="tv active" id="tv-vakken">
    <div class="sh"><div class="st">Mijn vakken</div><button class="bp" onclick="addVak()">＋ Vak toevoegen</button></div>
    <div id="vakkenList"></div>
    <button class="avb" onclick="addVak()">＋ Voeg vak toe</button>
  </div>
  <div class="tv" id="tv-predict">
    <div class="sh"><div class="st">Wat ga ik staan?</div></div>
    <div class="pc">
      <div class="pt">📈 Benodigde toetscijfer berekenen</div>
      <div class="pd">Selecteer een vak en bereken welk cijfer je nodig hebt voor een komende toets om je doelgemiddelde te halen.</div>
      <div class="fl"><div class="fll">Vak</div><select class="gin" id="pVak" onchange="doPredict()"><option value="">— Kies een vak —</option></select></div>
      <div class="fl"><div class="fll">Gewenst gemiddelde</div><input type="number" class="gin num" id="pTarget" value="6.0" min="1" max="10" step="0.1" oninput="doPredict()"></div>
      <div class="fl"><div class="fll">Weging van de nieuwe toets</div><input type="number" class="gin num" id="pWeight" value="1" min="0.1" max="10" step="0.5" oninput="doPredict()"></div>
      <div class="rb" id="pResult"><div class="rn" id="pRN"></div><div class="rd" id="pRD"></div><div class="pt2"><div class="pf" id="pPF" style="width:0%"></div></div></div>
    </div>
    <div class="pc">
      <div class="pt">🎯 Scenario simulator — per vak</div>
      <div class="pd">Vul per vak een verwacht nieuw cijfer en weging in en zie hoe je gemiddelde verandert.</div>
      <div id="scenCards"></div>
      <div style="background:var(--s2);border-radius:var(--r2);padding:16px 20px;border:1px solid var(--border2)">
        <div style="font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:1.2px;color:var(--text3);margin-bottom:6px">Verwacht totaalgemiddelde</div>
        <div id="scenTotal" style="font-family:'Clash Display',sans-serif;font-size:36px;font-weight:700;color:var(--text3)">—</div>
      </div>
    </div>
  </div>
  <div class="tv" id="tv-overview">
    <div class="sh"><div class="st">Volledig overzicht</div></div>
    <div id="ovContent"></div>
  </div>
</div>
<div class="modal-bg" id="backupModal">
  <div class="modal">
    <div class="mt">💾 Back-up & herstel</div>
    <div class="md">Exporteer je cijfers als bestand om ze veilig te bewaren, of importeer een eerder opgeslagen back-up. Je cijfers worden ook automatisch in je browser opgeslagen.</div>
    <div class="ma">
      <button class="bp" onclick="exportData()">⬇ Exporteer back-up</button>
      <button class="bs" onclick="showImport()">⬆ Importeer back-up</button>
      <button class="bd" onclick="confirmReset()">🗑 Alles wissen</button>
      <button class="bs" onclick="closeModal('backupModal')">Sluiten</button>
    </div>
    <div id="importArea" style="display:none;margin-top:20px">
      <div class="fll" style="margin-bottom:8px">Plak hier je back-up tekst:</div>
      <textarea id="importText" placeholder='{"vakken":[...]}'></textarea>
      <div class="ma">
        <button class="bp" onclick="importData()">✓ Importeren</button>
        <button class="bs" onclick="document.getElementById('importArea').style.display='none'">Annuleren</button>
      </div>
    </div>
  </div>
</div>
<div class="toast" id="toast"></div>
<script>
const PASS=5.5,SK='cijferapp_v3',COLS=['#3d7eff','#8b5cf6','#10d982','#f59e0b','#f43f5e','#06b6d4','#ec4899','#84cc16','#f97316','#a855f7'];
let vakken=[],uid=1,gid=1,openVakken=new Set(),undoH=[],saveTimer=null;

// STORAGE
function save(){try{localStorage.setItem(SK,JSON.stringify({vakken,uid,gid,at:new Date().toISOString()}));showSaved();}catch(e){toast(‘⚠️ Opslaan mislukt’);}}
function dsave(){clearTimeout(saveTimer);saveTimer=setTimeout(save,600);}
function load(){try{const r=localStorage.getItem(SK);if(!r)return false;const d=JSON.parse(r);if(!d.vakken||!d.vakken.length)return false;vakken=d.vakken;uid=d.uid||Math.max(…vakken.map(v=>v.id))+1;gid=d.gid||Math.max(0,…vakken.flatMap(v=>v.grades.map(g=>g.id)))+1;return true;}catch(e){return false;}}
function showSaved(){const i=document.getElementById(‘si’),l=document.getElementById(‘sl’);i.classList.add(‘saved’);l.textContent=‘Opgeslagen ✓’;setTimeout(()=>{i.classList.remove(‘saved’);l.textContent=lastSavedStr();},2000);}
function lastSavedStr(){try{const d=JSON.parse(localStorage.getItem(SK)||’{}’);if(!d.at)return’Nog niet opgeslagen’;const t=new Date(d.at);return`Opgeslagen ${t.getHours().toString().padStart(2,'0')}:${t.getMinutes().toString().padStart(2,'0')}`;}catch(e){return’’;}}

// BACKUP
function openBackup(){document.getElementById(‘importArea’).style.display=‘none’;document.getElementById(‘backupModal’).classList.add(‘show’);}
function closeModal(id){document.getElementById(id).classList.remove(‘show’);}
function exportData(){const b=new Blob([JSON.stringify({vakken,uid,gid},null,2)],{type:‘application/json’});const a=document.createElement(‘a’);a.href=URL.createObjectURL(b);a.download=‘CijferApp_backup_’+new Date().toLocaleDateString(‘nl-NL’).replace(///g,’-’)+’.json’;a.click();toast(‘✅ Back-up gedownload!’);}
function showImport(){document.getElementById(‘importArea’).style.display=‘block’;}
function importData(){try{const d=JSON.parse(document.getElementById(‘importText’).value.trim());if(!d.vakken)throw 0;pushH();vakken=d.vakken;uid=d.uid||1;gid=d.gid||1;openVakken=new Set();save();closeModal(‘backupModal’);rebuild();toast(‘✅ Back-up hersteld!’);}catch(e){toast(‘❌ Ongeldige back-up’);}}
function confirmReset(){if(!confirm(‘Weet je zeker dat je ALLES wilt wissen?’))return;pushH();vakken=[];uid=1;gid=1;openVakken=new Set();localStorage.removeItem(SK);closeModal(‘backupModal’);rebuild();toast(‘🗑 Alles gewist’);}

// HELPERS
function avg(gs){const v=gs.filter(g=>g.val!==’’&&!isNaN(+g.val)&&+g.wt>0);if(!v.length)return null;return v.reduce((s,g)=>s+(+g.val)*(+g.wt),0)/v.reduce((s,g)=>s+(+g.wt),0);}
function needed(gs,tgt,nw){const v=gs.filter(g=>g.val!==’’&&!isNaN(+g.val)&&+g.wt>0);const tw=v.reduce((s,g)=>s+(+g.wt),0),ts=v.reduce((s,g)=>s+(+g.val)*(+g.wt),0);return(tgt*(tw+nw)-ts)/nw;}
function gc(v){if(v===null)return’var(–text3)’;if(v>=PASS+1.5)return’var(–green)’;if(v>=PASS)return’#5ee8a0’;if(v>=PASS-.5)return’var(–orange)’;return’var(–red)’;}
function gcls(v){if(v===null)return’cm’;if(v>=PASS)return’cg’;if(v>=PASS-.5)return’co’;return’cr’;}
function fmt(v,d=1){return v===null?’—’:(+v).toFixed(d);}
function esc(s){return String(s).replace(/&/g,’&’).replace(/</g,’<’).replace(/>/g,’>’).replace(/”/g,’"’);}
function clone(o){return JSON.parse(JSON.stringify(o));}
function pushH(){undoH.push(clone(vakken));if(undoH.length>30)undoH.shift();document.getElementById(‘undoBtn’).disabled=false;}
function undo(){if(!undoH.length)return;vakken=undoH.pop();if(!undoH.length)document.getElementById(‘undoBtn’).disabled=true;openVakken=new Set([…openVakken].filter(id=>vakken.find(v=>v.id===id)));save();rebuild();toast(‘↩ Ongedaan gemaakt’);}
function toast(msg){const t=document.getElementById(‘toast’);t.textContent=msg;t.classList.add(‘show’);setTimeout(()=>t.classList.remove(‘show’),2500);}

// CRUD
function addVak(){pushH();const id=uid++;vakken.push({id,name:`Vak ${vakken.length+1}`,color:COLS[vakken.length%COLS.length],grades:[]});openVakken.add(id);dsave();rebuild();setTimeout(()=>{const i=document.querySelector(`#vc-${id} .vni`);if(i){i.focus();i.select();}},50);}
function delVak(id){if(!confirm(‘Vak verwijderen?’))return;pushH();vakken=vakken.filter(v=>v.id!==id);openVakken.delete(id);save();rebuild();toast(‘🗑 Vak verwijderd’);}
function addGrade(vid){pushH();const vak=vakken.find(v=>v.id===vid);if(!vak)return;const id=gid++;vak.grades.push({id,desc:’’,val:’’,wt:‘1’});dsave();const gl=document.querySelector(`#vc-${vid} .grades-list`);const gh=document.querySelector(`#vc-${vid} .gh`);if(!gh){rebuildBody(vid);}else{const nl=document.querySelector(`#vc-${vid} .ngl`);if(nl)nl.remove();const row=mkRow(vid,vak.grades[vak.grades.length-1]);gl.appendChild(row);setTimeout(()=>row.querySelector(’.gin:first-child’).focus(),30);}updVak(vid);updSum();}
function delGrade(vid,gid2){pushH();const vak=vakken.find(v=>v.id===vid);if(!vak)return;vak.grades=vak.grades.filter(g=>g.id!==gid2);const row=document.getElementById(`gr-${vid}-${gid2}`);if(row)row.remove();if(!vak.grades.length){const gh=document.querySelector(`#vc-${vid} .gh`);if(gh)gh.remove();const gl=document.querySelector(`#vc-${vid} .grades-list`);if(gl)gl.remove();const b=document.querySelector(`#vc-${vid} .vb`);if(b&&!b.querySelector(’.ngl’)){const l=document.createElement(‘div’);l.className=‘ngl’;l.style.cssText=‘text-align:center;padding:16px;color:var(–text3);font-size:13px;’;l.textContent=‘Geen cijfers — voeg ze hieronder toe’;b.insertBefore(l,b.querySelector(’.agb’));}}dsave();updVak(vid);updSum();}

// FIELD HANDLERS (no re-render — fixes keyboard disappearing)
function onDesc(vid,gid2,v){const vak=vakken.find(x=>x.id===vid);if(!vak)return;const g=vak.grades.find(g=>g.id===gid2);if(g){g.desc=v;dsave();}const l=document.querySelector(`#chl-${vid}-${gid2}`);if(l)l.textContent=v||‘Toets’;}
function onVal(vid,gid2,v){const vak=vakken.find(x=>x.id===vid);if(!vak)return;const g=vak.grades.find(g=>g.id===gid2);if(!g)return;g.val=v;dsave();updPill(vid,gid2,v);updVak(vid);updSum();doPredict();calcScen();}
function onWt(vid,gid2,v){const vak=vakken.find(x=>x.id===vid);if(!vak)return;const g=vak.grades.find(g=>g.id===gid2);if(!g)return;g.wt=v;dsave();updVak(vid);updSum();doPredict();calcScen();}
function onName(vid,v){const vak=vakken.find(x=>x.id===vid);if(vak){vak.name=v;dsave();updPredSel();updScenName(vid,v);if(document.getElementById(‘tv-overview’).classList.contains(‘active’))renderOv();}}

// TARGETED UPDATES
function updPill(vid,gid2,v){const p=document.getElementById(`pill-${vid}-${gid2}`);if(!p)return;const n=v!==’’&&!isNaN(+v)?+v:null;const c=gc(n);p.style.background=c+‘22’;p.style.color=c;p.textContent=n!==null?n.toFixed(1):’—’;}
function updVak(vid){const vak=vakken.find(v=>v.id===vid);if(!vak)return;const a=avg(vak.grades);const ae=document.querySelector(`#vc-${vid} .va`);if(ae){ae.textContent=fmt(a);ae.style.color=gc(a);}const fl=vak.grades.filter(g=>g.val!==’’&&!isNaN(+g.val));const sl=document.querySelector(`#vc-${vid} .vsl`);if(sl)sl.textContent=`${fl.length} cijfer${fl.length!==1?'s':''}`;updStats(vid);const fi=document.querySelector(`#vc-${vid} .vfi`);if(fi)fi.innerHTML=footInfo(vak,a);rebuildChart(vid);}
function footInfo(vak,a){if(a===null)return’Voeg cijfers toe om te berekenen’;if(a>=PASS)return`✅ Voldoende! Huidig: <strong>${a.toFixed(2)}</strong>`;const n=needed(vak.grades,PASS,1);return`⚠️ Voor een 5,5: nog <strong>${Math.min(10,Math.max(1,n)).toFixed(1)}</strong> nodig (weging 1)`;}
function updStats(vid){const vak=vakken.find(v=>v.id===vid);if(!vak)return;const fl=vak.grades.filter(g=>g.val!==’’&&!isNaN(+g.val));const a=avg(vak.grades);const hi=fl.length?Math.max(…fl.map(g=>+g.val)):null;const lo=fl.length?Math.min(…fl.map(g=>+g.val)):null;const s=document.querySelector(`#vc-${vid} .vsr`);if(!s)return;const sa=s.querySelector(’.sa’);if(sa){sa.textContent=fmt(a,2);sa.style.color=gc(a);}const sh=s.querySelector(’.shi’);if(sh)sh.textContent=fmt(hi);const sl=s.querySelector(’.slo’);if(sl){sl.textContent=fmt(lo);sl.style.color=gc(lo);}const sc=s.querySelector(’.sco’);if(sc)sc.textContent=fl.length;}
function rebuildChart(vid){const vak=vakken.find(v=>v.id===vid);if(!vak)return;const fl=vak.grades.filter(g=>g.val!==’’&&!isNaN(+g.val));const crs=document.querySelector(`#vc-${vid} .crs`);const cw=document.querySelector(`#vc-${vid} .vct`);if(!crs||!cw){if(fl.length)rebuildBody(vid);return;}if(!fl.length){cw.style.display=‘none’;return;}cw.style.display=‘block’;crs.innerHTML=fl.map(g=>{const p=Math.max(4,(+g.val/10)*100);const c=gc(+g.val);return`<div class="cr2"><div class="cl" id="chl-${vid}-${g.id}" title="${esc(g.desc||'Toets')}">${esc(g.desc||'Toets')}</div><div class="ct"><div class="cf" style="width:${p}%;background:${c};">${(+g.val).toFixed(1)}</div><div class="cpl"></div></div></div>`;}).join(’’);}
function updScenName(vid,name){const e=document.querySelector(`#sc-${vid} .svn`);if(e)e.textContent=name;}

// FULL REBUILD
function mkRow(vid,g){const v=g.val!==’’&&!isNaN(+g.val)?+g.val:null;const c=gc(v);const d=document.createElement(‘div’);d.className=‘gr’;d.id=`gr-${vid}-${g.id}`;d.innerHTML=`<input type="text" class="gin" placeholder="Omschrijving..." value="${esc(g.desc)}" oninput="onDesc(${vid},${g.id},this.value)"><input type="number" class="gin num" placeholder="—" min="1" max="10" step="0.1" value="${esc(g.val)}" oninput="onVal(${vid},${g.id},this.value)"><input type="number" class="gin num" placeholder="1" min="0.1" max="20" step="0.5" value="${esc(g.wt)}" oninput="onWt(${vid},${g.id},this.value)"><div class="gp" id="pill-${vid}-${g.id}" style="background:${c}22;color:${c};">${v!==null?v.toFixed(1):'—'}</div><button class="db" onclick="delGrade(${vid},${g.id})">✕</button>`;return d;}
function rebuildBody(vid){const vak=vakken.find(v=>v.id===vid);if(!vak)return;const b=document.querySelector(`#vc-${vid} .vb`);if(!b)return;const a=avg(vak.grades);const fl=vak.grades.filter(g=>g.val!==’’&&!isNaN(+g.val));const hi=fl.length?Math.max(…fl.map(g=>+g.val)):null;const lo=fl.length?Math.min(…fl.map(g=>+g.val)):null;const chartH=fl.map(g=>{const p=Math.max(4,(+g.val/10)*100);const c=gc(+g.val);return`<div class="cr2"><div class="cl" id="chl-${vid}-${g.id}" title="${esc(g.desc||'Toets')}">${esc(g.desc||'Toets')}</div><div class="ct"><div class="cf" style="width:${p}%;background:${c};">${(+g.val).toFixed(1)}</div><div class="cpl"></div></div></div>`;}).join(’’);b.innerHTML=`<div class="vsr"><div class="vst"><div class="vsv sa" style="color:${gc(a)}">${fmt(a,2)}</div><div class="vsl2">Gemiddelde</div></div><div class="vst"><div class="vsv shi" style="color:var(--green)">${fmt(hi)}</div><div class="vsl2">Hoogste</div></div><div class="vst"><div class="vsv slo" style="color:${gc(lo)}">${fmt(lo)}</div><div class="vsl2">Laagste</div></div><div class="vst"><div class="vsv sco" style="color:var(--blue2)">${fl.length}</div><div class="vsl2">Cijfers</div></div></div>${vak.grades.length?`<div class="gh"><span>Omschrijving</span><span>Cijfer</span><span>Weging</span><span>Status</span><span></span></div><div class="grades-list"></div>`:`<div class="ngl" style="text-align:center;padding:16px;color:var(--text3);font-size:13px;">Geen cijfers — voeg ze hieronder toe</div>`}<button class="agb" onclick="addGrade(${vid})">＋ Voeg cijfer toe</button>${fl.length?`<div class="vct"><div class="vct-title">Cijfers visualisatie</div><div class="crs">${chartH}</div></div>`:''}<div class="vf"><div class="vfi">${footInfo(vak,a)}</div><button class="dvb" onclick="delVak(${vid})">🗑 Verwijder</button></div>`;const gl=b.querySelector(’.grades-list’);if(gl)vak.grades.forEach(g=>gl.appendChild(mkRow(vid,g)));}
function renderVakken(){const el=document.getElementById(‘vakkenList’);if(!vakken.length){el.innerHTML=’<div class="es"><div class="ei">📚</div><div class="ett">Nog geen vakken</div><div class="es2">Klik op “+ Vak toevoegen” om te beginnen</div></div>’;return;}el.innerHTML=vakken.map((vak,vi)=>{const isOpen=openVakken.has(vak.id);const a=avg(vak.grades);const fl=vak.grades.filter(g=>g.val!==’’&&!isNaN(+g.val));return`<div class="vc" id="vc-${vak.id}" style="animation-delay:${vi*.05}s"><div class="vh" onclick="toggleVak(${vak.id})"><div class="vs" style="background:${vak.color}"></div><div class="vn"><input type="text" class="vni" value="${esc(vak.name)}" placeholder="Vaknaam..." onclick="event.stopPropagation()" oninput="onName(${vak.id},this.value)"><div class="vsl">${fl.length} cijfer${fl.length!==1?'s':''}</div></div><div class="va" style="color:${gc(a)}">${fmt(a)}</div><div class="vch ${isOpen?'open':''}">▼</div></div><div class="vb ${isOpen?'open':''}"></div></div>`;}).join(’’);vakken.forEach(vak=>rebuildBody(vak.id));}
function toggleVak(id){const b=document.querySelector(`#vc-${id} .vb`);const c=document.querySelector(`#vc-${id} .vch`);if(!b)return;const o=b.classList.contains(‘open’);if(o){b.classList.remove(‘open’);c&&c.classList.remove(‘open’);openVakken.delete(id);}else{b.classList.add(‘open’);c&&c.classList.add(‘open’);openVakken.add(id);}}
function rebuild(){renderVakken();updSum();updPredSel();renderScen();if(document.getElementById(‘tv-overview’).classList.contains(‘active’))renderOv();document.getElementById(‘sl’).textContent=lastSavedStr();}

// SUMMARY
function updSum(){const avgs=vakken.map(v=>avg(v.grades)).filter(a=>a!==null);const tot=avgs.length?avgs.reduce((s,a)=>s+a,0)/avgs.length:null;const pass=avgs.filter(a=>a>=PASS).length;const fail=avgs.filter(a=>a<PASS).length;const hi=avgs.length?Math.max(…avgs):null;const hv=hi!==null?vakken.find(v=>{const a=avg(v.grades);return a!==null&&Math.abs(a-hi)<.001;}):null;document.getElementById(‘sAvg’).textContent=fmt(tot);document.getElementById(‘sAvg’).className=‘sc-val ‘+gcls(tot);document.getElementById(‘sSub’).textContent=avgs.length?`gemiddelde over ${avgs.length} vak${avgs.length!==1?'ken':''}`:‘Voeg vakken toe’;document.getElementById(‘sPass’).textContent=pass;document.getElementById(‘sFail’).textContent=fail;document.getElementById(‘sTotal’).textContent=avgs.length;document.getElementById(‘sHigh’).textContent=fmt(hi);document.getElementById(‘sHighSub’).textContent=hv?hv.name:’—’;}

// PREDICT
function updPredSel(){const s=document.getElementById(‘pVak’);const cur=s.value;s.innerHTML=’<option value="">— Kies een vak —</option>’+vakken.map(v=>`<option value="${v.id}" ${v.id==cur?'selected':''}>${esc(v.name)}</option>`).join(’’);}
function doPredict(){const vid=+document.getElementById(‘pVak’).value;const tgt=+document.getElementById(‘pTarget’).value;const wt=+document.getElementById(‘pWeight’).value;const box=document.getElementById(‘pResult’);if(!vid||isNaN(tgt)||isNaN(wt)||wt<=0){box.classList.remove(‘show’);return;}const vak=vakken.find(v=>v.id===vid);if(!vak){box.classList.remove(‘show’);return;}const n=needed(vak.grades,tgt,wt);const cur=avg(vak.grades);box.classList.add(‘show’);const rn=document.getElementById(‘pRN’);const rd=document.getElementById(‘pRD’);const pf=document.getElementById(‘pPF’);let col,pct,txt;if(n<=1){rn.textContent=‘≤ 1.0 ✅’;col=‘var(–green)’;pct=100;txt=`Je haalt al een ${tgt.toFixed(1)} ongeacht je toetscijfer. Huidig: ${fmt(cur,2)}.`;}else if(n>10){rn.textContent=’> 10 ❌’;col=‘var(–red)’;pct=8;txt=`Niet meer haalbaar met huidige cijfers. Huidig: ${fmt(cur,2)}.`;}else{rn.textContent=n.toFixed(2);col=n<=7?‘var(–green)’:n<=8.5?‘var(–orange)’:‘var(–red)’;pct=Math.max(5,((10-n)/9)*100);txt=`Je hebt een ${n.toFixed(2)} nodig (weging ${wt}) voor een ${tgt.toFixed(1)} in ${vak.name}. Huidig: ${fmt(cur,2)}.`;}rn.style.color=col;rd.textContent=txt;pf.style.width=pct+’%’;pf.style.background=col;}

// SCENARIO
function renderScen(){const el=document.getElementById(‘scenCards’);if(!vakken.length){el.innerHTML=’<p style="color:var(--text3);font-size:13px;margin-bottom:12px">Voeg eerst vakken toe.</p>’;return;}el.innerHTML=vakken.map(vak=>{const cur=avg(vak.grades);return`<div class="svc" id="sc-${vak.id}"><div class="svh"><div class="svd" style="background:${vak.color}"></div><div class="svn">${esc(vak.name)}</div><div class="svc2">Huidig: <b style="color:${gc(cur)}">${fmt(cur)}</b></div></div><div class="sff"><div class="sfl"><label>Verwacht nieuw cijfer</label><input type="number" class="gin num" id="sv-${vak.id}" placeholder="—" min="1" max="10" step="0.1" oninput="calcScen()"></div><div class="sfl"><label>Weging van deze toets</label><input type="number" class="gin num" id="sw-${vak.id}" value="1" min="0.1" max="10" step="0.5" oninput="calcScen()"></div></div><div class="sr2"><div class="srl">Nieuw gemiddelde dit vak</div><div class="srn" id="sr-${vak.id}" style="color:var(--text3)">—</div></div></div>`;}).join(’’);calcScen();}
function calcScen(){let tot=0,cnt=0,fails=0;vakken.forEach(vak=>{const ve=document.getElementById(`sv-${vak.id}`);const we=document.getElementById(`sw-${vak.id}`);const re=document.getElementById(`sr-${vak.id}`);if(!ve)return;const nv=parseFloat(ve.value),nw=parseFloat(we.value)||1;const na=(!isNaN(nv)&&nv>=1&&nv<=10)?avg([…vak.grades,{val:nv,wt:nw}]):avg(vak.grades);if(re){re.textContent=fmt(na,2);re.style.color=gc(na);}if(na!==null){tot+=na;cnt++;if(na<PASS)fails++;}});const el=document.getElementById(‘scenTotal’);if(!cnt){el.textContent=’—’;el.style.color=‘var(–text3)’;return;}const a=tot/cnt;el.textContent=a.toFixed(2)+(fails>0?` (${fails} onvoldoende)`:’ ✅’);el.style.color=gc(a);}

// OVERVIEW
function renderOv(){const el=document.getElementById(‘ovContent’);if(!vakken.length){el.innerHTML=’<p style="color:var(--text3);text-align:center;padding:40px">Nog geen vakken.</p>’;return;}const bars=vakken.map(vak=>{const a=avg(vak.grades);const p=a!==null?Math.max(4,(a/10)*100):0;const c=gc(a);return`<div class="fcw"><div class="fck"><div class="fcf" style="height:${p}%;background:${c};"><div class="fcfl" style="color:${c}">${fmt(a)}</div></div><div class="fcpl"></div></div><div class="fcl">${esc(vak.name)}</div></div>`;}).join(’’);const cards=vakken.map((vak,vi)=>{const a=avg(vak.grades);const fl=vak.grades.filter(g=>g.val!==’’&&!isNaN(+g.val));const p=a!==null?Math.max(4,(a/10)*100):0;const isP=a!==null&&a>=PASS;const pb=isP?‘rgba(16,217,130,.12)’:a!==null?‘rgba(244,63,94,.12)’:‘var(–s3)’;const pc=isP?‘var(–green)’:a!==null?‘var(–red)’:‘var(–text3)’;const gl=fl.slice(0,5).map(g=>`<div class="ogr"><span style="color:var(--text2);flex:1;overflow:hidden;text-overflow:ellipsis;white-space:nowrap">${esc(g.desc||'Toets')}</span><span style="font-family:'Clash Display',sans-serif;font-weight:700;color:${gc(+g.val)};margin-left:8px">${(+g.val).toFixed(1)}</span><span style="color:var(--text3);font-size:11px;margin-left:5px">×${g.wt}</span></div>`).join(’’);const more=fl.length>5?`<div style="font-size:11px;color:var(--text3);margin-top:5px">+${fl.length-5} meer...</div>`:’’;return`<div class="oc" style="animation-delay:${vi*.05}s"><div class="ot"><div class="od" style="background:${vak.color}"></div><div class="on">${esc(vak.name)}</div><div class="oa" style="color:${gc(a)}">${fmt(a)}</div></div><div style="font-size:12px;color:var(--text3)">${fl.length} cijfer${fl.length!==1?'s':''}</div><div class="ob"><div class="obf" style="width:${p}%;background:${gc(a)}"></div><div class="opl"></div></div><div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:10px"><span class="op" style="background:${pb};color:${pc}">${a!==null?(isP?'Voldoende':'Onvoldoende'):'Geen data'}</span><span style="font-size:11px;color:var(--text3)">grens 5,5</span></div>${gl}${more}</div>`;}).join(’’);el.innerHTML=`<div class="fcc"><div class="fct">📊 Gemiddelden per vak</div><div class="fcb">${bars}</div></div><div class="og">${cards}</div>`;}

// TABS
function switchTab(tab,btn){document.querySelectorAll(’.tb’).forEach(b=>b.classList.remove(‘active’));btn.classList.add(‘active’);document.querySelectorAll(’.tv’).forEach(v=>v.classList.remove(‘active’));document.getElementById(‘tv-’+tab).classList.add(‘active’);if(tab===‘predict’){updPredSel();renderScen();doPredict();}if(tab===‘overview’)renderOv();}

// INIT
(function(){const loaded=load();if(!loaded){const addV=(name,color)=>{const id=uid++;vakken.push({id,name,color,grades:[]});return id;};const setG=(id,list)=>{const v=vakken.find(x=>x.id===id);if(v)v.grades=list.map((r,i)=>({id:gid++,desc:r[0],val:r[1],wt:r[2]}));};const w=addV(‘Wiskunde’,’#3d7eff’);const n=addV(‘Nederlands’,’#10d982’);const e=addV(‘Engels’,’#8b5cf6’);setG(w,[[‘Toets H1’,‘7.2’,‘1’],[‘Toets H2’,‘5.8’,‘1’],[‘Proefwerk’,‘6.5’,‘2’]]);setG(n,[[‘Schrijfopdracht’,‘6.8’,‘1’],[‘Grammatica’,‘4.9’,‘1’]]);setG(e,[[‘Listening test’,‘8.1’,‘1’],[‘Essay’,‘7.5’,‘2’]]);openVakken.add(w);}else{if(vakken.length)openVakken.add(vakken[0].id);}rebuild();document.getElementById(‘sl’).textContent=loaded?lastSavedStr():‘Demodata — voeg jouw eigen vakken toe’;})();
</script>

</body>
</html>