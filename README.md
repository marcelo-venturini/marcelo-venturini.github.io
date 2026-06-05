# Marcelo Venturini — Portfolio

Personal CV / portfolio site, hosted on GitHub Pages.
Three languages: English (default), Spanish, Italian.
Editorial/document aesthetic — serif headings, muted slate-navy accent,
card-based content blocks.

## File structure

```
/
├── index.html                  ← English (root)
├── style.css                   ← shared by all three languages
├── profile.jpg                 ← your photo (4:5 aspect ratio works best)
│
├── es/
│   └── index.html              ← Spanish
│
├── it/
│   └── index.html              ← Italian
│
├── docs/
│   ├── CV_Marcelo_Venturini_EN.pdf
│   ├── CV_Marcelo_Venturini_ES.pdf
│   └── CV_Marcelo_Venturini_IT.pdf
│
├── Projects/                   ← one PDF per project (filenames must
│   ├── emg-thesis.pdf            match the href in the HTML)
│   ├── levodopa-device.pdf
│   └── ultrasonic-pic.pdf
│
└── Certificates/
    ├── Academic_Transcript_UNC.pdf
    └── PoliTo_Degree.pdf
```

**Anything referenced from HTML must exist at that path** — empty placeholder
PDFs work fine until you have the real ones.

## How "graduated" is communicated

Three places, intentionally:
1. **Eyebrow label above the name** — "RECENT GRADUATE · M.SC. 2026" (slightly
   tinted in accent navy, so it stands out without shouting).
2. **First sentence of the intro paragraph** — explicit and natural.
3. **Status row in the contact block** — first row, with a small accent dot.

If you want to make it louder, look for `.hero-label--graduated` in
`style.css` and increase its weight, size, or color.

## Changing the color

All colors are CSS variables at the top of `style.css`:

```css
:root {
  --accent:       #1f3753;   /* navy-leaning slate — main accent */
  --accent-hover: #182b41;
  --accent-soft:  #e6ebef;
  --page-bg:      #edf0f2;
  --text:         #18212a;
  --text-muted:   #53606b;
  --text-soft:    #6b7782;
  ...
}
```

For a deeper navy, try `--accent: #14274a` or `--accent: #11203d`. For
something warmer, `#3d2c20` (dark brown) also works with the rest of the
palette unchanged. Edit one variable and the entire site retints.

## Changing typography

The headings use Palatino/Book Antiqua (serif) and the body uses Aptos/Segoe
UI (sans). Both are system fonts — no web font loading, fast page loads,
serious feel. To swap fonts, edit the `--serif` and `--sans` variables at the
top of `style.css`.

## Adding a project

Find this block in any of the three `index.html` files (inside `.projects-grid`):

```html
<article class="project-card">
  <div class="project-top">
    <h3>Project Title</h3>
    <p class="project-context">Category | Year</p>
  </div>

  <p class="project-summary">Short paragraph.</p>

  <ul class="project-highlights">
    <li>Bullet point 1.</li>
    <li>Bullet point 2.</li>
  </ul>

  <div class="project-links">
    <a href="Projects/file.pdf" target="_blank">View Project</a>
  </div>
</article>
```

Copy/paste, edit. The grid is two columns and auto-flows.

**Remember**: add the project in all three language files. Inside `/es/` and
`/it/`, the PDF path needs `../Projects/file.pdf` (one folder up), not
`Projects/file.pdf`.

## Adding an experience

Same idea, inside `.experience-list`:

```html
<article class="experience-card">
  <div class="experience-header">
    <div>
      <h3>Role Title</h3>
      <p class="experience-company">Organization</p>
    </div>
    <div class="experience-meta">
      <span>Year – Year</span>
      <span>Location</span>
    </div>
  </div>

  <p class="experience-summary">Short paragraph.</p>

  <ul class="experience-highlights">
    <li>Bullet point.</li>
  </ul>

  <div class="experience-tags">
    <span class="tag">Tag 1</span>
    <span class="tag">Tag 2</span>
  </div>
</article>
```

## Adding a credential (education entry)

Inside `#education .sidebar-block`:

```html
<article class="credential-item">
  <h3>Degree Name</h3>
  <p class="credential-institution">Institution</p>
  <p class="credential-meta">Years | Location</p>
  <ul class="compact-list">
    <li>Bullet point.</li>
  </ul>
</article>
```

The bottom border between credentials appears automatically.

## Local preview

Open `index.html` directly in a browser — everything works offline. The
language switch needs the `es/` and `it/` folders to exist relative to each
file (which they do in the repo).

## Deploy

Standard GitHub Pages: push to `main` on `<username>.github.io` and it's live
at `https://<username>.github.io`.

## Notes on this template

- No JavaScript. Everything is static HTML + CSS. The page loads instantly.
- The footer is the only thing that breaks the central content column —
  it spans the full viewport width on purpose, for visual closure.
- The hero photo is 170px wide on desktop. If your image is larger it'll be
  scaled down via `object-fit: cover` (4:5 aspect). For best results, crop
  your photo to roughly that ratio.
