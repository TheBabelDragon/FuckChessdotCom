<!-- FULL FUCK YOU EDITION: Play + Trash Talk + Stakes – Fuck Chess.com & Lichess Moderation Vibes -->
<div style="max-width: 440px; margin: 0 auto; font-family: system-ui; background: #0a0a0a; color: #ffdddd; padding: 24px; border-radius: 16px; border: 3px solid #c62828; box-shadow: 0 10px 40px rgba(200,0,0,0.4);">
  <div style="text-align: center; margin-bottom: 20px;">
    <span style="font-size: 42px;">♟️💀</span>
    <h2 style="margin: 8px 0 4px; font-size: 23px; color: #ff6666;">Come Get Your Ass Kicked</h2>
    <p style="font-size: 14px; opacity: 0.95;">Real humans or transparent bot friends.<br>Fuck Chess.com bots. Fuck quiet chess. Name-call freely here.</p>
  </div>

  <!-- Mini boards (aggressive teaser) -->
  <div style="display: flex; justify-content: center; gap: 14px; margin-bottom: 20px;">
    <div id="mini1" style="width: 100px; height: 100px; border: 3px solid #c62828; border-radius: 10px; overflow: hidden;"></div>
    <div id="mini2" style="width: 100px; height: 100px; border: 3px solid #c62828; border-radius: 10px; overflow: hidden;"></div>
  </div>

  <div style="display: grid; gap: 12px; margin-bottom: 24px;">
    <button onclick="startGame('human', 300, 0)" style="padding: 18px; font-size: 17px; font-weight: 800; background: linear-gradient(#d32f2f, #b71c1c); color: white; border: none; border-radius: 12px; cursor: pointer;">
      👊 Play a Real Human – 5|0 (then come back and roast them here)
    </button>
    <button onclick="startGame('human', 600, 5)" style="padding: 18px; font-size: 17px; font-weight: 800; background: linear-gradient(#d32f2f, #b71c1c); color: white; border: none; border-radius: 12px; cursor: pointer;">
      👊 Play a Real Human – 10|5 (name-calling arena opens after)
    </button>
    <button onclick="startGame('bot', 300, 0, 6)" style="padding: 18px; font-size: 17px; font-weight: 800; background: linear-gradient(#f57c00, #e65100); color: white; border: none; border-radius: 12px; cursor: pointer;">
      🤖 Play a Bot Friend (Level 6) – Roast the silicon anyway
    </button>
  </div>

  <!-- Savage Trash Talk Panel (the real half of the fun) -->
  <div style="background: #1f0000; padding: 16px; border-radius: 12px; border: 2px solid #c62828; margin-bottom: 20px;">
    <div style="text-align: center; font-size: 16px; font-weight: 700; color: #ff8888; margin-bottom: 10px;">💬 UNFILTERED TRASH TALK ZONE (local meme board)</div>
    <div id="trashchat" style="height: 180px; overflow-y: auto; background: #330000; padding: 12px; border-radius: 8px; margin-bottom: 12px; font-size: 14.5px; line-height: 1.6; color: #ffdddd;"></div>
    <div style="display: flex; gap: 8px;">
      <input id="trashInput" type="text" placeholder="Call them a fucking fish, patzer, engine whore..." style="flex: 1; padding: 12px; background: #440000; color: #ffdddd; border: 1px solid #c62828; border-radius: 8px;">
      <button onclick="sendTrash()" style="padding: 12px 20px; background: #c62828; color: white; border: none; border-radius: 8px; cursor: pointer; font-weight: 700;">SEND ROAST</button>
    </div>
    <div style="margin-top: 10px; display: flex; flex-wrap: wrap; gap: 6px; justify-content: center; font-size: 13px;">
      <button onclick="quickTrash('You fucking patzer 😂')" style="background:#c62828; color:white; border:none; padding:6px 10px; border-radius:6px; cursor:pointer;">Patzer</button>
      <button onclick="quickTrash('Engine abusing cunt')" style="background:#c62828; color:white; border:none; padding:6px 10px; border-radius:6px; cursor:pointer;">Engine whore</button>
      <button onclick="quickTrash('GG you fish 🍣')" style="background:#c62828; color:white; border:none; padding:6px 10px; border-radius:6px; cursor:pointer;">Fish</button>
      <button onclick="quickTrash('Rematch so I can destroy you again 🔥')" style="background:#c62828; color:white; border:none; padding:6px 10px; border-radius:6px; cursor:pointer;">Rematch bitch</button>
    </div>
  </div>

  <!-- Emoji Stakes (now feeds into trash talk) -->
  <div style="background: #1a1a1a; padding: 14px; border-radius: 12px; border: 1px solid #555;">
    <div style="text-align: center; font-size: 15px; font-weight: 600; margin-bottom: 10px;">🎲 Emoji Stakes (brag or shame)</div>
    <div id="ledger" style="font-size: 26px; min-height: 50px; text-align: center; background: #222; padding: 10px; border-radius: 8px;">No blood drawn yet 🍰</div>
    <div style="display: flex; flex-wrap: wrap; gap: 6px; justify-content: center; margin-top: 10px;">
      <button onclick="addStake('🎂')" style="font-size: 24px; padding: 8px 12px; background: #2e7d32; border: none; border-radius: 6px;">🎂 I won</button>
      <button onclick="addStake('🍕')" style="font-size: 24px; padding: 8px 12px; background: #2e7d32; border: none; border-radius: 6px;">🍕 I won</button>
      <button onclick="addStake('☕')" style="font-size: 24px; padding: 8px 12px; background: #2e7d32; border: none; border-radius: 6px;">☕ I won</button>
      <button onclick="addStake('🍔💀')" style="font-size: 22px; padding: 8px 12px; background: #c62828; border: none; border-radius: 6px;">🍔 Lost (shame)</button>
      <button onclick="resetLedger()" style="font-size: 13px; padding: 8px 12px; background: #555; border: none; border-radius: 6px;">Reset shame</button>
    </div>
  </div>

  <div style="margin-top: 24px; text-align: center; font-size: 13px; opacity: 0.8; color: #ffaaaa;">
    Click play → Lichess game (real chat there too)<br>
    This widget: pure unfiltered vibes. Fuck quiet chess.
  </div>
