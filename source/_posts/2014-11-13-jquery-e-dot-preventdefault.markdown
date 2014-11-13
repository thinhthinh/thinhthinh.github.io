---
layout: post
title: "jQuery: e.preventDefault()"
date: 2014-11-13 08:17:01 -0500
comments: true
categories: jQuery
---

> `e.preventDefault()` lets you play Kanye to the browser's Taylor Swift.

A browser responds to events within a document with default behaviors. 

For example, when a `<a>` element is clicked, the browser will automatically interpret the `href` attribute and reload the window. Other examples include:
- A form submit button submits the form
- The space bar scrolling down the page

Yet often while designing your web application, you will want to define this behavior. You tell the default behavior to **stop** through `.preventDefault()`. Here's an example:

```javascript
$('a').click(function(event){
  event.preventDefault();
  //Go ahead Kanye, do your thing
});
```

Don't ever let the haters get you down. `.preventDefault()` them.

->![Haters gonna hate](http://media.giphy.com/media/7qWeVklfBavh6/giphy.gif)<-


