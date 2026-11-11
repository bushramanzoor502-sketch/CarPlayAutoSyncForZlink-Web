# Car Play Auto Sync for ZLINK — product website

Marketing site (single page) plus a standalone privacy policy page for the **Car Play Auto Sync for ZLINK**
Android app (`C:\github\SmartCarConnect-1`, package `utiledge.carplayandroid.carmirroring.auto.sync`).
Same setup as the Full Audery website: no build step, no dependencies, deployed by GitHub Pages
(`.github/workflows/deploy.yml`, on push to `master`).

```bash
python -m http.server 8080   # then open http://127.0.0.1:8080/
```
(On Windows, Python's built-in server may send `.webp` as `application/octet-stream`, so images can look
broken locally. GitHub Pages serves them correctly.)

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
- `assets/img/icons/` — launcher icon from `mipmap-xxxhdpi/`.

## Before going live
1. Confirm the Play Store URL works once the app is published.
2. `ads.txt` was copied from the Full Audery site (`pub-7900893619696665`). Confirm this app uses the same
   AdMob account, or replace it.
3. The app's `PRIVACY_POLICY_URL` (SettingsScreen.kt) points to a Google Sites page; switch it to this
   site's `privacy.html` once deployed, if wanted.
4. Make `og:image` absolute once the domain is known.
