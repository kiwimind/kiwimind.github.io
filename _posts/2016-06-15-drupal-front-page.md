---
layout: post
title: Drupal 8 - drupal_is_front_page
---

There seem to be a few posts around at the moment about being able to use Drupal 8 with the `drupal_is_front_page()` function.

This isn't the case, as shown by https://api.drupal.org/api/drupal/includes!path.inc/function/drupal_is_front_page/7.x. There is no Drupal 8 version.

Now, you're able to use:

	if (\Drupal::service('path.matcher')->isFrontPage())