</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/chessboardjs/0.3.0/chessboard-0.3.0.min.js"></script>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/chessboardjs/0.3.0/chessboard-0.3.0.min.css">

<script>
// CONFIG
const YOUR_LICHESS_TOKEN = ""; // optional

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

// Trash talk functions
function loadTrash() {
  const saved = localStorage.getItem('fuckYouTrashChat') || '';
  document.getElementById('trashchat').innerHTML = saved || '<em>Waiting for the first roast... come on, don\'t be a patzer</em>';
}

function addTrashLine(line) {
  const chat = document.getElementById('trashchat');
  const time = new Date().toLocaleTimeString([], {hour:'2-digit', minute:'2-digit'});
  const newLine = `<div style="margin:6px 0; color:#ffaaaa;">[${time}] ${line}</div>`;
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

// Stakes (can be called from trash too if you want)
function loadLedger() {
  const saved = localStorage.getItem('chessEmojiLedger') || '';
  document.getElementById('ledger').innerHTML = saved || 'No blood drawn yet 🍰';
}

function addStake(emoji) {
  let current = localStorage.getItem('chessEmojiLedger') || '';
  current += emoji + ' ';
  localStorage.setItem('chessEmojiLedger', current.trim());
  document.getElementById('ledger').innerHTML = current.trim();
  // Optional: auto post to trash
  addTrashLine(`Stakes updated: ${emoji}`);
}

function resetLedger() {
  if (confirm('Clear the shame ledger?')) {
    localStorage.removeItem('chessEmojiLedger');
    document.getElementById('ledger').innerHTML = 'Ledger wiped clean 💀';
  }
}

// Mini boards – aggressive positions
const positions = ['start', 'rnbqkbnr/pppp1ppp/8/8/4P3/8/PPPP1PPP/RNBQKBNR b KQkq - 0 1'];
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
