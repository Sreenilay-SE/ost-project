# PRD — Open Source Tech Community Website
# Remaining Tasks (production-ready completion)
# Format: - [Task name]: [What to build] that [clear success condition]

---

- [Dead Code Removal]: Remove ui.js from the project and delete its orphaned `#back-btn` create/event-bus logic that duplicates scene.js functionality, such that `index.html` has no reference to ui.js, only one `#back-btn` is created (in scene.js), and zero `ost:flyto` / `ost:home` / `window.OST3D` references remain anywhere in the codebase

- [Discord Link Fix]: Replace the placeholder `https://discord.gg` href on the Discord connect-btn in `index.html` with the real Discord invite URL, and update the `.connect-btn.telegram` CSS class in `style.css` to `.connect-btn.instagram` with the correct Instagram brand color (`#E4405F`), such that both the Discord and Instagram buttons display on-brand indicator dots and all four connect buttons link to real destinations

- [WebGL Fallback]: Add a `<noscript>` block and a WebGL capability check in `scene.js` that fires before the renderer is created, such that if `WebGLRenderingContext` is unavailable the canvas is hidden and a full-viewport fallback `<div id="no-webgl">` is shown with the community name, tagline, and WhatsApp join link styled consistently with the existing design system variables in `style.css`

- [Reduced Motion Support]: Add a `@media (prefers-reduced-motion: reduce)` block to `style.css` that disables all `@keyframes` animations (loader-spin, float-dot, transitions), and add a matching guard in `scene.js` that sets all per-frame rotation/floating increments to zero when `window.matchMedia('(prefers-reduced-motion: reduce)').matches` is true, such that the page is fully usable with zero motion on accessibility-mode devices

- [Touch & Mobile 3D Interaction]: Add a `touchend` event listener on the canvas in `scene.js` that performs the same raycaster hit-test as the existing `click` handler using `e.changedTouches[0]` coordinates, such that tapping any of the four orbital nodes on a mobile/tablet touchscreen correctly triggers `flyToNode()` and reveals the corresponding info panel

- [SEO Meta Tags]: Add `<meta property="og:image">`, `<meta property="og:url">`, `<meta property="og:type">`, `<meta name="twitter:card">`, `<meta name="twitter:title">`, and `<meta name="twitter:description">` tags to the `<head>` in `index.html` with real values matching the community branding, such that pasting the site URL into WhatsApp, Twitter, or Slack generates a rich link preview with image, title, and description

- [Web App Manifest]: Create a `manifest.json` file in the project root with `name`, `short_name`, `theme_color: "#C9A96E"`, `background_color: "#F0F2F5"`, `display: "standalone"`, and an `icons` array referencing `opensource tech logo.jpeg` at 192×192 and 512×512, and add `<link rel="manifest" href="manifest.json">` and `<meta name="theme-color" content="#C9A96E">` to `index.html`, such that the site passes Chrome's "Add to Home Screen" installability check

- [Robots & Sitemap]: Create `robots.txt` in the project root that allows all crawlers and references `sitemap.xml`, and create `sitemap.xml` with a single `<url>` entry for the canonical homepage, such that Google Search Console can be verified and both files return valid content when fetched directly from the browser

- [Resources Panel — Real Links]: Replace the four static `.r-card` divs in `index.html` (Learning Guides, Session Recordings, Study Materials, Peer Q&A) with `<a>` anchor tags that each have a real `href` (WhatsApp community link as fallback, or actual resource URLs), a hover state in `style.css` that shows a gold right-arrow (`→`) icon, and a `target="_blank" rel="noopener"` attribute, such that clicking any resource card navigates the user to actual content rather than doing nothing

- [Activities Panel — CTA Button]: Add a primary CTA button inside `panel-activities` in `index.html` below the four-pillar list that links to the WhatsApp community (`https://chat.whatsapp.com/BqyJTWr9iXh6Z7IisCwiUT`) and uses the existing `.btn-primary` class from `style.css`, such that the Activities panel has a clear next action and the button is visible and clickable when the panel is in `.visible` state

