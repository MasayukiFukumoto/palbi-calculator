# palbi-calculator
This is a open-link. 

**最新版** https://masayukifukumoto.github.io/palbi-calculator/

**旧版**  https://masayukifukumoto.github.io/palbi-calculator/2025.05/


**This is a conversation log with ChatGPT o3.**


https://github.com/MasayukiFukumoto/palbi-calculator/blob/main/README.md#palbi-calculator

  

  

  

  



  



    

Below is a single English prompt you can paste into Deep-Research with GitHub-API scope.
Place this in README.md—nothing else.
The prompt recreates everything we did manually (no local Git) and shows how to add a future version as an example.
Lines beginning with # are explanatory comments for the agent.


This is the link that I made this README for the palbi-calculator in English and Japanese.
https://chatgpt.com/share/6829fa08-702c-8006-a9aa-bbfe17ffd63d

SYSTEM:
You are OpenAI Deep-Research with GitHub-API scope.

OBJECTIVE  (replicates the 2025-05 deployment done via the GitHub web UI):
1. Ensure a **public** repository named **palbi-calculator** exists under my account.
2. Add / overwrite the root file **index.html** with the plain-text UTF-8 source for  
   “PALBI Calculator Basic ver.2025-05” (fully functional calculator).
   • Include SEO tags: description, keywords, and minimal Open-Graph tags.
3. Enable GitHub Pages: branch = main, folder = /(root).
4. Verify the URL  
   `https://<username>.github.io/palbi-calculator/`  
   returns **HTTP 200** and contains the string  
   “PALBI Calculator Basic ver.2025.05”.
5. Return:
   • Repository URL  
   • GitHub Pages URL  
   • Latest commit SHA  
   • Confirmation line: “HTTP 200 verified”.

# ---  EXAMPLE: how to publish a future version (e.g., 2026-01) ---
# To keep old releases online, store each in a sub-folder YYYY.MM.
# Steps (do NOT execute now; shown only as reference):
#   mkdir 2026.01
#   copy current index.html to 2026.01/index.html
#   edit root index.html → update title to “ver.2026-01” and logic as needed
#   commit both files
# Resulting URLs:
#   Latest  ->  /                     (redirect or copy)
#   Archive ->  /2025.05/  /2026.01/  etc.
# ---------------------------------------------------------------

CONSTRAINTS:
• Repository must stay MIT-licensed.
• If the repo already exists, update index.html instead of recreating.
• Abort and report any permission errors.

FILE PAYLOAD (index.html)  ⬇⬇ (paste the full plain-text HTML between the dashed lines)
----------------------------------------------------------------
<!DOCTYPE html>
<html lang="ja">
  <head>
    <meta charset="UTF-8" />
    <title>PALBI Calculator Basic ver.2025.05 – PALBI/ALBI/Fib-4/Child-Pugh</title>

    <!-- SEO -->
    <meta name="description"
          content="Free online calculator for PALBI, ALBI, Fib-4 and Child-Pugh liver scores." />
    <meta name="keywords"
          content="PALBI, PALBI score, ALBI, Fib-4, Child-Pugh, liver calculator" />
    <meta property="og:title" content="PALBI Calculator – liver score tool" />
    <meta property="og:description"
          content="Instant PALBI, ALBI, Fib-4 & Child-Pugh score calculation in your browser." />

    <style>
      :root { font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
              Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
              --primary:#0066cc; line-height:1.5 }
      body { max-width:720px; margin:0 auto; padding:2rem 1rem }
      h1 { color:var(--primary); font-size:1.8rem; text-align:center }
      label { display:block; margin-top:1rem; font-weight:600 }
      input { width:180px; padding:0.4rem }
      button { margin-top:1.2rem; padding:0.6rem 1.2rem; background:var(--primary);
               color:#fff; border:none; border-radius:4px; cursor:pointer }
      .grid { display:grid; gap:0.5rem 1rem;
              grid-template-columns:repeat(auto-fit,minmax(200px,1fr)) }
      .result { margin-top:1.5rem; font-size:1.1rem; color:green }
      .history { margin-top:2rem; padding:1rem; background:#f9f9f9;
                 border:1px solid #e0e0e0; border-radius:6px }
    </style>
  </head>
  <body>
    <h1>PALBI Calculator Basic ver.2025.05</h1>

    <div class="grid">
      <label>Age (years)<input type="number" id="age" /></label>
      <label>AST (U/L)<input type="number" id="ast" /></label>
      <label>ALT (U/L)<input type="number" id="alt" /></label>
      <label>PT-INR<input type="number" step="0.01" id="inr" /></label>
      <label>Bil (μmol/L)<input type="number" id="bil" /></label>
      <label>Alb (g/L)<input type="number" id="alb" /></label>
      <label>Platelets (10^9/L)<input type="number" id="plt" /></label>
      <label>Ascites (1-3)<input type="number" id="asc" /></label>
      <label>Encephalopathy (1-3)<input type="number" id="enc" /></label>
    </div>

    <button onclick="calc()">Calculate</button>
    <div class="result" id="out"></div>

    <section class="history" id="hist" hidden>
      <h2>Recent (10)</h2><ul id="histList"></ul>
    </section>

    <script>
      function calc(){
        const v=id=>parseFloat(document.getElementById(id).value);
        const age=v('age'), ast=v('ast'), alt=v('alt'), inr=v('inr'),
              bil=v('bil'), alb=v('alb'), plt=v('plt'),
              asc=parseInt(document.getElementById('asc').value),
              enc=parseInt(document.getElementById('enc').value);
        if([age,ast,alt,inr,bil,alb,plt,asc,enc].some(x=>isNaN(x))){
          out.innerHTML='<span style=\"color:red\">Please fill all fields.</span>';return;}
        const logB=Math.log10(bil), logP=Math.log10(plt);
        const palbi=2.02*logB-0.37*logB**2-0.04*alb-3.48*logP+1.01*logP**2;
        const palbiG=palbi<=-2.53?'1':palbi<=-2.09?'2':'3';
        const albi=0.66*logB-0.0852*alb;
        const fib4=(age*ast)/(plt*Math.sqrt(alt));
        const bS=bil>51.3?3:bil>34.2?2:1, aS=alb<28?3:alb<35?2:1, iS=inr>1.7?3:inr>1.5?2:1;
        const child=bS+aS+iS+asc+enc, cClass=child<=6?'A':child<=9?'B':'C';
        out.innerHTML=`PALBI <b>${palbi.toFixed(3)}</b> (G${palbiG}) | ALBI <b>${albi.toFixed(3)}</b> | Fib-4 <b>${fib4.toFixed(2)}</b> | C-P <b>${child}</b> (Class ${cClass})`;
        const key='liverHist';
        const hist=JSON.parse(localStorage.getItem(key)||'[]');
        hist.unshift({t:new Date().toLocaleString(),palbi:palbi.toFixed(2)});
        if(hist.length>10)hist.pop();
        localStorage.setItem(key,JSON.stringify(hist));
        updateHist();
        localStorage.setItem('liverCount',(parseInt(localStorage.getItem('liverCount')||'0')+1));
      }
      function updateHist(){
        const list=document.getElementById('histList');
        const hist=JSON.parse(localStorage.getItem('liverHist')||'[]');
        if(!hist.length){histElem.hidden=true;return;}
        histElem.hidden=false;
        list.innerHTML=hist.map(x=>`<li>${x.t} – PALBI:${x.palbi}</li>`).join('');
      }
      updateHist();
    </script>
  </body>
</html>
----------------------------------------------------------------


Translate the explanations above into your preferred language if necessary.
