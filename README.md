# Oceanology MkDocs

Documentation site for Oceanology built with MkDocs and Material theme.

## Setup

1. Have python 3 installed [here](https://www.python.org/downloads/) and Clone this repository

2. Create and activate a virtual environment (recommended):
```
python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
```
or
```
pip install -r requirements.txt
```

## Local Development

To start the development server:
```
mkdocs serve
```
This will start a local server at `http://127.0.0.1:8000`. The site will automatically reload when you make changes to the content.

## Building the Site

To build the static site:
```
mkdocs build
```
This will create a `site` directory containing the built static site.

## Deployment

To deploy to GitHub Pages:


For latest (x.x.x)
```
mike deploy --push --update-aliases vx.x.x latest
```

For non latest (x.x.x)
```
mike deploy --push --update-aliases vx.x.x
```

Set latest (only once)
```
mike set-default --push latest
```
mkdocs deploy command but we are using versioning so avoid this command.
```
mkdocs gh-deploy --force
```
This command builds the documentation and pushes it to the `gh-pages` branch of your repository. The `--force` flag ensures the `gh-pages` branch is overwritten with the new content.

Make sure your repository settings have GitHub Pages configured to serve from the `gh-pages` branch.

## Project Structure

```
mkdocs.yml    # The configuration file
```

### Made with ❤️ and ☕

These docs are made with love and fueled by coffee.
