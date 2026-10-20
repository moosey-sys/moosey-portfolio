# Moosey — Design in motion

Portfolio website by **Win Min Thaw (Moosey)**, showcasing the Guru International School website and staff dashboard.

**Live portfolio:** https://win-min-thaw-guru-portfolio.vercel.app/

## Features

- Floating intro screenshots, labelled cursor, spotlight and pointer parallax
- Automatic light/dark appearance changes while scrolling
- Manual Auto → Dark → Light appearance control
- Four interactive admin showcase tabs: traffic, enquiries, news and gallery
- Light/dark screenshot comparison and enlarged image previews
- Scroll progress, animated project counts and floating back-to-top link
- Subtle image tilt and content entrance effects
- Facebook, Instagram, Discord and GitHub links with matching icons
- Responsive layouts, keyboard controls, motion pause and reduced-motion support

The admin showcase uses screenshots; it does not expose a live staff session or family messages. Traffic figures are historical captures. The school’s backend and credentials are not included.

## Run locally

No installation or build step is required:

```sh
python3 -m http.server 4174 --bind 127.0.0.1
```

Open http://127.0.0.1:4174/.

## Source files

| File | Purpose |
| --- | --- |
| `index.html` | Page structure, content and social links |
| `style.css` | Responsive styling, themes and animation |
| `app.js` | Scroll themes, interactions, previews and motion |
| `appearance.js` | Initial light appearance before the page loads |
| `assets/` | School screenshots, crest and local font |
| `vercel.json` | Static deployment settings and security headers |
| `robots.txt`, `sitemap.xml` | Search discovery |

## Deploy to Vercel

From this directory, using an authenticated Vercel CLI:

```sh
vercel deploy --prod
```

Existing local Vercel project metadata is excluded from Git. To use Git-based deployments, import this repository in Vercel or connect it to the existing portfolio project. This site is static and needs no environment variables.

## Appearance behavior

Every page load starts in Auto mode. Sections choose light or dark appearance as the visitor scrolls. A manual Dark or Light selection lasts for that visit; Auto restores scroll-driven appearance.

## Credits

Portfolio design and development: Win Min Thaw (Moosey). School identity and school photographs belong to their respective owners. The portfolio presents the Guru International School project.
