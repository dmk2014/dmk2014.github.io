---
layout: post
title: Setup HTTPS with GitHub Pages
---

[GitHub Pages](https://pages.github.com) allows websites to be hosted directly from GitHub repositories. Recently, the team at GitHub [added support for HTTPS](https://blog.github.com/2018-05-01-github-pages-custom-domains-https/) to custom domains that are hosted using GitHub Pages. The certificates used are provided free of charge by [Let's Encrypt](https://letsencrypt.org). I have previously used Let's Encrypt in a professional setting, it is an excellent project, and it's great to see it being embraced by GitHub.

Setting up a custom domain for HTTPS is straightforward, though a little different from previous GitHub Pages configurations. Before starting, I removed all previously configured *A records* that pointed to GitHub as well as a *CNAME record* that had been configured for my *username.github.io* address.

 I decided to use the apex domain `darrenkeane.me` to host this website. As GitHub will not redirect requests made to HTTPS endpoints, I also needed to configure a redirect for the `www` subdomain. All DNS records were configured using my hosting providers DNS control panel.

## Domain Setup

### A Records

Once any existing A records for the apex domain have been removed, four new A records should be created to point to the IP addresses [specified by GitHub](https://help.github.com/articles/setting-up-an-apex-domain/). These are:

1. 185.199.108.153
2. 185.199.109.153
3. 185.199.110.153
4. 185.199.111.153

The DNS records may take a few minutes to update. You can quickly check if the DNS update has propagated using `dig +noall +answer yourdomain.com`.

### WWW Subdomain

I also want this website to be accessible using the `www` subdomain. To achieve this, a *URL Redirect Record* should be created. I configured a *301 Permanent Redirect* to communicate that any requests to the subdomain should be redirected to the apex domain.

The complete DNS configuration looks as follows in my hosting providers control panel. This may differ depending on the hosting provider used. The [GitHub Pages Help](https://help.github.com/articles/using-a-custom-domain-with-github-pages/) articles are an excellent resource, if required.

![GitHub Pages DNS Configuration](/resources/2018-08-06/DNS-Configuration.png)

## GitHub Pages Setup

### Enforce HTTPS

In repository settings, under GitHub Pages, ensure `enforce HTTPS` is selected. This ensures that the website will no longer be served over HTTP .

### Refresh Custom Domain

You may need to remove and re-add the custom domain for certificate generation to occur. It can take a few minutes for the certificate to be generated. Once completed the website will display a green lock in the browser. Let's Encrypt certificates are valid for three months and are automatically renewed when using GitHub Pages.
