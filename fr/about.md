---
layout: page
title: À propos
lang: fr
permalink: /fr/about/
---

{% assign _lang = page.lang | default: 'en' %}{% assign t = site.data.translations[_lang] %}{{ t.about_text }}
