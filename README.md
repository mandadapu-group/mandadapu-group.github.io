# Mandadapu Group at UC Berkeley

A plain Jekyll site designed for a clean, old-school academic group page. It uses a shared layout with includes and minimal CSS. No third-party themes or plugins are used.

**Approach**
- Plain Jekyll layouts + includes (`_layouts/default.html`, `_includes/nav.html`).
- Minimal, readable CSS in `assets/style.css`.
- Two-column layout with a left navigation sidebar.

**Structure**
- `_config.yml` contains only the essential site settings.
- `_layouts/default.html` defines the sidebar + main content layout.
- `_includes/nav.html` holds the navigation links.
- `assets/style.css` holds all styling.
- Top‑level `.md` files are pages (`index.md`, `people.md`, etc.).

**Edit Navigation**
- Update links in `_includes/nav.html`.
- Keep URLs relative and prefixed with `{{ site.baseurl }}` for GitHub Pages compatibility.

**Add a New Page**
1. Create a new `.md` file at the repo root.
2. Add front matter with `layout: default` and `title: Your Page Title`.
3. Add a link in `_includes/nav.html`.

**GitHub Pages Build**
- GitHub Pages typically builds from the `master` branch and the repository root for user/organization sites.
- The workflow in `.github/workflows/jekyll-docker.yml` runs `jekyll build` in a Docker container on pushes to `master` as a build check (it does not deploy).
- No unsupported plugins are used, so the site is GitHub Pages compatible.

**Local Preview (Bundler)**
- Use a modern Ruby (rbenv/asdf recommended; avoid macOS system Ruby).
- `bundle install`
- `bundle exec jekyll serve`

**Docker Preview**
- `docker run --rm -it -p 4000:4000 -v "$PWD":/srv/jekyll -w /srv/jekyll jekyll/jekyll:pages jekyll serve --host 0.0.0.0`

**Notes**
- `Gemfile.lock` is not tracked to avoid Bundler/Ruby version pinning issues; GitHub Pages uses its own pinned versions during deployment.
