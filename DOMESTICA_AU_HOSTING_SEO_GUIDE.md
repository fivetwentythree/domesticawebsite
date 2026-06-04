# Domestica.au Hosting, SEO, and AI Discovery Guide

This site is a static GitHub Pages export. The cleanest launch path is to keep GitHub Pages as the host and attach `domestica.au` as the custom domain.

## 1. Register or confirm the domain

1. Confirm `domestica.au` is registered under the correct owner.
2. Make sure the registrant has an Australian presence, which `.au` direct domains require.
3. Keep domain ownership with the business owner, not a developer, contractor, or temporary personal account.
4. Enable registrar account security: strong password, MFA, current recovery email, and auto-renew.

If the domain is not registered yet, register it through an auDA-accredited registrar. For `.au` direct domains, common eligibility evidence includes an Australian driver's licence, passport, ABN, ACN, Australian trade mark, or another accepted Australian presence record.

## 2. Configure GitHub Pages

In the GitHub repository:

1. Go to `Settings` > `Pages`.
2. Set the source to the `main` branch and `/ (root)`.
3. Enter the custom domain as `domestica.au`.
4. Save the Pages settings.
5. Wait for DNS checks to pass.
6. Enable `Enforce HTTPS` once GitHub allows it. This can take time after the DNS records are correct.

This repository already includes:

- `CNAME` with `domestica.au`
- `.nojekyll`
- `index.html`
- `assets/`
- `robots.txt`
- `sitemap.xml`
- `llms.txt`

## 3. Configure DNS

At the DNS provider for `domestica.au`, use these records for an apex-domain GitHub Pages setup.

### Required apex records

Create four `A` records:

| Type | Host | Value |
| --- | --- | --- |
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |

Optional but recommended IPv6 records:

| Type | Host | Value |
| --- | --- | --- |
| AAAA | @ | 2606:50c0:8000::153 |
| AAAA | @ | 2606:50c0:8001::153 |
| AAAA | @ | 2606:50c0:8002::153 |
| AAAA | @ | 2606:50c0:8003::153 |

### Recommended www record

Add a `CNAME` record:

| Type | Host | Value |
| --- | --- | --- |
| CNAME | www | fivetwentythree.github.io |

The `www` record should point to the GitHub Pages owner hostname, not a repository path.

### Remove conflicting records

Remove or avoid:

- Parked-domain `A` records from the registrar
- Old `CNAME` records for `@`
- Forwarding records that redirect with frames
- Wildcard records like `*.domestica.au`
- Duplicate `AAAA` records from another host

## 4. Verify DNS

After DNS changes propagate, run:

```sh
dig domestica.au +noall +answer -t A
dig domestica.au +noall +answer -t AAAA
dig www.domestica.au +nostats +nocomments +nocmd
```

Expected `A` values are the four GitHub Pages IP addresses. Expected `www` value is a CNAME chain beginning with `fivetwentythree.github.io`.

Then check these URLs in a browser:

- `https://domestica.au/`
- `https://www.domestica.au/`
- `https://domestica.au/robots.txt`
- `https://domestica.au/sitemap.xml`
- `https://domestica.au/llms.txt`

One of `domestica.au` or `www.domestica.au` should be the canonical version. This repository uses `https://domestica.au/` as canonical.

## 5. Domain migration SEO changes already made

The repo has been updated so crawlers see `domestica.au` as the primary website:

- `index.html`: canonical URL, Open Graph URL, Open Graph image, Twitter image, and JSON-LD structured data now use `https://domestica.au/`.
- `robots.txt`: sitemap now points to `https://domestica.au/sitemap.xml`; `OAI-SearchBot` is explicitly allowed for ChatGPT search discovery.
- `sitemap.xml`: homepage URL now points to `https://domestica.au/`.
- `llms.txt`: official site and AI summary now point to `https://domestica.au/`.
- `CNAME`: GitHub Pages custom domain set to `domestica.au`.

## 6. Google SEO launch checklist

