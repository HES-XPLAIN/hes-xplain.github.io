# HES-XPLAIN Website

Website for HES-XPLAIN - An open platform for accelerating the development of eXplainable AI systems

## Contribution

The website is built with [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/),
allowing the actual content to be entirely written with [Markdown](https://www.markdownguide.org/).

### Install Python and Poetry

- Install [Python](https://www.python.org/).
- Install [poetry](https://python-poetry.org/docs/#installation) and add it to your PATH.

Ensure `python` and `poetry` are accessible in the `$PATH` environment variable.

To check the installation, check the following commands return an output:

```shell
python --version
poetry --version
```

Install python dependencies and activate the virtualenv:

```shell
poetry install
poetry shell
```

To serve the model locally:

```shell
mkdocs serve
```

And connect your browser at http://127.0.0.1:8000/ to visualize it.

## Customization

### Theme

The theme is partially customized in the `mkdocs.yml` file. The modified variables are found in the `docs/assets/stylesheets/custom.css` file.

### HTML Templates

The customizations of the homepage are done in the `material/overrides` folder.

- `material/overrides/main.html` extends the `base.html` template from MkDocs Material.
- `material/overrides/home.html` is the template for the homepage.

> Note: The styles in `material/overrides/home.html` depend on the theme names defined in `mkdocs.yml`.

The `material/overrides/home.html` is specified in the `docs/index.md` file:

```markdown
---
template: overrides/home.html
---
```

You can add your own customizations in the `material/overrides` folder. See the [MkDocs Material documentation](https://squidfunk.github.io/mkdocs-material/customization/#template-overrides) for more details.

You can also look how the [MkDocs Material homepage](https://github.com/squidfunk/mkdocs-material) is built.
