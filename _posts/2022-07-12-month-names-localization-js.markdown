---
layout: post
title: "Month names with localization in Javascript"
date: 2022-07-12 05:10:08 +0530
categories: javascript
---

# Generate month names with localization

```javascript
const months = Array.from({ length: 12 }, (e, i) => {
  return new Date(null, i + 1, null).toLocaleDateString("en", {
    month: "short/long",
  });
});
```

will log as

```javascript
[
  "Jan",
  "Feb",
  "Mar",
  "Apr",
  "May",
  "Jun",
  "Jul",
  "Aug",
  "Sep",
  "Oct",
  "Nov",
  "Dec",
];
```
