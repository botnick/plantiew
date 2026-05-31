# plantiew.com — coming-soon landing

แพลตฟอร์มช่วยวางแผนเที่ยวสำหรับคนไทย เปลี่ยนข้อมูลเที่ยวที่กระจัดกระจายให้เป็นแพลนรายวัน
พร้อมสถานที่ จุดแวะ แผนที่ แหล่งข้อมูล และ PDF — หน้า landing สำหรับช่วง coming soon.

Static site (HTML/CSS/JS, no build step). Light/airy OTA-style UI, IBM Plex Sans Thai, custom SVG icons (no emoji).

## Files
| File | Purpose |
|------|---------|
| `index.html` | Landing page (full SEO: meta, OG, Twitter, JSON-LD `@graph` WebSite + SoftwareApplication + Organization + FAQPage, hreflang, canonical) |
| `privacy.html` / `terms.html` | Legal pages (PDPA-aware) |
| `og-image.png` | Open Graph share image (1200×630) |
| `favicon-32.png` `favicon.ico` `apple-touch-icon.png` `icon-192.png` `icon-512.png` `logo.png` | Icons + PWA |
| `site.webmanifest` | PWA manifest |
| `robots.txt` / `sitemap.xml` | Crawl directives |
| `og-card.html` / `icon.html` | Source templates for rendering `og-image.png` / icons (noindex, disallowed in robots) |

## Waitlist
The waitlist form posts to [Web3Forms](https://web3forms.com) (free, no backend). The public access key
lives in `index.html` (`input[name="access_key"]`) — Web3Forms keys are meant to be client-side.

## Deploy
Serve the folder at the **site root** of `https://plantiew.com/`. All canonical / OG / schema / sitemap
URLs are absolute to that domain, so OG previews, sitemap, and structured data only resolve once deployed there.

After deploy:
1. Open `https://plantiew.com/sitemap.xml` — must return valid XML (not 404).
2. Submit `sitemap.xml` in Google Search Console (verify the `plantiew.com` property first; host/protocol must match the `loc` URLs).
3. Add a `CNAME` if using GitHub Pages with the custom domain.

## Regenerate assets
`og-image.png` and the icons are rendered from `og-card.html` / `icon.html` via headless Chrome
(`--screenshot --window-size=...`). Edit the source HTML, re-render, done.
