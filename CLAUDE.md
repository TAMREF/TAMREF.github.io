# CLAUDE.md — Personal Academic Website + Blog (Quarto + GitHub Pages)

You are helping me set up and maintain a personal academic website + blog using **Quarto** and **GitHub Pages**.
Assume I’m comfortable editing `.qmd/.yml` and using git, and I’m fine with `.qmd` posts.

Feel free to edit / remove current assets.

## High-level goals

1. **Website structure**
   - A clean academic homepage with:
     - About page
     - Publications page (generated from BibTeX)
     - Blog index
     - Optional: Projects / Talks / Notes sections
   - Minimal, readable design. Prioritize typography and math readability.

2. **Writing experience**
   - I want to write posts in Markdown/Quarto (`.qmd`) with LaTeX-style math.
   - Math should support:
     - `equation`, `align`, `gather`, etc.
     - **Automatic equation numbering** (AMS-style tagging)
     - `\label{...}`, `\ref{...}`, `\eqref{...}` cross-references.

3. **Bibliography & citations**
   - I want citations inside posts using Pandoc/Quarto cite syntax like `[@KEY]`.
   - I keep a `references.bib` (BibTeX).
   - I want a convenient workflow where a citation key like `@arXiv:2504.06033` is possible **if I define that as the BibTeX entry key**.
   - Publications page should be generated from the same bib file.
   - Output style: prefer short in-text citations (author-year or numeric is fine), but keep it consistent across the site.
   - Do not invent bib entries; if needed, add a placeholder and mark it clearly.

4. **Deployment**
   - Deploy via **GitHub Pages** using a **GitHub Actions workflow** that renders Quarto and publishes `docs/` (or `gh-pages` branch; pick one and be consistent).
   - Site should build reliably on a fresh environment.

5. **Comments (optional)**
   - Comments are not required, but if easy, add **giscus** integration (GitHub Discussions-based).
   - Make it a toggle in config (easy to remove).

## Non-goals

- No heavy JavaScript framework migrations (e.g., React/Next) unless explicitly requested.
- No server-side components.
- No vendor lock-in beyond Quarto + GitHub Pages.

## Implementation requirements

### Quarto project conventions
- Use a standard Quarto website project layout:
  - `_quarto.yml` as the main config
  - `index.qmd` for landing page
  - `about.qmd`
  - `publications.qmd`
  - `posts/` directory for blog posts
  - `assets/` for images and static files
  - `styles.css` for light custom styling
  - `references.bib` at project root (or `bibliography/refs.bib`, but be consistent)

- Blog:
  - Enable Quarto blog listing
  - Each post in `posts/YYYY-MM-DD-title/index.qmd` (preferred) or `posts/YYYY-MM-DD-title.qmd`
  - Include front matter: title, date, categories/tags, draft (optional)

### Math rendering (important)
- Use **MathJax** (not KaTeX) to support AMS equation numbering and labels.
- Configure MathJax to use **AMS tags** so `align` gets numbers and `\label/\ref` works.
- Keep math configuration in one place (prefer `_quarto.yml` or a shared include).
- Provide a minimal test post that demonstrates:
  - a numbered `equation`
  - a numbered `align`
  - `\label` + `\eqref` cross-reference

### Citations & bibliography
- Use Pandoc citations in `.qmd`:
  - Example: `Blah blah [@arXiv:2504.06033].`
- Configure bibliography globally so posts automatically pick it up.
- Use a consistent CSL (citation style) file if needed.
- Publications page:
  - Render a curated list from bib entries, grouped by type (preprints / conference / journal) if possible.
  - If grouping is too hard without extra tooling, do a single list but keep it neat.
  - Do not duplicate data: publications should source from the bib file.

### GitHub Pages deployment
- Provide a GitHub Actions workflow that:
  - checks out repo
  - installs Quarto
  - renders the site
  - publishes to GitHub Pages
- Choose one of:
  1) publish the rendered site from `docs/` on `main`
  2) publish to `gh-pages` branch
- Prefer the approach that is simplest and most robust for Quarto.

### Writing style / UX
- Navigation should include: Home, About, Publications, Blog (and optionally Projects).
- Keep the theme simple (Quarto built-in theme is fine; add small CSS tweaks).
- Ensure code blocks and math are readable and not cramped.
- No emojis, no gimmicky visuals.

## What I want you to output when you work

When making changes, always present:
1. A short summary of what you changed and why.
2. The exact file tree (only relevant parts).
3. Full contents of each modified/added file.

If there are multiple valid options, pick one and commit to it. Avoid long “pros/cons” lists.

## Initial deliverable (do this first)

Generate an initial Quarto project skeleton that includes:
- `_quarto.yml` with:
  - website title, navbar, blog listing, MathJax AMS tagging enabled
  - global bibliography config pointing to `references.bib`
- `index.qmd` (brief academic landing page)
- `about.qmd` (placeholder sections: bio, research interests, contact)
- `publications.qmd` (generated/structured around bibliography)
- `posts/2026-01-05-welcome/index.qmd`:
  - demonstrates math equation numbering + cross-reference
  - demonstrates at least one citation key `[@arXiv:2504.06033]` (assume bib entry exists)
- `references.bib` with a placeholder entry using key `arXiv:2504.06033` (do NOT fabricate details; put a clearly-marked placeholder)
- `styles.css` with minimal typography tweaks
- `.github/workflows/deploy.yml` for GitHub Pages

After initial scaffold, be ready to iterate:
- add giscus comments (optional toggle)
- refine publications formatting
- add a “Notes” section if asked
- add custom domain instructions if asked
