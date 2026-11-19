# QualTrack landing page (qualtrack.app)

Static, single-page marketing site for QualTrack, a Windows desktop app that tracks Navy small-arms and crew-served weapons qualifications per OPNAVINST 3591.1G. Audience: SAMIs, CSWIs, ATOs, and weapons/security department leadership.

## Structure
- `index.html`: the whole site. All CSS is inline in `<style>`; one small inline script draws the decorative dashboard rows.
- `assets/logo.png`: purple "Q" bullseye logo, transparent background.
- `assets/favicon.png`, `assets/apple-touch-icon.png`: browser and home-screen icons.
- `feedback.html`: a short user-feedback form (adopt Y/N, saves time Y/N + optional hours per week, what could be better, optional contact email), linked from the landing page footer. Same look as `index.html`, with its CSS copied inline.
- No build step, no framework, no package.json. Open `index.html` in a browser to preview.

## Design rules (keep these)
- Minimal startup aesthetic (Linear / Vercel / Raycast). Lots of negative space.
- Dark theme only. Colors live as CSS variables in `:root`: bg `#1a1d2e`, hero glow `#2c3148`, surface `#242838`, border `#3a4058`, text `#f0f2f7` / `#d0d5e2` / muted `#9ba3b8`, accent `#7ba4d9`.
- Status colors (green/yellow/orange/red) are a tiny motif only: dots, the thin spectrum line, the abstract dashboard. Never large fills.
- Fonts: Geist (sans) and Geist Mono (small details like "OPNAVINST 3591.1G", "v1.0"), loaded from Google Fonts.
- No stock photos, military clichés (flags, camo, eagles, guns), sign-up forms, pricing, testimonials, or cookie banners. The feedback form is the one form on the site.
- No heavy animation; only the subtle hero fade-in (respects prefers-reduced-motion).
- Must stay responsive and look good at phone width (~390px) with no horizontal scroll.
- The dashboard preview must stay abstract: no real names or ID numbers.
- Footer disclaimer "Not an official U.S. Navy or DoD product." must remain.

## Open items before launch
- The hero shows a disabled "Coming soon" button. The real "Download for Windows" link is commented out above it; at launch, swap them and point its href at the installer (planned: GitHub Releases `latest/download` URL).
- `contact@qualtrack.app` is a placeholder email.
- The feedback form is a stub: Submit shows the thank-you message and logs the answers to the browser console, but sends nothing. Wire it to a backend (marked `STUB` in the script) before relying on it.

## Hosting
GitHub Pages from `main` (pjsully75116/qualtrack-site), custom domain qualtrack.app with HTTPS enforced. DNS is at Namecheap (BasicDNS): four A records for `@` to GitHub Pages' IPs and a `www` CNAME to `pjsully75116.github.io`. Pushing to `main` deploys.
