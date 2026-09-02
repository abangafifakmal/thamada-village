# Thamada Village × Teh O Ice 50¢ — website

Live at **https://thamadavillage.com** (GitHub Pages, custom domain). The old URL https://abangafifakmal.github.io/thamada-village/ redirects there.

Single-file static site. No build step, no framework.

- `index.html` — the whole site (HTML + CSS + JS inline)
- `og.png` — social share image (WhatsApp / Facebook preview, 1200×630)
- `photo-*.jpg`, `logo-*.png` — photos from the kedai's own menu shoot and Instagram
- `dv-*.jpg` — web-size crops of the owner's professional menu photos (Google Drive folder "2. Links (Photo)" from the menu designer). `dv-hero-*` = hero showcase 4:3, `dv-plate-*` = signature tiles 1:1, `dv-mNN` = marquee squares, `dv-table-spread` = the table section.
- `CNAME` — custom domain for GitHub Pages (do not delete)
- `sitemap.xml`, `robots.txt` — for Google Search Console

## Where things are

- Domain: Cloudflare Registrar, account Afifakmal9301@gmail.com, auto-renew on. DNS: 4 × A records to GitHub Pages + CNAME `www` → `abangafifakmal.github.io`, all DNS-only (grey cloud). Keep them DNS-only or GitHub's HTTPS certificate breaks.
- Email: Cloudflare Email Routing, `hello@thamadavillage.com` forwards to afifakmal9301@gmail.com (change the destination in Cloudflare → Email → Email Routing).
- Analytics: Google Analytics 4, property "thamadavillage.com", Measurement ID `G-T83KV31HD5` (account: Afifakmal9301@gmail.com). The tag is in `<head>`; custom click events (`whatsapp_click`, `call_click`, `waze_click`, `maps_click`, `delivery_click`, `social_click`, `menu_view`, `nearest_kedai_click`) are sent from the last `<script>` in `index.html`, with params `branch`, `place`, `purpose`, `platform`.
- Search: Google Search Console, domain property `thamadavillage.com`, sitemap submitted.
- Hosting: this repo, branch `main`, root. Settings → Pages → Enforce HTTPS is on.

## Editing

- The table (v6): `#table` is a pinned scroll scene (`.tscene` height sets scroll length, `.tpin` is sticky). Rows in the ticket carry `data-price`; the total is computed from them. Body uses `overflow-x:clip` on purpose — `overflow-x:hidden` on body breaks `position:sticky` for the nav and this scene.
- Motion (v5): hero showcase cards are the `<figure class="show-card">` list in the hero; add/remove a figure and the dots update automatically. Photo marquee = `<div class="marq">`, keep both copies of the list identical. Text band = `<div class="band">`. Scroll reveal = `data-rv` attribute. Everything respects `prefers-reduced-motion`.

- Prices / menu items: search for `<div class="item">` in `index.html`. One line per item: name, code, tags, price, optional description.
- Hours: the branch cards (`#gelang-patah`, `#larkin`), the footer, the FAQ, and the JSON-LD block in `<head>`. The open/closed pill logic is in the `<script>` at the bottom (`BR` object: closing times; Tuesday closure).
- Photos: replace the file with the same name, same square/4:3 crop, ≤ 1600px wide, JPEG quality ~85.
- Phone numbers and links: search for the number; each appears in the branch card, footer, FAQ and WhatsApp chooser. Every WhatsApp link carries a prefilled `?text=`. General/reserve buttons use the owner's template ("Hi, saya click dari website thamadavillage.com. / Nak reserve meja : / Nama : / Tarikh : / Masa : / Bilangan Pax :", line breaks as `%0A`); pickup, careers and feedback keep their own first line. Keep the "click dari website" line so the kedai knows the chat came from the website.
- After a change to the menu or hours, bump `<lastmod>` in `sitemap.xml`.

## If the domain ever moves

Search `index.html` for `thamadavillage.com` and replace (canonical, `og:url`, `og:image`, JSON-LD `url` fields), update `CNAME`, and point the new DNS at the same GitHub Pages IPs.
