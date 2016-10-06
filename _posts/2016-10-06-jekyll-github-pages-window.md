---
layout: post
title: Run Jekyll on Windows and Deploy to GitHub Pages
---

# Introduction
[Jekyll][jekyll-link] is static website generation tool built on Ruby. This article will describe how to install Jekyll using a Windows operating system, build a website locally, and deploy it to GitHub pages.

# Install Jekyll
Although Jekyll does not officially support Window, it is relatively straightforward to install. Jekyll depends on Ruby. There are a few different ways to do this on Windows - one simple approach is to use the [Chocolatey](Chocolatey) package manager.

1. Using an elevated command prompt, [install Chocolatey](https://chocolatey.org/install).
2. Install [Ruby](https://www.ruby-lang.org/en/) using `choco install ruby -y`.
3. Install [Jekyll][jekyll-link] using `gem install jekyll`.

You can verify that Jekyll is correctly installed by running `jekyll` at the command prompt.

> Tip: With Chocolatey installed, you can run `refreshenv` at the command line to quickly reload environment variables.

# Create a Website
This article will not go in depth on how to create a website with Jekyll. This topic is covered extensively on the [Jekyll Documentation](https://jekyllrb.com/docs/). However, for demonstration, a few simple commands will get us up and running.

1. Use `jekyll new my-website` to create a website.
2. Use `jekyll serve` to run a development server at `localhost:4000`. This will command will build the website and watch the directory for changes.

# Deploy Using GitHub Pages
[GitHub Pages](https://pages.github.com/) is a service that allows websites to be hosted directly from GitHub repositories. The version of Jekyll against which a website is built on GitHub pages may not be the current release version. To avoid unexpected issues, we can use the [GitHub Pages Ruby Gem](https://github.com/github/pages-gem) to maintain a local development environment in sync wit GitHub Pages.

1. In your projects Gemfile, comment out the line `gem "jekyll", "3.2.1"`.
2. Add a new line `gem "github-pages", group: :jekyll_plugins`.
3. Run `bundle update github-pages` to install the latest version of the Gem.
4. Use `jekyll serve` as usual for local development, now in sync with GitHub Pages.

# Troubleshooting

**Missing Bundles**

TODO: Describe using bundle install to include missing dependencies. Is this a bug with the latest Jekyll version?

**GitHub Pages Gem**

TODO: I encountered some issues setting up GitHub Pages on my local machine. Include cacert.pem and generating a GitHub token.

http://stackoverflow.com/questions/38133562/cant-preview-github-pages
https://www.hieule.info/programming/fix-errors-github-metadata-ssl-certificate-running-jekyll-serve/


[jekyll-link]: https://jekyllrb.com/
