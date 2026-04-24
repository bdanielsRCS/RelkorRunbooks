# Relkor Runbooks

A public, static GitHub Pages site that hosts operational runbooks, test guides, and deliverables across every Relkor client engagement.

**Live URL:** _TBD after first deploy_ (typically `https://<owner>.github.io/RelkorRunbooks/`)

---

## Structure

```
RelkorRunbooks/
├── index.html               ← landing page with client tiles
├── _shared/
│   └── styles.css           ← shared stylesheet (dark-mode library theme)
├── lantern/                 ← one folder per client
│   ├── index.html           ← client landing page listing that client's docs
│   ├── inbound-dc-search-runbook.html
│   └── d360-deployment-loe.docx
├── .nojekyll                ← prevents GitHub Pages from processing as Jekyll
├── .gitignore
└── README.md                ← (this file)
```

## Adding a new client

1. `mkdir <clientname>` (lowercase, no spaces — e.g. `datavant`, `titan-health`)
2. Copy `lantern/index.html` as a starter and edit the eyebrow, title, lede, and tile grid
3. Add a tile to the root `index.html` under "Active projects" linking to `<clientname>/`
4. Commit + push — GitHub Pages auto-deploys in ~1 min

## Adding a new runbook to an existing client

1. Drop the HTML file (or .docx / .pdf) into the client's folder
2. Add a new `<a class="tile">` block in that client's `index.html`:
   ```html
   <a href="your-runbook.html" class="tile">
     <span class="tile-ribbon active">live</span>
     <span class="tile-icon">🧪</span>
     <div class="tile-title">Runbook title</div>
     <div class="tile-desc">Short description.</div>
     <div class="tile-meta">
       <span class="chip html">HTML</span>
       <span>Ticket ref · version</span>
     </div>
   </a>
   ```
3. Commit + push

## Conventions

- **File naming:** kebab-case, all lowercase: `inbound-dc-search-runbook.html`
- **Ribbons:** use `active` (green) for live, `draft` (yellow) for WIP, `soon` (gray) for placeholders
- **Chip colors in tile-meta:** `html` (blue), `docx` (purple), `md` (green) — matches `_shared/styles.css`
- **Individual runbooks self-style** — they don't need to pull from `_shared/styles.css` (most have styling inlined for portability). The shared stylesheet is only for the landing and index pages.
- **Client folder names:** short, lowercase, hyphenated — this becomes part of the URL

## Why GitHub Pages (not Salesforce Sites)

- Free, permanent, zero Salesforce licensing overhead
- Version-controlled by default
- Drop a file, commit, push → live in ~60 seconds
- Clients can be linked to just their folder (`/lantern/`) — each client's URL looks clean and scoped

## Icon ideas for future clients

🏮 Lantern · 🛡️ Titan · 🏔️ Northwestern · 🔷 Datavant · 🛍️ Entergy · ✈️ United · 🛗 Centric — pick something that visually distinguishes each client.
