# PALBI Calculator / PALBI 計算ツール

Free, client-side calculator for **PALBI**, **ALBI**, **Fib-4**, and **Child-Pugh** liver scores.  
肝機能スコア **PALBI / ALBI / Fib-4 / Child-Pugh** をブラウザだけで即座に計算できます（入力値は一切送信されません）。

| &nbsp; | URL |
|-------|-----|
| **Live (latest)**<br>最新版 | https://masayukifukumoto.github.io/palbi-calculator/ |
| **Archive 2025-05**<br>旧版 | https://masayukifukumoto.github.io/palbi-calculator/2025.05/ |
| **Conversation log**<br>ChatGPT o3 議事録 | https://chatgpt.com/share/6829fa08-702c-8006-a9aa-bbfe17ffd63d |

---

## Features / 特長 ✨

* **Offline-ready** – pure HTML + JS, no server calls  
  **オフラインでも利用可** – 100 % クライアント実装
* **Dual language UI** – Japanese / English toggle  
  **日英切替** ボタンひとつ
* **Unit-safe PALBI** – 日本語 UI は血小板「万/µL」入力→自動で ×10³/µL に換算  
* Local history & statistics (browser `localStorage`)  
  最近10回の計算履歴と平均値を自動保存

---

## Quick start

```bash
git clone https://github.com/MasayukiFukumoto/palbi-calculator.git
cd palbi-calculator
open index.html   # or double-click the file








Re-deploy or update with OpenAI Deep-Research 🤖
深層自動化エージェントで 再現 / 将来バージョン公開 ができる 1-shot プロンプトを示します。
Copy everything inside the dashed block verbatim into Deep-Research (GitHub-API scope).
The agent will (1) ensure the repo exists, (2) upload index.html, (3) enable GitHub Pages, (4) verify HTTP 200.

<details> <summary>📋 Deep-Research Prompt (クリックして展開)</summary>


SYSTEM: You are OpenAI Deep-Research with GitHub-API scope.

OBJECTIVE (replicates the 2025-05 deployment done via the GitHub web UI):

Ensure a public repository named palbi-calculator exists under my account.
Add / overwrite the root file index.html with the plain-text UTF-8 source for
“PALBI Calculator Basic ver.2025-05” (fully functional calculator).
• Include SEO tags: description, keywords, and minimal Open-Graph tags.
Enable GitHub Pages: branch = main, folder = /(root).
Verify the URL
https://<username>.github.io/palbi-calculator/
returns HTTP 200 and contains the string
“PALBI Calculator Basic ver.2025.05”.
Return:
• Repository URL
• GitHub Pages URL
• Latest commit SHA
• Confirmation line: “HTTP 200 verified”.

--- EXAMPLE: how to publish a future version (e.g., 2026-01) ---
To keep old releases online, store each in a sub-folder YYYY.MM.
Steps (do NOT execute now; shown only as reference):
mkdir 2026.01
copy current index.html to 2026.01/index.html
edit root index.html → update title to “ver.2026-01” and logic as needed
commit both files
Resulting URLs:
Latest -> / (redirect or copy)
Archive -> /2025.05/ /2026.01/ etc.
---------------------------------------------------------------
CONSTRAINTS:
• Repository must stay MIT-licensed.
• If the repo already exists, update index.html instead of recreating.
• Abort and report any permission errors.

FILE PAYLOAD (index.html) ⬇⬇ (paste the full plain-text HTML between the dashed lines)
----------------------------------------------------------------
<title>PALBI Calculator Basic ver.2025.05 – PALBI/ALBI/Fib-4/Child-Pugh</title>
<!-- SEO -->
<meta name="description"
      content="Free online calculator for PALBI, ALBI, Fib-4 and Child-Pugh liver scores." />
<meta name="keywords"
      content="PALBI, PALBI score, ALBI, Fib-4, Child-Pugh, liver calculator" />
<meta property="og:title" content="PALBI Calculator – liver score tool" />
<meta property="og:description"
      content="Instant PALBI, ALBI, Fib-4 & Child-Pugh score calculation in your browser." />

<!-- …(full HTML omitted here for brevity; include entire file when you run the agent)… -->
----------------------------------------------------------------



License
MIT

MIT ライセンスのもとで自由に改変・再配布いただけます。
Please keep the copyright notice.

yaml
Copy
Edit

---

### 変更ポイント

* **可読性**：表・箇条書き・折りたたみで情報量を整理しました。  
* **二言語**：各セクションを日本語 / 英語併記。  
* **Deep-Research Prompt**：長文を `<details>` に収納し、README を開いた直後はコンパクトに。
