# Western Mass Bitcoin — Site Migration

## What we're doing
Migrating westernmassbitcoin.com off WordPress to a plain HTML/CSS static site.
Hosting target: Cloudflare Pages (via GitHub repo).
No frameworks. No build tools. No themes. Just clean HTML and CSS.

## Live site to replicate
https://westernmassbitcoin.com

Study this site carefully before writing any code. Match the design as closely as
possible — layout, colors, fonts, spacing, logo placement, nav structure, and
the event listing style.

## What's already in this folder
- `/images/` — WordPress images already downloaded (logo, coin graphics, backgrounds)
  - Logo-Header.png
  - HO-Group1.png (yellow coins)
  - HO-Group2.png (black coins)
  - HO-Group3.png (group background)
  - HO2-768x769.png (global image)
  - Butt-Upcoming.png (upcoming event button graphic)
  - Butt-Past.png (past event button graphic)

## Site structure to build

### Pages
- `index.html` — Homepage (hero, about section, upcoming events, past events)
- `resources.html` — Resources page
- `contact.html` — Subscribe/contact page
- `events/meetup-44.html` — Individual event page (use as template)
- Duplicate the event template for meetups #44 through #50 (upcoming) and #35–#43 (past)

### Navigation (matches live site)
- Home → index.html
- About → index.html#about
- Events → index.html#events
- Resources → resources.html
- Subscribe → contact.html
- "Support Us" button → resources.html#support

### Footer (matches live site)
- Logo
- Tagline: "The Western Mass Bitcoin Meetup is on a mission to find and connect
  bitcoiners in the area and has been growing quickly."
- Nav links: Home, About, Events, Resources, Contact
- Subscribe section with email input
- Copyright: "Copyright © Western Mass Bitcoin Meetup | Designed by Twist Digital"
- Twitter/X icon → https://x.com/MassBitcoin
- Nostr icon → https://snort.social/p/npub1ynn5qnnc95qaqjejrtyazfdgutlxvme3djywe6s9wg76k68s37sqsl2qfd

## Design details

### Colors
- Background: black (#000 or very dark)
- Accent: Bitcoin orange/yellow (#F7931A or similar — check live site)
- Text: white on dark backgrounds
- Buttons: match live site style

### Key social links
- Twitter/X: https://x.com/MassBitcoin
- Nostr: https://primal.net/p/nprofile1qqszfe6qfeuz6qwsfvep4jw3yk5w9lnxduckez8vagzhy0dtdrcglgq9gy2p5

### Subscribe form
The Formspree account has already been created. Use this endpoint directly — no
setup needed, just wire it into the HTML:

  https://formspree.io/f/myknlwbn

Form requirements:
- Fields: email address (required), name (optional)
- Method: POST to the Formspree endpoint above
- On submit: show a thank-you message ("Thanks! We'll keep you posted on upcoming meetups.")
- Use this form in both the contact.html page AND the footer subscribe section on every page

## Upcoming events (from live site)
| # | Date | Location |
|---|------|----------|
| 44 | Sun Apr 12 2026 6pm | Peppa's Pizza, East Longmeadow |
| 45 | Sun May 10 2026 6pm | Peppa's Pizza, East Longmeadow |
| 46 | Sun Jun 7 2026 6pm | Peppa's Pizza, East Longmeadow |
| 47 | Sun Jul 19 2026 6pm | Peppa's Pizza, East Longmeadow |
| 48 | Sun Aug 16 2026 6pm | Peppa's Pizza, East Longmeadow |
| 49 | Sun Sep 13 2026 6pm | Peppa's Pizza, East Longmeadow |
| 50 | Sun Oct 11 2026 6pm | Peppa's Pizza, East Longmeadow |

## Past events (from live site)
| # | Date | Location |
|---|------|----------|
| 43 | Sun Mar 15 2026 6pm | Peppa's Pizza, East Longmeadow |
| 42 | Sun Feb 15 2026 6pm | Peppa's Pizza, East Longmeadow |
| 41 | Sun Jan 18 2026 6pm | Peppa's Pizza, East Longmeadow |
| 40 | Sun Dec 7 2025 6pm | Peppa's Pizza, East Longmeadow |
| 39 | Sun Nov 23 2025 6pm | Peppa's Pizza, East Longmeadow |
| 38 | Sat Oct 18 2025 6pm | The Dante Club, West Springfield |
| 37 | Sun Sep 14 2025 6pm | Peppa's Pizza, East Longmeadow |
| 36 | Sun Aug 17 2025 6pm | Peppa's Pizza, East Longmeadow |
| 35 | Sun Jul 20 2025 1pm | Beefsteak, Great Barrington |

## Git setup

1. Initialize a git repo in this folder: `git init`
2. Connect to the GitHub remote (repo already created at github.com):
   `git remote add origin https://github.com/[USERNAME]/westernmassbitcoin.git`
3. After building the site, commit everything and push:
   `git add -A && git commit -m "Initial static site build" && git push -u origin main`

## Folder structure to create

```
westernmassbitcoin/
├── CLAUDE.md
├── index.html
├── resources.html
├── contact.html
├── events/
│   ├── meetup-44.html
│   ├── meetup-45.html
│   └── ... (one per event)
├── css/
│   └── style.css
└── images/
    └── (already populated)
```

## After the build — Cloudflare Pages setup (human does this, not Claude)
1. Go to cloudflare.com → Pages → Create a project
2. Connect to GitHub → select the westernmassbitcoin repo
3. Build settings: no build command needed (plain HTML), output directory = `/`
4. Deploy
5. Add custom domain: westernmassbitcoin.com
6. Update nameservers at domain registrar to Cloudflare's nameservers

## What NOT to do
- Do not use Hugo, Jekyll, or any static site generator
- Do not use npm, node, or any package manager
- Do not use React, Vue, or any JavaScript framework
- Do not use WordPress or PHP
- Keep it simple: HTML + CSS + minimal vanilla JS only
