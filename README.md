# Zoho Project Template

A starter template for any Zoho marketing project — works for Shift, CRM, Books, Desk, and any future product.

This template gives every project the same **three foundations**:

1. **Project coding rules** (`.cursorrules`) — Zoho-wide HTML/CSS standards. Cursor reads these automatically.
2. **Design system tokens** (`design-system/ods-design-system.css`) — All ODS colors, typography, spacing, radii, and components as CSS variables.
3. **Reference structure** (`examples/index.html.example`) — A starter page showing the required section pattern.

---

## Folder structure

```
zoho-project-template/
├── .cursorrules                       Cursor-read project rules
├── .gitignore
├── README.md
│
├── design-system/                     Read-only: design tokens + components
│   └── ods-design-system.css
│
└── examples/                          Reference HTML pages
    └── index.html.example
```

Designers keep this folder structure intact when they clone — `design-system/` stays as the in-repo source of truth, `examples/` stays as reference.

---

## How to use

### Start a new project

```bash
git clone https://github.com/muthuveerapandi-s-2874/zoho-project-template my-new-project
cd my-new-project
rm -rf .git
git init
git add -A
git commit -m "chore: initialize from zoho-project-template"
```

Open the folder in Cursor.

### Build a page

Open Cursor's Claude Code panel and invoke the visual language skill for your product:

- **Shift:** `/shift-visual-language build me a [page type]`
- **CRM:** `/crm-visual-language ...` *(when available)*
- **Other products:** their respective skills

Claude will:

- Read `.cursorrules` automatically (Cursor passes them in)
- Reference `design-system/ods-design-system.css` for tokens
- Apply the visual language for your specific product
- Generate the page following all three layers

### Verify a generated page

After Claude generates a page, do a quick sanity check:

```bash
# Should be many — page uses CSS variables
grep -c "var(--" your-page.html

# Should be 0 (or close to 0) — no hardcoded hex colors outside the CSS file
grep -c "#[0-9a-fA-F]\{6\}" your-page.html
```

---

## What is in this template

| File | Purpose |
|---|---|
| `.cursorrules` | Project rules: HTML semantic correctness, section structure, CSS rules, accessibility, image handling. Cursor applies these automatically to every prompt. |
| `design-system/ods-design-system.css` | Resolved CSS artifact from the ODS design system. All tokens (colors, typography, spacing, radius, CTA component) as CSS variables. **Read-only — do not edit.** |
| `examples/index.html.example` | Reference page showing the required section structure (`zwc-section-name → content-wrap → inner-content`) and how to import the design system. |
| `.gitignore` | Standard ignores for web projects. |

---

## Folder conventions for designers

When you're working in a new project cloned from this template:

| Folder | Use it for |
|---|---|
| Project root (`./`) | Your generated pages — `index.html`, `pricing.html`, `signup.html`, etc. |
| `design-system/` | Don't edit. Pulled fresh from this template when you sync. |
| `examples/` | Reference only. Your real pages live at the project root. |
| (Future) `assets/` | Images, fonts, icons — when your project has any. |
| (Future) `scripts/` | Build scripts or page-specific JS — when you need them. |

The template is intentionally minimal. Folders get added when content justifies them, not preemptively.

---

## Keeping in sync with updates

The CSS file and rules will evolve. To pull the latest into an existing project:

```bash
# From inside your project folder:
curl -O https://raw.githubusercontent.com/muthuveerapandi-s-2874/zoho-project-template/main/design-system/ods-design-system.css \
  -o design-system/ods-design-system.css

curl -O https://raw.githubusercontent.com/muthuveerapandi-s-2874/zoho-project-template/main/.cursorrules
```

Or just clone the template fresh and copy your project files into the new clone.

---

## Sources

- **Design system source:** [design-skills-marketplace](https://github.com/muthuveerapandi-s-2874/design-skills-marketplace) — JSON tokens and visual language skills.
- **CSS artifact:** generated from the marketplace and synced here.

If the CSS file ever drifts from the design system source, the marketplace repo is the source of truth.

---

## License

MIT.
