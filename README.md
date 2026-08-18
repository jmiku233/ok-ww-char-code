# Wuthering Waves Character Codes Repository (ok-ww-char-code)

A static repository and download catalog for Wuthering Waves character codes and team configurations.

## 🌟 Features

- **Automated Extraction**: Reads each `.zip` under `codes/` and parses its internal `team.json`.
- **Team-based Grouping**: Groups code packages by team compositions.
- **Team JSON APIs**:
  - `teams.json` — Aggregated catalog of all teams and codes.
  - `teams/<team_slug>.json` — Dedicated JSON metadata and download URLs for each individual team.
- **Modern Responsive Web UI**:
  - Instant client-side search & filtering by character names, authors, versions, or descriptions.
  - One-click ZIP download and direct URL copy.
  - Character badges and metadata inspection.
- **Automated GitHub Actions CI/CD**:
  - Automatically runs on pushes to `main` (when new `.zip` files or scripts are updated).
  - Automatically updates root `index.html`, `teams.json`, and `teams/*.json`.
  - Deploys static pages to GitHub Pages.

---

## 📁 Directory Structure

```text
ok-ww-char-code/
├── .github/
│   └── workflows/
│       └── deploy.yml          # GitHub Actions workflow
├── codes/                      # Place your .zip files here
│   ├── Aemeath_Augusta_Baizhi_11_1.0.0.zip
│   ├── Aemeath_Brant_Calcharo_3_1.0.0.zip
│   └── Augusta_Baizhi_Buling_4_1.0.0.zip
├── scripts/
│   └── generate.js             # Generator script (Node.js)
├── teams/                      # Auto-generated JSON for each team
│   ├── Aemeath_Augusta_Baizhi.json
│   ├── Aemeath_Brant_Calcharo.json
│   └── Augusta_Baizhi_Buling.json
├── index.html                  # Auto-generated static UI
├── teams.json                  # Auto-generated aggregated index
├── package.json
└── README.md
```

---

## 🚀 Getting Started

### 1. Install Dependencies

```bash
npm install
```

### 2. Generate Static Pages & Team JSONs

```bash
npm run build
```

This will:
1. Scan `codes/*.zip`
2. Extract and parse `team.json` inside each archive
3. Generate individual team JSONs under `teams/`
4. Generate `teams.json` in the root directory
5. Generate `index.html` in the root directory

---

## 📦 Zip Structure Requirement

Each `.zip` in `codes/` should contain a `team.json` file at its root with the following structure:

```json
{
  "name": "Aemeath_Augusta_Baizhi",
  "description": "Team description or build guide",
  "author": "AuthorName",
  "version": "1.0.0",
  "team": "Aemeath, Augusta, Baizhi"
}
```

---

## 🌐 GitHub Pages Setup

1. Push your repository to GitHub.
2. In GitHub repository **Settings** -> **Pages**:
   - Source: Select **GitHub Actions**.
3. When you push new `.zip` files to `codes/`, the workflow in `.github/workflows/deploy.yml` will automatically build the static pages and deploy them.
