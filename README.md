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

## Store badges

- **Google Play** is live: both badges (hero + final CTA) use Google's official
  `assets/google-play-badge.svg`, linked to
  `https://play.google.com/store/apps/details?id=com.swipeclean.swipe_clean`.
- **App Store** is a dimmed "Coming soon" pill (class `.as-badge.soon`) styled to match the
  Google badge. When iOS ships, turn each `.as-badge` `<span>` into an `<a href="...">` pointing
  at `https://apps.apple.com/app/id<your-app-id>` and drop the `soon` class.

## Before going live

1. **Set the domain.** Update `og:url` in `index.html` and the URLs in `sitemap.xml`/`robots.txt`
   if you move off the current GitHub Pages URL.
2. **Fill the Terms governing-law placeholder** (`terms/index.html`, Section 12).

## Deploying

- **Netlify / Vercel / Cloudflare Pages:** set the publish/root directory to `website/`.
- **GitHub Pages:** push `website/` contents to the Pages branch/root.
- **Any web server (Nginx/Apache/S3):** upload the folder; clean URLs work out of the box.

Local preview: `cd website && python3 -m http.server 8080` → open http://localhost:8080

## Design

Mirrors the app's design system: dark `#161622` background, indigo→purple gradient
(`#667EEA`→`#764BA2`), Nunito typeface, rounded cards, and the same pastel category accents.
