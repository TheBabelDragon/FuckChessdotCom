# FuckChessdotCom ♟️💀

The ultimate middle finger to [Chess.com](http://Chess.com) bots and quiet chess.

Drop this widget on your profile, Gist, Carrd, Discord, wherever.

**[Open the widget →](index.html)** (or copy the raw HTML)

Real humans only. Transparent bots. Full unfiltered trash talk. Emoji stakes. Fuck quiet chess.
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>FuckChessdotCom Widget</title>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/chessboardjs/0.3.0/chessboard-0.3.0.min.js"></script>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/chessboardjs/0.3.0/chessboard-0.3.0.min.css">
  <style>
    body { margin:0; background:#0a0a0a; font-family:system-ui, sans-serif; color:#ffdddd; }
    #widget { max-width:460px; margin:20px auto; padding:24px; background:#0a0a0a; border:3px solid #c62828; border-radius:16px; box-shadow:0 10px 40px rgba(200,0,0,0.5); }
    h1 { font-size:28px; text-align:center; margin:0 0 8px; color:#ff6666; }
    p { text-align:center; opacity:0.9; margin:0 0 20px; }
    .mini-boards { display:flex; justify-content:center; gap:16px; margin-bottom:24px; }
    .mini { width:108px; height:108px; border:3px solid #c62828; border-radius:10px; overflow:hidden; }
    button.play { width:100%; padding:18px; margin-bottom:12px; font-size:17px; font-weight:800; background:linear-gradient(#d32f2f,#b71c1c); color:white; border:none; border-radius:12px; cursor:pointer; }
    button.play:hover { filter:brightness(1.1); }
    .section { background:#1f0000; padding:16px; border-radius:12px; border:2px solid #c62828; margin-bottom:20px; }
    .section h3 { margin:0 0 12px; text-align:center; color:#ff8888; }
    #trashchat { height:190px; overflow-y:auto; background:#330000; padding:12px; border-radius:8px; margin-bottom:12px; line-height:1.5; }
    #trashInput { flex:1; padding:12px; background:#440000; color:#ffdddd; border:1px solid #c62828; border-radius:8px; }
    .quick { font-size:13px; padding:6px 10px; background:#c62828; color:white; border:none; border-radius:6px; cursor:pointer; margin:3px; }
    #ledger { font-size:26px; min-height:52px; text-align:center; background:#222; padding:12px; border-radius:8px; }
  </style>
</head>
<body>

<div id="widget">
  <h1>♟️💀 FuckChessdotCom</h1>
  <p>Real humans or transparent bot friends.<br>Fuck Chess.com bots. Fuck quiet chess.<br>Name-call freely here.</p>

  <!-- Mini boards -->
  <div class="mini-boards">
    <div id="mini1" class="mini"></div>
    <div id="mini2" class="mini"></div>
  </div>

  <!-- Play buttons -->
  <button class="play" onclick="startGame('human', 300, 0)">👊 Play a Real Human – 5|0 (then roast them here)</button>
  <button class="play" onclick="startGame('human', 600, 5)">👊 Play a Real Human – 10|5 (name-calling arena opens after)</button>
  <button class="play" onclick="startGame('bot', 300, 0, 6)">🤖 Play a Bot Friend (Level 6) – Roast the silicon anyway</button>

  <!-- Trash talk zone -->
  <div class="section">
    <h3>💬 UNFILTERED TRASH TALK ZONE (local meme board)</h3>
    <div id="trashchat"></div>
    <div style="display:flex; gap:8px;">
      <input id="trashInput" type="text" placeholder="Call them a fucking fish, patzer, engine whore...">
      <button onclick="sendTrash()" style="padding:12px 20px; background:#c62828; color:white; border:none; border-radius:8px; font-weight:700;">SEND ROAST</button>
    </div>
    <div style="margin-top:10px; text-align:center;">
      <button class="quick" onclick="quickTrash('You fucking patzer 😂')">Patzer</button>
      <button class="quick" onclick="quickTrash('Engine abusing cunt')">Engine whore</button>
      <button class="quick" onclick="quickTrash('GG you fish 🍣')">Fish</button>
      <button class="quick" onclick="quickTrash('Rematch so I can destroy you again 🔥')">Rematch bitch</button>
    </div>
  </div>

  <!-- Emoji stakes -->
  <div class="section" style="border-color:#555;">
    <h3 style="color:#ffdd88;">🎲 Emoji Stakes (brag or shame)</h3>
    <div id="ledger">No blood drawn yet 🍰</div>
    <div style="margin-top:12px; display:flex; flex-wrap:wrap; gap:6px; justify-content:center;">
      <button onclick="addStake('🎂')" style="font-size:24px; padding:8px 14px; background:#2e7d32; border:none; border-radius:6px;">🎂 I won</button>
      <button onclick="addStake('🍕')" style="font-size:24px; padding:8px 14px; background:#2e7d32; border:none; border-radius:6px;">🍕 I won</button>
      <button onclick="addStake('☕')" style="font-size:24px; padding:8px 14px; background:#2e7d32; border:none; border-radius:6px;">☕ I won</button>
      <button onclick="addStake('🍔💀')" style="font-size:22px; padding:8px 14px; background:#c62828; border:none; border-radius:6px;">🍔 Lost (shame)</button>
      <button onclick="resetLedger()" style="font-size:13px; padding:8px 14px; background:#555; border:none; border-radius:6px;">Reset shame</button>
    </div>
  </div>

  <div style="text-align:center; margin-top:20px; font-size:13px; opacity:0.8;">
    Click play → opens real Lichess game (real chat there too)<br>
    This widget = pure unfiltered vibes. Fuck quiet chess.
  </div>
</div>

<script>
// ====================== CONFIG ======================
const YOUR_LICHESS_TOKEN = "";   // optional, get at lichess.org/account/oauth/token (challenge:write)

// ====================== GAME START ======================
async function startGame(type, limit, increment, botLevel = null) {
  if (type === 'human') {
    const params = new URLSearchParams({ 'clock.limit': limit, 'clock.increment': increment, variant: 'standard', rated: false });
    let url = `https://lichess.org/api/challenge/open?${params.toString()}`;
    if (YOUR_LICHESS_TOKEN) {
      try {
        const res = await fetch('https://lichess.org/api/challenge/open', {
          method: 'POST',
          headers: { Authorization: `Bearer ${YOUR_LICHESS_TOKEN}`, 'Content-Type': 'application/json' },
          body: JSON.stringify({ clock: { limit, increment }, variant: 'standard', rated: false })
        });
        if (res.ok) {
          const data = await res.json();
          url = data.challenge.url || url;
        }
      } catch(e) {}
    }
    window.open(url, '_blank');
  } else {
    const level = botLevel || 6;
    window.open(`https://lichess.org/?time=${Math.floor(limit/60)}+${increment}#ai=${level}`, '_blank');
  }
}

// ====================== TRASH TALK ======================
function loadTrash() {
  const saved = localStorage.getItem('fuckYouTrashChat') || '';
  document.getElementById('trashchat').innerHTML = saved || '<em>Waiting for the first roast... don’t be a patzer</em>';
}

function addTrashLine(line) {
  const chat = document.getElementById('trashchat');
  const time = new Date().toLocaleTimeString([], {hour:'2-digit', minute:'2-digit'});
  const newLine = `<div style="margin:6px 0;">[${time}] ${line}</div>`;
  chat.innerHTML += newLine;
  chat.scrollTop = chat.scrollHeight;
  localStorage.setItem('fuckYouTrashChat', chat.innerHTML);
}

function sendTrash() {
  const input = document.getElementById('trashInput');
  const msg = input.value.trim();
  if (!msg) return;
  addTrashLine(`<strong>You:</strong> ${msg}`);
  input.value = '';
}

function quickTrash(text) {
  addTrashLine(`<strong>Quick roast:</strong> ${text}`);
}

// ====================== EMOJI STAKES ======================
function loadLedger() {
  const saved = localStorage.getItem('chessEmojiLedger') || '';
  document.getElementById('ledger').innerHTML = saved || 'No blood drawn yet 🍰';
}

function addStake(emoji) {
  let current = localStorage.getItem('chessEmojiLedger') || '';
  current += emoji + ' ';
  localStorage.setItem('chessEmojiLedger', current.trim());
  document.getElementById('ledger').innerHTML = current.trim();
  addTrashLine(`Stakes updated → ${emoji}`);
}

function resetLedger() {
  if (confirm('Clear the shame ledger?')) {
    localStorage.removeItem('chessEmojiLedger');
    document.getElementById('ledger').innerHTML = 'Ledger wiped clean 💀';
  }
}

// ====================== MINI BOARDS ======================
const positions = [
  'start',
  'rnbqkbnr/pppp1ppp/8/8/4P3/8/PPPP1PPP/RNBQKBNR b KQkq - 0 1'
];

window.onload = () => {
  positions.forEach((pos, i) => {
    new Chessboard(`mini${i+1}`, {
      draggable: false,
      position: pos,
      pieceTheme: 'https://lichess1.org/assets/piece/cburnett/{piece}.svg',
      showNotation: false
    });
  });
  loadTrash();
  loadLedger();
};
</script>
</body>
</html>
