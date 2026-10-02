[gethub.txt](https://github.com/user-attachments/files/32984987/gethub.txt)
v<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Sala</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Public+Sans:wght@400;500;600;700&family=Source+Serif+4:ital,opsz,wght@0,8..60,400;0,8..60,600;1,8..60,400&display=swap" rel="stylesheet">
<style>
:root{
  --palco:#191D25; --palco-2:#222731; --palco-3:#2E3441; --borda:#383F4E;
  --claro:#E9ECF2; --apagado:#9AA3B4;
  --tinta:#1C3FAA; --tinta-viva:#5D7EF2; --lacre:#C9382E; --selo:#3E9C72;
  --folha:#FBFBF8; --pauta:#DDE5F3; --margem:#E7A39E; --texto:#22262E; --suave:#646B78;
  --sans:'Public Sans',system-ui,-apple-system,'Segoe UI',sans-serif;
  --serif:'Source Serif 4',Georgia,serif;
}
*{box-sizing:border-box}
html,body{margin:0;height:100%}
body{background:var(--palco);color:var(--claro);font:15px/1.5 var(--sans);-webkit-font-smoothing:antialiased;
  padding:env(safe-area-inset-top,0) env(safe-area-inset-right,0) env(safe-area-inset-bottom,0) env(safe-area-inset-left,0)}
button,input{font:inherit;color:inherit}
:focus-visible{outline:2px solid var(--tinta-viva);outline-offset:2px}
.oculto{display:none!important}
svg{width:20px;height:20px;flex:none}

/* ---------- Estados simples ---------- */
.estado{min-height:100%;display:flex;align-items:center;justify-content:center;padding:32px;text-align:center}
.estado > div{max-width:480px}
.estado .marca{font-family:var(--serif);font-weight:600;font-size:56px;line-height:1;margin:0 0 28px;color:var(--claro)}
.estado h1{font-family:var(--serif);font-weight:600;font-size:28px;margin:0 0 8px}
.estado p{color:var(--apagado);margin:0}

/* ---------- Antes de entrar ---------- */
.pre{min-height:100%;display:grid;grid-template-columns:minmax(0,1.25fr) minmax(320px,1fr);gap:48px;align-items:center;max-width:1160px;margin:0 auto;padding:40px 32px}
.previa{position:relative;aspect-ratio:16/9;background:var(--palco-2);border-radius:14px;overflow:hidden}
.previa video{width:100%;height:100%;object-fit:cover;transform:scaleX(-1)}
.previa .sem-cam{position:absolute;inset:0;display:grid;place-items:center;color:var(--apagado);font-size:14px}
.previa .botoes{position:absolute;left:0;right:0;bottom:14px;display:flex;justify-content:center;gap:10px}
.pre-info .num{font-family:var(--serif);font-style:italic;color:var(--apagado);font-size:17px;margin:0}
.pre-info h1{font-family:var(--serif);font-weight:600;font-size:clamp(28px,3.4vw,42px);line-height:1.1;margin:6px 0 10px}
.pre-info .org{color:var(--apagado);margin:0 0 18px}
.pre-info .pauta{margin:0 0 24px;padding-left:20px;color:#C9CFDB}
.pre-info .pauta li{margin:2px 0}
.campo{display:block;margin-bottom:12px}
.campo span{display:block;font-size:13px;font-weight:600;margin-bottom:5px;color:#C9CFDB}
.campo input{width:100%;background:var(--palco-2);border:1px solid var(--borda);border-radius:8px;padding:10px 12px}
.campo input:focus{outline:none;border-color:var(--tinta-viva);box-shadow:0 0 0 3px rgba(93,126,242,.25)}
.dupla{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.btn{display:inline-flex;align-items:center;justify-content:center;gap:8px;border:0;border-radius:9px;padding:12px 20px;font-weight:600;cursor:pointer;background:var(--tinta-viva);color:#fff}
.btn:hover{background:#4C6DE0}
.btn:disabled{opacity:.6;cursor:progress}
.btn.cheio{width:100%;margin-top:6px}
.erro-msg{color:#FF8A80;font-size:13.5px;min-height:20px;margin:8px 0 0}
.nota{font-size:13px;color:var(--apagado);margin:12px 0 0}
.nota.alerta{color:#F2C46D}

/* ---------- Botões redondos (controles) ---------- */
.ctl{width:48px;height:48px;border-radius:50%;border:0;display:grid;place-items:center;cursor:pointer;background:var(--palco-3);color:var(--claro);transition:background .15s}
.ctl:hover{background:#3A4252}
.ctl.desligado{background:var(--lacre);color:#fff}
.ctl.ativo{background:var(--tinta-viva);color:#fff}
.ctl.sair{width:64px;border-radius:24px;background:var(--lacre);color:#fff}
.ctl.sair:hover{background:#B02E25}
.ctl:disabled{opacity:.4;cursor:not-allowed}

/* ---------- Sala ---------- */
.sala{display:grid;grid-template-columns:minmax(0,1fr) 400px;grid-template-rows:58px minmax(0,1fr) 84px;height:100vh;height:100dvh}
body.sem-registro .sala{grid-template-columns:minmax(0,1fr) 0}
body.sem-registro .registro{display:none}
.topo{grid-column:1/-1;display:flex;align-items:center;gap:16px;padding:0 20px;min-width:0}
.topo .marca{font-family:var(--serif);font-weight:600;font-size:22px}
.topo .tit{flex:1;min-width:0;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;color:#C9CFDB}
.topo .tempo{color:var(--apagado);font-size:13.5px;font-variant-numeric:tabular-nums;white-space:nowrap}
.aviso-rede{position:fixed;top:66px;left:50%;transform:translateX(-50%);background:#5A4512;color:#FBE3A6;padding:8px 14px;border-radius:8px;font-size:13.5px;z-index:30;max-width:90vw;text-align:center}

.palco{grid-column:1;grid-row:2;padding:6px 16px 0;min-height:0}
.grade{display:grid;gap:10px;height:100%;min-height:0}
.tile{position:relative;background:var(--palco-2);border-radius:12px;overflow:hidden;min-height:0}
.tile video{width:100%;height:100%;object-fit:cover;display:block;background:#11141A}
.tile.eu video.espelho{transform:scaleX(-1)}
.tile.tela video{object-fit:contain}
.tile .avatar{position:absolute;inset:0;display:none;place-items:center;background:var(--palco-2)}
.tile .avatar b{width:84px;height:84px;border-radius:50%;background:var(--tinta);display:grid;place-items:center;font-size:30px;font-weight:600;color:#fff}
.tile.sem-video .avatar{display:grid}
.tile .rot{position:absolute;left:10px;bottom:10px;display:flex;align-items:center;gap:6px;background:rgba(17,20,26,.72);padding:4px 10px;border-radius:7px;font-size:13px;max-width:calc(100% - 20px)}
.tile .rot span{white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.tile .rot svg{width:15px;height:15px;color:#FF8A80;display:none}
.tile.mudo .rot svg{display:block}
.tile .rot em{font-style:normal;color:var(--apagado);font-size:12px}
.tile .conectando{position:absolute;top:10px;right:10px;font-size:12px;color:var(--apagado);background:rgba(17,20,26,.72);padding:3px 9px;border-radius:6px;display:none}
.tile.aguardando .conectando{display:block}

.controles{grid-column:1;grid-row:3;display:flex;align-items:center;justify-content:center;gap:12px}

/* O registro: folha pautada sobre a mesa escura */
.registro{grid-column:2;grid-row:2/4;margin:6px 16px 16px 0;display:flex;flex-direction:column;min-height:0;
  background:var(--folha);color:var(--texto);border-radius:4px;box-shadow:0 24px 50px -20px rgba(0,0,0,.6);overflow:hidden}
.registro header{padding:16px 20px 12px 20px;border-bottom:1px solid #E3E7EF;display:flex;justify-content:space-between;align-items:flex-start;gap:10px}
.registro h2{font-family:var(--serif);font-weight:600;font-size:20px;margin:0}
.registro header p{margin:2px 0 0;color:var(--suave);font-size:12.5px}
.registro .fechar{background:none;border:0;color:var(--suave);cursor:pointer;padding:4px;display:none}
.registro .aviso-sr{background:#FBEFD8;color:#6B4705;font-size:12.5px;padding:8px 20px}
.folha{
  --l:30px;flex:1;overflow-y:auto;
  background-image:
    linear-gradient(to right,transparent 58px,var(--margem) 58px,var(--margem) 59px,transparent 59px),
    repeating-linear-gradient(to bottom,transparent 0,transparent calc(var(--l) - 1px),var(--pauta) calc(var(--l) - 1px),var(--pauta) var(--l));
  background-attachment:local;
  padding:var(--l) 18px var(--l) 70px;font-family:var(--serif);font-size:15.5px;line-height:var(--l)}
.fala{position:relative;margin:0}
.fala .h{position:absolute;left:-64px;width:48px;text-align:right;font-family:var(--sans);font-size:11px;color:#9AA3B2;font-variant-numeric:tabular-nums}
.fala b{font-weight:600;color:var(--tinta)}
.fala.minha b{color:#2F7D5B}
.interim{color:#8C94A3;font-style:italic;margin:0}
.folha .vazio{color:#8C94A3;font-style:italic;margin:0}

.fundo{position:fixed;inset:0;background:rgba(8,10,14,.6);display:flex;align-items:center;justify-content:center;padding:16px;z-index:60}
.caixa{background:var(--palco-2);border:1px solid var(--borda);border-radius:14px;padding:26px;width:min(420px,100%)}
.caixa h2{font-family:var(--serif);font-weight:600;font-size:23px;margin:0 0 6px}
.caixa p{color:var(--apagado);margin:0 0 20px}
.caixa .acoes{display:flex;flex-direction:column;gap:8px}
.caixa .btn.sec{background:var(--palco-3);color:var(--claro)}
.caixa .btn.perigo{background:var(--lacre)}
.toast{position:fixed;left:50%;bottom:104px;transform:translateX(-50%);background:var(--claro);color:var(--texto);padding:9px 16px;border-radius:9px;font-size:14px;z-index:70;opacity:0;transition:opacity .2s;pointer-events:none}
.toast.on{opacity:1}

@media (max-width:900px){
  .pre{grid-template-columns:1fr;gap:24px;padding:20px 16px}
  .sala{grid-template-columns:1fr}
  body.sem-registro .sala{grid-template-columns:1fr}
  .registro{position:fixed;left:8px;right:8px;bottom:92px;top:30%;margin:0;z-index:40}
  .registro .fechar{display:block}
  body:not(.ver-registro) .registro{display:none}
  .palco{padding:4px 8px 0}
  .topo{padding:0 12px}
  .controles{gap:8px}
  .ctl{width:44px;height:44px}
  .dupla{grid-template-columns:1fr}
}
@media (prefers-reduced-motion:reduce){*{transition:none!important}}
</style>
</head>
<body>

<!-- Carregando / erro / fim -->
<div id="telaEstado" class="estado"><div><p class="marca">Sala</p><h1 id="estTit">Abrindo a sala…</h1><p id="estMsg"></p></div></div>

<!-- Antes de entrar -->
<div id="telaPre" class="pre oculto">
  <div>
    <div class="previa">
      <video id="previa" autoplay playsinline muted></video>
      <div class="sem-cam oculto" id="semCamPre">Câmera desligada</div>
      <div class="botoes">
        <button class="ctl" id="pMic" title="Ligar ou desligar microfone"></button>
        <button class="ctl" id="pCam" title="Ligar ou desligar câmera"></button>
      </div>
    </div>
    <p class="nota" id="notaMidia"></p>
  </div>
  <div class="pre-info">
    <p class="num" id="preNum"></p>
    <h1 id="preTit"></h1>
    <p class="org" id="preOrg"></p>
    <ol class="pauta" id="prePauta"></ol>
    <form id="fEntrar">
      <label class="campo"><span>Seu nome completo</span><input id="iNome" maxlength="80" autocomplete="name" required></label>
      <div class="dupla">
        <label class="campo"><span>E-mail</span><input id="iEmail" type="email" maxlength="120" autocomplete="email"></label>
        <label class="campo"><span>Cargo ou função</span><input id="iCargo" maxlength="80"></label>
      </div>
      <button class="btn cheio" id="bEntrar" type="submit">Entrar na reunião</button>
      <p class="erro-msg" id="erroEntrar"></p>
      <p class="nota" id="notaSR"></p>
    </form>
  </div>
</div>

<!-- Reunião -->
<div id="telaSala" class="sala oculto">
  <div class="topo">
    <span class="marca">Sala</span>
    <span class="tit" id="salaTit"></span>
    <span class="tempo" id="tempo"></span>
  </div>
  <div class="palco"><div class="grade" id="grade"></div></div>
  <div class="controles">
    <button class="ctl" id="cMic" title="Microfone"></button>
    <button class="ctl" id="cCam" title="Câmera"></button>
    <button class="ctl" id="cTela" title="Apresentar a tela"></button>
    <button class="ctl ativo" id="cReg" title="Registro ao vivo"></button>
    <button class="ctl" id="cLink" title="Copiar link da reunião"></button>
    <button class="ctl sair" id="cSair" title="Sair da reunião"></button>
  </div>
  <section class="registro" aria-label="Registro ao vivo">
    <header>
      <div><h2>Registro ao vivo</h2><p>Sua fala entra aqui enquanto o microfone estiver ligado.</p></div>
      <button class="fechar" id="fecharReg" title="Fechar registro"></button>
    </header>
    <div class="aviso-sr oculto" id="avisoSR">Este navegador não transcreve fala. Use Chrome ou Edge no computador para que suas falas entrem no documento.</div>
    <div class="folha" id="folha"><p class="vazio" id="folhaVazia">As falas aparecem aqui assim que alguém começar a falar.</p><p class="interim" id="interim"></p></div>
  </section>
</div>

<div id="avisoRede" class="aviso-rede oculto"></div>
<div id="modal"></div>
<div id="toast" class="toast" role="status" aria-live="polite"></div>

<script>
/* ============================================================
 *  CONFIGURAÇÃO: cole aqui a URL do App da Web do Apps Script
 * ============================================================ */
const API_URL = 'https://script.google.com/macros/s/AKfycbxZOnRToy_FH5CxU3u5XWyDNPgF4GdCtkUtXMVj3QA35CgvAvFlCL4hi2l1rWjMseRx/exec';

const ICE = [{ urls: ['stun:stun.l.google.com:19302', 'stun:stun1.l.google.com:19302'] }];
const SR = window.SpeechRecognition || window.webkitSpeechRecognition;
const qs = new URLSearchParams(location.search);
const SALA = (qs.get('s') || '').trim();
const CHAVE = qs.get('h') || '';
const ENCERRADOS = ['Encerrada', 'Documento gerado', 'Em assinatura', 'Concluída'];

const S = {
  info: null, peer: null, host: false, nome: '', email: '', cargo: '',
  stream: new MediaStream(), tela: null, mic: false, cam: false, temMic: false, temCam: false,
  ultimaSeq: 0, saida: [], falasPend: [], presenca: [], conns: new Map(),
  dentro: false, fim: false, falhas: 0, entrouEm: 0,
  rec: null, recAtivo: false, recBloqueado: false
};
const $ = id => document.getElementById(id);

const I = {
  mic: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="9" y="3" width="6" height="11" rx="3"/><path d="M5 11a7 7 0 0 0 14 0"/><path d="M12 18v3"/></svg>',
  micOff: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="9" y="3" width="6" height="11" rx="3"/><path d="M5 11a7 7 0 0 0 14 0"/><path d="M12 18v3"/><path d="M4 4l16 16"/></svg>',
  cam: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="6" width="13" height="12" rx="2"/><path d="M16 10.5l5-3v9l-5-3"/></svg>',
  camOff: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="6" width="13" height="12" rx="2"/><path d="M16 10.5l5-3v9l-5-3"/><path d="M3 3l18 18"/></svg>',
  tela: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="4" width="18" height="12" rx="2"/><path d="M8 20h8"/><path d="M12 16v4"/></svg>',
  reg: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M6 3h9l4 4v14H6z"/><path d="M9 11h7"/><path d="M9 15h7"/><path d="M9 7h3"/></svg>',
  link: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M10 14a4 4 0 0 0 5.66 0l3-3a4 4 0 0 0-5.66-5.66l-1 1"/><path d="M14 10a4 4 0 0 0-5.66 0l-3 3a4 4 0 0 0 5.66 5.66l1-1"/></svg>',
  sair: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3.5 14.5c4.7-4.2 12.3-4.2 17 0l-1.8 2.6-3.9-1.1v-2.6a9.5 9.5 0 0 0-5.6 0V16l-3.9 1.1z"/></svg>',
  x: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><path d="M6 6l12 12M18 6L6 18"/></svg>'
};

/* ================= Utilidades ================= */
function esc(s) { return String(s == null ? '' : s).replace(/[&<>"']/g, c => ({ '&': '&amp;', '<': '&lt;', '>': '&gt;', '"': '&quot;', "'": '&#39;' }[c])); }
function iniciais(n) { return String(n || '?').trim().split(/\s+/).filter(Boolean).slice(0, 2).map(x => x[0]).join('').toUpperCase(); }
function tipoLabel(t) { return ({ 'Ata': 'Ata', 'Relatório': 'Relatório', 'Reunião': 'Resumo de reunião' })[t] || t; }
async function api(corpo) {
  const r = await fetch(API_URL, { method: 'POST', headers: { 'Content-Type': 'text/plain;charset=utf-8' }, body: JSON.stringify(corpo) });
  const j = await r.json();
  if (!j.ok) throw new Error(j.erro || 'O servidor da Sala não respondeu.');
  return j;
}
function mostrar(qual) { ['telaEstado', 'telaPre', 'telaSala'].forEach(id => $(id).classList.toggle('oculto', id !== qual)); }
function telaEstado(tit, msg) { $('estTit').textContent = tit; $('estMsg').textContent = msg || ''; mostrar('telaEstado'); }
function toast(msg) { const t = $('toast'); t.textContent = msg; t.classList.add('on'); clearTimeout(t._t); t._t = setTimeout(() => t.classList.remove('on'), 2600); }
function avisoRede(msg) { const a = $('avisoRede'); a.textContent = msg; a.classList.toggle('oculto', !msg); }
function linkParticipantes() { return location.origin + location.pathname + '?s=' + encodeURIComponent(SALA); }
async function copiar(t) {
  try { await navigator.clipboard.writeText(t); toast('Link copiado.'); }
  catch (e) { prompt('Copie o link da reunião:', t); }
}

/* ================= Início ================= */
(async function iniciar() {
  if (!/^https:\/\//.test(API_URL)) return telaEstado('A sala ainda não foi configurada', 'Cole a URL do App da Web na variável API_URL deste arquivo.');
  if (!SALA) return telaEstado('Link incompleto', 'Abra o link exatamente como você recebeu do organizador.');
  try { S.info = await api({ action: 'info', sala: SALA, h: CHAVE }); }
  catch (e) { return telaEstado('Não foi possível abrir a sala', e.message); }
  if (ENCERRADOS.includes(S.info.status)) return telaEstado('Esta reunião já foi encerrada', 'O documento está com o organizador.');
  montarPre();
  await abrirMidia();
})();

function montarPre() {
  const i = S.info;
  document.title = i.titulo + ' | Sala';
  $('preNum').textContent = tipoLabel(i.tipo) + ' nº ' + i.numero;
  $('preTit').textContent = i.titulo;
  $('preOrg').textContent = i.organizador ? 'Organização: ' + i.organizador + (i.host ? ' (você)' : '') : (i.host ? 'Você é o organizador desta reunião.' : '');
  $('prePauta').innerHTML = (i.pauta || '').split('\n').filter(x => x.trim()).map(x => `<li>${esc(x)}</li>`).join('');
  try {
    const p = JSON.parse(localStorage.getItem('sala_eu') || '{}');
    $('iNome').value = p.nome || ''; $('iEmail').value = p.email || ''; $('iCargo').value = p.cargo || '';
  } catch (e) {}
  if (!SR) { $('notaSR').textContent = 'Seu navegador não transcreve fala. Use Chrome ou Edge no computador para que suas falas entrem no documento.'; $('notaSR').classList.add('alerta'); }
  else $('notaSR').textContent = 'Use fone de ouvido: assim a transcrição registra só a sua voz.';
  $('pMic').onclick = () => { alternarMic(); atualizarBotoesPre(); };
  $('pCam').onclick = () => { alternarCam(); atualizarBotoesPre(); };
  $('fEntrar').addEventListener('submit', entrar);
  mostrar('telaPre');
}

async function abrirMidia() {
  const audio = { echoCancellation: true, noiseSuppression: true, autoGainControl: true };
  try {
    S.stream = await navigator.mediaDevices.getUserMedia({ audio, video: { width: { ideal: 960 }, height: { ideal: 540 } } });
  } catch (e) {
    try {
      S.stream = await navigator.mediaDevices.getUserMedia({ audio });
      $('notaMidia').textContent = 'Câmera indisponível. Você entra só com áudio.';
    } catch (e2) {
      S.stream = new MediaStream();
      $('notaMidia').textContent = 'Não foi possível acessar câmera e microfone. Permita o acesso no ícone do cadeado, ao lado do endereço, e recarregue a página. Você ainda pode entrar para ver e ouvir.';
    }
  }
  S.temMic = S.stream.getAudioTracks().length > 0;
  S.temCam = S.stream.getVideoTracks().length > 0;
  S.mic = S.temMic; S.cam = S.temCam;
  $('previa').srcObject = S.stream;
  atualizarBotoesPre();
}

function atualizarBotoesPre() {
  botaoMicCam($('pMic'), $('pCam'));
  $('semCamPre').classList.toggle('oculto', S.cam);
  $('previa').style.visibility = S.cam ? 'visible' : 'hidden';
}
function botaoMicCam(bMic, bCam) {
  bMic.innerHTML = S.mic ? I.mic : I.micOff;
  bMic.classList.toggle('desligado', !S.mic);
  bMic.disabled = !S.temMic;
  bMic.title = S.mic ? 'Desligar microfone' : 'Ligar microfone';
  bCam.innerHTML = S.cam ? I.cam : I.camOff;
  bCam.classList.toggle('desligado', !S.cam);
  bCam.disabled = !S.temCam;
  bCam.title = S.cam ? 'Desligar câmera' : 'Ligar câmera';
}

/* ================= Entrar ================= */
async function entrar(ev) {
  ev.preventDefault();
  $('erroEntrar').textContent = '';
  S.nome = $('iNome').value.trim(); S.email = $('iEmail').value.trim(); S.cargo = $('iCargo').value.trim();
  if (S.nome.length < 3) { $('erroEntrar').textContent = 'Digite seu nome completo. Ele vai aparecer no documento.'; return; }
  try { localStorage.setItem('sala_eu', JSON.stringify({ nome: S.nome, email: S.email, cargo: S.cargo })); } catch (e) {}
  const b = $('bEntrar'); b.disabled = true; b.textContent = 'Entrando…';
  try {
    const r = await api({ action: 'entrar', sala: SALA, h: CHAVE, nome: S.nome, email: S.email, cargo: S.cargo });
    S.peer = r.peer; S.host = r.host;
  } catch (e) {
    $('erroEntrar').textContent = e.message;
    b.disabled = false; b.textContent = 'Entrar na reunião';
    return;
  }
  S.dentro = true; S.entrouEm = Date.now();
  montarSala();
  iniciarRec();
  ciclo();
}

/* ================= Sala ================= */
function montarSala() {
  $('salaTit').textContent = tipoLabel(S.info.tipo) + ' nº ' + S.info.numero + ', ' + S.info.titulo;
  $('cTela').innerHTML = I.tela; $('cReg').innerHTML = I.reg; $('cLink').innerHTML = I.link; $('cSair').innerHTML = I.sair;
  $('fecharReg').innerHTML = I.x;
  if (!navigator.mediaDevices || !navigator.mediaDevices.getDisplayMedia || !S.temCam) $('cTela').classList.add('oculto');
  if (!SR) $('avisoSR').classList.remove('oculto');
  if (window.matchMedia('(max-width:900px)').matches) $('cReg').classList.remove('ativo');

  $('cMic').onclick = () => { alternarMic(); atualizarControles(); };
  $('cCam').onclick = () => { alternarCam(); atualizarControles(); };
  $('cTela').onclick = alternarTela;
  $('cReg').onclick = alternarRegistro;
  $('fecharReg').onclick = alternarRegistro;
  $('cLink').onclick = () => copiar(linkParticipantes());
  $('cSair').onclick = pedirSaida;

  const el = document.createElement('div');
  el.className = 'tile eu';
  el.innerHTML = `<video autoplay playsinline muted class="espelho"></video><div class="avatar"><b>${esc(iniciais(S.nome))}</b></div>
    <div class="rot">${I.micOff}<span>${esc(S.nome)}</span><em>você</em></div>`;
  el.querySelector('video').srcObject = S.stream;
  $('grade').appendChild(el);

  atualizarControles();
  layoutGrade();
  mostrar('telaSala');
  setInterval(atualizarTempo, 15000); atualizarTempo();
}

function atualizarTempo() {
  const min = Math.floor((Date.now() - S.entrouEm) / 60000);
  const pessoas = S.presenca.length || 1;
  $('tempo').textContent = `${pessoas} ${pessoas === 1 ? 'pessoa' : 'pessoas'}, ${min < 1 ? 'agora há pouco' : 'há ' + min + ' min'}`;
}

function atualizarControles() {
  botaoMicCam($('cMic'), $('cCam'));
  const eu = document.querySelector('.tile.eu');
  if (eu) {
    eu.classList.toggle('mudo', !S.mic);
    eu.classList.toggle('sem-video', !S.cam && !S.tela);
    eu.classList.toggle('tela', !!S.tela);
    eu.querySelector('video').classList.toggle('espelho', !S.tela);
  }
  $('cTela').classList.toggle('ativo', !!S.tela);
  $('cTela').title = S.tela ? 'Parar de apresentar' : 'Apresentar a tela';
}

function alternarMic() {
  if (!S.temMic) return;
  S.mic = !S.mic;
  S.stream.getAudioTracks().forEach(t => t.enabled = S.mic);
  if (S.dentro) { if (S.mic) iniciarRec(); else pararRec(); }
}
function alternarCam() {
  if (!S.temCam) return;
  S.cam = !S.cam;
  S.stream.getVideoTracks().forEach(t => t.enabled = S.cam);
}
function alternarRegistro() {
  if (window.matchMedia('(max-width:900px)').matches) {
    document.body.classList.toggle('ver-registro');
    $('cReg').classList.toggle('ativo', document.body.classList.contains('ver-registro'));
  } else {
    document.body.classList.toggle('sem-registro');
    $('cReg').classList.toggle('ativo', !document.body.classList.contains('sem-registro'));
  }
}

/* ---------- Apresentar tela ---------- */
async function alternarTela() {
  if (S.tela) { pararTela(); return; }
  try { S.tela = await navigator.mediaDevices.getDisplayMedia({ video: true, audio: false }); }
  catch (e) { return; }
  const t = S.tela.getVideoTracks()[0];
  t.onended = pararTela;
  trocarVideo(t);
  document.querySelector('.tile.eu video').srcObject = S.tela;
  atualizarControles();
}
function pararTela() {
  if (!S.tela) return;
  S.tela.getTracks().forEach(t => t.stop());
  S.tela = null;
  trocarVideo(S.stream.getVideoTracks()[0] || null);
  const v = document.querySelector('.tile.eu video');
  if (v) v.srcObject = S.stream;
  atualizarControles();
}
function videoAtual() { return S.tela ? S.tela.getVideoTracks()[0] : (S.stream.getVideoTracks()[0] || null); }
function trocarVideo(track) {
  for (const c of S.conns.values()) {
    const tr = c.pc.getTransceivers().find(x => x.receiver && x.receiver.track && x.receiver.track.kind === 'video');
    if (tr) tr.sender.replaceTrack(track).catch(() => {});
  }
}

/* ================= Ciclo com o servidor ================= */
async function ciclo() {
  if (!S.dentro || S.fim) return;
  const corpo = {
    action: 'sync', sala: SALA, peer: S.peer, nome: S.nome, cargo: S.cargo,
    estado: { mic: S.mic, cam: S.cam || !!S.tela, tela: !!S.tela },
    sinais: S.saida.splice(0), falas: S.falasPend.splice(0), ultimaSeq: S.ultimaSeq
  };
  try {
    const r = await api(corpo);
    S.falhas = 0; avisoRede('');
    S.presenca = r.peers;
    for (const sg of r.sinais) { try { await receberSinal(sg.from, sg.data); } catch (e) { console.warn('sinal', e); } }
    reconciliar();
    adicionarFalas(r.falas);
    atualizarTempo();
    if (ENCERRADOS.includes(r.status)) { finalizar('O organizador encerrou a reunião', 'O documento será redigido e enviado para assinatura.'); return; }
  } catch (e) {
    S.saida.unshift(...corpo.sinais);
    S.falasPend.unshift(...corpo.falas);
    if (++S.falhas >= 3) avisoRede('Conexão instável com o servidor da Sala. Tentando de novo…');
  }
  setTimeout(ciclo, 1000);
}

/* ================= Vídeo entre navegadores (WebRTC) ================= */
function novaConexao(id, ofertante) {
  const pc = new RTCPeerConnection({ iceServers: ICE });
  const c = { id, pc, criado: Date.now(), conectou: false, desde: 0, remoto: null };
  const a = S.stream.getAudioTracks()[0];
  const v = videoAtual();
  if (a) pc.addTrack(a, S.stream); else if (ofertante) pc.addTransceiver('audio', { direction: 'recvonly' });
  if (v) pc.addTrack(v, S.stream); else if (ofertante) pc.addTransceiver('video', { direction: 'recvonly' });
  pc.ontrack = ev => {
    let st = ev.streams && ev.streams[0];
    if (!st) { c.remoto = c.remoto || new MediaStream(); c.remoto.addTrack(ev.track); st = c.remoto; }
    c.remoto = st;
    const el = document.querySelector(`.tile[data-id="${id}"]`);
    if (el) { const vid = el.querySelector('video'); if (vid.srcObject !== st) { vid.srcObject = st; vid.play().catch(() => {}); } }
  };
  pc.onconnectionstatechange = () => {
    const s = pc.connectionState;
    const el = document.querySelector(`.tile[data-id="${id}"]`);
    if (s === 'connected') { c.conectou = true; c.desde = 0; if (el) el.classList.remove('aguardando'); }
    else if (s === 'disconnected' || s === 'failed') { c.desde = c.desde || Date.now(); if (el) el.classList.add('aguardando'); }
  };
  return c;
}
function iceCompleto(pc) {
  return new Promise(res => {
    if (pc.iceGatheringState === 'complete') return res();
    const t = setTimeout(res, 2500);
    pc.addEventListener('icegatheringstatechange', () => { if (pc.iceGatheringState === 'complete') { clearTimeout(t); res(); } });
  });
}
async function ligarPara(id) {
  fechar(id);
  const c = novaConexao(id, true);
  S.conns.set(id, c);
  try {
    await c.pc.setLocalDescription(await c.pc.createOffer());
    await iceCompleto(c.pc);
    if (S.conns.get(id) === c) S.saida.push({ to: id, data: { tipo: 'oferta', sdp: c.pc.localDescription.sdp } });
  } catch (e) { console.warn('oferta', e); }
}
async function receberSinal(de, data) {
  if (!data) return;
  if (data.tipo === 'oferta') {
    fechar(de);
    const c = novaConexao(de, false);
    S.conns.set(de, c);
    await c.pc.setRemoteDescription({ type: 'offer', sdp: data.sdp });
    await c.pc.setLocalDescription(await c.pc.createAnswer());
    await iceCompleto(c.pc);
    if (S.conns.get(de) === c) S.saida.push({ to: de, data: { tipo: 'resposta', sdp: c.pc.localDescription.sdp } });
  } else if (data.tipo === 'resposta') {
    const c = S.conns.get(de);
    if (c && c.pc.signalingState === 'have-local-offer') await c.pc.setRemoteDescription({ type: 'answer', sdp: data.sdp });
  }
}
function fechar(id) {
  const c = S.conns.get(id);
  if (!c) return;
  try { c.pc.close(); } catch (e) {}
  S.conns.delete(id);
}

function reconciliar() {
  const outros = S.presenca.filter(p => p.id !== S.peer);
  const ids = new Set(outros.map(p => p.id));
  for (const id of [...S.conns.keys()]) if (!ids.has(id)) fechar(id);
  document.querySelectorAll('.tile[data-id]').forEach(el => { if (!ids.has(el.dataset.id)) el.remove(); });
  const agora = Date.now();
  for (const p of outros) {
    atualizarTile(garantirTile(p), p);
    const c = S.conns.get(p.id);
    if (S.peer < p.id) {
      // quem tem o identificador menor faz a chamada
      if (!c) ligarPara(p.id);
      else if (c.pc.connectionState === 'failed' || (!c.conectou && agora - c.criado > 20000) || (c.desde && agora - c.desde > 12000)) ligarPara(p.id);
    } else if (c && (c.pc.connectionState === 'failed' || (c.desde && agora - c.desde > 15000))) {
      fechar(p.id);
    }
  }
  layoutGrade();
}
function garantirTile(p) {
  let el = document.querySelector(`.tile[data-id="${p.id}"]`);
  if (el) return el;
  el = document.createElement('div');
  el.className = 'tile aguardando';
  el.dataset.id = p.id;
  el.innerHTML = `<video autoplay playsinline></video><div class="avatar"><b></b></div>
    <div class="rot">${I.micOff}<span></span><em></em></div><div class="conectando">Conectando…</div>`;
  $('grade').appendChild(el);
  const c = S.conns.get(p.id);
  if (c && c.remoto) el.querySelector('video').srcObject = c.remoto;
  return el;
}
function atualizarTile(el, p) {
  const e = p.estado || {};
  el.querySelector('.rot span').textContent = p.nome;
  el.querySelector('.rot em').textContent = p.host ? 'organização' : '';
  el.querySelector('.avatar b').textContent = iniciais(p.nome);
  el.classList.toggle('mudo', e.mic === false);
  el.classList.toggle('sem-video', e.cam === false);
  el.classList.toggle('tela', !!e.tela);
}
function layoutGrade() {
  const g = $('grade');
  const n = g.children.length;
  const cols = n <= 1 ? 1 : n <= 4 ? 2 : n <= 9 ? 3 : 4;
  g.style.gridTemplateColumns = `repeat(${cols}, minmax(0, 1fr))`;
  g.style.gridTemplateRows = `repeat(${Math.ceil(n / cols)}, minmax(0, 1fr))`;
}

/* ================= Transcrição ================= */
function iniciarRec() {
  if (!SR || !S.mic || !S.dentro || S.fim || S.recAtivo || S.recBloqueado) return;
  const rec = new SR();
  rec.lang = 'pt-BR'; rec.continuous = true; rec.interimResults = true; rec.maxAlternatives = 1;
  rec.onresult = ev => {
    let parcial = '';
    for (let i = ev.resultIndex; i < ev.results.length; i++) {
      const r = ev.results[i];
      if (r.isFinal) { const t = arrumar(r[0].transcript); if (t) S.falasPend.push(t); }
      else parcial += r[0].transcript;
    }
    mostrarParcial(parcial);
  };
  rec.onerror = ev => {
    if (ev.error === 'not-allowed' || ev.error === 'service-not-allowed') {
      S.recBloqueado = true;
      $('avisoSR').textContent = 'A transcrição foi bloqueada pelo navegador. Permita o microfone para esta página e recarregue.';
      $('avisoSR').classList.remove('oculto');
    }
  };
  rec.onend = () => {
    S.recAtivo = false; mostrarParcial('');
    if (S.mic && S.dentro && !S.fim && !S.recBloqueado) setTimeout(iniciarRec, 250);
  };
  try { rec.start(); S.rec = rec; S.recAtivo = true; } catch (e) { S.recAtivo = false; }
}
function pararRec() { if (S.rec) { try { S.rec.stop(); } catch (e) {} } }
function arrumar(t) {
  t = String(t || '').trim();
  if (!t) return '';
  t = t.charAt(0).toUpperCase() + t.slice(1);
  if (!/[.!?…]$/.test(t)) t += '.';
  return t;
}
function mostrarParcial(t) {
  const el = $('interim');
  el.textContent = t ? S.nome.split(' ')[0] + ': ' + t : '';
  if (t) rolarFolha(true);
}
function adicionarFalas(lista) {
  const folha = $('folha'), parcial = $('interim');
  const perto = folha.scrollHeight - folha.scrollTop - folha.clientHeight < 80;
  let novas = 0;
  (lista || []).forEach(f => {
    if (f.seq <= S.ultimaSeq) return;
    S.ultimaSeq = f.seq;
    const p = document.createElement('p');
    p.className = 'fala' + (f.peer === S.peer ? ' minha' : '');
    p.innerHTML = `<span class="h">${esc(f.hora)}</span><b>${esc(f.nome)}:</b> ${esc(f.texto)}`;
    folha.insertBefore(p, parcial);
    novas++;
  });
  if (novas) { $('folhaVazia').classList.add('oculto'); rolarFolha(perto); }
}
function rolarFolha(forcar) { const f = $('folha'); if (forcar) f.scrollTop = f.scrollHeight; }

/* ================= Sair ================= */
function pedirSaida() {
  if (!S.host) { finalizar('Você saiu da reunião', 'Pode fechar esta aba.'); return; }
  $('modal').innerHTML = `<div class="fundo" onclick="if(event.target===this)this.parentNode.innerHTML=''">
    <div class="caixa"><h2>Sair da reunião</h2><p>Encerrar para todos fecha a sala e libera o registro para virar documento.</p>
    <div class="acoes"><button class="btn perigo" id="mEnc">Encerrar para todos</button>
    <button class="btn sec" id="mSair">Só sair</button>
    <button class="btn sec" onclick="document.getElementById('modal').innerHTML=''">Continuar na reunião</button></div></div></div>`;
  $('mSair').onclick = () => { $('modal').innerHTML = ''; finalizar('Você saiu da reunião', 'A reunião continua para os outros participantes.'); };
  $('mEnc').onclick = async () => {
    const b = $('mEnc'); b.disabled = true; b.textContent = 'Encerrando…';
    try { await api({ action: 'encerrar', sala: SALA, h: CHAVE }); }
    catch (e) { b.disabled = false; b.textContent = 'Encerrar para todos'; toast(e.message); return; }
    $('modal').innerHTML = '';
    finalizar('Reunião encerrada', 'Volte ao painel da Sala para redigir o documento.');
  };
}
function avisarSaida() {
  if (!S.peer) return;
  try {
    navigator.sendBeacon(API_URL, new Blob([JSON.stringify({ action: 'sair', sala: SALA, peer: S.peer })], { type: 'text/plain' }));
  } catch (e) {}
}
async function finalizar(tit, msg) {
  if (S.fim) return;
  // envia as últimas falas antes de sair
  if (S.falasPend.length && S.dentro) {
    try { await api({ action: 'sync', sala: SALA, peer: S.peer, nome: S.nome, sinais: [], falas: S.falasPend.splice(0), ultimaSeq: S.ultimaSeq, estado: {} }); } catch (e) {}
  }
  S.fim = true; S.dentro = false;
  pararRec(); avisarSaida();
  for (const id of [...S.conns.keys()]) fechar(id);
  if (S.tela) S.tela.getTracks().forEach(t => t.stop());
  S.stream.getTracks().forEach(t => t.stop());
  avisoRede('');
  telaEstado(tit, msg);
}
window.addEventListener('pagehide', () => { if (S.dentro) avisarSaida(); });
</script>
</body>
</html>
