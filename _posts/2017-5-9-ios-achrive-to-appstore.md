---
layout: post
title:  "ios 打包发布"
date:   2017-5-9 14:00:00 +0800
categories:  cordova ios achrive
---

## ios 发布

1. 在 build 处不选择模拟器，选择 Generic -> iOS -> Device
2. plist 文件 添加需要用户权限的提示语
3. 检查 Bundle Identifier, Version, Build
4. click `Product` -> `Achrive`
5. click `Validate`
6. click `Upload to App Store`
7. [itunesconnect][0]

**tips**:

+ Upload 之后记得及时检查邮件，看有没有什么问题

 [0] : https://itunesconnect.apple.com/WebObjects/iTunesConnect.woa/ra/ng/app/1187762307/ios/versioninfo