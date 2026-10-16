# reelmark.fish

The website for ReelMark, the California ocean sport fishing regulations app.
Plain HTML and CSS served by GitHub Pages from the `main` branch root, with no
build step, frameworks or scripts. Fonts come from Google Fonts.

| File | What it is |
| --- | --- |
| `index.html` | Landing page. Edit by hand. |
| `privacy.html` | Privacy Policy. **Generated, do not edit.** Served at reelmark.fish/privacy. |
| `terms.html` | Terms of Use. **Generated, do not edit.** Served at reelmark.fish/terms. |
| `assets/style.css` | The one stylesheet for every page, with brand colors from the app's `mobile/src/constants/theme.ts` and a dark-mode palette. |
| `assets/` | Logo and icons cut from `mobile/src/assets` in firstcast-mvp, plus `contours.svg` (the chart-line background). |
| `CNAME` | The custom domain, `reelmark.fish`. |
| `.nojekyll` | Tells Pages to serve the files as they are. |

## Privacy and Terms are generated

The legal text lives in the app repo (firstcast-mvp) as markdown:
`memory/privacy_policy.md` and `memory/terms_of_use.md`. Those files are the
single source of truth for both this site and the app's in-app Legal screen.
To change the policy, edit the markdown there, then regenerate:

```bash
cd ~/Documents/GitHub/firstcast-mvp
python3 scripts/publish_site.py ~/Documents/GitHub/reelmark-site
python3 scripts/legal_to_ts.py
```

The first command rewrites `privacy.html` and `terms.html` here; the second
rewrites the app's `mobile/src/content/legal.ts`. Commit both repos. The
generated pages keep the headings and the "Last updated" date from the
markdown, so update that date when the text changes.

The page header and footer for the legal pages live in
`scripts/publish_site.py`. If you change the header or footer in
`index.html`, change them there too.

## Join the beta link

The "Email us to join the beta" button in `index.html` is a `mailto:` link to
support@reelmark.fish with the subject "ReelMark beta". When there is a public
TestFlight link, replace that `href` (there is a comment next to it).

## Preview locally

```bash
python3 -m http.server 8080 --directory ~/Documents/GitHub/reelmark-site
```

Then open http://localhost:8080.
