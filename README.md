# MBR Theme Generator

**A browser-based WordPress theme scaffolding tool that produces secure, production-ready themes in seconds.**

Version 1.6.2 | Built by [Robert Palmer](https://littlewebshack.com) | Free, no upsells, no premium tier

---

## What is it?

MBR Theme Generator is a single HTML file that runs entirely in your browser. You configure the options you need, hit Generate, and download a fully structured WordPress theme as a zip file. No server required, no account needed, no data collected.

Every theme it produces scores 10/10 on security. Output escaping on every echo, nonce verification on every form, input sanitisation throughout, prepared SQL statements, ABSPATH checks on all files, enqueued assets only, no eval() or extract() anywhere. This is not optional -- it is baked into every file the generator outputs.

The generated themes are Theme Check compliant out of the box.

## Who is it for?

Developers, freelancers, and agencies who want a clean starting point for client projects without inheriting someone else's opinions about layout or design. If you have ever grabbed a starter theme and spent the first hour ripping out things you did not need, this tool is for you.

## Features

### Theme Types

Choose from Minimal Blog, Business, Portfolio, or WooCommerce as your starting point. Each produces an appropriate set of template files and configuration.

### Structure Options

Configurable navigation menus (up to 10), footer widget areas (up to 10), optional sidebar, and the choice to split header and footer into their own template parts.

### Developer Features

All optional, all toggleable:

- Custom Post Type boilerplate with proper capability mapping and security
- Custom Taxonomy boilerplate with sanitisation
- Theme Customizer with colour, typography, and layout controls
- Block Editor support with theme.json, block styles, and editor stylesheet
- Starter Block Patterns for common layouts
- Breadcrumb navigation with Schema.org markup
- Numbered pagination for archives
- Post thumbnails with custom size definitions
- Header / Footer Builder

### Page Builder Compatibility

Toggle support for any combination of:

- **Gutenberg (Block Editor)** -- Full-width and wide block alignment support. Adds .alignwide, .alignfull, .alignleft, .alignright CSS with negative-margin breakout from the content container. Editor canvas width matching so the backend reflects the frontend. Custom block style variations. Body class on pages using blocks.

- **Elementor** -- Theme Builder location registration for header, footer, single, and archive templates. Full-width and canvas page templates. Elementor 4.x atomic elements compatibility (e-heading, e-paragraph, e-button, e-image, e-divider, e-svg, e-youtube, e-self-hosted-video, e-flexbox, e-div-block, e-tabs). Body class on Elementor-built pages. Style dequeue on canvas templates. Content width adjustment for full-width templates. Zero CSS overrides -- the theme stays out of Elementor's way entirely.

- **Bricks Builder** -- Theme support declaration. Template rendering hooks so Bricks takes over when it has a template assigned. Body class and style dequeue on Bricks-rendered pages. Full-width and canvas page templates.

- **Oxygen Builder** -- Full-takeover template support. Detects Oxygen-controlled pages and dequeues both theme stylesheets. The template includes a hook to Oxygen's main template.

- **Beaver Builder** -- Theme support for Beaver Themer headers, footers, and parts. Header and footer override detection is integrated into the theme's template files. Content width adjustment when the builder is active. Full-width and canvas page templates.

- **WPBakery (Visual Composer)** -- Body class on WPBakery-built pages. Content width adjustment for stretched rows. Default editor post types configuration. Editor style registration. Full-width and canvas page templates.

When any page builder is enabled, the generated theme's `.site-content` container automatically removes its max-width and padding constraints on builder-controlled pages. Each builder's integration file is conditionally loaded only when its plugin is active.

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
- Security headers (X-Content-Type-Options, X-Frame-Options, Referrer-Policy)
- XML-RPC disabled by default
- WordPress version removed from head and feeds
- Theme Check compliant

### Other Bits

- Generates a branded screenshot.png with theme name, type badge, version, and Security 10/10 indicator
- Produces a README.md inside the theme
- Creates a languages folder ready for translation
- Mobile-responsive navigation with accessible toggle
- Skip-to-content link and screen-reader-text styles
- CSS custom properties for easy colour theming
- Clean, semantic HTML5 markup throughout

## How to Use

1. Open `mbr-theme-generator.html` in any modern browser
2. Fill in your theme details (name, slug, author, version, etc.)
3. Pick a theme type
4. Toggle the structure options, features, and page builder compatibility you need
5. Click Generate and Download Theme
6. Unzip into your WordPress `wp-content/themes/` directory
7. Activate and start building

That is it. No build step, no npm install, no dependencies beyond JSZip (bundled via CDN).

## Try it Online

The generator is live at [littlewebshack.com](https://littlewebshack.com).

## Requirements

- Any modern browser (Chrome, Firefox, Safari, Edge)
- WordPress 6.0 or later (for generated themes)
- PHP 7.4 or later (for generated themes)

## Philosophy

This tool exists because starter themes should not require a learning curve of their own. The generated output is deliberately simple PHP and CSS that any WordPress developer can read, understand, and modify. There is no abstraction layer, no framework dependency, and no build process in the generated theme.

The page builder compatibility follows one principle: stay out of the builder's way. The theme provides clean markup, removes its own layout constraints on builder-controlled pages, and lets each builder's CSS do its job. This applies equally to Elementor's atomic elements, Bricks' template system, Oxygen's full-page takeover, Beaver Builder's Themer locations, and WPBakery's stretched rows.

## Changelog

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

GPL v2 or later. Generated themes inherit the licence you select in the configuration panel.

## Credits

Built by [Robert Palmer](https://littlewebshack.com). Part of the MBR plugin suite, distributed independently via [littlewebshack.com](https://littlewebshack.com) and [GitHub](https://github.com/harbourbob).

If you find this useful, you can [buy me a coffee](https://buymeacoffee.com/robertpalmer).
