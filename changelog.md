Part 2: Responsive Design
- Implemented mobile-first with relative units (rem/em for fonts, % for widths).
- Added media queries: 768px (tablet: 2-cols, larger fonts), 1024px (desktop: 3-cols, multi-column resources).
- Used srcset/sizes for responsive images (e.g., hero scales from 600px to 1200px).
- Tested via DevTools (emulated iPhone/iPad/Desktop); iterated on nav wrapping for mobile.



 Initial Setup - Part 1: HTML Structure
-  Fixed `<nav>` (unordered list with 7 links: Home, About Us, Adopt, Foster, Resources, Contact, Donate), `<main>` (hero/section/article for content), and `<footer>` . Used `<header>` for logo and `<section>` for modular content

- Populated Tail to Heart-themed content: index.html (hero with Unsplash image, mission blurb, 3 featured pets); aboutUs.html (history paragraph, 4 team member articles with placeholders, partners list); adopt.html (intro, 6 pet profiles with breed/age/story/images, application form); foster.html (benefits list, pet needs section, foster form); resources.html (guides/FAQs/programs in ordered/unordered lists); contact.html (address/hours, contact form); donation.html (impact stats, options table, donation form).

- Implemented accessibility and linking: `alt` attributes on all ~20 images (e.g., "Heartwarming image of a rescued dog"); `required` on form fields (name/email/message); internal anchors (e.g., `<a href="adopt.html" class="nav-link">Adopt</a>`); `lang="en"` on `<html>`; viewport meta for mobile.

- Added placeholders: Unsplash URLs (e.g., `https://source.unsplash.com/400x300/?golden-retriever`) for images; basic forms (inputs/selects/textarea with labels).

- Git: Initialized repo (`git init`), added files (`git add .`), first commit (`git commit -m "Initial commit: Created 7 semantic HTML pages with Tail to Heart content, navigation, forms, and accessibility features"`), 

- Testing: Opened pages in Chrome—verified linking (no 404s), semantic validation via W3C HTML Validator (0 errors), basic mobile view (stacked content via browser resize). No CSS yet—raw HTML renders cleanly across pages.

 Part 2: CSS Implementation - Base Styles, Typography, Layouts, and Visuals 
- Developed external `style.css` (~200 lines initial) and linked via `<link rel="stylesheet" href="style.css">` in each HTML `<head>`, demonstrating external cascading (global rules apply site-wide, overridden by classes).

- Applied CSS reset (`* { margin: 0; padding: 0; box-sizing: border-box; }`) to normalize browsers (e.g., removes default ul margins, ensures consistent padding on mobile).

