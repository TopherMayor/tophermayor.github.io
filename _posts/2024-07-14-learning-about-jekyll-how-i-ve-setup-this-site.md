---
layout: post
title: 'Learning about Jekyll: How I''ve Setup This Site'
date: 2024-07-14 18:09 -0700
categories: [LOG, JULY]
tags: [chirpy, github, documentation]
---

DOCUMENTATION UNDER DEVELOPMENT

## Resources
* https://github.com/cotes2020/chirpy-starter
* https://chirpy.cotes.page/
* https://github.com/jekyll/jekyll-compose
* https://techno-tim.github.io/
## Configuration
 
All the initial value changes made to ```/path/to/_config.yml```
```yml
# Change to your timezone › https://kevinnovak.github.io/Time-Zone-Picker
timezone: America/Los_Angeles

title: TopherMayor # the main title

tagline: A Site logging everything I learn # it will display as the sub-title

description: >- # used by seo meta and the atom feed
  A minimal, responsive and feature-rich Jekyll theme for technical writing.

# Fill in the protocol & hostname for your site.
# e.g. 'https://username.github.io', note that it does not end with a '/'.
url: "https://tophermayor.github.io"

github:
  username: TopherMayor # change to your github username

twitter:
  username: TopherMayor # change to your twitter username

social:
  # Change to your full name.
  # It will be displayed as the default author of the posts and the copyright owner in the Footer
  name: Christopher John Sison Mayor
  email: toph.homelab@gmail.com # change to your email address
  links:
    # The first element serves as the copyright owner's link
    - https://twitter.com/TopherMayor # change to your twitter homepage
    - https://github.com/TopherMayor # change to your github homepage
    # Uncomment below to add more social links
    # - https://www.facebook.com/username
    - https://www.linkedin.com/in/christopher-mayor-72406498

# the avatar on sidebar, support local or CORS resources
avatar: https://pbs.twimg.com/profile_images/1812302049389764610/iNB8n9cr_400x400.jpg

```

## Deployment
Options:
* GitHub Pages

* Self Host


## Jekyll-Compose

Aliases added to ```~/.bash_aliases```
```bash
alias jpage='bundle exec jekyll page'
alias jpost='bundle exec jekyll post'
alias jdraft='bundle exec jekyll draft'
alias jrename='bundle exec jekyll rename'
alias junpub='bundle exec jekyll unpublish'
```