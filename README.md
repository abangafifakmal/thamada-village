# Thamada Village × Teh O Ice 50¢ — website

Live at **https://thamadavillage.com** (GitHub Pages, custom domain). The old URL https://abangafifakmal.github.io/thamada-village/ redirects there.

Single-file static site. No build step, no framework.

- `index.html` — the whole site (HTML + CSS + JS inline)
- `og.png` — social share image (WhatsApp / Facebook preview, 1200×630)
- `photo-*.jpg`, `logo-*.png` — photos from the kedai's own menu shoot and Instagram
- `CNAME` — custom domain for GitHub Pages (do not delete)

## Where things are

- Domain: Cloudflare Registrar, account Afifakmal9301@gmail.com, auto-renew on. DNS: 4 × A records to GitHub Pages + CNAME `www` → `abangafifakmal.github.io`, all DNS-only (grey cloud). Keep them DNS-only or GitHub's HTTPS certificate breaks.
- Email: Cloudflare Email Routing, `hello@thamadavillage.com` forwards to the owner's inbox.
- Hosting: this repo, branch `main`, root. Settings → Pages → Enforce HTTPS is on.

## Editing

- Prices / menu items: search for `<div class="item">` in `index.html`. One line per item: name, code, tags, price, optional description.
- Hours: the branch cards (`#gelang-patah`, `#larkin`), the footer, the FAQ, and the JSON-LD block in `<head>`. The open/closed pill logic is in the `<script>` at the bottom (`BR` object: closing times; Tuesday closure).
- Photos: replace the file with the same name, same square/4:3 crop, ≤ 1600px wide, JPEG quality ~85.
- Phone numbers and links: search for the number; each appears in the branch card, footer, FAQ and WhatsApp chooser.

## If the domain ever moves

Search `index.html` for `thamadavillage.com` and replace (canonical, `og:url`, `og:image`, JSON-LD `url` fields), update `CNAME`, and point the new DNS at the same GitHub Pages IPs.
