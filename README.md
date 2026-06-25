# eudi-docs-site

This repository contains the documentation for the Reference Implementation of the EU Digital Identity Wallet project, built with [MkDocs](https://www.mkdocs.org/) and the [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) theme.

Take a look at [docs.eudi.dev](https://docs.eudi.dev/latest/) to check the published docs.

## Prerequisites

- Python 3.x and pip

## Local build

Install required plugins (take a look at the [mkdocs.yml](mkdocs.yml) file for reference on the required plugins):

```bash
pip install mkdocs "mkdocs-material[imaging]" mike
```

Then, serve locally:

```bash
mkdocs serve
```

The local deployment will be available at [http://127.0.0.1:8000/](http://127.0.0.1:8000/).

## Deploy (GitHub Pages)

If you want, you could deploy directly from the local machine to a remote `gh-pages` branch using the following command:

```bash
mkdocs gh-deploy
```

however, it is recommended to use a proper Continuous Integration chain to do so.