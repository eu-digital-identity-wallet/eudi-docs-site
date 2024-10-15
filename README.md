# eudi-doc-developers-hub-site

This guide will help you quickly get started with MkDocs.

## Installation

To install MkDocs, use `pip`:

```bash
pip install mkdocs mkdocs-multirepo-plugin mkdocs-material pymdown-extensions
```

## Serving the Documentation

To view your documentation locally, navigate to the project directory and run:

```bash
mkdocs serve
```
Your documentation will be available at http://127.0.0.1:8000/ in your browser.

## Deploy on Github pages

MkDocs has built-in support for deploying to GitHub Pages.

```bash
mkdocs gh-deploy
```
This command will automatically push the contents of the site/ directory to the gh-pages branch of your repository.
The site will be available at https://<.username.>.github.io/<.repository.>/.

## Configuration

The configuration file for MkDocs is mkdocs.yml, where you can customize the site name, theme, and other settings.
