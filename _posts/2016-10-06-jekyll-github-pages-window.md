---
layout: post
title: Run Jekyll on Windows and Deploy to GitHub Pages
---

# Introduction
[Jekyll][jekyll-link] is static website generation tool built on Ruby. This article will describe how to install Jekyll using a Windows operating system, create and run a website locally, and deploy it to GitHub pages.

# Install Jekyll
Although Jekyll does not officially support Window, it is relatively straightforward to install. Jekyll depends on Ruby. There are a few different ways to install Ruby on Windows - one simple approach is to use the [Chocolatey](Chocolatey) package manager.

1. Using an elevated command prompt, [install Chocolatey](https://chocolatey.org/install).
2. Install [Ruby](https://www.ruby-lang.org/en/) using `choco install ruby -y`.
3. Install [Jekyll][jekyll-link] using `gem install jekyll`.

You can verify that Jekyll is correctly installed by running `jekyll` at the command prompt.

> Tip: With Chocolatey installed, you can run `refreshenv` at the command line to quickly reload environment variables.

# Create a Website
This article will not go in depth on how to create a website with Jekyll a topic which is covered extensively in the [Jekyll Documentation](https://jekyllrb.com/docs/). However, for demonstration, a few simple commands will get us up and running.

1. Use `jekyll new my-website` to create a website.
2. Use `jekyll serve` to build the website and watch the directory for changes. You can view the built website at `localhost:4000`.

# Deploy Using GitHub Pages
[GitHub Pages](https://pages.github.com/) is a service that allows websites to be hosted directly from GitHub repositories. The version of Jekyll against which a website is built on GitHub pages may not be the current release version. To avoid unexpected issues, we can use the [GitHub Pages Ruby Gem](https://github.com/github/pages-gem) to maintain a local development environment in sync wit GitHub Pages.

1. In your projects Gemfile, comment out the line `gem "jekyll", "VERSION"`.
2. Add a new line `gem "github-pages", group: :jekyll_plugins`.
3. Run `bundle update github-pages` to install the latest version of the gem.
4. Use `jekyll serve` as before for development.

Your website will now be built to the same configuration as GitHub Pages. Deployment is as simple as pushing your changes to the [correct branch](https://help.github.com/articles/user-organization-and-project-pages/).

# Troubleshooting

I'm a Jekyll and Ruby novice. Below are the resolutions to some issues that I encountered which may also be of help to others.

**GitHub Pages Gem**

After switching to the GitHub Pages gem, Jekyll failed with two errors - missing GitHub API Authentication and missing SSL Certs. I discovered a resolution to these issues in [Chris' post](http://knightcodes.com/miscellaneous/2016/09/13/fix-github-metadata-error.html).

To resolve the GitHub API Authentication issue:

1. Create a GitHub access token as described in the [documentation](https://help.github.com/articles/creating-an-access-token-for-command-line-use/).
2. Assign the token value to a system environment variable named `JEKYLL_GITHUB_TOKEN`.

To resolve the SSL Certs issue (do not do this anywhere other than a development machine):

1. Download the contents of [this](https://curl.haxx.se/ca/cacert.pem) PEM file.
2. Assign the path of the file to a system environment variable named `SSL_CERT_FILE`.

**Multiple Version of the Same Gem**

Ruby may give out if their are multiple versions of the same gem installed. There are two ways around this. One is to remove all but one version of the offending gem. The other is to use the [bundler](http://bundler.io/) gem which can manage dependencies for you. Using `bundle exec jekyll serve` will solve dependency issues here.

**Chocolatey Config Access Denied**

I encountered this issue after installing Chocolatey and attempting to run `choco` for the first time. It could not access the `C:\ProgramData\chocolately\config` directory. This occurred as a result of the default security settings for `C:\ProgramData`. The simplest workaround is to run `choco` once from an elevated command prompt to create the config file.

**Missing Gems**

Jekyll may complain about missing gems. To fix this issue, run `gem install BUNDLE` for each required gem.

[jekyll-link]: https://jekyllrb.com/
