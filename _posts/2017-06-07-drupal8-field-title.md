---
layout: post
title: Drupal 8 - expose title field in a content type's manage display configuration
---

Drupal 8 has now put the page title into a block, which can be very useful when it fits into your general site layout.

What happens though, when you want to have something non-standard?

Recently I needed to place the title field alongside an intro field within a hero block, which I wouldn't have thought was that uncommon.

After some searching around, it seems to be an often asked question and has been raised a few times on drupal.org.

I found an article on https://www.unleashed-technologies.com/blog/2017/05/22/why-we-ditched-display-suite-module-drupal-8 that seemed to solve this problem, so have included the code block below to save you having to type it out.

```
<?php

/**
 * @file
 * Expose title field in a content type's manage display configuration.
 */

use Drupal\node\Entity\NodeType;
use \Drupal\Core\Entity\EntityInterface;
use \Drupal\Core\Entity\Display\EntityViewDisplayInterface;

/**
 * Implements hook_entity_extra_field_info().
 */
function field_title_entity_extra_field_info() {
  $extra = array();

  foreach (NodeType::loadMultiple() as $bundle) {
    $extra['node'][$bundle->Id()]['display']['title_field'] = array(
      'label' => t('Title'),
      'description' => t('Title field'),
      'weight' => 100,
      'visible' => TRUE,
    );
  }

  return $extra;
}

/**
 * Implements hook_ENTITY_TYPE_view().
 */
function field_title_node_view(array &$build, EntityInterface $entity, EntityViewDisplayInterface $display, $view_mode) {

  $current_node = \Drupal::routeMatch()->getParameter('node');
  if ($current_node) {
    // You can get nid and anything else you need from the node object.
    $title = $current_node->getTitle();
  }

  if ($display->getComponent('title_field')) {
    $build['title_field'] = [
      '#type' => 'markup',
      '#markup' => $title,
      '#prefix' => '<h1>',
      '#suffix' => '</h1>',
    ];
  }
}
```

Also on a gist here: https://gist.github.com/kiwimind/93ee41ef619cba3b890de7ccf8c7a338
