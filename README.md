# flaviomalagutti.com

Personal academic website. Plain HTML and one CSS file — no build step, no dependencies.

## Files

```
index.html            Home (hero, bio, selected research)
research.html         Working papers, publications, work in progress
presentations.html    Recorded talks
teaching.html         Courses and student feedback
assets/site.css       All styling (design tokens at the top)
assets/hero.jpg       Hero photograph
assets/portrait.jpg   Portrait
assets/Malagutti_CV.pdf   CV, served from this domain
CNAME                 Custom domain for GitHub Pages
.nojekyll             Serve files as-is, no Jekyll processing
```

## Editing

Adding a paper means copying an `<article class="entry">` block in `research.html`
and changing the text. The `insight` block is optional but it is the thing
people remember, so keep writing them.

Colors, fonts and spacing all come from the CSS custom properties in the
`:root` block at the top of `assets/site.css`. Change them there, not inline.
There is a matching `prefers-color-scheme: dark` block right below it.

## Preview locally

```bash
python3 -m http.server 8765
```

Then open http://localhost:8765.

## Deploy (GitHub Pages)

1. Create a public repo on GitHub and push this folder to `main`.
2. Repo → Settings → Pages → Source: "Deploy from a branch", branch `main`, folder `/ (root)`.
3. Settings → Pages → Custom domain: `www.flaviomalagutti.com`, and tick "Enforce HTTPS".
4. At the domain registrar, replace the current Google Sites records with:
   - `CNAME` record, host `www`, value `<github-username>.github.io`
   - Four `A` records for the apex `flaviomalagutti.com` pointing at
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
     (or an `ALIAS`/`ANAME` to `<github-username>.github.io` if the registrar supports it)

DNS takes anywhere from a few minutes to a few hours to propagate. Keep the
Google Sites version up until the new one resolves.
