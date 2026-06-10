<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Signing Portal</title>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --ink:        #0f1117;
      --ink-soft:   #5a5f72;
      --surface:    #f7f8fc;
      --panel:      #ffffff;
      --border:     #e2e4ed;
      --accent:     #2a55e8;
      --accent-dk:  #1e42c4;
      --success-bg: #edfaf3;
      --success-bd: #3ecf77;
      --success-tx: #156634;
      --danger:     #e84040;
      --radius:     10px;
      --shadow:     0 2px 12px rgba(15,17,23,.08);
    }

    body {
      font-family: 'Inter', system-ui, sans-serif;
      background: var(--surface);
      color: var(--ink);
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 40px 20px 60px;
    }

    header {
      width: 100%;
      max-width: 760px;
      margin-bottom: 32px;
    }

    .wordmark {
      font-size: 13px;
      font-weight: 600;
      letter-spacing: .08em;
      text-transform: uppercase;
      color: var(--ink-soft);
    }

    h1 {
      font-size: clamp(22px, 4vw, 30px);
      font-weight: 700;
      letter-spacing: -.02em;
      margin-top: 6px;
      line-height: 1.2;
    }

    h1 span {
      color: var(--accent);
    }

    /* ── URL card ── */
    .card {
      background: var(--panel);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      padding: 28px 28px 24px;
      width: 100%;
      max-width: 760px;
    }

    label {
      display: block;
      font-size: 13px;
      font-weight: 600;
      color: var(--ink-soft);
      letter-spacing: .04em;
      text-transform: uppercase;
      margin-bottom: 8px;
    }

    .input-row {
      display: flex;
      gap: 10px;
    }

    input[type="url"] {
      flex: 1;
      height: 44px;
      padding: 0 14px;
      border: 1.5px solid var(--border);
      border-radius: 8px;
      font-size: 14px;
      color: var(--ink);
      background: var(--surface);
      outline: none;
      transition: border-color .15s;
    }

    input[type="url"]:focus {
      border-color: var(--accent);
      background: #fff;
    }

    input[type="url"]::placeholder { color: #adb2c4; }

    button {
      height: 44px;
      padding: 0 22px;
      background: var(--accent);
      color: #fff;
      border: none;
      border-radius: 8px;
      font-size: 14px;
      font-weight: 600;
      cursor: pointer;
      white-space: nowrap;
      transition: background .15s, transform .08s;
    }

    button:hover  { background: var(--accent-dk); }
    button:active { transform: scale(.97); }
    button:disabled { background: #adb2c4; cursor: default; }

    .hint {
      margin-top: 10px;
      font-size: 12px;
      color: var(--ink-soft);
    }

    /* ── Success banner ── */
    #success-banner {
      display: none;
      align-items: flex-start;
      gap: 14px;
      background: var(--success-bg);
      border: 1.5px solid var(--success-bd);
      border-radius: var(--radius);
      padding: 20px 24px;
      width: 100%;
      max-width: 760px;
      margin-top: 20px;
      animation: slideIn .3s ease;
    }

    #success-banner.visible { display: flex; }

    @keyframes slideIn {
      from { opacity: 0; transform: translateY(-8px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    .success-icon {
      flex-shrink: 0;
      width: 36px;
      height: 36px;
      background: var(--success-bd);
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .success-icon svg { display: block; }

    .success-body strong {
      display: block;
      font-size: 15px;
      font-weight: 700;
      color: var(--success-tx);
      margin-bottom: 4px;
    }

    .success-body p {
      font-size: 13px;
      color: var(--success-tx);
      opacity: .85;
    }

    /* ── iframe overlay ── */
    #overlay {
      display: none;
      position: fixed;
      inset: 0;
      background: rgba(15,17,23,.55);
      backdrop-filter: blur(3px);
      z-index: 100;
      align-items: center;
      justify-content: center;
      animation: fadeIn .2s ease;
    }

    #overlay.visible { display: flex; }

    @keyframes fadeIn {
      from { opacity: 0; } to { opacity: 1; }
    }

    .modal {
      position: relative;
      width: min(92vw, 960px);
      height: min(88vh, 700px);
      background: var(--panel);
      border-radius: 14px;
      box-shadow: 0 24px 64px rgba(15,17,23,.28);
      display: flex;
      flex-direction: column;
      overflow: hidden;
      animation: popIn .22s cubic-bezier(.34,1.56,.64,1);
    }

    @keyframes popIn {
      from { opacity: 0; transform: scale(.93); }
      to   { opacity: 1; transform: scale(1); }
    }

    .modal-bar {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 14px 18px;
      border-bottom: 1px solid var(--border);
      background: var(--panel);
      flex-shrink: 0;
    }

    .modal-title {
      font-size: 13px;
      font-weight: 600;
      color: var(--ink-soft);
    }

    .close-btn {
      height: 30px;
      width: 30px;
      padding: 0;
      background: var(--surface);
      color: var(--ink);
      border-radius: 6px;
      font-size: 18px;
      line-height: 1;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .close-btn:hover { background: var(--border); }

    #signing-frame {
      flex: 1;
      border: none;
      width: 100%;
    }

    /* ── Event log ── */
    .log-wrap {
      width: 100%;
      max-width: 760px;
      margin-top: 20px;
    }

    .log-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 8px;
    }

    .log-label {
      font-size: 12px;
      font-weight: 600;
      text-transform: uppercase;
      letter-spacing: .06em;
      color: var(--ink-soft);
    }

    #clear-log {
      height: 26px;
      padding: 0 10px;
      background: transparent;
      color: var(--ink-soft);
      border: 1px solid var(--border);
      font-size: 12px;
      border-radius: 6px;
    }

    #clear-log:hover { background: var(--surface); }

    #event-log {
      background: #0f1117;
      color: #c9d1e0;
      border-radius: var(--radius);
      font-family: 'JetBrains Mono', 'Fira Code', 'Cascadia Code', monospace;
      font-size: 12px;
      line-height: 1.7;
      padding: 16px 18px;
      min-height: 140px;
      max-height: 220px;
      overflow-y: auto;
    }

    .log-entry { display: flex; gap: 10px; }
    .log-time  { color: #5a6278; flex-shrink: 0; }

    .log-entry.register  .log-msg { color: #f5c518; }
    .log-entry.activate  .log-msg { color: #75bfff; }
    .log-entry.success   .log-msg { color: #3ecf77; }
    .log-entry.error-ev  .log-msg { color: #ff6b6b; }
    .log-entry.started   .log-msg { color: #c9d1e0; }
    .log-entry.other     .log-msg { color: #8892a4; }

    .log-empty { color: #3a3f52; font-style: italic; }
  </style>
</head>
<body>

  <header>
    <div class="wordmark">Signing Portal</div>
    <h1>Open a <span>signing session</span> in a secure overlay</h1>
  </header>

  <!-- URL input card -->
  <div class="card">
    <label for="signing-url">Signing URL</label>
    <div class="input-row">
      <input
        id="signing-url"
        type="url"
        placeholder="https://sandbox.esignlive.com/a/…"
        autocomplete="off"
        spellcheck="false"
      />
      <button id="open-btn" onclick="openSigning()">Open signing</button>
    </div>
    <p class="hint">Paste a Conga Sign / OneSpan Sign iframe URL and click the button to start.</p>
  </div>

  <!-- Success banner (hidden until SIGNER_COMPLETE) -->
  <div id="success-banner">
    <div class="success-icon">
      <svg width="18" height="18" viewBox="0 0 18 18" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M3.75 9.75L7.5 13.5L14.25 5.25" stroke="white" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </div>
    <div class="success-body">
      <strong>Document signed successfully</strong>
      <p>The signer completed the transaction. The signing session has been closed.</p>
    </div>
  </div>

  <!-- Event log -->
  <div class="log-wrap">
    <div class="log-header">
      <span class="log-label">ESL event log</span>
      <button id="clear-log" onclick="clearLog()">Clear</button>
    </div>
    <div id="event-log">
      <span class="log-empty">No events yet — open a signing session to begin.</span>
    </div>
  </div>

  <!-- iframe overlay modal -->
  <div id="overlay">
    <div class="modal">
      <div class="modal-bar">
        <span class="modal-title">OneSpan / Conga Sign</span>
        <button class="close-btn" onclick="closeModal()" title="Close">✕</button>
      </div>
      <iframe id="signing-frame" allowfullscreen></iframe>
    </div>
  </div>

<script>
  /* ── State ── */
  let signingOrigin = null;
  let logInitialised = false;

  /* ── Open modal ── */
  function openSigning() {
    const url = document.getElementById('signing-url').value.trim();
    if (!url) {
      alert('Please enter a signing URL first.');
      return;
    }

    try { signingOrigin = new URL(url).origin; }
    catch { signingOrigin = '*'; }

    // Reset success banner
    document.getElementById('success-banner').classList.remove('visible');

    document.getElementById('signing-frame').src = url;
    document.getElementById('overlay').classList.add('visible');
    appendLog('ESL:PORTAL:IFRAME_OPENED', 'other');
  }

  /* ── Close modal ── */
  function closeModal() {
    document.getElementById('overlay').classList.remove('visible');
    document.getElementById('signing-frame').src = 'about:blank';
    signingOrigin = null;
  }

  /* ── ESL message handler ── */
  window.addEventListener('message', function(event) {
    const data = event.data;

    // Ignore non-ESL messages (browser extensions, etc.)
    if (typeof data !== 'string' || !data.startsWith('ESL:')) return;

    switch (data) {

      /* Mandatory handshake — must respond with ACTIVATE_EVENTS */
      case 'ESL:MESSAGE:REGISTER':
        event.source.postMessage('ESL:MESSAGE:ACTIVATE_EVENTS', event.origin);
        appendLog(data, 'register');
        appendLog('ESL:MESSAGE:ACTIVATE_EVENTS  ← sent', 'activate');
        break;

      /* 🎉 Target event — close iframe, show success */
      case 'ESL:MESSAGE:SUCCESS:SIGNER_COMPLETE':
        appendLog(data, 'success');
        closeModal();
        document.getElementById('success-banner').classList.add('visible');
        break;

      /* All other events — echo back to avoid blocking interruptible ones */
      default:
        event.source.postMessage(data, event.origin);
        const cls = classifyEvent(data);
        appendLog(data, cls);
        break;
    }
  }, false);

  /* ── Log helpers ── */
  function classifyEvent(data) {
    if (data.includes(':SUCCESS:'))  return 'success';
    if (data.includes(':ERROR:'))    return 'error-ev';
    if (data.includes(':STARTED:'))  return 'started';
    return 'other';
  }

  function appendLog(msg, type) {
    const log = document.getElementById('event-log');

    if (!logInitialised) {
      log.innerHTML = '';
      logInitialised = true;
    }

    const now = new Date();
    const ts  = now.toTimeString().slice(0, 8) + '.' + String(now.getMilliseconds()).padStart(3, '0');

    const entry = document.createElement('div');
    entry.className = `log-entry ${type}`;
    entry.innerHTML = `<span class="log-time">${ts}</span><span class="log-msg">${escHtml(msg)}</span>`;
    log.appendChild(entry);
    log.scrollTop = log.scrollHeight;
  }

  function clearLog() {
    const log = document.getElementById('event-log');
    log.innerHTML = '<span class="log-empty">Log cleared.</span>';
    logInitialised = false;
  }

  function escHtml(str) {
    return str.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }

  /* ── Allow pressing Enter in input ── */
  document.getElementById('signing-url').addEventListener('keydown', function(e) {
    if (e.key === 'Enter') openSigning();
  });
</script>
</body>
</html>
