---
title: "GeolocationPosition: toJSON() method"
short-title: toJSON()
slug: Web/API/GeolocationPosition/toJSON
page-type: web-api-instance-method
browser-compat: api.GeolocationPosition.toJSON
---

{{APIRef("Geolocation API")}}

متد **`toJSON()``** از رابط {{domxref("GeolocationPosition")}} یک {{Glossary("Serialization","سریال‌ساز")}} است؛ این متد یک نمایش JSON از شیء {{domxref("GeolocationPosition")}} برمی‌گرداند.

## Syntax

```js-nolint
toJSON()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}} که سریال‌سازی شده‌ی شیء {{domxref("GeolocationPosition")}} است.

## مثال‌ها

### استفاده از متد `toJSON()`

در این مثال، فراخوانی `position.toJSON()` یک نمایش JSON از شیء `GeolocationPosition` برمی‌گرداند.

```js
navigator.geolocation.getCurrentPosition((position) => {
  console.log(position.toJSON());
});
```

این کد یک شیء JSON مانند زیر را در کنسول ثبت می‌کند:

```json
{
  "timestamp": 1717509611840,
  "coords": {
    "accuracy": 13.0,
    "latitude": 53.0,
    "longitude": 8.0,
    "altitude": null,
    "altitudeAccuracy": null,
    "heading": null,
    "speed": null
  }
}
```

برای دریافت یک رشته‌ی JSON، می‌توانید مستقیماً از [`JSON.stringify(position)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) استفاده کنید؛ این متد به‌طور خودکار `toJSON()` را فراخوانی می‌کند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{jsxref("JSON")}}