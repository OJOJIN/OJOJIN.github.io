---
title: "안드로이드 네트워크 보안 구성"
description: "📱안드로이드 nttp 통신에 필요한 network-security-config 을 설정하는 방법에 대해 알아보자"
date: 2023-07-06
update: 2023-07-06
tags:
  - android
  - issue
---

### 상황

안드로이드 retrofit을 사용하여 API통신을 시도하는데 계속해서 onFailure이 호출되는 것을 확인했다.

AndroidManifest 내에 INTERNET 권한도 허용되어있는 상태였다.

```xml
<uses-permission android:name="android.permission.INTERNET" />
```

###

안드로이드 9 버전부터는 Http를 더이상 지원안한다고 한다.(Https 지원)  

따라서 추가적인 네트워크 보안 구성을 적용 해주어야한다.

### 해결방안


모든 http 연결을 허가하는 방법으로 문제를 해결했다.

<br>

<res/xml/network\_security\_config.xml>
```xml
<?xml version="1.0" encoding="utf-8"?>
<network-security-config>
    <base-config cleartextTrafficPermitted="true"></base-config>
</network-security-config>
```

<AndroidManifest.xml>
```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest ... >
    <application android:networkSecurityConfig="@xml/network_security_config"
                    ... >
        ...
    </application>
</manifest>  
```

##
##

출처 : https://developer.android.com/training/articles/security-config?hl=ko
