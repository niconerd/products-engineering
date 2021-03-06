---
date: 2017-08-28
title: Plugin Namespacing
categories:
  - Guidelines

description: Plugin conventions for Namespaces, Assets and Classes
icon: fa-file-text-o
---
Each plugin and major product area has its own prefix for hooks and `tribe()` container slugs. The
prefixes are as follows:

| Product | Hook prefix | Container prefix |
|---------|-------------|-------|
| Tribe Common | `tribe_` | `common.` |
| Event Aggregator | `tribe_aggregator_` | `aggregator.` |
| The Events Calendar | `tribe_events_` | `tec.` |
| The Events Calendar PRO | `tribe_events_pro_` | `pro.` |
| Community Events | `tribe_events_community_` | `community.` |
| Community Tickets | `tribe_community_tickets_` | `community-tickets.` |
| Eventbrite Tickets | `tribe_events_eventbrite_` | `eventbrite.` |
| Filter Bar | `tribe_events_filter_` | `filterbar.` |
| Event Tickets | `tribe_tickets_` | `tickets.` |
| Event Tickets Plus | `tribe_tickets_plus_` | `tickets-plus.` |
| Image Widget | `tribe_image_` | `image.` |
| Image Widget Plus | `tribe_image_plus_` | `image-plus.` |

_Despite being embedded within the-events-calendar, Event Aggregator deserves (and gets) its own prefix._

## Hook examples

```php
<?php
// hook in tribe common for firing the bacon action
do_action( 'tribe_bacon' );

// hook in TEC for firing the potato action
do_action( 'tribe_events_potato' );

// hook in the Event Aggregator section of TEC for firing the squid action
do_action( 'tribe_aggregator_squid' );
```

## Container slug examples

```php
<?php
// declare singleton for the panda class in tribe-common, then call it
tribe_singleton( 'common.panda', 'Tribe__Panda' );
tribe( 'common.panda' );

// declare singleton for the squirrel admin class in TEC, then call it
tribe_singleton( 'tec.admin.squirrel', 'Tribe__Events__Admin__Squirrel' );
tribe( 'tec.admin.squirrel' );

// declare singleton for the baboon class in the Event Aggregator code within TEC, then call it
tribe_singleton( 'aggregator.baboon', 'Tribe__Events__Aggregator__Baboon' );
tribe( 'aggregator.baboon' );
```

## Style and script slugs

When registering and enqueuing scripts and styles, we should append `-css` in the case of stylesheets. Example:

| Asset slug              | Asset type |
|-------------------------|------------|
| `tribe-post-editor`     | JS         |
| `tribe-post-editor-css` | CSS        |

_Note that in this instance we prefer hyphens over underscores._