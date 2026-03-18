# northharbor.dev

Public website for [NorthHarbor Development](https://northharbor.dev) — the open source org for principled human-AI collaboration tools.

Live at **[northharbor.dev](https://northharbor.dev)**

## Local Development

```bash
bundle install
bundle exec jekyll serve
```

Site runs at `http://localhost:4000`.

## Deployment

Deployed via GitHub Pages from the `main` branch. The `CNAME` file points to `northharbor.dev`.

## Structure

```
_layouts/default.html    # Base layout (nav, footer, content slot)
_includes/project-card.html  # Reusable project card partial
assets/style.css         # Site stylesheet (derived from HALOS design language)
index.md                 # Homepage
about.md                 # About page
CNAME                    # Custom domain
```

## Blueprint Usage

This repo can serve as a starting point for new NorthHarbor product sites:

1. Fork or copy this repo
2. Update `_config.yml` — title, description, URL
3. Update `CNAME` — your subdomain (e.g., `yourproject.northharbor.dev`)
4. Adjust CSS tokens in `assets/style.css` — accent colors, gradients
5. Replace nav links in `_layouts/default.html`
6. Replace content in `index.md` and add pages as needed

## License

Content and code in this repository are licensed under [CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/).
