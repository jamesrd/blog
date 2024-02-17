+++
author = "James DeVries"
title = "Modifying Page Layout"
date = "2024-02-17"
description = "Adding a static link to another website"
tags = [
    "hugo", "blog",
]
+++

## Overview:

Currently my blog is hosted on a separate [Github repo](https://github.com/jamesrd/blog)
from the rest of my main website.

To put a link from the blog back to my main website I decided to modify the footer
layout from the [HugoTex](https://github.com/kaisugi/HugoTeX) theme. I wanted to make
the change without directly modifying the original theme files.

__Solution:__ Hugo searches for files in the `layouts/` folder before using the files from the 
theme's `layouts/` folder.

_Reference page:_ [Hugo: Customizing a theme](https://gohugobrasil.netlify.app/themes/customizing/)

## Steps:

1. Look in the `themes/<theme name>/layouts` directory to find the theme file
you want to modify.
1. Copy the file to your root `layouts/` directory, matching the directory structure
that the original file is in. For example:
    - Theme file: `themes/HugoTex/layouts/partials/footer.html`
    - Is copied to: `layouts/partials/footer.html`
1. Now modify the copied file to make your changes.