- [About Panel — Member Count Stat]: Add a stat row inside `panel-about` in `index.html` below the pills section showing at minimum one real metric (e.g. member count, cities, or projects) formatted as a large number + label using a new `.panel-stat` CSS class in `style.css`, such that the About panel communicates social proof with at least one concrete figure displayed in the accent-gold color

- [Members / Core Team Section]: Add a fifth info panel `panel-team` in `index.html` and a corresponding fifth orbital node in the `nodeData` array in `scene.js` (or integrate into the About panel as a scrollable sub-section) that shows 3–6 core team member cards with name, role, and optional avatar or initials using a new `.team-grid` CSS class in `style.css`, such that when the About or Team node is clicked, real human faces/names are shown representing the community leadership

- [Upcoming Events Section]: Add a static but realistic events list inside `panel-activities` in `index.html` or as a new `panel-events` panel, containing at minimum two upcoming workshop/event entries each with a date, title, and short description, styled with a new `.event-item` CSS class in `style.css` that uses a left gold border-accent, such that the Activities section communicates an active community schedule and is not purely descriptive text

- [Footer HTML Section]: Add a `<footer id="site-footer">` element to `index.html` positioned at `z-index: 10` below the canvas using `position: fixed; bottom: 0` with a minimal one-line layout containing copyright text (`© 2025 Open Source Tech`), a privacy/contact email link, and redundant social icon links, styled with new `.site-footer` rules in `style.css` using `var(--surface)` background and `var(--border)` top border, such that the footer is always visible on desktop without overlapping the back button, and hides on mobile below 480px

- [404 Fallback Page]: Create a `404.html` file in the project root that imports the same `style.css` and matches the visual design system (same fonts, same background color `var(--bg) = #F0F2F5`, same `.btn-primary` button) and contains an h1 "Page Not Found", a short message, and a "Return Home" button linking to `index.html`, such that navigating to any non-existent route on the deployed site shows a branded error page instead of the host's default 404

- [Hero Mobile Layout Fix]: Update the `@media (max-width: 768px)` block in `style.css` so that `#hero-hud` has `top: 100px` (below the 68px nav) instead of `top: 50%` on small screens, reduces `.hero-title` font-size to `clamp(38px, 9vw, 52px)`, and wraps `.hero-actions` in `flex-direction: column` with `align-items: flex-start`, such that on a 375px-wide mobile screen the hero headline, subtitle, and both action buttons are fully visible without being clipped by the 3D canvas or overflowing the viewport

- [Panel Scroll on Small Screens]: Update `.info-panel` in `style.css` to add `overflow-y: auto; max-height: calc(100vh - 160px)` inside the `@media (max-width: 768px)` block, and add `overscroll-behavior: contain` and `-webkit-overflow-scrolling: touch` to `.panel-glass`, such that on a 375px mobile screen the Activities and Resources panels (which have the most content) are fully scrollable without the page itself scrolling or the panel being cut off

- [Keyboard Focus Styles]: Add a `:focus-visible` CSS rule in `style.css` for `a, button, .node-label` that shows a `2px solid var(--accent-gold)` outline with `outline-offset: 3px` and `border-radius: 4px`, and remove any existing `outline: none` overrides, such that keyboard-only navigation (Tab key) shows a clearly visible gold focus ring on all interactive elements, passing WCAG 2.1 AA focus-visibility requirements

- [ARIA Landmark Roles]: Add `role="banner"` to `<nav id="nav">`, `role="main"` to `<div id="hero-hud">`, `role="complementary"` to each `.info-panel`, and `aria-live="polite"` with `aria-atomic="true"` to a new `<div id="panel-announcer" class="sr-only">` element in `index.html` that scene.js updates with the active panel name on `flyToNode()`, such that screen reader users receive an audible announcement when a panel opens or closes
