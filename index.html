<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Wheel of Win — Simple</title>
  <style>
    :root{font-family:system-ui,-apple-system,Segoe UI,Roboto,"Helvetica Neue",Arial;}
    body{margin:0;display:flex;min-height:100vh;gap:20px;padding:24px;background:#f7f8fb;color:#111;}
    .left, .right {background:white;border-radius:10px;padding:18px;box-shadow:0 6px 18px rgba(20,20,50,0.06);}
    .left{flex:1;display:flex;flex-direction:column;align-items:center;gap:12px;max-width:720px;}
    .right{width:320px;display:flex;flex-direction:column;gap:12px;}
    canvas{border-radius:50%;}
    textarea{width:100%;height:220px;padding:10px;border-radius:8px;border:1px solid #ddd;resize:vertical;}
    input[type="number"]{width:70px;}
    .controls{display:flex;gap:8px;flex-wrap:wrap;align-items:center;}
    button{padding:10px 14px;border-radius:8px;border:0;background:#2b6ef6;color:white;cursor:pointer;}
    button.secondary{background:#6b7280;}
    .winner{font-weight:700;font-size:20px;padding:12px;border-radius:8px;background:#f0f9ff;border:1px solid #d7efff;text-align:center;}
    label{font-size:13px;color:#444;}
    a.small{font-size:12px;color:#6b7280;text-decoration:none;}
    .top-row{display:flex;gap:12px;align-items:center;width:100%;justify-content:space-between;}
    .wheel-holder{display:flex;flex-direction:column;align-items:center;gap:8px;}
    .pointer{width:0;height:0;border-left:14px solid transparent;border-right:14px solid transparent;border-bottom:18px solid #ff3b30;margin-top:-8px;}
    footer{font-size:12px;color:#666;margin-top:6px;}
  </style>
</head>
<body>

  <div class="left">
    <div class="top-row" style="width:100%">
      <div>
        <h2 style="margin:0">Wheel of Win — Simple</h2>
        <div style="font-size:13px;color:#666">Paste names (one per line) then Create Wheel → Spin.</div>
      </div>
      <div style="text-align:right">
        <a class="small" href="https://wheelofnames.com/" target="_blank" rel="noopener">Reference: wheelofnames.com</a>
      </div>
    </div>

    <div class="wheel-holder">
      <div class="pointer" title="pointer"></div>
      <canvas id="wheelCanvas" width="520" height="520"></canvas>
    </div>

    <div style="display:flex;gap:10px;align-items:center;margin-top:6px;">
      <div class="controls">
        <button id="spinBtn">Spin</button>
        <button id="createBtn" class="secondary">Create Wheel</button>
        <button id="clearBtn" class="secondary">Clear</button>
      </div>
      <div style="margin-left:12px">
        <label>Spin time (s)</label><br>
        <input id="spinDuration" type="number" min="1" max="20" value="6">
      </div>
    </div>

    <div style="width:100%;margin-top:8px;">
      <div class="winner" id="winnerBox">No winner yet</div>
    </div>

    <footer>Built with Winwheel.js. You can customize colors, font and animation in the script. (Uses an open library.)</footer>
  </div>

  <div class="right">
    <label for="namesInput">Names / options (one per line)</label>
    <textarea id="namesInput" placeholder="Alice
Bob
Charlie
Delta"></textarea>

    <label>Segment colors (optional, comma separated hex). If left blank random colors are used.</label>
    <input id="colorsInput" placeholder="#e74c3c,#f1c40f,#2ecc71" style="padding:8px;border-radius:6px;border:1px solid #ddd;">

    <label>Advanced: Spins (how many full spins)</label>
    <input id="spinsInput" type="number" min="1" max="50" value="8">

    <div style="display:flex;gap:8px;align-items:center;margin-top:6px;">
      <button id="saveBtn" class="secondary">Save wheel (copy JSON)</button>
      <button id="loadBtn" class="secondary">Load wheel (paste JSON)</button>
    </div>

    <small style="color:#666">Tip: put each name on its own line. The wheel adjusts slice sizes automatically.</small>
  </div>

  <!-- Libraries: TweenMax (animation shim used by Winwheel examples) and Winwheel.js from CDN -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/1.20.2/TweenMax.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/winwheel@2.8.1/Winwheel.min.js"></script>

  <script>
    // Utility: simple color generator (pastel)
    function randomPastel() {
      const h = Math.floor(Math.random()*360);
      const s = 70 + Math.floor(Math.random()*10);
      const l = 55 + Math.floor(Math.random()*5);
      return `hsl(${h} ${s}% ${l}%)`;
    }

    // Build segments from names
    function buildSegments(names, colors) {
      const segments = [];
      for (let i=0;i<names.length;i++){
        const text = names[i].trim();
        if (!text) continue;
        const fillStyle = (colors && colors[i]) ? colors[i].trim() : randomPastel();
        segments.push({ 'fillStyle': fillStyle, 'text': text });
      }
      return segments;
    }

    let theWheel = null;

    function createWheelFromInputs() {
      const namesRaw = document.getElementById('namesInput').value.trim();
      if (!namesRaw) { alert('Please enter at least one name.'); return null; }
      const names = namesRaw.split(/\r?\n/).filter(s=>s.trim().length>0);
      const colorInput = document.getElementById('colorsInput').value.trim();
      let colors = null;
      if (colorInput) {
        colors = colorInput.split(',').map(c=>c.trim()).filter(Boolean);
      }
      const segments = buildSegments(names, colors);
      if (segments.length === 0) { alert('No valid names found.'); return null; }

      // if existing wheel, stop animations and clear
      if (theWheel && theWheel.stopAnimation) {
        theWheel.stopAnimation(false);
      }

      // Create the wheel
      theWheel = new Winwheel({
        'canvasId'     : 'wheelCanvas',
        'numSegments'  : segments.length,
        'outerRadius'  : 240,
        'textFontSize' : 16,
        'textMargin'   : 6,
        'segments'     : segments,
        'animation'    : {
          'type'     : 'spinToStop',
          'duration' : Number(document.getElementById('spinDuration').value) || 6,
          'spins'    : Number(document.getElementById('spinsInput').value) || 8,
          'callbackFinished' : onFinish,
        }
      });

      // draw once
      theWheel.draw();
      document.getElementById('winnerBox').textContent = 'Ready — press Spin';
      return theWheel;
    }

    function onFinish(selected) {
      // Winwheel passes indicatedSegment with text property in many builds; handle both forms
      let winnerText = '';
      if (!selected) {
        // fallback: compute indicated segment
        const indicated = theWheel.getIndicatedSegment();
        winnerText = indicated ? indicated.text : 'Unknown';
      } else if (selected.text) {
        winnerText = selected.text;
      } else if (selected.segment && selected.segment.text) {
        winnerText = selected.segment.text;
      } else {
        winnerText = String(selected);
      }

      const box = document.getElementById('winnerBox');
      box.textContent = `Winner: ${winnerText}`;
      // highlight winner slice briefly
      try {
        const seg = theWheel.getIndicatedSegment();
        const oldStyle = seg.fillStyle;
        seg.fillStyle = '#ffd54f';
        theWheel.draw();
        setTimeout(()=>{ seg.fillStyle = oldStyle; theWheel.draw(); }, 1200);
      } catch(e){}
    }

    // attach events
    document.getElementById('createBtn').addEventListener('click', ()=>{
      createWheelFromInputs();
    });

    document.getElementById('clearBtn').addEventListener('click', ()=>{
      document.getElementById('namesInput').value = '';
      document.getElementById('colorsInput').value = '';
      if (theWheel && theWheel.stopAnimation) { theWheel.stopAnimation(false); }
      const ctx = document.getElementById('wheelCanvas').getContext('2d');
      ctx.clearRect(0,0,520,520);
      document.getElementById('winnerBox').textContent = 'No winner yet';
      theWheel = null;
    });

    document.getElementById('spinBtn').addEventListener('click', ()=>{
      if (!theWheel) {
        const ok = createWheelFromInputs();
        if (!ok) return;
      }
      // update animation parameters if user changed duration/spins after creation
      theWheel.animation.duration = Number(document.getElementById('spinDuration').value) || theWheel.animation.duration;
      theWheel.animation.spins = Number(document.getElementById('spinsInput').value) || theWheel.animation.spins;
      theWheel.startAnimation();
      document.getElementById('winnerBox').textContent = 'Spinning...';
    });

    // click on wheel to spin (nice UX)
    document.getElementById('wheelCanvas').addEventListener('click', ()=>{
      document.getElementById('spinBtn').click();
    });

    // save wheel -> copy JSON of segments (simple)
    document.getElementById('saveBtn').addEventListener('click', ()=>{
      if (!theWheel) { alert('Create the wheel first.'); return; }
      const data = {
        segments: theWheel.segments.map(s=>({text:s.text, fillStyle:s.fillStyle}))
      };
      const json = JSON.stringify(data, null, 2);
      navigator.clipboard?.writeText(json).then(()=>{ alert('Wheel JSON copied to clipboard'); }, ()=>{ prompt('Wheel JSON (copy manually):', json); });
    });

    // load wheel from JSON pasted by user
    document.getElementById('loadBtn').addEventListener('click', ()=>{
      const pasted = prompt('Paste wheel JSON (segments array with text and optional fillStyle):');
      if (!pasted) return;
      try {
        const obj = JSON.parse(pasted);
        if (!obj.segments || !Array.isArray(obj.segments)) throw 'Invalid JSON';
        // populate names and colors inputs for convenience
        document.getElementById('namesInput').value = obj.segments.map(s=>s.text||'').join('\\n');
        const colors = obj.segments.map(s=>s.fillStyle||'').join(',');
        document.getElementById('colorsInput').value = colors;
        createWheelFromInputs();
      } catch(e) {
        alert('Could not parse JSON: '+e);
      }
    });

    // create initial demo wheel
    document.addEventListener('DOMContentLoaded', ()=>{
      const demo = ['Alice','Bob','Charlie','Delta','Eve','Frank'];
      document.getElementById('namesInput').value = demo.join('\\n');
      createWheelFromInputs();
    });
  </script>
</body>
</html>
