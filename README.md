# Moosey — Design in motion

A floating, interactive portfolio by **Win Min Thaw (Moosey)** presenting the design and development of the Guru International School website and staff dashboard.

[**Explore the live portfolio ↗**](https://win-min-thaw-guru-portfolio.vercel.app/) · [View the school project ↗](https://www.guru-school.org/)

## Project overview

The portfolio takes visitors from a motion-led introduction through the public school website, its main visitor journeys, and the admin tools behind it. Real screenshots and short descriptions explain what each feature does.

This repository contains the standalone portfolio, built with **HTML, CSS and JavaScript**. The featured Guru school website is a separate **React** project. Dashboard panels here are interactive screenshot presentations, not live administrative tools.

## Features and how to use them

| Feature | Visitor experience |
| --- | --- |
| Floating introduction | Layered website screenshots and design chips float gently around the headline. |
| Cursor effects | On supported desktop pointers, a labelled Moosey cursor, soft spotlight and parallax react to movement inside the intro. |
| Automatic scroll themes | The page changes between light and dark as visitors reach different sections. Every page load starts in Auto mode. |
| Manual theme control | The top-right control cycles **Auto → Dark → Light → Auto**. Dark or Light holds that appearance for the current visit. |
| Motion control | The pause button stops CSS animations and disables pointer effects. Resume restores them. |
| Project highlights | Counters introduce the featured school project’s 10 public pages, four admin workspaces and two language options. These describe project features, not visitor analytics. |
| Image tilt | Supported desktop pointers gently tilt the main project image and visitor-experience screenshots. |
| Screenshot viewer | Click a project screenshot to open a larger image with a feature explanation. Close with **×** or **Escape**. Focus returns to the triggering control. |
| Theme comparison | The Light / Dark buttons in the visitor-experience section switch between school homepage screenshots. This is separate from the portfolio’s overall theme control. |
| Dashboard showcase | Select Traffic, Enquiries, News or Gallery to change the screenshot, description and feature list. |
| Keyboard navigation | Dashboard tabs support **Left / Right arrows**, **Home** and **End**. Buttons and links have visible focus styling. |
| Scroll progress | A line at the top of the viewport shows progress through the page. |
| Back to top | A floating arrow appears after scrolling; the footer also includes a return link. |
| Social links | Branded Facebook, Instagram, Discord and GitHub cards and footer icons open the supplied profiles in a new tab. |
| Responsive layout | Screenshots, content and social cards adapt to desktop and mobile layouts. |
| Reduced motion | The site respects the device’s reduced-motion preference and avoids decorative pointer motion and entrance animation. |
| Moosey branding | Header and footer use an aligned `moosey*` wordmark. A compact `m*` icon represents the portfolio in browser tabs. |

## Page sections

1. **Introduction** — Moosey branding, floating previews and a short developer introduction.
2. **Selected project** — Guru’s website, live link, project scope and technical context.
3. **Visitor experience** — Programmes, gallery, contact and appearance previews.
4. **Behind the scenes** — Four selectable staff-dashboard previews.
5. **Process** — How the visitor experience, content tools and implementation connect.
6. **Contact** — Facebook, Instagram, Discord and GitHub profiles.

### Automatic theme sequence

| Section | Appearance in Auto mode |
| --- | --- |
| Introduction | Light |
| Selected project | Light |
| Visitor experience | Dark |
| Dashboard showcase | Dark |
| Process | Light |
| Contact | Dark |

The active section is determined around 40% down the viewport. Scrolling upward reverses the changes. Returning to Auto after a manual selection immediately applies the current section’s appearance.

## Dashboard previews

- **Traffic:** daily, monthly and yearly activity controls, visitor / visit measures and CSV reporting.
- **Enquiries:** searching, filtering and following up with family requests. The screenshot shows an empty inbox.
- **News:** bilingual announcement fields, school news and publishing controls.
- **Gallery:** image uploads, categories, captions, albums and visibility management.

These descriptions refer to capabilities of the featured school project. The portfolio does not connect to the school’s private APIs, sign in to its dashboard or modify its records. Traffic values are historical screenshot captures. Credentials and family messages are not included.

## Technology

- Semantic HTML for content and page structure
- CSS for responsive layout, appearance changes, floating elements and animation
- Browser JavaScript for tabs, dialogs, scroll themes, counters and pointer effects
- Local screenshots, icons and font assets
- Vercel static hosting, with no build step or runtime dependencies

No environment variables, database or backend service is required to run this portfolio.

## Run locally

Clone the repository, then serve it using Python 3:

```sh
git clone https://github.com/moosey-sys/moosey-portfolio.git
cd moosey-portfolio
python3 -m http.server 4174 --bind 127.0.0.1
```

Open **http://127.0.0.1:4174/**. Stop the server with **Ctrl+C**.

Use an HTTP server instead of opening `index.html` directly: the site uses root-relative asset paths such as `/assets/home-light.jpg`.

## Repository structure

```text
moosey-portfolio/
├── index.html           # Content, page sections, icons and social links
├── style.css            # Layout, appearance, breakpoints and motion
├── app.js               # Tabs, image dialogs, scroll and pointer interactions
├── appearance.js        # Initial light appearance before main script loads
├── favicon.ico          # Multi-size Moosey browser icon
├── assets/
│   ├── moosey-icon.png  # 96 × 96 Moosey favicon
│   ├── moosey-touch.png # 180 × 180 home-screen icon
│   ├── crest.png        # School identity within the featured case study
│   ├── display.woff2    # Local display font
│   └── *.jpg            # Public-site and sanitized dashboard screenshots
├── robots.txt           # Crawler discovery
├── sitemap.xml          # Canonical portfolio URL
├── vercel.json          # Static hosting and response headers
├── .vercelignore        # Files excluded from deployment
├── .gitignore           # Local hosting metadata and secrets excluded from Git
└── README.md
```

## Customize the portfolio

| Change | Where to edit |
| --- | --- |
| Name, introduction and section content | `index.html` |
| Facebook, Instagram, Discord or GitHub destination | Contact cards and footer anchors in `index.html` |
| Colors, type sizes, spacing and mobile layout | `style.css` |
| Floating, tilt and entrance effects | `style.css` and pointer handlers in `app.js` |
| Light/dark section sequence | Each section’s `data-scene-theme` attribute in `index.html` |
| Theme activation point | `updateScrollAppearance()` in `app.js` |
| Dashboard tab text and screenshot | The `features` object in `app.js` |
| Screenshot viewer explanation | `data-image`, `data-title` and `data-description` on screenshot buttons |
| Project highlight numbers | `data-count` values and their visible labels in `index.html` |
| Tab / home-screen icon | `favicon.ico`, `assets/moosey-icon.png`, `assets/moosey-touch.png` and icon links in the HTML head |

Keep screenshot captions accurate when replacing images. If you change the deployment domain, update the canonical and social-image URLs in `index.html`, plus `robots.txt` and `sitemap.xml`.

## Deploy to Vercel

### Existing local project

From this directory, using an authenticated Vercel CLI:

```sh
vercel deploy --prod
```

Local `.vercel/` project metadata is excluded from Git. A fresh clone needs to be linked to the intended Vercel project before deploying updates to it.

### Import from GitHub

1. In Vercel, import `moosey-sys/moosey-portfolio` or connect it to the existing portfolio project.
2. Use **Other** for the framework preset.
3. Use the repository root as the root directory.
4. Keep the build command disabled and output directory set to `.` as configured in `vercel.json`.
5. Deploy and check the returned production URL.

A GitHub push updates the repository. Automatic production deployment on future pushes requires the Vercel Git integration to be connected; this README does not imply that connection has been configured.

## Hosting settings

`vercel.json` declares static hosting and sends:

- A Content Security Policy restricting page resources to this origin
- `X-Content-Type-Options: nosniff`
- `X-Frame-Options: DENY`
- `Referrer-Policy: strict-origin-when-cross-origin`

Social links navigate to their destinations; the page does not embed third-party social widgets.

## Validation

JavaScript syntax checks:

```sh
node --check app.js
node --check appearance.js
```

Browser checks performed during development included desktop and narrow-mobile layouts, automatic theme changes, manual theme controls, pointer effects, motion pause, tab selection, screenshot dialogs and social-link destinations. This is a static presentation site; there is no application test runner configured in this repository.

## Recent updates

- Added automatic light/dark transitions driven by page sections, with Auto mode on each visit.
- Added scroll progress, project counters, screenshot tilt and a floating back-to-top link.
- Added Facebook, Instagram, Discord and GitHub cards with matching footer icons.
- Replaced the school crest as the portfolio favicon with a compact Moosey mark.
- Adjusted the Moosey header and footer wordmark sizing and star alignment.

## Credits

Portfolio design and development: **Win Min Thaw (Moosey)**. School identity and school photographs belong to their respective owners. The Guru International School project is presented as a featured case study.

## Mobile layout parity update

The responsive header provides all desktop navigation links through a keyboard-accessible mobile/tablet menu. Both floating intro previews are positioned inside the mobile screen, and decorative labels remain available. Mobile admin tabs use a two-column layout with larger touch targets; screenshots retain their full proportions and open in the same detail dialog. Social icons, theme controls and motion controls remain accessible. Pointer-specific hover and cursor effects apply to desktop pointers; touch users can open the same screenshots and use the same feature controls.

Browser checks for this update covered 320px and 390px phone layouts, a 768px tablet layout, desktop navigation, menu open/close, tab selection, image dialogs and horizontal overflow.
