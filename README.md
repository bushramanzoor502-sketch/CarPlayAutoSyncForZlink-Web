# Car Play Auto Sync for ZLINK — product website

Marketing site (single page) plus a standalone privacy policy page for the **Car Play Auto Sync for ZLINK**
Android app (`C:\github\SmartCarConnect-1`, package `utiledge.carplayandroid.carmirroring.auto.sync`).
No build step, no dependencies. Hosted on Netlify (https://carplayautosyncforzlink-web.netlify.app).
`.github/workflows/netlify-deploy.yml` publishes it with the Netlify CLI on every push to `master` (README-only
changes are skipped). It needs one repo secret (Settings > Secrets and variables > Actions):
`NETLIFY_AUTH_TOKEN` (Netlify: User settings > Applications > Personal access tokens). The Project ID
`725a4e21-44ba-4de3-89d9-4e84380bab2e` is in the workflow; a `NETLIFY_SITE_ID` secret would override it. It can also be run by hand from the Actions tab.

```bash
python -m http.server 8080   # then open http://127.0.0.1:8080/
```
(On Windows, Python's built-in server may send `.webp` as `application/octet-stream`, so images can look
broken locally. Netlify serves them correctly.)

## Sections (`index.html`)
| Anchor | Section |
|---|---|
| `#top` | Hero: headline, CTAs, stats, phone with the real Home dashboard screenshot |
| `#features` | 14 feature cards, one per real app feature |
| `#screens` | Horizontal gallery of real screenshots |
| `#drive` | Drive Mode (landscape head-unit screenshot) |
| `#ai` | AI Car Modification + Inspection with AI |
| `#how` | 4-step setup |
| `#privacy` | Privacy teaser band |
| `#support` / `#permissions` | Quick guides + permission table |
| `#faq` | FAQ and troubleshooting |
| `#contact` | Support email, Gmail link, copy button |
| `#get` | Final download CTA |

## Design
Colours are copied from the app's `ui/theme/Color.kt` (light, warm coral theme): canvas `#FFF7F3`,
panels `#FFFFFF`, primary `#FF6B4A`, text `#221814`, muted `#6E574F`, outline `#E2D1C8`, plus the
dashboard's pastel washes. The site is always light, like the app. Font: Nunito (the app bundles it).

## Assets
- `assets/img/screens/` — real screenshots from the phone (status bar cropped; number plate and the
  Drive Mode map blurred so no real location is shown).
- `assets/img/art/` — car and inspection art from the app's `res/drawable-nodpi/`.
- `assets/img/icons/` — launcher icon from `mipmap-xxxhdpi/`, resized: `icon_96.webp` (header/footer), `favicon_64.png`, `apple_180.png`.
- `_headers` — Netlify cache rules: 7 days for `/assets/*` (bump the `?v=` query when a file changes).

## Before going live
1. Confirm the Play Store URL works once the app is published.
2. `ads.txt` and `app-ads.txt` carry the app's AdMob publisher ID `pub-7900893619696665` (App ID
   `ca-app-pub-7900893619696665~4754109472`). Play Console's developer website must be this site's root for
   AdMob to find `app-ads.txt`.
3. Live at https://carplayautosyncforzlink-web.netlify.app (Netlify, deploys from `master`). The app's `PRIVACY_POLICY_URL` points to `/privacy.html` there.
4. `og:image` already uses the absolute Netlify URL.
