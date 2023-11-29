---
title: "Flutter Error Cocoapods"
slug: "Flutter Error Cocoapods"
date: 2023-11-01T12:38:37+09:00
draft: false
---

## 플루터를 실행하려고 할 때 'pop repo update'가 뜨는 경우

```
cd iso
rm Podfile.lock
pod install --repo-update
cd ..
flutter clean 
```

후에 재살행 