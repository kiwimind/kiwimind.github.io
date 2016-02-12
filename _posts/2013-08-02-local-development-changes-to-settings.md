---
layout: post
title: Local development changes to settings.php
---

When syncing a DB from production to dev, there are some settings which I often end up turning off in the UI.

It’s possible to add some lines to your dev settings.php to force settings on local only. Make sure to not use these line in your production environment as you will want the settings on.

    // Turn off css and js aggregation
    $conf['preprocess_css'] = 0;
    $conf['preprocess_js'] = 0;
    
    // Turn on LESS developer mode
    $conf['less_devel'] = 1;

    // Turn off page and block caching
    $conf['cache'] = 0;
    $conf['block_cache'] = 0;
    
    // Turn on full error logging
    $conf['error_level'] = 2;
