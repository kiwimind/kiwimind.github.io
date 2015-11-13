---
layout: post
title: Remove lock on Drupal account
---

If you’ve had someone fail their login attempt 5 times, their account gets locked for a period of time.

To remove the account locks, use the following:

```
drush sqlq “DELETE FROM flood”
```

Of course, if you’re using drush aliases, then you can just use the following from your local machine:

```
drush @alias.prod sqlq “DELETE FROM flood”
```
