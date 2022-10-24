# Welcome to the MkDocs Template

[![Publish MkDocs via GitHub Pages](https://github.com/lnnrtwttkhn/mkdocs-template/actions/workflows/main.yml/badge.svg)](https://github.com/lnnrtwttkhn/mkdocs-template/actions/workflows/main.yml)

## About

!!! tip "Delete the contents of this page"
    If you use this template for your own project documentation or group wiki, you might want to delete all the contents from this landing page.

## Getting Started :sparkles:

On the [main GitHub repository website](https://github.com/lnnrtwttkhn/mkdocs-template) click on the green `Use this template` button (or click [here](https://github.com/lnnrtwttkhn/mkdocs-template/generate)).

1. Choose the **owner** of the new repository (mandatory):
This can be your personal GitHub account (e.g., in my case `lnnrtwttkhn`) or the account of your organization (e.g., your research group).
Note that you already need to be a member of your organization to be able to create a new repository in your organization's account.
2. Choose a **repository name** (mandatory):
You are free to choose any repository name that does not already exist in your or your orgamization's GitHub account.
For example, if you are creating a documentation for your research group, you could name the repository `lab-docs`.
3. Add a short **description** of your repositoy (optional).
For example, if you are creating a documentation for your research group, you could write something like "Documentation of the Example Lab at Example University".
4. Choose if your repository should be **public** (anyone on the internet can see the contents of your repository but you choose who can edit) or **private** (you choose who can see and edit the contents of your repository).
5. **Include all branches**: If you enable this option, *all* branches of the `mkdocs-template` repository will be included in your repository (for a list of all branches, click [here](https://github.com/lnnrtwttkhn/mkdocs-template/branches)).
I recommend to **not** include all branches
6. Click the green `Create repository from template` button

Done! :tada:

A new repository for your documentation based on the the template should be created within a few seconds.
You will notice that all the files in the template repository have been added as one `Initial commit`.
Now you can start adding your changes.

## Deployment

### Deployment to GitHub Pages using GitHub Actions

Immediately after you create the new repository, a GitHub Actions workflow should trigger the build of the documentation website (you can check in the `Actions` tab on the repository's main GitHub page).
However, the website is not yet deployed to GitHub Pages, meaning that it is not yet available on the internet.

!!! warning "GitHub Pages sites built from private repositories are still public!"
    Unless you are on one of GitHub's paid plans, GitHub Pages sites published from a private repository are public!
    Once you enabled deployment (see instructions below), GitHub will also alert you to this fact in the `Pages` menu option under the `Settings` tab of your GitHub repository:
    > Caution: This repository is private but the published site will be public.

To enable deployment to GitHub Pages, follow these instructions:

1. On your repository main page, click on the `Settings` tab.
2. In the menu bar, click on `Pages`.
3. In the section `Build and deployment` select the `Source` option `Deploy from a branch`.
4. For the `Branch` option select `gh-pages`, keep `/(root)` and confirm with `Save`.

Once you clicked `Save` you can set the additional option to **enforce HTTPS**.
GitHub explains this option as follows:

> HTTPS provides a layer of encryption that prevents others from snooping on or tampering with traffic to your site.
> When HTTPS is enforced, your site will only be served over HTTPS. [Learn more](https://docs.github.com/en/pages/getting-started-with-github-pages/securing-your-github-pages-site-with-https).

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.
