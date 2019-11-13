---
title: "Details: Frontend"
date: 2019-02-11T19:30:08+10:00
draft: false
weight: 6
summary: Additional Frontend Documentation
---

## Change Settings

Certificates can be exchanged. The path can also be specified in the configuration with the `-c` argument.

The hostname API can be changed via the environment variable `LEL_HOSTNAME`. Or via a configuration with the `-c` argument.

![pic](/user/pic_custom-url-api.png)

The frontend-script can be replaced via the environment variable `LEL_FRONTEND_URL`.

![pic](/user/pic_custom-url.png)

## Stats

When opening LeL several count stats are displayed.

![pic](/user/pic_stats.png)

Among them is also the error count. The number can be clicked to display the exact error message.

Currently errors indicate that multiple notes have the same `name` values. Names are considered unique.

![pic](/user/pic_stats_error.png)

## DarkMode

Now you can switch between light and dark mode.
![pic](/user/pic_darkmode.png)

## Markdown editor

If you only want to use LeL as a display, now markdownOnly view got you covered.

![pic](/user/pic_markdownonly.png)

## TagSearch

Tags can also be searched in the navigator through the `tags:` prefix:

![pic](/user/pic_nav_tags.png)