- Set base typography and colors: `html { font-size: 16px; scroll-behavior: smooth; }`; `body { font-family: 'Open Sans', sans-serif; font-size: 1rem; line-height: 1.6; color: #8B4513; background: #F5F5DC; overflow-x: hidden; }` (beige theme for warmth); Poppins imports via Google Fonts link; heading scales (h1: 2.5rem/700 weight #8FBC8F, h2: 2rem/600, h3: 1.5rem/500 #8B4513) with rem for zoom scalability; p/ul/ol margins (1rem bottom).

- Implemented layouts: Flexbox for nav (`.nav-container { display: flex; justify-content: space-between; align-items: center; max-width: 1200px; margin: 0 auto; }`—logo left, links right) and cards (`.cards { display: flex; flex-direction: column; gap: 1.5rem; }`—stacks on base/mobile); CSS Grid for pet profiles (`.pet-grid { display: grid; grid-template-columns: 1fr; gap: 1.5rem; }`—single-column base); images responsive (`img { max-width: 100%; height: auto; border-radius: 8px; }`).

- Added visuals and interactivity: Sage nav/footer (`nav { background: #8FBC8F; position: fixed; top: 0; width: 100%; z-index: 1000; box-shadow: 0 2px 5px; min-height: 60px; }`); sky blue hero (`.hero { background: #87CEEB; padding: 4rem 1rem; margin-top: 80px; border-radius: 0 0 20px 20px; }`); coral buttons/links (`.cta-button, a { color: #FF7F50; transition: 0.3s; }`); card styling (`.card { background: white; border: 1px solid #8FBC8F; padding: 1.5rem; box-shadow: 0 2px 4px; transition: box-shadow 0.3s; }`—hovers lift to 0 4px 8px); form inputs (full-width, sage borders, coral focus); pseudo-classes (a:hover { color: #8FBC8F; }, :focus { outline: 2px solid #87CEEB; } for accessibility); main padding (2rem 1rem, max-width 1200px centered).

- Git: Committed (`git add style.css *.html` > `git commit -m "Added external style.css: Reset, typography (rem/Poppins/Open Sans), Flexbox/Grid layouts, visual theme (colors/shadows/hovers), and form styling"` > `git push origin main`—used PAT for auth).
- Testing: Reloaded all pages—consistent sage nav/footer, coral hovers work; cards shadow on mouseover; no horizontal scroll (DevTools Elements tab); cross-browser (Chrome/Edge: identical; Firefox: minor shadow diff). Raw responsive base: Content stacks on 375px resize.

Part 2: Responsive Design Enhancements and Breakpoints (3.1) 
- Adopted mobile-first: Base single-column (e.g., pet-grid 1fr, cards column)—progressive via min-width media queries for tablet/desktop overrides.

- Defined breakpoints (per 3.1): Mobile (<768px: phones like iPhone 375px—compact/single-column); Tablet (768px-1023px: iPad 768px—2-column/medium); Desktop (≥1024px: laptops—3-column/full). Modified layouts (multi→single column switch), fonts (scale +0.5-1rem), nav (gaps/padding adjust), content (padding increases).
- Enhanced media queries (~150 lines): 

   - Mobile (@media max-width: 767px): h1 2rem, body 0.95rem; nav compact (padding 0.5rem, gaps 0.5rem, font 0.9rem, flex-direction: column for stacking on <320px, min-height 50px touch-friendly); main/hero padding 1.5rem 0.75rem, margin-top 70px; forms padding 0.6rem; resources column-count: 1.

  - Tablet (@media min-width: 768px): h1 3rem, body 1.1rem; pet-grid repeat(2,1fr), cards row/wrap gap 2rem; nav one-line (gaps 1.5rem, no wrap, padding 1rem); main/hero 3rem 2rem, margin-top 90px; buttons larger (1rem 2rem).

   - Desktop (@media min-width: 1024px): h1 3.5rem, body 1.125rem; pet-grid repeat(3,1fr), cards auto-fit minmax(300px,1fr) gap 2.5rem; resources column-count: 2 gap 2rem; nav gaps 2rem, padding 0 2rem; main 4rem 3rem.

- Added image optimization: `srcset`/`sizes` to hero img in index.html (srcset="https://source.unsplash.com/600x300/?rescue-dog 1x, https://source.unsplash.com/1200x600/?rescue-dog 2x"; sizes="(max-width: 768px) 100vw, 1200px") for 1x/2x density (smaller loads on mobile); all imgs max-width 100%.

- Nav-specific fit: flex-wrap: wrap on .nav-links/.nav-container; white-space: nowrap on links/logo; flex-shrink: 1 on li; body overflow-x: hidden—no overflow on 375px (links wrap 2-3 lines, logo centers/stacks).

- Git: Committed (`git add style.css index.html` > `git commit -m "Implemented responsive breakpoints (3.1): Mobile-first media queries for column switches (1-2-3), font/nav/content mods; added srcset/sizes to hero; enhanced nav wrapping for tablet/phone fit"` > `git push`).

- Testing: DevTools Device Toggle—iPhone (375px): Nav wraps (3-4 links/line, no scroll), single-column pets stack, hero srcset fetches 600x300; iPad (768px): 2-column grid, nav one-line fits <820px; Desktop (1024px): 3-column auto-fit, multi-column resources. Network tab (Slow 3G): Optimized images; resize/rotate: Smooth (no breaks); zoom 200%: Rem scales text/layout.

 Fixes, Polish, and Final Testing (Date: e.g., 2023-10-15)
- Resolved Git issues: "Access rights" error fixed by generating GitHub PAT (Settings > Developer > Tokens classic, repo scope, 90-day expiration); unset old credentials (`git config --global --unset credential.helper`); verified remote (`git remote -v` shows HTTPS URL); future pushes use username + PAT (stored via `git config --global credential.helper store`).

- Accessibility polish: Added focus styles (`:focus { outline: 2px solid #87CEEB; outline-offset: 2px
