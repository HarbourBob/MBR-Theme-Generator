# MBR Theme Generator

> **A single HTML file that produces complete, security-first WordPress themes and child themes in seconds. No build step. No installer. No upsells. Free as in actually free.**

Open the file in any modern browser, configure your theme, click generate, and a ready-to-install zip lands in your downloads folder. That's the whole tool.

[**▸ Try it now**](https://littlewebshack.com/mbr-theme-generator/) — runs entirely in your browser.
[**▸ Read the user guide (PDF)**](docs/mbr-theme-generator-user-guide-v1_8_1.pdf)

---

## What it makes

**Classic themes** — the traditional kind. Header, footer, single, page, archive, search, 404, comments, sidebar. Optional Customiser-driven Header & Footer Builder with sticky modes, mobile menu styles, CTA buttons, and back-to-top. Page builder compatibility for Elementor, Bricks, Oxygen, Beaver, WPBakery, and Gutenberg.

**Block themes (Full Site Editing)** — `theme.json` v3, six HTML templates, two parts, ten block patterns, three style variations (Dark, Sepia, High Contrast), and Google Fonts bundled locally so you stay GDPR-clean by default.

**Child themes (new in v1.8.1)** — a complete child theme builder for both classic and block parents. Pick from a dozen common presets (Twenty Twenty-Five, Astra, GeneratePress, Hello Elementor, Kadence, Blocksy, OceanWP, Storefront, and more) or paste a custom slug. Override colours, typography, layout, templates, or add `functions.php` scaffolds — and ship the result as a clean, safe-to-activate child theme.

---

## Why this exists

Most "WordPress theme generators" you'll find online fall into one of three traps:

- **Bloated** — sign up, watch ads, pay £29 to remove the watermark, get a theme full of dependencies on the vendor's own plugin.
- **Outdated** — built for WordPress 4.x, no FSE support, no `theme.json`, no idea what a block theme is.
- **Footgun-shaped** — they generate child themes with empty override stubs that break your front end on activation, or `theme.json` that erases the parent's palette because nobody told the author that WordPress doesn't deep-merge arrays.

This one is none of those. It's a single HTML file, runs entirely in your browser, costs nothing, and gets the boring details right.

### What "gets the details right" actually means

- **Every PHP file starts with `ABSPATH` checks.** Every `echo` is escaped. Every form has a nonce. Every input is sanitised. Every database query is prepared. No `eval()`, no `extract()`, ever.
- **Classic child theme override stubs delegate to the parent by default.** Activate the child theme and your site looks identical to the parent's. Customise progressively by replacing the delegation block with your own markup — never accidentally break the front end.
- **FSE child theme `theme.json` overrides emit the full parent palette with your edits applied.** Override one colour without erasing the other seven. The generator ships with the actual palettes from Twenty Twenty-Two through Twenty Twenty-Five, so it knows what slugs to use and what the parent's defaults are.
- **WordPress.org submission-ready out of the box.** `LICENSE`, `readme.txt`, `rtl.css`, `languages/{slug}.pot`, screenshot, and the WCAG 2.1 AA skip-to-content link for block themes. All present, all valid.
- **No runtime calls to anyone else's servers.** Block themes that use Google Fonts have the WOFF2 files bundled into the zip at generation time. No `fonts.googleapis.com` requests at runtime. No cookie-banner impact.

---

## Quickstart

1. **[Download the latest release](https://github.com/harbourbob/mbr-theme-generator/releases/latest)** or clone this repo.
2. Open `mbr-theme-generator-1_8_1.html` in Chrome, Firefox, Edge, or Safari.
3. Pick **New Theme** or **Child Theme** at the top of the form.
4. Fill in the basics (name, author, description, version), pick a style, toggle features.
5. Click **Generate & Download**. A zip file lands in your downloads folder.
6. Upload to WordPress: **Appearance → Themes → Add New → Upload Theme**.

That's it. No build step, no `npm install`, no accounts, no cloud anything.

---

## Highlights

### The Header & Footer Builder (classic themes)

Customiser-driven panels with live preview. Layout presets, Smart Sticky (slides out on scroll-down, snaps back on scroll-up), shadow-on-scroll, transparent header for landing pages, search slide-out, CTA button, three mobile menu styles (dropdown, slide-in, full-screen overlay). Footer with widget columns, custom copyright using `{year}` and `{site}` placeholders, back-to-top button.

### Block themes that don't phone home

Pick Business or Portfolio with Block style and the generator fetches the matching Google Fonts at generation time, drops them into `assets/fonts/`, and writes `theme.json` `fontFace` entries pointing at the local files. The finished theme is fully self-contained — no runtime DNS lookups, no cross-origin handshakes, no GDPR exposure from font loading.

If Google Fonts is unreachable when you generate (offline, corporate firewall), the generator gracefully falls back to system-font stacks. No half-finished output, no dangling empty `assets/fonts/` directory.

### The Child Theme Builder

The headline feature of v1.8.1. Two paths, depending on parent type:

**Classic parents** (Hello Elementor, Astra, GeneratePress, etc.): toggle which templates you want to override and the generator scaffolds delegation stubs. Each stub `require`s the parent's equivalent file inside an `ABSPATH` guard and a `file_exists()` check. Activate immediately, customise progressively, never break the front end.

**Block (FSE) parents** (Twenty Twenty-Two through Twenty Twenty-Five, plus custom): toggle theme.json overrides for colour palette, typography, or layout. The generator ships with the actual palettes for the WordPress default block themes, so the colour fields render dynamically with the parent's real slugs (TT5's `accent-1` through `accent-6`, TT4's longer base/contrast/accent system, TT2's `foreground`/`background`/`primary`/`secondary`/`tertiary`). Type new values, leave others blank to inherit. The output is a `theme.json` that contains the full parent palette with your edits merged in — so WordPress's array-replacement merge behaviour produces the right outcome.

For custom FSE parents, paste the parent's `palette` array (or its full `theme.json`) and the colour fields render dynamically from your paste. Live parse feedback as you type.

### Save and load configurations

Save the entire generator state as a JSON file, reload it later. Build a library of starter configs for your common project types and a new client theme is two clicks away. Format is versioned (currently v4), backwards-compatible with older saves.

### Live theme-aware preview

The screenshot you see in the generator is composed from your actual settings — palette, typography, content type — and rendered as SVG that updates as you change anything. The same SVG is rasterised to a 1200×900 PNG and shipped as `screenshot.png` in the zip. What you see is what WordPress shows.

---

## What's in a generated theme

### Classic theme

```
your-theme/
├── style.css
├── functions.php
├── index.php
├── header.php / footer.php
├── single.php / page.php / archive.php / search.php / 404.php
├── comments.php / sidebar.php
├── assets/css/ assets/js/
├── inc/                          (feature files: customiser, etc.)
├── template-parts/               (optional)
├── languages/{slug}.pot
├── README.md / readme.txt / LICENSE / rtl.css
└── screenshot.png
```

### Block theme

```
your-theme/
├── style.css                     (theme header + skip-link CSS)
├── theme.json                    (v3 schema, full design tokens)
├── functions.php                 (minimal setup)
├── index.php                     (fallback stub)
├── templates/                    (6 HTML templates)
├── parts/                        (header.html, footer.html)
├── patterns/                     (10 block patterns)
├── styles/                       (3 style variations)
├── assets/fonts/                 (locally-bundled Google Fonts)
├── languages/{slug}.pot
├── README.md / readme.txt / LICENSE / rtl.css
└── screenshot.png
```

### Classic child theme

```
my-child/
├── style.css                     (Template: parent-slug, custom CSS)
├── functions.php                 (modern parent + child enqueue)
├── header.php                    (delegates to parent)        ← optional
├── footer.php / single.php / page.php / etc.                   ← all optional
├── README.md / readme.txt / LICENSE
└── screenshot.png
```

### FSE child theme

```
my-child/
├── style.css                     (Template: parent-slug)
├── theme.json                    (full parent palette + your overrides)
├── functions.php                 (minimal scaffolds, no parent enqueue)
├── templates/index.html          ← optional
├── parts/header.html             ← optional
├── README.md / readme.txt / LICENSE
└── screenshot.png
```

---

## Browser compatibility

The generator runs in any modern browser. Tested in:

- Chrome 120+
- Firefox 120+
- Edge 120+
- Safari 17+

Mobile browsers work but the form is dense — desktop is recommended for the actual generation step.

---

## Requirements (for the generated themes)

| | New theme (classic) | New theme (block) | Classic child | FSE child |
|---|---|---|---|---|
| WordPress | 6.0+ | 6.4+ | 6.0+ | 6.4+ |
| PHP | 7.4+ | 7.4+ | 7.4+ | 7.4+ |
| Parent installed | — | — | yes | yes |

The minimum WordPress and PHP versions can be bumped per-theme in Section 1 of the generator if you want to require something newer.

---

## Documentation

- **[User guide (PDF)](docs/mbr-theme-generator-user-guide-v1_8_1.pdf)** — the comprehensive 38-page manual covering every setting, with worked examples for the child theme builder
- **[Changelog](CHANGELOG.md)** — release history and version notes
- **[Contributing](CONTRIBUTING.md)** — bug reports, feature requests, and pull requests welcome

---

## Philosophy

This tool follows a few principles I keep coming back to in everything I publish:

1. **Free with no upsells.** Every feature works the same regardless of who you are. No "Pro version" hiding the useful settings.
2. **No accounts, no telemetry.** The generator runs entirely in your browser. Nothing is uploaded anywhere.
3. **No external dependencies at runtime.** A theme generated by this tool makes zero network calls to anyone other than the site it's installed on.
4. **Security by default.** Every output is escaped. Every input is sanitised. Every form has a nonce. Doing the boring thing properly is the actual feature.
5. **Honest about limits.** When something doesn't work — like FSE block template overrides not being able to delegate to parent the way classic ones can — the docs and the UI say so plainly rather than glossing over it.

---

## Releases

Tagged releases live in [Releases](https://github.com/harbourbob/mbr-theme-generator/releases). Each release contains a single self-contained HTML file. Download the latest, open it, generate themes.

The generator stores `_version` in saved JSON configs; older configs (v1, v2, v3) load correctly in v1.8.1 via backwards-compat paths.

---

## Other plugins from the same brand

If this is useful, you might also like:

- **[MBR WP Performance](https://littlewebshack.com/mbr-wp-performance/)** — performance optimisations for WordPress without the bloat
- **[MBR Cookie Consent](https://littlewebshack.com/mbr-cookie-consent/)** — GDPR-compliant cookie banner with geolocation, A/B testing, IAB TCF v2.3, Google Consent Mode v2
- **[MBR Advanced Asset Manager](https://littlewebshack.com/mbr-advanced-asset-manager/)** — per-page CSS/JS dequeue control with global blocking
- **[MBR Live Radio Player](https://wordpress.org/plugins/mbr-live-radio-player/)** — Icecast/Shoutcast/HLS streaming player

All free. All no-upsell. All built the same way.

---

## Licence

GPL-2.0-or-later — same as WordPress itself. The generated themes inherit whichever licence you select in the form (GPL-2.0-or-later, GPL-3.0-or-later, or MIT).

---

## Author

Built by **[Robert Palmer](https://madebyrobert.co.uk)** — freelance WordPress developer based in Cleethorpes, UK. Specialises in bespoke e-commerce solutions and free, enterprise-quality plugins.

Find me at [littlewebshack.com](https://littlewebshack.com), [madebyrobert.co.uk](https://madebyrobert.co.uk), or on GitHub as [@harbourbob](https://github.com/harbourbob).

If the generator saves you time and you'd like to say thanks: [buy me a coffee](https://buymeacoffee.com/robertpalmer). Entirely optional, never required, won't unlock anything that isn't already free.
