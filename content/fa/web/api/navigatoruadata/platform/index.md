---
title: "NavigatorUAData: platform property"
short-title: platform
slug: Web/API/NavigatorUAData/platform
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.NavigatorUAData.platform
---

{{APIRef("User-Agent Client Hints API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

ویژگی فقط خواندنی **`platform`** از رابط {{domxref("NavigatorUAData")}} اطلاعات برند پلتفرم را برمی‌گرداند.

## مقدار

یک رشته حاوی برند پلتفرم. برای مثال، `"Windows"`.

## مثال‌ها

مثال زیر مقدار `platform` را در کنسول چاپ می‌کند.

```js
console.log(navigator.userAgentData.platform);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- هدر {{HTTPHeader("Sec-CH-UA-Platform")}} (یک [راهنمای مشتری با آنتروپی پایین](/en-US/docs/Web/HTTP/Guides/Client_hints#low_entropy_hints)) حاوی همان اطلاعات است.