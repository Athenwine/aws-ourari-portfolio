# Aws Ourari — Portfolio Site

A multi-page, static portfolio site. No build step, no framework — just HTML, CSS, and a small
JS file, so it will run anywhere: double-click it open locally, or drag it onto any static host.

## What's inside

```
index.html            Home
about.html             Education, skills, certifications, languages
experience.html        Work experience + volunteering
projects.html          Projects hub (links to the 4 pages below)
project-vistasy.html   Capstone case study
project-animal.html    Animal Classification System
project-spotify.html   Spotify Music Trends Analytics
project-quiz.html      Django Quiz Management Platform
contact.html           Contact / calling card
assets/style.css       All styling (one shared file, edit here for site-wide changes)
assets/script.js       Mobile nav toggle + scroll-reveal animation
assets/aws-ourari-resume.pdf   Your resume, wired to the "Download Resume" button on Home
```

## Viewing it locally

Just open `index.html` in a browser — every page works straight off disk, no server required.

If you want to preview it exactly as it'll behave once deployed (some browsers are picky about
local file paths), run a tiny local server instead:

```bash
cd path/to/this/folder
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## How to fix / edit things

- **Text content**: every page is plain HTML — search for the text you want to change directly
  in the relevant `.html` file and edit it in place.
- **Colors, fonts, spacing, animations**: all in `assets/style.css`. The top of the file has a
  `:root` block with the color variables (`--red`, `--black`, `--white`, etc.) — change those and
  the whole site updates.
- **Adding a new project page**: duplicate `project-quiz.html`, rename it, update the content, and
  add a card + link to it on `projects.html`.
- **Swapping the resume PDF**: replace `assets/aws-ourari-resume.pdf` with a new file of the same
  name, or update the `href` on the "Download Resume" button in `index.html` if you rename it.
- **Nav links**: the header/footer markup is repeated at the top and bottom of every page (by
  design, so the site works with zero JavaScript and no server-side includes). If you rename a
  page or add a new one, update the `<nav class="primary-nav">` block in *every* HTML file.

## How to deploy

Pick whichever is easiest for you — all three are free for a personal site like this.

### Option A — Netlify (easiest, no account needed to try it)
1. Go to https://app.netlify.com/drop
2. Drag the whole project folder onto the page.
3. Netlify gives you a live URL immediately. Create a free account to keep it permanently and
   optionally connect a custom domain.

### Option B — GitHub Pages (free, ties into your GitHub profile)
1. Create a new repository on GitHub, e.g. `aws-ourari-portfolio`.
2. Push this folder's contents to the repository:
   ```bash
   cd path/to/this/folder
   git init
   git add .
   git commit -m "Initial portfolio site"
   git branch -M main
   git remote add origin https://github.com/Athenwine/aws-ourari-portfolio.git
   git push -u origin main
   ```
3. In the repo on GitHub: **Settings → Pages → Source → Deploy from a branch**, choose `main` and
   `/ (root)`, save.
4. Your site will be live at `https://Athenwine.github.io/aws-ourari-portfolio/` within a couple
   of minutes.

### Option C — Vercel
1. Go to https://vercel.com/new and import the same GitHub repo from Option B (or drag-and-drop
   the folder via the Vercel CLI: `npx vercel`).
2. No build settings needed — it's a static site, Vercel will serve it as-is.

## Optional: custom domain
All three hosts above let you attach a custom domain (e.g. `awsourari.com`) for free once you own
one — look for "Domain settings" in whichever host you pick.

## Optional: a working contact form
Right now the "Contact" page uses `mailto:` links, which just open the visitor's email client —
reliable and requires zero setup. If you'd rather have an actual on-page form that emails you
directly, the simplest no-backend option is [Formspree](https://formspree.io) (free tier): sign
up, get a form endpoint, and point a `<form action="https://formspree.io/f/xxxxxxx" method="POST">`
at it inside `contact.html`. Ask me if you want this wired up.
