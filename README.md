# giacomogonella.github.io

Personal academic website, served by GitHub Pages. Plain HTML/CSS, no build step:
push to `main` and the site updates at <https://giacomogonella.github.io>.

## Structure

```
index.html        all content (the only file you'll usually edit)
styles.css        all styling
images/avatar.jpg profile photo
images/svgs/      social icons
posters/          poster PDFs, linked from publications
assets/cv.pdf     CV, linked from the nav button
```

## Common edits (all in `index.html`)

### Add a news item

Add a new `<li>` at the **top** of the list in `<section id="news">`:

```html
<li>
  <span class="news-date">Jun 2026</span>
  <span class="news-body">
    Something happened, with an optional <a href="https://...">link</a>.
  </span>
</li>
```

### Add a publication

Copy an existing `<li class="pub-item">` in `<section id="publications">` and edit it.
Each entry has:

- `pub-title` — the title, plus a badge: `<span class="venue-badge">Preprint</span>`
  for arXiv, or `<span class="venue-badge venue-conf">EACL 2026</span>` (teal) for an
  accepted paper.
- `pub-authors` — your name wrapped in `<strong>`.
- `pub-meta` — CV-style venue line, e.g.
  `In <em>Findings of ACL: EACL 2026</em>, pp.&nbsp;6657–6677, Rabat, Morocco. ACL.`
- `pub-links` — pill buttons (`<a class="btn">`) for Paper / Poster / etc., plus the
  BibTeX toggle button.
- `bibtex-box` — the BibTeX entry inside `<pre><code>...</code></pre>`. Keep this
  `<div>` **immediately after** `pub-links`: the toggle script finds it via
  `nextElementSibling`.

When a preprint gets accepted: change the badge to `venue-badge venue-conf` with the
venue name, update `pub-meta`, and replace the BibTeX with the official one.

### Add a poster

Drop the PDF in `posters/` and add a button to that publication's `pub-links`:

```html
<a class="btn" href="posters/file-name.pdf" target="_blank" rel="noopener">Poster</a>
```

### Update the CV

Replace `assets/cv.pdf` (keep the same filename, no edits needed).

### Update the photo

Replace `images/avatar.jpg`. Keep it roughly square and under ~300 KB.

## Conventions

- Affiliation order: **FBK first**, then University of Trento.
- Colors and fonts are CSS variables / Google Fonts set at the top of `styles.css`
  (accent: `--accent: #1f6f78`; fonts: Newsreader for headings, Inter for body).

## Preview locally

```bash
python3 -m http.server
# open http://localhost:8000
```
