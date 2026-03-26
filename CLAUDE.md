# LAFA ADR Diagrams

Standalone site for LAFA's Architecture Decision Record diagrams. Single-page HTML with Mermaid.js charts, dark theme, and sticky TOC sidebar.

## Repo Structure

```
lafa-adr-diagrams/
├── index.html      ← The entire site (self-contained HTML + CSS + JS)
├── Dockerfile      ← nginx:alpine serving index.html
├── nginx.conf      ← nginx config with Railway $PORT
├── .gitignore
└── CLAUDE.md
```

## Stack

- **HTML/CSS** — self-contained, no build step
- **Mermaid.js v10** — CDN-loaded, renders diagrams client-side
- **nginx:alpine** — static file server via Docker
- **Railway** — hosting with auto-deploy

## Design System

| Token | Value | Usage |
|-------|-------|-------|
| Primary | `#FF5500` | Active nodes, headers, highlights |
| Background | `#0F0F0F` | Page background |
| Card bg | `#1A1A1A` | Card backgrounds |
| Border | `#2A2A2A` | Card borders, dividers |
| Muted text | `#9CA3AF` | Subtitles, descriptions |
| Subgraph bg | `#1F1510` | Mermaid subgraph containers |

### Node styles

- **Q2 active**: `fill:#FF5500,stroke:#FF5500,color:#FFFFFF`
- **Supporting**: `fill:#2A2A2A,stroke:#FF5500,color:#FFFFFF`
- **Future/dashed**: `fill:#1A1A1A,stroke:#FF5500,stroke-dasharray:5 5,color:#9CA3AF`

## Deploy

### Railway (production)

```bash
# From this directory:
railway up
```

URL: https://lafa-adr-diagrams-production.up.railway.app/

Railway project: `lafa-adr-diagrams` (ID: `0952710c-923e-47b7-b487-ddae62442c31`)

### GitHub

```bash
git add index.html
git commit -m "update: description of changes"
git push origin main
```

Repo: https://github.com/josediaz-lafa/lafa-adr-diagrams

### Local preview

```bash
python3 -m http.server 8000
# Open http://localhost:8000/
```

## Workflow

1. Edit `index.html`
2. Preview locally with `python3 -m http.server`
3. Commit and push to GitHub
4. Deploy to Railway with `railway up`

## Content Structure

18 cards organized in 4 sections:

| Section | Cards |
|---------|-------|
| **Foundations** | Principles, System Landscape, Module Map, Decisions Summary, Infrastructure Evolution, Migration Path, Cost Breakdown, AI Architecture |
| **Architecture** | Module Architecture, Adapter Pattern, Auth & RLS |
| **DAE / Payroll** | Payroll Pipeline, Rules Classification, Payroll Lifecycle, Runa Export |
| **LTO Credit** | LTO Lifecycle, Payment Schedule, Collections |

## What NOT to Do

- Don't add a build step — this is intentionally a single HTML file
- Don't split into multiple files — self-contained is the point
- Don't change the font (Inter Tight) — matches LAFA brand
- Don't use light theme — dark theme matches lafa.mx website
