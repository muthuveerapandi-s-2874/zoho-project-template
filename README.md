# Zoho Project Template

A starter template for Zoho marketing pages and product sites — works for any Zoho product (Shift, CRM, Books, Desk, Projects, etc.).

This template gives every project the same **three foundations**:

1. **Project coding rules** (`.cursorrules`) — Zoho-wide HTML/CSS standards. Cursor reads these automatically.
2. **Design system tokens** (`ods-design-system.css`) — All ODS colors, typography, spacing, radii, and components as CSS variables.
3. **Reference structure** (`index.html.example`) — A starter page showing the required section structure.

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

You are ready. Open the folder in Cursor.

### Build a page

Open Cursor's Claude Code panel and invoke the visual language skill for your product:

- **Shift:** `/shift-visual-language build me a [page type]`
- **CRM:** `/crm-visual-language ...` *(when available)*
- **Other products:** their respective skills

Claude will:

- Read `.cursorrules` automatically (Cursor passes them in)
- Reference `ods-design-system.css` for tokens
- Apply the visual language for your specific product
- Generate the page following all three layers

### Verify a generated page

After Claude generates a page, do a quick sanity check:

```bash
# Should show many — uses CSS variables
grep -c "var(--" your-page.html

# Should show 0 — no hardcoded colors outside the CSS file
grep -c "#[0-9a-fA-F]\{6\}" your-page.html
```

---

## What is in this template

| File | Purpose |
|---|---|
| `.cursorrules` | Project rules: HTML semantic correctness, section structure, CSS rules, accessibility, image handling. Cursor applies these automatically to every prompt. |
| `ods-design-system.css` | Resolved CSS artifact from the ODS design system. All tokens (colors, typography, spacing, radius, CTA component) as CSS variables. **Read-only — do not edit.** |
| `index.html.example` | Reference page showing the required section structure (`zwc-section-name → content-wrap → inner-content`) and how to import the design system. |
| `.gitignore` | Standard ignores for web projects. |

---

## Updating

The CSS file and rules will evolve over time. To pull the latest into an existing project:

```bash
# From inside your project folder:
curl -O https://raw.githubusercontent.com/muthuveerapandi-s-2874/zoho-project-template/main/ods-design-system.css
curl -O https://raw.githubusercontent.com/muthuveerapandi-s-2874/zoho-project-template/main/.cursorrules
```

Or just clone the template fresh and copy your project files into the new clone.

---

## Sources

- **Design system source:** [design-skills-marketplace](https://github.com/muthuveerapandi-s-2874/design-skills-marketplace) — the JSON tokens and visual language skills
- **CSS artifact:** generated from `design-skills-marketplace/design-system/` and synced here

If the CSS file ever drifts from the design system source, the marketplace repo is the source of truth.

---

## License

MIT.
