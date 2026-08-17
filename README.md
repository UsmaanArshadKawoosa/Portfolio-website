# Portfolio Website

A compact, static portfolio website for Usmaan Kawoosa. This repository contains a single-file static site (index.html) that showcases skills, experience, and projects dynamically loaded from GitHub.

## Overview

This project is a personal portfolio website implemented as a single static HTML file (index.html). It presents a hero section, an "about" terminal, skills, experience timeline, contact cards, and a projects grid which is populated from the GitHub API at runtime.

## Features

- Responsive layout (works on desktop and mobile)
- Project showcase automatically loaded from GitHub (client-side)
- Contact links (email, phone, GitHub, LinkedIn)
- Animated background canvas and cursor glow
- Scroll progress bar and reveal animations
- Simple typewriter effect for the hero label
- Accessibility-minded semantic HTML and links that open in new tabs where appropriate

## Tech Stack

- Frontend: plain HTML, vanilla JavaScript
- Styling: embedded CSS (no preprocessor)
- APIs / integrations: GitHub REST API (client-side unauthenticated requests)
- Libraries: none (no external JS libraries included)
- Deployment: static site (any static host — Netlify, Vercel, GitHub Pages)

## Website Structure

- index.html — entire site (HTML, CSS, and JavaScript in one file)

Only a single file is required to run the site.

## GitHub Integration

The site dynamically loads public repositories using the GitHub REST API. Implementation details (from index.html):

- GitHub username: defined in the JS constant `GITHUB_USERNAME` (value in repo: "UsmaanArshadKawoosa").
- Portfolio repo name: defined in `PORTFOLIO_REPO` (value: "portfolio-website"). The loader filters out forks and excludes the repository matching `PORTFOLIO_REPO`.
- API endpoint: `https://api.github.com/users/${GITHUB_USERNAME}/repos?per_page=100&sort=updated&direction=desc`
- Filtering logic: removes forked repos and the portfolio repository, then sorts by updated date.
- Project cards display: name (formatted), description, primary language, star count, topics (if present), created year, and last-updated date.
- Behavior: uses unauthenticated requests; new public repositories appear automatically (subject to GitHub API rate limits for unauthenticated requests).

Note: the contact section contains an explicit GitHub link to `github.com/UsmaanAK` while the JS loader uses `UsmaanArshadKawoosa`. If you want the projects loaded from a different account, edit the `GITHUB_USERNAME` constant in index.html.

## Running Locally

This is a static site. Two easy ways to run locally:

1. Open file directly
   - Double-click `index.html` or open it in a browser.

2. Serve with a simple static server (recommended to avoid file:// issues):
   - Python 3: `python -m http.server 8000` then open http://localhost:8000
   - Node (if you prefer): `npx http-server . -p 8000` (install http-server if needed)

There is no build step or package.json in this repository.

## Deployment

No deployment configuration (vercel.json, netlify.toml, etc.) is included. Deploy this repository as a static site on any provider that supports static hosting:

- GitHub Pages: push to a branch and enable Pages in repository settings.
- Vercel / Netlify: connect the repo and deploy; they will serve index.html.

## Customization

Edit `index.html` to change content:

- Personal information and the JSON-like terminal block: in the `#terminal-content` element under the About section.
- Hero text, name, and headline: inside the hero section near the top of the file.
- Contact links (email, phone, GitHub, LinkedIn): in the Contact section (mailto, tel, and href values).
- GitHub integration: update `GITHUB_USERNAME` and `PORTFOLIO_REPO` constants in the inline JavaScript near the bottom of index.html.
- Styling and layout: CSS is embedded at the top of index.html — update variables under `:root` for colors and fonts.

## Project Tree

- index.html
- README.md
- .gitignore

## Screenshots / Preview

No screenshot assets are included in this repository. Open `index.html` in a browser to preview the site.

## Future Improvements (realistic and non-invasive)

- Extract CSS/JS to separate files for maintainability.
- Add a small build step (optional) to minify assets.
- Add an authenticated GitHub token option (server-side or via build) to avoid rate limits and show private repo data (only if desired).
- Add automated deployment configuration (vercel.json or GitHub Pages workflow) if you want one-click deploys.
- Move contact details to environment or a config file if you prefer not to store them in plain HTML.

## Author

Usmaan Kawoosa

Links visible in the site:
- GitHub (JS loader account): https://github.com/UsmaanArshadKawoosa (used by the projects loader in index.html)
- GitHub (contact link visible on site): https://github.com/UsmaanAK
- LinkedIn: https://www.linkedin.com/in/usmaan-kawoosa-17aba1261/

---

If you'd like, the README can be shortened or expanded with screenshots, a live demo link, or sample commits. I did not add or change any visual or functional code in the site itself.