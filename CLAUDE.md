# QualTrack landing page (qualtrack.app)

Static, single-page marketing site for QualTrack, a Windows desktop app that tracks Navy small-arms and crew-served weapons qualifications per OPNAVINST 3591.1G. Audience: SAMIs, CSWIs, ATOs, and weapons/security department leadership.

## Structure
- `index.html`: the whole site. All CSS is inline in `<style>`; one small inline script draws the decorative dashboard rows.
- `assets/logo.png`: purple "Q" bullseye logo, transparent background.
- `assets/favicon.png`, `assets/apple-touch-icon.png`: browser and home-screen icons.
- `feedback.html`: a short user-feedback form (adopt Y/N, hours saved per week 0–10+, what could be better, optional contact email), linked from the landing page footer. Same look as `index.html`, with its CSS copied inline.
  - Answers post in the background to the owner's "QualTrack Feedback" Google Form (`GOOGLE_FORM` and `FIELDS` at the top of the script); visitors never leave the page. Responses are in that form's Responses tab.
  - Sent values must match the Google Form's choices exactly ("Yes"/"No", "0"–"10+"), or Google silently drops the answer. If a question is added, renamed to a different type, or its choices change in the Google Form, update the page to match and re-read the field IDs from the form's `FB_PUBLIC_LOAD_DATA_`.
  - The post is `no-cors`, so the page can't confirm Google accepted it. Test a real submission after any change.
- `about.html`: a short About Us page (the founding team's story, written by the owner; keep its wording) ending in "Help us get there." with a button to the feedback page.
- Every page's footer links Feedback and About Us; keep the three footers in sync.
- No build step, no framework, no package.json. Open `index.html` in a browser to preview.

## Design rules (keep these)
- Minimal startup aesthetic (Linear / Vercel / Raycast). Lots of negative space.
- Dark theme only. Colors live as CSS variables in `:root`: bg `#1a1d2e`, hero glow `#2c3148`, surface `#242838`, border `#3a4058`, text `#f0f2f7` / `#d0d5e2` / muted `#9ba3b8`, accent `#7ba4d9`.
- Status colors (green/yellow/orange/red) are a tiny motif only: dots, the thin spectrum line, the abstract dashboard. Never large fills.
- Fonts: Geist (sans) and Geist Mono (small details like "OPNAVINST 3591.1G" and the "Beta" badge), loaded from Google Fonts.
- No stock photos, military clichés (flags, camo, eagles, guns), sign-up forms, pricing, testimonials, or cookie banners. The feedback form is the one form on the site.
- No heavy animation; only the subtle hero fade-in (respects prefers-reduced-motion).
- Must stay responsive and look good at phone width (~390px) with no horizontal scroll.
- The dashboard preview must stay abstract: no real names or ID numbers.
- Footer disclaimer "Not an official U.S. Navy or DoD product." must remain.

## Download (live since 2026-11-19, beta 0.2.0)
- The hero's "Download for Windows" button links to `https://github.com/pjsully75116/qualtrack-site/releases/latest/download/QualTrackSetup.exe`: the newest GitHub Release of *this* repo. The app's source repo is private, so its own releases are not public.
- To publish a new version: build it in the app repo (`build-release.ps1`), then create a release here tagged `vX.Y.Z` with the installer attached under the exact name `QualTrackSetup.exe` (plus the portable zip and a `SHA256SUMS.txt`). The button needs no change; update the "Beta X.Y.Z" line under it.
- Each build stops opening about 5 months after it is built (0.2.0: after 19 Apr 2027), so post a newer release before then.
- The project owner shares the link with a few testers only; the AGPL licensing of the app's PDF library (iText) must be settled before any wide release (see the app repo's TODO.md).

## Open items
- `contact@qualtrack.app` is a placeholder email.

## Hosting
GitHub Pages from `main` (pjsully75116/qualtrack-site), custom domain qualtrack.app with HTTPS enforced. DNS is at Namecheap (BasicDNS): four A records for `@` to GitHub Pages' IPs and a `www` CNAME to `pjsully75116.github.io`. Pushing to `main` deploys.
