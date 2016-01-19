---
layout: post
title: Facebook share showing incorrect text?
---

Recently I had an issue where a Facebook share popup was showing incorrect translated text.

It seems that Facebook had scraped a previous version of the page, possibly during testing, and this was being displayed on the share popup.

Simple enough to solve: visit [Facebook's Debugger][1] to see what information has been stored from the most recent scrape. This page will also allow you to update the information stored against this page for future use.

Nice simple tool.

[1]: https://developers.facebook.com/tools/debug/
