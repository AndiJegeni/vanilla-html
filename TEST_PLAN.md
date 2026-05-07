# Test Plan — AndiJegeni/vanilla-html (Kilo Studio Site)

**Version:** 1.0  
**Date:** 2026-07-11  
**Tester:** QA Agent  
**Scope:** Static front-end site — `vanilla-html` (Kilo design-studio marketing site, 4 pages)

---

## 1. Scope & Objectives

### In Scope
- HTML structure and semantic correctness across all 4 pages (index, work, about, contact)
- CSS validity, layout integrity, and responsive behaviour
- JavaScript functionality (clock widget)
- Accessibility (ARIA, alt text, keyboard navigation, colour contrast)
- Navigation link correctness and cross-page consistency
- Performance indicators (external resource loading, unused code)

### Out of Scope
- Backend / API endpoints (none — static site)
- Browser automation / visual regression screenshots
- SEO ranking or Core Web Vitals measured in a real browser

### Objectives
1. Identify structural or semantic HTML issues.
2. Verify CSS custom properties and responsive breakpoints.
3. Verify the clock widget initialises correctly.
4. Surface accessibility defects.
5. Identify placeholder or stub content.
6. Produce a prioritised issue list.

---

## 2. Test Environment

| Item | Detail |
|------|--------|
| Repo under test | `AndiJegeni/vanilla-html` |
| Branch | `main` |
| Pages | index.html, work.html, about.html, contact.html |
| Build tool | Vite (dev only — no build step in package.json) |
| Analysis method | Static code review |
| Date of snapshot | 2026-07-11 |

---

## 3. Test Cases

### Group A — HTML Structure

| ID | Description |
|----|-------------|
| A-01 | DOCTYPE and lang attribute present on all pages |
| A-02 | Meta charset and viewport declared on all pages |
| A-03 | OG / Twitter meta tags present on index.html |
| A-04 | Nav links resolve to correct pages |
| A-05 | Active nav state (`class="active"`) correct per page |
| A-06 | No duplicate `id` attributes on same page |
| A-07 | Footer copyright year is current (shown as 2019–2026) |
| A-08 | All external links use `rel="noopener noreferrer"` |
| A-09 | `og:image` and `twitter:image` reference `/og-image.png` — file must exist |

### Group B — CSS

| ID | Description |
|----|-------------|
| B-01 | All CSS custom properties defined in `:root` |
| B-02 | Responsive breakpoints cover 980 px and 640 px |
| B-03 | Marquee animation runs without jank (infinite loop) |
| B-04 | `.header-cta` hides gracefully on mobile |
| B-05 | Colour contrast meets WCAG AA |
| B-06 | Google Fonts import does not block first paint |

### Group C — JavaScript

| ID | Description |
|----|-------------|
| C-01 | `tick()` runs immediately on DOMContentLoaded |
| C-02 | `setInterval(tick, 30000)` updates clock every 30 s |
| C-03 | Clock falls back gracefully if `Intl` is unavailable |

### Group D — Accessibility

| ID | Description |
|----|-------------|
| D-01 | `<nav>` has `aria-label` or is uniquely identifiable |
| D-02 | Headings follow correct hierarchy |
| D-03 | Interactive elements focusable via keyboard |
| D-04 | Marquee not announced repeatedly by screen readers (aria-hidden or role=presentation) |
| D-05 | Footer links are descriptive (not bare "↗") |

### Group E — Content Quality

| ID | Description |
|----|-------------|
| E-01 | Placeholder social links (`href="#"`) replaced before production |
| E-02 | `og:image` asset (`/og-image.png`) exists in repository |
| E-03 | Work rows link to real case-study pages, not generic `work.html` |
| E-04 | Contact email `hello@kilo.studio` is operational |

---

## 4. Pass / Fail Criteria

- **Pass:** The code meets the stated requirement with no observable defect.
- **Fail:** A defect exists that would cause incorrect rendering, broken functionality, accessibility barrier, or misleading content.
- **Warning:** The code works but represents a quality or maintainability risk.
