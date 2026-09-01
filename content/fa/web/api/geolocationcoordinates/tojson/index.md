---
title: "GeolocationCoordinates: toJSON() method"
short-title: toJSON()
slug: Web/API/GeolocationCoordinates/toJSON
page-type: web-api-instance-method
browser-compat: api.GeolocationCoordinates.toJSON
---

{{APIRef("Geolocation API")}}

متد **`toJSON()`** از رابط {{domxref("GeolocationCoordinates")}} یک سریالساز است؛ این متد یک نمایش JSON از شیء {{domxref("GeolocationCoordinates")}} بازمی‌گرداند.

## نحو

```js-nolint
toJSON()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}} که سریالسازی شیء {{domxref("GeolocationCoordinates")}} است.

## مثال‌ها

### استفاده از متد `toJSON()`

در این مثال، فراخوانی `position.coords.toJSON()` یک نمایش JSON از شیء `GeolocationCoordinates` بازمی‌گرداند.

```js
navigator.geolocation.getCurrentPosition((position) => {
  console.log(position.coords.toJSON());
});
```

این کار یک شیء JSON مانند زیر را ثبت می‌کند:

```json
{
  "accuracy": 12.0,
  "latitude": 53.0,
  "longitude": 8.0,
  "altitude": null,
  "altitudeAccuracy": null,
  "heading": null,
  "speed": null
}
```

برای دریافت یک رشته JSON، می‌توانید مستقیماً از [`JSON.stringify(position.coords)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) استفاده کنید؛ این متد به‌طور خودکار `toJSON()` را فراخوانی می‌کند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{jsxref("JSON")}}