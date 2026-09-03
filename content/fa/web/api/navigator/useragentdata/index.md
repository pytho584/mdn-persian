---
title: "Navigator: userAgentData property"
short-title: userAgentData
slug: Web/API/Navigator/userAgentData
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Navigator.userAgentData
---

{{securecontext_header}}{{APIRef("User-Agent Client Hints API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`userAgentData`** در رابط {{domxref("Navigator")}} یک شیء {{domxref("NavigatorUAData")}} برمی‌گرداند که می‌توان از آن برای دسترسی به {{domxref("User-Agent Client Hints API", "", "", "nocode")}} استفاده کرد.

## مقدار

یک شیء {{domxref("NavigatorUAData")}}.

## مثال‌ها

مثال زیر مقدار {{domxref("NavigatorUAData.brands")}} را در کنسول چاپ می‌کند.

```js
console.log(navigator.userAgentData.brands);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [HTTP Client hints](/en-US/docs/Web/HTTP/Guides/Client_hints)
- [بهبود حریم خصوصی کاربران و تجربه توسعه‌دهندگان با User-Agent Client Hints](https://developer.chrome.com/docs/privacy-security/user-agent-client-hints)