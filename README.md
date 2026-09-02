# Thamada Village × Teh O Ice 50¢ — website

Single-file static site. No build step, no framework. Hosted on GitHub Pages.

- `index.html` — the whole site (HTML + CSS + JS inline)
- `og.png` — social share image (WhatsApp / Facebook preview, 1200×630)

## Custom domain (when ready)

1. Add a file named `CNAME` to this repo containing just the domain, e.g. `thamadavillage.my`
2. At the domain registrar, add DNS records:
   - `A` records for the apex: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - `CNAME` record for `www` → `abangafifakmal.github.io`
3. Repo → Settings → Pages → Custom domain → enter the domain → tick "Enforce HTTPS" once the cert is issued.
4. In `index.html`, search for `abangafifakmal.github.io/thamada-village` and replace with the new domain (canonical, `og:url`, `og:image`, JSON-LD `url` fields).

## Swapping in real photos

In the "Signature plates" section, each card has an `<svg>` inside `<div class="art">`.
Replace the `<svg>…</svg>` with `<img src="photos/nasi-kerabu.jpg" alt="Nasi Kerabu">` (square crop, ~800×800).

## Editing prices or menu items

Search for `<div class="item">` in `index.html`. Each item is one line: name, optional tags, price, optional description.

## Phone numbers, hours, addresses

All in plain text near the top of each branch card (`#gelang-patah`, `#larkin`) and again in the footer and the JSON-LD block in `<head>`. Opening hours logic (open/closed pill) is in the `<script>` at the bottom: `OPEN`, `CLOSE`, and Tuesday closure.
