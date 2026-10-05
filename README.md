# Gym occupancy

A single static page that shows the live number of people at a PureGym Denmark
center (default: Haderslev, center id 288), plus today's hourly chart. Meant to
be opened on a phone.

It calls PureGym's (unofficial, reverse-engineered) app API directly from the
browser. That API allows cross-origin requests, so no server is needed.

## No secrets in this repo

The repo contains no credentials. On first open, the page asks for:

- **Member number**, not your email
- **Password**, the same one used for mit.puregym.dk
- **Center id**, 288 for Haderslev
- **App API key**, the `Fw-Api-Key` value from the PureGym app

These are saved only in that browser's `localStorage` on that device, and are
sent only to `mit.puregym.dk`. Use **Settings → Clear** to remove them.

## Publish on GitHub Pages

1. Create a new repository on github.com, e.g. `gym`. On a free account it must be public.
2. Push this folder:
   ```powershell
   git remote add origin https://github.com/<your-user>/gym.git
   git push -u origin main
   ```
3. In the repo: **Settings → Pages → Source: Deploy from a branch → `main` / `(root)` → Save**.
4. After a minute, open `https://<your-user>.github.io/gym/` on your phone.
5. Optional: use **Share → Add to Home Screen** for an app-like icon.

The page is not secret: anyone with the URL can open it. Without credentials
saved in their own browser, they only see the empty setup form. `noindex`
asks search engines not to list it.

## Behavior

- Loads once when opened; after that it only updates when you press **Refresh**.
- The current hour is highlighted in the chart.

This depends on an undocumented PureGym API and may stop working if PureGym
changes it. Keep it for personal use.
