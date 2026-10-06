<div align="center">

# Ankush Kumar Singh | Portfolio

**A 3D, animated, multilingual developer portfolio with a walking video avatar, voice AI, 5 playable games and a real backend.**

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)
![Redis](https://img.shields.io/badge/Upstash_Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white)

[Live demo](https://ankush-kumar-singh.vercel.app/) | [YouTube](https://www.youtube.com/@Techpulsehindienglish) | [LinkedIn](https://www.linkedin.com/in/ankush-kumar-singh-3066a4214) | [GitHub](https://github.com/Ankushkushwahav)

</div>

---

## Preview

| Hero with background-free walking video | Projects and portfolios, 3 per row |
|---|---|
| ![Hero](docs/hero.jpg) | ![Showcase](docs/showcase.jpg) |

| Arcade section | Job match checker |
|---|---|
| ![Arcade](docs/arcade.jpg) | ![Match](docs/match.jpg) |

![Games](docs/games.jpg)

> Screenshots were captured on a machine without web fonts, so the real site uses the Unbounded and Manrope fonts.

---

## Features

### Look and feel
- 3D tilting hero stage that follows the mouse, with floating tech tags and falling petals
- **Walking video avatar with the background removed**, drawn on a canvas (colour and alpha packed side by side in one MP4)
- Switch to the **full showreel** (3 original videos) with Intro and City chapter buttons, sound and pause
- Animated aurora background and an interactive constellation that reacts to the cursor
- Gradient animated headings, cursor glow, loader, scroll progress bar, section dots, scroll reveal and animated counters
- Light and dark theme (remembered in the browser)
- Fully responsive, respects `prefers-reduced-motion`

### Content
- About, skills, experience timeline, education and certifications taken from the resume
- **Role view:** Full Stack, Frontend or Backend re-filters skills and projects
- Tech filter chips on projects, expandable case studies
- **Projects and Portfolios showcase**, 3 cards per row, with live links
- **Project preview in a popup** with Laptop and Phone widths
- YouTube channel banner and social cards (Telegram, Instagram, Facebook, LinkedIn, GitHub, WhatsApp)
- 3D rotating **tech orbit** and a scrolling skills marquee

### Interactive tools
- **Does Ankush fit your role?** Paste a job description and get an honest match report (matched and missing technologies) that runs fully in the browser
- **Developer terminal** with commands: `help`, `about`, `skills`, `projects`, `experience`, `contact`, `theme`, `clear`
- **Command palette** (`Ctrl + K`)
- **Audio tour** that scrolls the page and speaks about each section (English or Hindi)
- Save contact QR (vCard) and a page QR, Save as PDF, Share button

### AI and voice
- **AI chat** that answers only from the resume (Claude via `/api/chat`, or a built-in FAQ fallback)
- **Hands-free voice mode** with barge-in: start once, then speak any time, even while the AI is talking
- **Live translation** to 14 languages plus any language typed into the box (AI translation when available)
- Hindi and English built in

### Arcade: 5 games
| Game | What it is |
|---|---|
| Neon Racer 3D | Pseudo-3D night racing with curves, traffic, checkpoints and a timer |
| Neon Tower Defense | 3 tower types, upgrades, endless waves and boss rounds |
| Reversi Grandmaster | Play against an alpha-beta search AI (Easy, Medium, Hard) |
| Labyrinth 3D | First-person raycast maze with orbs, exit and minimap |
| Orbital Slingshot | Gravity physics: drag to launch a probe and hit the target |

Best scores are saved in the browser. Keyboard, mouse and touch controls.

### Backend (Vercel serverless)
- Contact form to email through Gmail (Nodemailer) with an **automatic reply to the visitor**
- Optional **Telegram notification** on your phone
- Or use a **Formspree** URL instead of the Gmail backend
- Spam protection: hidden honeypot field and rate limiting (Redis backed)
- **Admin panel** (`/admin.html`): read messages, reply by email, delete, view stats, approve reviews, publish blog posts
- Privacy-friendly **analytics** counters (views, project opens, previews, resume downloads, contacts, chats, games)
- **Reviews** with moderation, a **blog**, and **live GitHub stats**
- Testimonials and project screenshots are config-driven (see below)

### Production polish
- SEO: Open Graph, Twitter card, JSON-LD person schema, `robots.txt`, `sitemap.xml`
- PWA: manifest, icons and service worker
- Resume PDF download button (appears when `resume.pdf` exists)

---

## Project structure

```text
.
|-- index.html            # the whole front end (HTML, CSS, JS, media)
|-- admin.html            # private admin panel
|-- resume.pdf
|-- og.png, icon-192.png, icon-512.png
|-- manifest.webmanifest, sw.js, robots.txt, sitemap.xml
|-- docs/                 # screenshots used in this README
`-- api/
    |-- _lib.js           # Redis, rate limit, admin auth helpers
    |-- contact.js        # form -> email, Telegram, stored message
    |-- chat.js           # AI chat (Anthropic API)
    |-- admin.js          # admin actions
    |-- track.js          # analytics counters
    |-- reviews.js        # reviews + moderation
    |-- blog.js           # blog posts
    `-- github.js         # live GitHub stats
```

## Run it

1. Fork or clone this repo and import it into [Vercel](https://vercel.com).
2. Add the environment variables below.
3. Deploy, then open `/admin.html`.

| Variable | Needed for |
|---|---|
| `GMAIL_USER`, `GMAIL_APP_PASSWORD` | Contact form emails and admin replies |
| `UPSTASH_REDIS_REST_URL`, `UPSTASH_REDIS_REST_TOKEN` | Stored messages, admin panel, analytics, reviews, blog |
| `ADMIN_PASSWORD` | Admin panel login |
| `TO_EMAIL` (optional) | Send notifications to another address |
| `TELEGRAM_BOT_TOKEN`, `TELEGRAM_CHAT_ID` (optional) | Phone notifications |
| `ANTHROPIC_API_KEY` (optional) | Public AI chat for every visitor (this costs money) |

No build step is needed. For local preview, open `index.html`; the `/api` features only work when deployed. Full step-by-step guide in Hinglish: see [DEPLOY.md](DEPLOY.md).

### Personalise (top of the script in `index.html`)
```js
var CAL = '';        // Calendly / Google Calendar link for "Book a call"
var FORM_URL = '';   // Formspree URL (instead of the Gmail backend)
var TESTI = [];      // [{name:'Name', role:'Manager', text:'...'}]
var SHOTS = {};      // {'CodeNest': 'img/codenest.png'} project screenshots
```

## What works where

| Feature | Static hosting only | Vercel with the API |
|---|---|---|
| Hero, projects, games, terminal, match checker, tour | Yes | Yes |
| Voice and AI chat | Built-in FAQ (Chrome or Edge for voice) | Full AI with an API key |
| Contact form | Opens Gmail, or Formspree if `FORM_URL` is set | Email, auto-reply, Telegram |
| Admin, analytics, reviews, blog, GitHub stats | No | Yes (with Redis) |

## Roadmap (planned, not built yet)

- [ ] Real testimonials and project screenshots
- [ ] Calendly booking embedded in the page
- [ ] Global leaderboard for the arcade games
- [ ] Markdown editor for blog posts in the admin panel
- [ ] Background-free versions of the remaining two video scenes
- [ ] Automated tests and a GitHub Actions workflow
- [ ] Case study pages with architecture diagrams

## Author

**Ankush Kumar Singh**, Full Stack Software Engineer (React.js, Node.js, Python/Django)
Sasaram, Bihar and New Delhi | ankushsingh3542@gmail.com

If you like this project, give it a star.
