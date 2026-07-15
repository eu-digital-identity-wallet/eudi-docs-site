# eudi-docs-site

Source for the **EUDI Wallet Reference Implementation** documentation portal published at
[docs.eudi.dev](https://docs.eudi.dev). The site is built with
[MkDocs](https://www.mkdocs.org/) and the
[Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) theme, and is
versioned with [mike](https://github.com/jimporter/mike).

Documentation content lives in [`docs/`](docs/). The navigation, theme and plugins are
configured in [`mkdocs.yml`](mkdocs.yml); brand styling lives in
[`docs/css/extra.css`](docs/css/extra.css).

## Prerequisites

- Python 3.x
- The [`cairo`](https://www.cairographics.org/) system library, required by the social-card
  plugin (`brew install cairo` on macOS; `apt-get install libcairo2` on Debian/Ubuntu).

## Local development

Install the pinned toolchain and serve the site with live reload:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
mkdocs serve
```

The site is then available at <http://127.0.0.1:8000/>.

To produce a static build in `site/` (the same command CI runs on pull requests):

```bash
mkdocs build
```

## Deployment

Deployment is automated — **do not run `mkdocs gh-deploy` manually**.

On every push to `main`, the [Deploy to Pages](.github/workflows/pages.yml) GitHub Actions
workflow uses `mike` to publish the built site to the `gh-pages` branch under the `latest`
alias, which serves [docs.eudi.dev](https://docs.eudi.dev). The workflow can also be
triggered manually from the Actions tab or via a `repository_dispatch` event of type
`trigger-build`.

## Contributing

Every page has an **Edit** link (pencil icon) that points to its source under `docs/`.
When adding or moving a page, update the `nav:` tree in `mkdocs.yml` accordingly. Please
run `mkdocs build` locally and confirm it completes without warnings before opening a pull
request.

## Licence

Content is licensed under the [CC-BY-4.0](LICENSE.md) or later, © European Union, 2026.
