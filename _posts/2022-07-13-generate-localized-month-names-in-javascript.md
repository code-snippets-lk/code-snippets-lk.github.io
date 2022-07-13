---
layout: post
title: "How to generate localized month names in Javascript?"
date: 2022-07-13
categories: javascript
tags: javascript
---

Here is a code snippet to generate months of the year with internationalization. (Change "en" and "short" to the required value)

```javascript
const months = Array.from({ length: 12 }, (e, i) => {
  return new Date(null, i + 1, null).toLocaleDateString("en", {
    month: "short",
  });
});
```

Output:

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

### Happy coding!