# Reflection Media — Site Bundle

A static, single-page marketing site. No build step. Drop the folder onto any static host.

## Folder structure

```
reflection-media-site/
├── index.html      ← the entire site (markup + styles + JS inline)
├── fonts/          ← 10 PP Editorial Old weights (loaded via @font-face)
├── images/         ← put jesse.jpg here
└── README.md
```

## Add the headshot

Save Jesse's headshot as `images/jesse.jpg` (4:5 portrait, 1600px wide is plenty). The page loads it automatically. While the file is missing, the page shows a styled placeholder card — no broken image icon.

If you'd rather use a different filename or extension, edit one line in `index.html`:

```html
<img src="images/jesse.jpg" ... />
```

## External assets used

These load from the public internet at runtime — no install needed:

- **General Sans** (body font) — Fontshare CDN
- **Vimeo player** — `player.vimeo.com` for the hero loop and 4 portfolio embeds

If your hosting environment blocks third-party requests, the page still renders; the body font falls back to the system sans stack and the Vimeo iframes show their normal "video failed to load" state.

## Vimeo embeds

The portfolio uses standard `player.vimeo.com/video/{ID}` URLs. If a video shows "Private video" in the player, it's because the videos are review-link-only. To fix:

1. Open the Vimeo source video.
2. Privacy → "Hide this video from Vimeo, but allow embedding on any domain."
3. The current embed will start working — no code change needed.

Alternatively, grab the official `<iframe>` embed code from Vimeo and paste it over the existing one.

## Booking link

Both `Get a Quote` and `Start a Project` route to your Google Calendar appointment URL. Search-and-replace this string if the URL ever changes:

```
https://calendar.google.com/calendar/u/0/appointments/schedules/AcZssZ0l6gLzGVscoM7kstjesSZBg75LzFBwXCjKDgVEwJFN16A7efqFNBro5NYcolh-IVgV-rFoZMfj
```

## Deploy

### Vercel (fastest)
```bash
cd reflection-media-site
npx vercel
```
Follow the prompts. First deploy gives you a `*.vercel.app` URL; add a custom domain in the Vercel dashboard.

### Netlify (drag & drop)
1. Go to https://app.netlify.com/drop
2. Drag the `reflection-media-site` folder onto the page.
3. Done. Add a custom domain from the site's settings.

### GitHub Pages
1. Create a new GitHub repo.
2. Upload the contents of `reflection-media-site/` (not the folder itself — the files inside).
3. Settings → Pages → Source: `main` branch, `/ (root)`.
4. Live at `https://<user>.github.io/<repo>/`.

### Plain server / cPanel / S3 / any static host
Upload the folder. Point the domain at it. That's it. No build, no Node, no env vars.

## Local preview before deploy

From inside the folder:

```bash
python3 -m http.server 8080
```

Open http://localhost:8080 — opens with the same path resolution the deployed site uses.

## Editing tips

- All copy lives in `index.html` — search for the heading you want to change.
- Colors are CSS variables at the top: `--black`, `--ivory`, `--ink`. Change once, propagates everywhere.
- The hero loop video ID is in the iframe `src` near the top of `<body>`. Swap the ID to change reels.
- Service tabs, portfolio cards, and circle medallions are all repeated blocks — copy-paste a block to add another.

## Footer info

Reflection Media LLC · +1 (714) 257-5509 · info@reflectionmedia.io · © 2021 Reflection Media · A God fearing business.
