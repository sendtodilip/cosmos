---
layout: post
title:  "New Learnings"
date:   2022-09-10 20:54:37 +0530
categories: PagePerformance, HTML, JavaScript, All
---

## Intersection Observr

The Intersection Observer API provides a way to asynchronously observe changes in the intersection of a target element with an ancestor element or with a top-level document's viewport.

```javascript
let options = {
  root: document.querySelector('#scrollArea'),
  rootMargin: '0px',
  threshold: 1.0
}

let observer = new IntersectionObserver(callback, options);
```
https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API 

                                   
                                  
                                  
