# MBR Theme Generator

**A browser-based WordPress theme scaffolding tool that produces secure, production-ready themes in seconds.**

Version 1.6.2 | Built by [Robert Palmer](https://littlewebshack.com) | Free, no upsells, no premium tier

---

## What is it?

MBR Theme Generator is a single HTML file that runs entirely in your browser. You configure the options you need, hit Generate, and download a fully structured WordPress theme as a zip file. No server required, no account needed, no data collected.

Every theme it produces scores 10/10 on security. Output escaping on every echo, nonce verification on every form, input sanitisation throughout, prepared SQL statements, ABSPATH checks on all files, enqueued assets only, no eval() or extract() anywhere. This is not optional -- it is baked into every file the generator outputs.

The generated themes are Theme Check compliant out of the box, and ship with the files needed for WordPress.org directory submission.

## Who is it for?

Developers, freelancers, and agencies who want a clean starting point for client projects without inheriting someone else's opinions about layout or design. If you have ever grabbed a starter theme and spent the first hour ripping out things you did not need, this tool is for you.

## Features

### Theme Style: Classic or Block (FSE)

Every generator run starts with a choice:

- **Classic** -- a traditional template-based WordPress theme with header.php, footer.php, the full set of template files, the Customiser, and optional Header and Footer Builder. Works on WordPress 6.0 and up.
- **Block (FSE)** -- a Full Site Editing theme with theme.json, 6 HTML templates, 2 template parts, 10 block patterns, and 3 style variations (Dark, Sepia, High Contrast). Edited entirely through Appearance > Editor. Requires WordPress 6.4 or later.

Switching between styles automatically hides settings that do not apply, so the interface stays relevant to what you're building.

### Theme Types

Choose from Minimal Blog, Business, Portfolio, or WooCommerce as your starting point. Each produces an appropriate set of template files and configuration.

For block themes, each type comes with its own design-token system:

- **Minimal** -- Georgia headings, system sans-serif body, no web fonts (zero network calls)
- **Business** -- Inter across the board, navy primary, orange accent
- **Portfolio** -- Playfair Display headings, system sans-serif body, dark primary, pink accent

Google Fonts required by Business and Portfolio are bundled **locally** at generation time. The finished theme makes no runtime requests to fonts.googleapis.com, which means GDPR-clean output with no consent-banner implications. If Google Fonts is unreachable when you generate, the theme gracefully falls back to its system-font stack with no broken references.

### Live Theme-Aware Preview

The generator shows a live preview of the theme's screenshot as you configure it. Palette, typography, and content-type-specific copy all flow through from your actual settings. The same SVG that renders in the browser is rasterised to the 1200x900 screenshot.png that ships inside the theme zip, so what you see is what WordPress displays.

### Custom Screenshot Upload

Prefer to ship your own screenshot? Click the preview area, upload a PNG or JPG (up to 2 MB, 1200x900 recommended). The upload replaces the auto-generated preview entirely and is preserved in the zip as screenshot.png or screenshot.jpg, bytes-for-bytes. Click Remove to revert to the auto-generated preview.

### Save and Load Configurations

Two small buttons above Generate let you save the entire generator state as JSON and reload it later:

- **Save Config** -- downloads a `{slug}-config.json` file capturing every setting (basics, theme style, type, all toggles, steppers, licence)
- **Load Config** -- reads a previously saved JSON and restores the state, including side effects like FSE section hiding and preview updates

The format is versioned, so future generator versions will recognise and reject incompatible configs rather than silently loading them wrong. Useful for iterating across sessions, sharing configs with clients, and building a library of starter presets.

### Structure Options (Classic)

Configurable navigation menus (up to 10), footer widget areas (up to 10), optional sidebar, and the choice to split header and footer into their own template parts.

### Developer Features

All optional, all toggleable:

- Custom Post Type boilerplate with proper capability mapping and security
- Custom Taxonomy boilerplate with sanitisation
- Theme Customizer with colour, typography, and layout controls (Classic only)
- Block Editor support with theme.json, block styles, and editor stylesheet (Classic only -- block themes include this by design)
- Starter Block Patterns for common layouts
- Breadcrumb navigation with Schema.org markup
- Numbered pagination for archives
- Post thumbnails with custom size definitions
- Header / Footer Builder (Classic only)
- Enhanced Security Headers toggle (new in 1.6.2)
- Disable XML-RPC toggle (new in 1.6.2)

### Page Builder Compatibility (Classic only)

Toggle support for any combination of:

- **Gutenberg (Block Editor)** -- Full-width and wide block alignment support. Adds .alignwide, .alignfull, .alignleft, .alignright CSS with negative-margin breakout from the content container. Editor canvas width matching so the backend reflects the frontend. Custom block style variations. Body class on pages using blocks.

- **Elementor** -- Theme Builder location registration for header, footer, single, and archive templates. Full-width and canvas page templates. Elementor 4.x atomic elements compatibility (e-heading, e-paragraph, e-button, e-image, e-divider, e-svg, e-youtube, e-self-hosted-video, e-flexbox, e-div-block, e-tabs). Body class on Elementor-built pages. Style dequeue on canvas templates. Content width adjustment for full-width templates. Zero CSS overrides -- the theme stays out of Elementor's way entirely.

- **Bricks Builder** -- Theme support declaration. Template rendering hooks so Bricks takes over when it has a template assigned. Body class and style dequeue on Bricks-rendered pages. Full-width and canvas page templates.

- **Oxygen Builder** -- Full-takeover template support. Detects Oxygen-controlled pages and dequeues both theme stylesheets. The template includes a hook to Oxygen's main template.

- **Beaver Builder** -- Theme support for Beaver Themer headers, footers, and parts. Header and footer override detection is integrated into the theme's template files. Content width adjustment when the builder is active. Full-width and canvas page templates.

- **WPBakery (Visual Composer)** -- Body class on WPBakery-built pages. Content width adjustment for stretched rows. Default editor post types configuration. Editor style registration. Full-width and canvas page templates.

When any page builder is enabled, the generated theme's `.site-content` container automatically removes its max-width and padding constraints on builder-controlled pages. Each builder's integration file is conditionally loaded only when its plugin is active.

Block themes skip this section entirely -- they use the WordPress Site Editor instead of third-party builders.

### Block Theme Specifics

For FSE themes the generator outputs:

- **theme.json v3** with a full design-token system: 7-colour palette, 2 gradients, 3 font families, 5 fluid font sizes, 7-step spacing scale, layout widths, element styles, and block styles
- **6 HTML templates**: index, single, page, archive, search, 404
- **2 template parts**: header (with skip-to-content link), footer
- **10 block patterns**: hero, features grid, CTA banner, testimonial, pricing tiers, team grid, logo cloud, newsletter, two-column feature, post list
- **3 style variations**: Dark, Sepia, High Contrast (switchable from the Styles sidebar in the Site Editor)

### Accessibility

- WCAG 2.1 AA skip-to-content link included in every generated theme (block themes get it in parts/header.html, classic themes in header.php)
- Screen-reader-text utility class with proper focus styling
- Accessible mobile navigation with keyboard close (Escape key)
- Semantic HTML5 markup throughout

### WordPress.org Submission Readiness

Every generated theme ships with the files needed for directory submission:

- **LICENSE** -- canonical text of the licence you selected (GPL v2, GPL v3, or MIT), with author and copyright year filled in
- **readme.txt** -- WordPress.org format with proper headers (Contributors, Stable tag, License URI, Tags), Description, Installation, FAQ, Changelog, and Copyright sections
- **rtl.css** -- RTL stylesheet stub with direction rules, table alignment, and float swaps
- **languages/{slug}.pot** -- empty gettext template with correct Project-Id-Version, POT-Creation-Date, and X-Domain headers, ready for `wp i18n make-pot` or Poedit

### Security (Always On)

Every generated theme includes, with no way to disable:

- Output escaping on every echo (esc_html, esc_attr, esc_url, wp_kses)
- Nonce verification on all forms
- Input sanitisation throughout
- Prepared SQL statements
- ABSPATH checks on every PHP file
- Enqueued assets only (no hardcoded script or style tags)
- No eval() or extract()
- CSRF protection
- Baseline security headers (X-Content-Type-Options, X-Frame-Options, Referrer-Policy)
- WordPress version removed from head and feeds
- Theme Check compliant

Configurable security (defaults to on):

- Enhanced security headers (Permissions-Policy, upgrade-insecure-requests)
- XML-RPC disabled

Generator-side protections (the tool itself):

- All user-entered values are sanitised before being written into the theme's PHP strings, HTML attributes, and CSS values, so a malformed input cannot break out of quotes or inject code
- JSZip is loaded with Subresource Integrity (SRI) hashes, so if the CDN is compromised your browser refuses to execute a tampered script
- Warnings when theme slug is empty or starts with a digit (both cause PHP activation errors)

### Other Bits

- Generates a theme-aware screenshot.png that reflects the actual palette and typography
- Produces a README.md inside the theme
- Creates a languages folder with .pot template
- Mobile-responsive navigation with accessible toggle
- Skip-to-content link and screen-reader-text styles
- CSS custom properties for easy colour theming
- Clean, semantic HTML5 markup throughout

## How to Use

1. Open `mbr-theme-generator.html` in any modern browser
2. Fill in your theme details (name, slug, author, version, etc.)
3. Choose Classic or Block (FSE) style
4. Pick a theme type
5. Toggle the structure options, features, and page builder compatibility you need
6. Optionally upload a custom screenshot
7. Click Generate and Download Theme
8. Unzip into your WordPress `wp-content/themes/` directory
9. Activate and start building

That is it. No build step, no npm install, no dependencies beyond JSZip (bundled via CDN with SRI).

## Try it Online

The generator is live at [littlewebshack.com](https://littlewebshack.com).

## Requirements

- Any modern browser (Chrome, Firefox, Safari, Edge)
- WordPress 6.0 or later for classic themes (6.4 or later for block themes)
- PHP 7.4 or later (for generated themes)

## Philosophy

This tool exists because starter themes should not require a learning curve of their own. The generated output is deliberately simple PHP and CSS that any WordPress developer can read, understand, and modify. There is no abstraction layer, no framework dependency, and no build process in the generated theme.

The page builder compatibility follows one principle: stay out of the builder's way. The theme provides clean markup, removes its own layout constraints on builder-controlled pages, and lets each builder's CSS do its job. This applies equally to Elementor's atomic elements, Bricks' template system, Oxygen's full-page takeover, Beaver Builder's Themer locations, and WPBakery's stretched rows.

Block themes follow the same principle with WordPress itself -- every design decision lives in theme.json so the user can override it from the Site Editor without editing a single file.

## Changelog

### 1.6.2

- **Block themes (Full Site Editing)** -- Full new output path producing theme.json v3, 6 HTML templates, 2 template parts, 10 block patterns, and 3 style variations (Dark, Sepia, High Contrast)
- **Google Fonts bundled locally** at generation time for block themes, with graceful offline fallback. No runtime calls to fonts.googleapis.com, GDPR-clean by default
- **Live theme-aware preview** -- SVG preview in the generator that reflects the actual palette, typography, and content type, updating as you configure. The same SVG becomes the theme's screenshot.png
- **Custom screenshot upload** with PNG/JPG validation, 2 MB limit, and graceful fallback to the auto-preview on remove
- **Save and load configurations as JSON** with versioned format (`_format: 'mbr-theme-config'`) for forward compatibility
- **WordPress.org submission bundle** -- LICENSE, readme.txt, rtl.css, and languages/{slug}.pot shipped in every generated theme (classic and block)
- **WCAG 2.1 AA skip-to-content link** in every generated theme
- **Enhanced Security Headers toggle** -- Permissions-Policy, upgrade-insecure-requests (default on)
- **Disable XML-RPC toggle** -- previously unconditional, now configurable (default on)
- **Subresource Integrity** on JSZip library load in the generator itself
- **Generator-side input sanitisation** prevents malformed input from injecting into generated PHP/HTML/CSS
- **Slug validation warnings** for empty or digit-prefixed slugs (both cause PHP activation errors)

### 1.4.2

- Added Gutenberg (Block Editor) page builder compatibility with full-width/wide alignment CSS, editor canvas matching, and custom block style variations
- Added Bricks Builder integration with template rendering hooks and style dequeue
- Added Oxygen Builder integration with full-takeover template support
- Added Beaver Builder integration with Themer header/footer support
- Added WPBakery (Visual Composer) integration with stretched row support
- Combined page builder CSS overrides into a single efficient selector block
- Page templates (full-width and canvas) now shared across all enabled builders
- Header and footer templates support simultaneous Elementor and Beaver Themer location checks

### 1.3.9

- Added Elementor 4.0.1 atomic elements compatibility
- Added Page Builder Compatibility section (Section 5) to the generator UI
- Elementor integration: Theme Builder locations, body class, canvas dequeue, content width adjustment
- Full-width and canvas page templates
- Layout constraint removal on Elementor-built pages via body class scoping

### 1.3.8

- Initial public release
- Security-first theme scaffolding with 10/10 security rating
- Four theme types: Minimal Blog, Business, Portfolio, WooCommerce
- Configurable structure, features, and developer tooling
- Client-side generation with no server dependency

## Licence

GPL v2 or later. Generated themes inherit the licence you select in the configuration panel (GPL v2, GPL v3, or MIT).

## Credits

Built by [Robert Palmer](https://littlewebshack.com). Part of the MBR plugin suite, distributed independently via [littlewebshack.com](https://littlewebshack.com) and [GitHub](https://github.com/harbourbob).

If you find this useful, you can [buy me a coffee](https://buymeacoffee.com/robertpalmer).
