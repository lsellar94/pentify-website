# Pentify Insights website

Static site exported from the redesign. Plain HTML, CSS and a little JavaScript, with no build step.

## Structure

| URL | File |
|---|---|
| `/` | `index.html` |
| `/services/` | `services/index.html` |
| `/partners/` | `partners/index.html` |
| `/about/` | `about/index.html` |
| `/assessment/` | `assessment/index.html` |
| `/blog/` | `blog/index.html` |
| `/blog/<post>/` | `blog/<post>/index.html` (same URLs as the old Squarespace posts) |

Also included:

- `assets/` holds the logos, client logos and headshots.
- `_redirects` sends old Squarespace URLs to the new pages with permanent (301) redirects.
- `404.html`, `robots.txt` and `sitemap.xml`.
- `netlify.toml` holds the hosting settings.

## Deploying on Netlify

1. **Without GitHub:** go to app.netlify.com/drop and drag this whole folder onto the page.
2. **With GitHub:** put these files in the root of the `pentify-website` repository, then in Netlify choose *Add new site → Import an existing project*. There's no build command, and the publish directory is the repository root.
3. Netlify gives you a temporary `*.netlify.app` address. Test everything there first.

## Forms

The newsletter sign-up on the homepage and the assessment lead form both use **Netlify Forms**. Netlify detects them automatically on deploy, and submissions appear under *Site → Forms*. Set up email notifications under *Forms → Form notifications*.

## Going live (Azure DNS)

In Netlify, go to *Domain management* and add `pentifyinsights.com` and `www.pentifyinsights.com`. Then, in Azure DNS:

- Change the `www` CNAME from `ext-cust.squarespace.com` to your `*.netlify.app` address.
- Replace the four Squarespace A records on the root domain with the one Netlify gives you.
- **Do not touch** the MX, SPF, DMARC or verification TXT records. They run your Microsoft 365 email.

Netlify issues the HTTPS certificate automatically. Once the site is live, cancel Squarespace.

## Analytics

There's a placeholder comment in each page's `<head>`. Paste the GA4 tag there.
