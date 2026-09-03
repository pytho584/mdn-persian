---
title: "NavigatorUAData: mobile property"
short-title: mobile
slug: Web/API/NavigatorUAData/mobile
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.NavigatorUAData.mobile
---

{{APIRef("User-Agent Client Hints API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

ویژگی فقط خواندنی **`mobile`** از رابط {{domxref("NavigatorUAData")}} مقداری را برمی‌گرداند که نشان می‌دهد آیا دستگاه یک دستگاه همراه (موبایل) است یا خیر.

## مقدار

یک {{jsxref("Boolean")}}؛ اگر دستگاه همراه باشد مقدار `true` است.

## مثال‌ها

مثال زیر مقدار `mobile` را در کنسول چاپ می‌کند.

```js
console.log(navigator.userAgentData.mobile);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- هدر {{HTTPHeader("Sec-CH-UA-Mobile")}} (یک [نکته مشتری با آنتروپی پایین](/en-US/docs/Web/HTTP/Guides/Client_hints#low_entropy_hints)) حاوی همان اطلاعات است.