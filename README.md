# Hasmitha Vasireddy, Portfolio

A single-page portfolio site (plain HTML/CSS/JS, no build step) built from
`Vasireddy_Hasmitha_Resume.pdf`, `Profile.pdf`, and the `Knowledge bank/`
achievements record. Palette matched to her LinkedIn banner: peach-to-lavender
gradient, deep indigo, gold accent.

## Structure

```
portfolio/
├── index.html              # the whole site
├── robots.txt               # search engine crawl rules
├── sitemap.xml               # search engine sitemap
├── assets/
│   ├── css/style.css       # theme + layout
│   ├── js/main.js          # nav toggle + scroll reveal
│   ├── images/
│   │   └── og-cover.jpg    # social share preview image
│   └── resume/
│       └── Hasmitha_Vasireddy_Resume.pdf   # kept locally only, see below
├── Vasireddy_Hasmitha_Resume.pdf   # your original source file
├── Profile.pdf                     # your original source file
└── Knowledge bank/                 # your source material, not linked from the site
```

`Knowledge bank/` contains internal career-prep material (interview bibles,
client names, unrounded numbers). It is not referenced anywhere in the site.

**Your résumé PDF is not public.** The hero originally had a "Download Résumé"
button; it now links to LinkedIn instead, and `assets/resume/` plus the two
root-level PDFs are excluded via `.gitignore` so they never get pushed. If you
ever want a downloadable résumé on the live site again, host the PDF somewhere
you control (e.g. a Google Drive link with "anyone with the link" sharing) and
point a button at that URL instead of committing the file to this repo.

## Before you publish: update the placeholder domain

`index.html`, `robots.txt`, and `sitemap.xml` all reference a placeholder URL,
`https://hasmithavasireddy.github.io/`. Once you know your actual GitHub Pages
URL (see step 5 below), find and replace that placeholder in those three
files so the canonical link, Open Graph tags, and sitemap all point to the
real address.

## Publish it with GitHub Pages

1. Create a new repository on GitHub (e.g. `hasmithavasireddy.github.io` for a
   root domain site, or any name like `portfolio` for a project site).
2. A `.gitignore` is already set up in this folder excluding `Knowledge bank/`,
   both source PDFs, and `assets/resume/`, so none of that gets pushed.
3. From this folder:
   ```bash
   git init
   git add index.html robots.txt sitemap.xml assets README.md
   # or `git add .` if you're fine publishing everything
   git commit -m "Initial portfolio site"
   git branch -M main
   git remote add origin <your-repo-url>
   git push -u origin main
   ```
4. On GitHub: **Settings → Pages → Build and deployment → Source → Deploy
   from a branch**, branch `main`, folder `/ (root)`. Save.
5. Your site goes live at:
   - `https://<username>.github.io/` if the repo is named `<username>.github.io`
   - `https://<username>.github.io/<repo-name>/` otherwise
6. Update the placeholder domain (see above) to match, commit, and push again.
7. Optional but recommended for search visibility: submit the site in
   [Google Search Console](https://search.google.com/search-console) once it
   is live, pointing at your `sitemap.xml`.

GitHub Pages usually takes a minute or two to build after the first push.

## SEO already set up

- Descriptive `<title>` and meta description
- `robots.txt` and `sitemap.xml`
- Open Graph and Twitter Card tags, with a matching `assets/images/og-cover.jpg`
  preview image for link shares (LinkedIn, Twitter/X, Slack, iMessage)
- JSON-LD structured data (`schema.org/Person`) describing your role, skills,
  and profile links, so search engines can understand the page beyond plain text
- Single `<h1>`, one `<h2>` per section, semantic `<section>`/`<article>` tags

## Customizing later

- **Headshot / photo**: drop an image into `assets/images/` and add an
  `<img>` in the `.hero-inner` or `.about-aside` block in `index.html`.
- **Colors**: all theme colors are CSS variables at the top of
  `assets/css/style.css` (`:root { --navy, --rose, --gold, --peach, --lavender, ... }`).
- **Content**: all copy lives directly in `index.html`, organized by section
  (`#about`, `#principles`, `#experience`, `#work`, `#skills`, `#education`, `#contact`).
- **Phone number**: intentionally left off the public contact section for
  privacy. Add it back in the `#contact` section if you want it listed.
- **Social preview image**: `assets/images/og-cover.jpg` was generated to
  match the site's palette. Regenerate it any time by editing the SVG source
  used to build it, or replace it with a screenshot of your own.
