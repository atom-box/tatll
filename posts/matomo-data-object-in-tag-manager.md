---
title: The Data Object
description: Matomo Tag Manager, Javascript objects, customize matomo for Ecommerce, Google Ads 
date: 2022-03-28
tags:
  - web analytics
layout: layouts/post.njk
---

## The object
In Matomo, the data layer is a Javascript object named `_mtm`. 

This object is used to store and push data for tracking purposes, similar to how other analytics platforms (like Google Tag Manager) utilize a data layer.

By pushing information into the _mtm object, you can pass various data points to Matomo for tracking user interactions, events, and custom variables. 

Here is an example of the code you would use to interact with the _mtm object in Matomo: 
```javascript
_mtm.push({ 'event': 'customEventName', 'customVariable': 'customValue' });
```

Matomo Tag Manager automatically syncs this _mtm object with the gtm data layer object. However if you do not want this to happen, you can turn it off. In the admin settings of Matomo there is a checkbox to do that.  


## The structure of the MTM Object
I tried to see the object by opening the browser >> devtools >> console. It showed me that `_mtm` contains this: 

```javascript
[
  {
    "mtm.startTime": 1730805033367,
    "event": "mtm.Start"
  },
  {
    "mtm.startTime": 1730805033368,
    "event": "mtm.Start"
  }
]
```
When I asked the console to show _mtm, it returned the following, which looks weird to me because 
* it's an array, with two objects
* they're one second apart but the second one probably overwrites the first one
    
I honestly don't know the answer. I can say that I got it fro a page that has TWO containers. Maybe that Matomo puts the object in an array and that allows there to be multiple containers?  I do know that we get a few emails from folks who organizer their tags by making 2, 3, even 7 containers per page. Maybe an array is how Matomo stores those.  


## What are examples of allowed values?

Here again is a typical script you  might use:
```javascript
_mtm.push({ 'event': 'customEventName', 'customVariable': 'customValue' });
```

The allowed values for properties like 'event' and custom properties such as 'customVariable' can be strings, numbers, or even complex objects depending on what you want to track. 

1. Event Tracking ('event' key):

* Page Interaction Events: click, formSubmit, videoPlay, scroll, etc.
* Custom Events: Any custom name you want to give, like productView, newsletterSignup, downloadFile, etc.

```javascript

_mtm.push({ 'event': 'click' });
_mtm.push({ 'event': 'newsletterSignup' });
```

2. Custom Variables or Dimensions ('customVariable', 'customDimension', etc.):

* Strings: Typically used for names, categories, or text-based values like userType, productCategory, or campaignName.
* Numbers: Useful for quantities, scores, or order totals, such as orderValue, pageDepth, or productQuantity.
* Booleans: Useful for true/false states, like isLoggedIn, isSubscribed, or isFirstVisit.
* Nested Objects or Arrays: For passing more complex data structures when you need multiple properties grouped together.

```javascript
_mtm.push({
    'event': 'productView',
    'productID': '12345',
    'productCategory': 'Electronics',
    'orderValue': 299.99,
    'isSale': true
});

_mtm.push({
    'event': 'pageScroll',
    'scrollDepth': 50,
    'pageSection': 'Reviews'
});
```

