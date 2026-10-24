# jensen-innovation.com

Static website for Jensen Innovation, hosted free on **GitHub Pages** at
https://www.jensen-innovation.com (domain at one.com).

```
/                       company page (list of apps)
/portaldex/             PortalDex app page (+ MobileApplication structured data)
/portaldex/privacy/     PortalDex privacy policy (use this URL in App Store / Play Console)
/assets/                style.css, icons
robots.txt sitemap.xml llms.txt CNAME 404.html .nojekyll
```

Plain HTML/CSS — no build step. Edit a file, commit, push; GitHub publishes in ~1 minute.

## Adding a future app
1. Copy `portaldex/` to `newapp/`, edit the text, icon and store links.
2. Add a card for it on `/index.html`, its URLs to `sitemap.xml`, and a section to `llms.txt`.

## One-time setup

### 1. GitHub
1. Create a **public** repo under `JensenInnovation`, e.g. `jensen-innovation-site`, and push this folder.
2. Repo → **Settings → Pages** → Source: *Deploy from a branch*, branch `main`, folder `/ (root)`.
3. Custom domain: `www.jensen-innovation.com` (already in the `CNAME` file).
4. After DNS works (step 2), tick **Enforce HTTPS**.
5. Account (not repo) → **Settings → Pages → Add a verified domain** → `jensen-innovation.com`,
   and add the TXT record GitHub shows at one.com. Prevents domain takeover.

### 2. DNS at one.com (Control panel → DNS settings)
| Record | Name | Value |
|---|---|---|
| A | @ (jensen-innovation.com) | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | jenseninnovation.github.io |

- **Delete** the old `A` records pointing to `46.30.211.38` (one.com web hosting) for `@` and `www`.
- **Do NOT touch** the `MX` records (`mx1–mx4.pub.mailpod10-cph3.one.com`) or SPF/TXT
  email records — that is your klaus@jensen-innovation.com email.
- DNS takes minutes to a few hours; HTTPS certificate follows automatically.

### 3. After it is live
- **Google Search Console** (search.google.com/search-console): add the domain, verify via
  DNS TXT at one.com, submit `https://www.jensen-innovation.com/sitemap.xml`.
- **Bing Webmaster Tools** (bing.com/webmasters): import from Search Console. Bing's index
  also feeds several AI assistants.
- **App Store Connect** → App Information: Privacy Policy URL =
  `https://www.jensen-innovation.com/portaldex/privacy/`, Marketing/Support URL =
  `https://www.jensen-innovation.com/portaldex/`.
- **Google Play Console** → Store presence: same privacy policy URL; website URL as above.
