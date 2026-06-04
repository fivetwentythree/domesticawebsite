# Domestica website

This repository is a static Domestica export ready for GitHub Pages at `https://domestica.au/`.

GitHub Pages should be configured to publish from the `main` branch, `/ (root)` folder. The root folder must contain `index.html`, `assets/`, `.nojekyll`, and `CNAME`.

## Custom domain

- Production domain: `https://domestica.au/`
- GitHub Pages source: `main` branch, `/ (root)`
- GitHub Pages custom domain value: `domestica.au`
- DNS apex records: point `domestica.au` at GitHub Pages.
- Optional `www` record: point `www.domestica.au` at the repository owner's GitHub Pages hostname.

See `DOMESTICA_AU_HOSTING_SEO_GUIDE.md` for the full hosting, DNS, SEO, and AI discovery checklist.

## SEO deployment checklist

- Canonical domain used in metadata: `https://domestica.au/`.
- Confirm the canonical URL, Open Graph URL, structured data URLs, `robots.txt`, `sitemap.xml`, `llms.txt`, and `CNAME` all use `domestica.au`.
- After deployment, verify the site in Google Search Console and Bing Webmaster Tools.
- Submit `https://domestica.au/sitemap.xml` in Search Console.
- Create or claim the Google Business Profile for Domestica Hobart and set the website, phone number, service area, photos, and business category there.