1. Create or log in to Google Search Console.
2. Add a Domain property for `domestica.au`.
3. Verify ownership using the DNS TXT record Google provides.
4. Submit the sitemap: `https://domestica.au/sitemap.xml`.
5. Use URL Inspection for `https://domestica.au/`.
6. Click `Request indexing` after the live test passes.
7. Inspect `https://domestica.au/robots.txt` and confirm it is reachable.
8. Test structured data with Google's Rich Results Test.
9. Create or claim the Google Business Profile for Domestica Hobart.
10. Set the same business name, phone, website, service area, business category, and photos in Google Business Profile.

For local SEO, the Google Business Profile is as important as the website. The website should support the business profile with consistent NAP data: name, address/service area, and phone.

## 7. Bing and Microsoft discovery

1. Create or log in to Bing Webmaster Tools.
2. Add `https://domestica.au/`.
3. Import from Google Search Console if available, or verify manually.
4. Submit `https://domestica.au/sitemap.xml`.
5. Use URL inspection for the homepage.

Bing visibility matters because several AI answer products use Bing or Bing-derived web discovery signals.

## 8. AI search and answer-engine discovery

AI visibility is not a separate ranking system you can directly control. The practical goal is to make the site easy to crawl, understand, cite, and associate with Hobart cleaning and Airbnb management.

This repo now supports that by:

- Serving `llms.txt` at the root.
- Allowing `OAI-SearchBot` in `robots.txt`.
- Keeping the homepage indexable.
- Using clear LocalBusiness and Service schema.
- Keeping canonical, sitemap, Open Graph, and AI-facing summary URLs aligned to `https://domestica.au/`.

Additional off-site work:

1. Make sure Google Business Profile links to `https://domestica.au/`.
2. Add the same website URL to Airbnb host/business profiles where appropriate.
3. Add the website to Apple Business Connect, Bing Places, and relevant Australian local directories.
4. Keep name, phone, and service area consistent everywhere.
5. Ask real customers for Google reviews after completed work.
6. Add real service pages later if you want to rank for separate searches such as `Airbnb cleaning Hobart`, `Airbnb management Hobart`, and `short stay cleaning Hobart`.

## 9. Content improvements to consider next

The current site is a single-page static site. It can rank, but dedicated pages usually give search engines and AI systems clearer evidence for each service.

Recommended future pages:

- `/airbnb-management-hobart/`
- `/airbnb-cleaning-hobart/`
- `/short-stay-turnover-cleaning-hobart/`
- `/general-cleaning-hobart/`
- `/contact/`

Each page should have a unique title, meta description, H1, service details, FAQs, internal links, and service-specific schema.

## 10. Post-launch QA

Run these checks after the DNS is live:

```sh
curl -I https://domestica.au/
curl -I https://www.domestica.au/
curl https://domestica.au/robots.txt
curl https://domestica.au/sitemap.xml
curl https://domestica.au/llms.txt
```

Confirm:

- Homepage returns `200`.
- HTTPS is valid.
- `www` redirects cleanly or serves the canonical site.
- Canonical tag points to `https://domestica.au/`.
- Sitemap URL returns XML.
- Robots file references `https://domestica.au/sitemap.xml`.
- Social preview image URL returns `200`.

## 11. Analytics

Add analytics after launch if not already configured:

1. Google Analytics 4.
2. Google Search Console.
3. Bing Webmaster Tools.
4. Optional: privacy-friendly analytics such as Plausible or Fathom.

Track:

- Organic search clicks.
- Google Business Profile calls and website clicks.
- Contact clicks or form submissions.
- ChatGPT referral traffic, which may include `utm_source=chatgpt.com`.

## 12. Ranking expectations

Changing the domain does not instantly improve rankings. Search engines need to crawl the new domain, process the sitemap, associate the site with the business entity, and compare it against competitors. For a small local service site, first indexing can happen quickly, but meaningful ranking movement often depends on Google Business Profile quality, reviews, citations, content depth, backlinks, and consistency across the web.
