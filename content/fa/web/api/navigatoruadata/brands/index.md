---
title: "NavigatorUAData: brands property"
short-title: brands
slug: Web/API/NavigatorUAData/brands
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.NavigatorUAData.brands
---

{{APIRef("User-Agent Client Hints API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`brands`** از رابط {{domxref("NavigatorUAData")}} یک آرایه از اطلاعات برند را برمی‌گرداند.

## مقدار

یک آرایه شامل اطلاعات زیر برای هر برند:

- `brand`
  - : یک رشته شامل نام برند. برای مثال، `"Google Chrome"`.
- `version`
  - : یک رشته شامل نسخه. برای مثال، `"91"`.

## مثال‌ها

مثال زیر مقدار `brands` را در کنسول چاپ می‌کند.

```js
console.log(navigator.userAgentData.brands);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTTPHeader("Sec-CH-UA")}} (یک [نکته مشتری با آنتروپی پایین](/en-US/docs/Web/HTTP/Guides/Client_hints#low_entropy_hints)) حاوی همان اطلاعات است.