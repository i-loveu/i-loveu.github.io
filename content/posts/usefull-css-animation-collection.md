---
title: "Usefull Css Animation Collection"
slug: "Usefull Css Animation Collection"
cafegories: ["css"]
tags: ["animation"]
date: 2021-05-05T15:42:17+09:00
draft: true
---

### floating

```css
.floating-box {
  transform: translatey(0px);
  animation: float 2s ease-in-out infinite;
}

@keyframes float {
  0% {
    transform: translatey(0px);
  }
  50% {
    transform: translatey(-20px);
  }
  100% {
    transform: translatey(0px);
  }
}
```
