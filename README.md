# Swipxl — Marketing Website

Static landing page + legal pages for the Swipxl photo-cleaner app. No build step, no
dependencies — just plain HTML/CSS. Drop the `website/` folder onto any static host.

## Structure

```
website/
├── index.html          # Landing page (ads + app marketing)
├── privacy/index.html  # Served at /privacy   (the app links here)
├── terms/index.html    # Served at /terms     (the app links here)
├── assets/
│   ├── icon.png        # App icon (also used as favicon)
│   └── screenshots/    # In-app screenshots used on the landing page
├── robots.txt
└── sitemap.xml
```

The privacy & terms pages live in their own folders so the URLs resolve as
`https://swipxl.app/privacy` and `https://swipxl.app/terms` on any standard host
(directory requests serve `index.html` by default). These exact paths are hard-coded
in the app, so **don't rename these folders.**

## Before going live

1. **Add the store links.** In `index.html`, search for `data-store=` — there are two badge
   sets (hero + final CTA). Replace each `href="#"` with the real URL:
   - Google Play: `https://play.google.com/store/apps/details?id=<your.package.id>`
   - App Store: `https://apps.apple.com/app/id<your-app-id>`
   Each placeholder is marked with a `<!-- TODO -->` comment.
2. **Set the domain.** Update the `og:url` in `index.html` and the URLs in `sitemap.xml`
   if you use a domain other than `swipxl.app`.
3. **Fill the Terms governing-law placeholder** (`terms/index.html`, Section 12).

## Deploying

- **Netlify / Vercel / Cloudflare Pages:** set the publish/root directory to `website/`.
- **GitHub Pages:** push `website/` contents to the Pages branch/root.
- **Any web server (Nginx/Apache/S3):** upload the folder; clean URLs work out of the box.

Local preview: `cd website && python3 -m http.server 8080` → open http://localhost:8080

## Design

Mirrors the app's design system: dark `#161622` background, indigo→purple gradient
(`#667EEA`→`#764BA2`), Nunito typeface, rounded cards, and the same pastel category accents.
