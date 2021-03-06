---
layout: post
title: |
    How-to: Hide Content
description: |
    How-to hide content but still make it accessible to screen readers.
last_updated: 2013-02-15
categories:
  - How-tos
---

Developers commonly use `display: none` to hide content on the page. Unfortunately, this simple and common action is a bit problematic for screen readers.

[Screen readers sometimes ignore display:none](http://www.456bereastreet.com/archive/200711/screen_readers_sometimes_ignore_displaynone/)[^bereast]. This means the content will be read despite being "hidden". To hide content completely from screen readers use the following:

    /* http://www.456bereastreet.com/archive/200711/screen_readers_sometimes_ignore_displaynone/ */
    .hidden {
        display:none;
        visibility:hidden;
    }

And for good measure you could consider adding the ARIA attribute `aria-hidden="true"` to the element.

There are also real world situations where you want to hide elements (e.g., a `form label`), but you still want text to be read by a screen reader. The "clip pattern" will hide the content visually, yet provide the content to screen readers[^clip]. Unlike positioning and negative text-indent, it works with rtl languages for localization.

    .visually-hidden { /*https://developer.yahoo.com/blogs/ydn/clip-hidden-content-better-accessibility-53456.html*/
        position: absolute !important;
        clip: rect(1px 1px 1px 1px); /* IE6, IE7 */
        clip: rect(1px, 1px, 1px, 1px);
        padding:0 !important;
        border:0 !important;
        height: 1px !important;
        width: 1px !important;
        overflow: hidden;
    } 
    body:hover .visually-hidden a, body:hover .visually-hidden input, body:hover .visually-hidden button { display: none !important; } 

Consider adding these HTML classes and CSS rules to your base stylesheet and use them when applicable.

[^bereast]: [Screen readers sometimes ignore display:none](http://www.456bereastreet.com/archive/200711/screen_readers_sometimes_ignore_displaynone/) 456 Berea Street (November 7, 2007)
[^clip]: [Clip Your Hidden Content For Better Accessibility](https://developer.yahoo.com/blogs/ydn/clip-hidden-content-better-accessibility-53456.html) Yahoo Accessibility Blog  (October 23, 2012)
