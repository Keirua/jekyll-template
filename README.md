# Jekyll template

Jekyll is a static website generator. It is flexible and easy to use, and one of its best benefits is that you can use CD tools provided by code hosting platforms such as GitHub Pages or GitLab Pages to make the built website available on the internet, at no cost.


## Features / Choices

This template aims at making it easier to use Jekyll to:

- **Publish websites** or at least landing pages, not blogs.
- **Get contributions from non-technical users**, purely with online code editors.
- **Build upon convention** rather than configuration.
- **Display page metadata**.

In order to achieve these goals, it provides:

1. Version lockdown of the entire stack, with guaranteed synchronisation with GitHub Pages production versions.
2. Pre-configured CI.
3. Auto-filled [meta tags for “social cards”](https://gist.github.com/MattiSG/fc7f65ad16fb8968e0f84b756efd9383) (content preview on major social media).


## Install Ruby with `rbenv`

We'll use `rbenv` to make sure that the Ruby version is the same across all environments.

### Install rbenv

For that, we'll start by [installing rbenv](https://github.com/rbenv/rbenv#installation). Make sure you read all the instructions and go through the `rbenv init` stage, otherwise it will not work!

> The alternative to rbenv is RVM. If you have it already installed on your system, or you prefer to use it for any reason, there is no need to switch to rbenv.

### Specify the Ruby version

Since we want to make sure that we use the same version of all dependencies and runtimes across all environments, and the only one we can't control is the one chosen by GitHub, we'll align all environments with that one. Thus, we'll get the Ruby version we want to use from their published [versions file](https://pages.github.com/versions.json).

The [`.ruby-version` file](https://github.com/rbenv/rbenv#choosing-the-ruby-version) should contain the… version of Ruby we want to use. In our case, that version is given in the `ruby` key of GitHub’s [versions file](https://pages.github.com/versions.json).

## Install Jekyll

We could install Jekyll with `gem`. However, we wouldn't know if later on GitHub updates their versions, and that could yield a conflict later on.

```
gem install bundler --no-ri --no-rdoc
bundle install
```

We can then test that everything went well with:

```
bundle exec jekyll doctor
```

## Set up your website

Edit the `_config.yml` to ensure the metadata matches your setup.

Replace `logo.png` with your own.

You can edit locally with the following options:

```
bundle exec jekyll serve --incremental --watch --safe --strict_front_matter
```

- `incremental` and `watch` improve your developer experience.
- `safe` mirrors GitHub Pages' setup.
- `strict_front_matter` allows to catch errors early.

### Change the menu

In order to avoid mixing content files with config & dev files, pages are never created at the root: they all get written in collections. In order to add a page to the menu, you can simply add it to `_toplevel`, as long as you set its URL with `permalink`. Prefix their filename with the index at which you'd like them to appear in the menu. The first one (by convention, index `0`) will appear on the left handside of the menu, along with your website logo.


## Publish to GitHub Pages

- Create a repository on GitHub.
- Push your content to it.
- Activate GitHub Pages in the settings.


## Set up Continuous Integration

We'll use [CircleCI](https://circleci.com). They offer a free plan for open-source.
Just log in with GitHub and activate builds for your repository.


## Edit content

### Markdown

- [Syntax reference](https://www.markdownguide.org/basic-syntax).
- [Tutoriel en français](https://openclassrooms.com/fr/courses/1304236-redigez-en-markdown).
