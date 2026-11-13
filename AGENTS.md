# AGENTS.md

Static Colorlib "Pointer" template. No package manager, build, test, lint, CI, or git repo. `index.html` is the one-page landing; `single.html` is the blog-post page.

## Preview
- Open `index.html` directly, or serve the root: `python -m http.server 8000` then http://localhost:8000.
- All asset URLs are relative; keep new files under the existing top-level dirs (`css`, `js`, `images`, `fonts`, `scss`).

## Styling
- `css/style.css` is the compiled output of `scss/style.scss`, which imports `bootstrap/*` plus `_site-base.scss`, `_site-navbar.scss`, `_site-blocks.scss`.
- There is no build script. Either edit `css/style.css` directly or edit SCSS and recompile it into `css/style.css` (e.g. with a Sass compiler). Do not introduce npm just to build unless asked.
- Bootstrap 4 is vendored in both `css/` and `scss/bootstrap/`; do not rewrite or upgrade it.

## JavaScript
- `js/main.js` depends on the script order at the bottom of both pages: jQuery 3.3.1 -> jQuery UI/popper/bootstrap -> owl/stellar/countdown/easing/aos/fancybox/sticky -> `main.js`. Add new libraries before `main.js` in BOTH pages.
- Behaviors bind to classes/IDs such as `.js-sticky-header`, `.js-menu-toggle`, `.main-menu`, `.slide-one-item`, `.nonloop-block-13`, `#date-countdown`, `.datepicker`. Renaming these silently breaks JS.
- Countdown target is hardcoded to `2020/10/10` (already past) in `main.js`.
- Vendored but unlinked libraries: `slick`, `typed`, `magnific-popup`, `mediaelement`.

## Shared markup
- Header, nav, and footer are duplicated in `index.html` and `single.html`; apply site-wide changes to both.
- Section anchors exist only in `index.html` (`#home-section`, `#about-section`, `#team-section`, `#services-section`, `#testimonials-section`, `#blog-section`, `#contact-section`).
- Icons use icomoon `icon-*` classes (`fonts/icomoon/style.css`); flaticon CSS is also loaded. Keep both when editing.
- The `index.html` hero background is the large animated `images/rainbow.gif`, set via inline style rather than CSS.
