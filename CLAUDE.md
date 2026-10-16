# CLAUDE.md

Personal portfolio site for **D24inc** (Art Levandoski): games, music and books made with AI.

## Stack and hosting

- A single static page: `index.html`, with all CSS inline in a `<style>` block. No JavaScript, no build step, no package manager.
- Hosted on GitHub Pages at `artlevandoski.com` (see `CNAME`). Pushing to `main` deploys.
- Fonts: Google Fonts, Bricolage Grotesque (headings and UI) and Newsreader (body).
- Images live in `images/`, named in kebab-case (`every-night.jpg`).

To preview, open `index.html` in a browser. No server is needed.

## Page structure

In order: a `nav`, then the hero `header` (an inline SVG logo plus the tagline), then `section#projects`, `#music`, `#books` and `#about`, and finally `footer#contact` with the social icons. If you add a new section, add a link to it in the `nav`.

## Conventions

- **Colors:** use the CSS custom properties (`--bg`, `--surface`, `--ink`, `--muted`, `--line`, `--accent`, `--accent-ink`, `--spark`, `--logo`). Don't hard-code colors; the one exception is `#172033`, used as hover text on `--spark`. Dark-mode values are defined twice: under `@media (prefers-color-scheme:dark)` and under `:root[data-theme="dark"]`. When you change a token, update both blocks.
- **Images:** every `<img>` gets descriptive `alt` text and `onerror="this.remove()"`, so a missing file fails gracefully.
- **Typography:** in text, write `&rsquo;` instead of a straight apostrophe.
- **Links:** external links are plain `href`s, with no `target="_blank"`.

## Adding content

**New album** (in `#music` `.grid`). Square art goes in `images/`:
```html
<article class="card">
  <img class="art" src="images/NAME.jpg" alt="Album cover for TITLE: short description" onerror="this.remove()">
  <span class="tag">Album · Suno</span>
  <h3>TITLE</h3>
  <p>The full album, made with Suno.</p>
  <a class="link" href="https://suno.com/playlist/ID">Listen on Suno</a>
</article>
```

**New project** (in `#projects` `.grid`). Use `class="shot"` for a 16:9 screenshot (optional). For MakePlay games, use `class="tag made"` with the MakePlay logo, matching the existing Lane Change! card.

**New book** (in `#books` `.books`): copy the existing `.book` block. The `.cover` shows the title as text when the cover image is missing. Use `p.hook` for the one-line tagline.

## Notes

- `.tracks`, `.play` and `.cover.alt` in the CSS are currently unused, left over from an earlier song-list layout.
