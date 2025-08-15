# Unified Olympiad Judging Page — IranTVTO × WorldSkills- Tirotir (v1)

> **Presented by Khuzestan TVTO – Izeh – AI Institute**

A lightweight, interactive **online/offline** judging page aligned with WorldSkills/TD22 principles. Two scoring tables — **Judgement (0–3)** and **Measurement** — combine into a live final score using configurable weights. Supports **local save**, **Print/PDF**, and **Export JSON/CSV (UTF‑8 with BOM)**. Skill rubrics are auto‑loaded/merged from `rubrics.en.json`.

**Online:** [Here](https://tirotir-ir.github.io/olympiad-tirotir-en/)

**Official TDs:** [https://skill.irantvto.ir/td22](https://skill.irantvto.ir/td22)
*This page is an executive summary of the official PDFs. For complete and up‑to‑date rules, always consult the official TD PDFs above.*

---

## Repo contents

* `index_en.html` — standalone judging UI (LTR, Tailwind CDN, tooltip, BOM CSV)
* `rubrics.en.json` — skill weights/criteria & environment chips
* `README_EN.md` — this guide (rename to `README.md` on the English branch)
* `LICENSE` (or `LICENSE_EN`) — MIT License

## Quick start (online *or* offline)

### A) **Online with GitHub Pages**

1. Place files in repo root (`index_en.html`, `rubrics.en.json`, `README_EN.md`, `LICENSE`).
2. **Settings → Pages** → Branch: `main`, Root: `/`.
3. Public URL: `https://<user>.github.io/<repo>/` (serves `index_en.html`).

### B) **Offline without a server (double‑click file)**

* Open `index_en.html` directly in a browser. The page works (local storage & scoring).
* Note: due to browser security, **`rubrics.en.json` may not load**. The page falls back to **built‑in templates**. Use C/D for local serving.

### C) **Offline with a simple local server** *(recommended)*

> Ensures Fetch/CORS and JSON loading work reliably.

* **Python 3**

  ```bash
  cd <repo>
  python -m http.server 5500
  # open: http://localhost:5500
  ```
* **Node.js — http-server**

  ```bash
  cd <repo>
  npx http-server -p 5500 --cors
  # open: http://localhost:5500
  ```
* **VS Code — Live Server**

  1. Install *Live Server*. 2) Right‑click `index_en.html` → **Open with Live Server**.

### D) **Offline with XAMPP (local Apache)**

* Start **Apache** (XAMPP Control Panel / manager‑osx).
* Copy files to web root, e.g. `htdocs/td22-en/`.
* Open `http://localhost/td22-en/` (or `http://localhost:8080/td22-en/` if port changed).

> If you change the port, adjust the URL accordingly. For permission issues on macOS/Linux, ensure the folder is readable (e.g., `chmod -R a+rX`).

---

## Daily use

1. Select **Skill** and **Module/Day**; enter **Competitor/Team ID** and **Judge name**.
2. **Judgement**: score 0–3 per aspect; row weights are editable (sum = 100).
3. **Measurement**: set *Max* and *Achieved* per indicator (quick **0/Full** buttons).
4. Set final weights **Judgement/Measurement** (must sum to 100).
5. Save/Load locally, **Export JSON/CSV**, **Print/PDF**, **Reset**, or **Reset to skill template**.

## Rubrics

* Loaded automatically from `rubrics.en.json` and merged with built‑in templates.
* Sample structure:

```json
[
  {
    "id": "web",
    "title": "Web Technologies (TD17)",
    "weights": { "judgement": 50, "measurement": 50 },
    "chips": ["USB not allowed for competitors", "C‑2: personal keyboard/mouse/headphones"],
    "judgement": [{ "name": "Code quality", "weight": 25 }],
    "measurement": [{ "name": "Validation & tests passed", "weight": 30 }]
  }
]
```

* Update by editing the JSON and pressing **Load rubrics.en.json** in the page.

## Tech notes

* **CSV encoding:** CSVs include a **UTF‑8 BOM** so Excel displays non‑ASCII correctly.
* **Print:** `print-color-adjust: exact` is enabled.
* **Tooltips:** long aspect/indicator names are shown via a lightweight tooltip on Hover/Focus.
* **Privacy:** all data stays in the browser (LocalStorage). Use **Export** for archiving.

## Branding

* Title & header: **Unified Olympiad Judging Page — IranTVTO × WorldSkills (v1)**.
* Footer credit: *Presented by Khuzestan TVTO – Izeh – AI Institute: `https://tirotir.ir`*.
* Official TDs: `https://skill.irantvto.ir/td22`.

## License

* Code under **MIT License** (`LICENSE` or `LICENSE_EN`).
