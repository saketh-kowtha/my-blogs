---
id: 723035
title: Benefit of maintaining separate Js file in HTML
description: The benefit of a separate file is that the browser will download it and store it in its cache. So the...
published_at: 2021-06-09T13:15:15.636Z
tag_list: html,javascript,css,webdev
---

      The benefit of a separate file is that the browser will download it and store it in its cache. So the Other pages that reference the same script will take it from the cache instead of downloading it, so the file is actually downloaded only once. This reduces traffic and makes pages faster.
