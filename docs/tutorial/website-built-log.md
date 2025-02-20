---
date: 2025-01-19
authors:
  - luomein
categories:
  - website
description: >
  GitPage and Material for MkDocs
---

# Website Built Log

I use the framework of `Material for MkDocs` and host my website on `GitPage`.

<!-- more -->

I follow the tutorial provided by [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/getting-started/)

## Set Up The GitPage

### Import Material for MkDocs sample website to my GitHub repo

In GitHub, when creating new repo, you can import an existing one on the Internet.

Here is the direct link to [Import your project to GitHub](https://github.com/new/import).

I think it is `git clone` on the cloud.

```
git clone https://github.com/squidfunk/mkdocs-material.git
```

### Create a new GitHub Action workflow to automate the website deployment

[Use the sample file, `ci.yml` provided by Material for MkDocs](https://squidfunk.github.io/mkdocs-material/publishing-your-site/#with-github-actions). Put the file in the path of .github/workflows/ci.yml 

### Solve website built issue

When the `ci` GitHub Action triggered, it will build the website. But there is an error related with the plugin, `minify`. So I marked it out in the `mkdocs.yml`.

```
# Plugins
plugins:
  - blog
  - search:
      separator: '[\s\u200b\-_,:!=\[\]()"`/]+|\.(?!\d)|&[lg]t;|(?!\b)(?=[A-Z][a-z])'
#  - minify:
#      minify_html: true

```

* 2025/02/20 updated

    Alternative way to fix this issue: Make sure `mkdocs-minify-plugin` is in the requirements.txt. And make sure in the Git Action, every time the website is deployed, `pip install -r requirements.txt` is called.

### Configure GitPage

In the settings of the GitHub repo, under `Pages` section,

* source: Deploy from a branch

* Branch: gh-pages

* Folder: /(root)

## Set Up Local Working Environment

### Create Python Virtual Environment	

```
python -m venv my-env
```
### Activate the Virtual Environment

```
source my-env/bin/activate
```
### Install Material for MkDocs in the Virtual Environment

```
pip install mkdocs-material
```

### Clone my repo from GitHub

```
git clone git@github.com:luomein/spectrum-log.git
```

### Run the Website locally

Under the virtual environment and in the root folder of the git project, run the command,

```
mkdocs serve
```
or
```
mkdocs serve -a 127.0.0.1:8001
```
