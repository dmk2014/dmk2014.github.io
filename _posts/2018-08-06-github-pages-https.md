---
layout: post
title: Setup HTTPS with GitHub Pages
---

[GitHub Pages](https://pages.github.com) allows websites to be hosted directly from GitHub repositories. Recently, the team at GitHub [added support for HTTPS](https://blog.github.com/2018-05-01-github-pages-custom-domains-https/) to custom domains that are hosted using GitHub Pages. The certificates used are provided free of charge by [Let's Encrypt](https://letsencrypt.org).

Setting up a custom domain for HTTPS is straightforward, though a little different from previous GitHub Pages configurations. I decided to use the apex domain `darrenkeane.me` to host this website. As GitHub will not redirect requests to HTTPS endpoints, I also needed to configure a redirect for the `www` subdomain. All DNS records were configured using my hosting providers DNS control panel.

## Configure A Records

Any existing A records for the apex domain should be removed. Then, four A records should be configured to point to the IP addresses [specified by GitHub](https://help.github.com/articles/setting-up-an-apex-domain/). These are:

- 185.199.108.153
- 185.199.109.153
- 185.199.110.153
- 185.199.111.153

The DNS records may take a few minutes to update. You can quickly check using `dig +noall +answer yourdomain.com`.

## Configure WWW Subdomain

I also want users to be able to visit this website using the `www` subdomain. To achieve this, a URL Redirect Record was created. It is an unmasked redirect that redirects any subdomain requests to the apex domain.

The complete DNS configuration looks as follows. This may differ depending on the hosting provider used.

![GitHub Pages DNS Configuration](/resources/2018-08-06/DNS-Configuration.png)

## GitHub Pages Setup

### Enforce HTTPS

In repository settings, under GitHub Pages, ensure `enforce HTTPS` is selected. This ensures that the website will no longer be served over HTTP .

### Refresh Custom Domain

You may need to remove and re-add the custom domain for certificate generation to occur. It can take a few minutes for the certificate to be generated. Once completed the website will display a green lock in the browser. Let's Encrypt certifcates are valid for three months and will be automatically renewed when using GitHub Pages.
