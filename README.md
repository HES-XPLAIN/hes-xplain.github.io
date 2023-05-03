# website

Website for HES-XPLAIN - An open platform for accelerating the development of eXplainable AI systems

## Contribution

The website is built with [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/),
allowing the actual content to be entirely written with [Markdown](https://www.markdownguide.org/).

### Install Python and Poetry

* Install [Python](https://www.python.org/).
* Install [poetry](https://python-poetry.org/docs/#installation) and add it to your PATH.

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
