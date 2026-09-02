---
title: "NavigationDestination: sameDocument property"
short-title: sameDocument
slug: Web/API/NavigationDestination/sameDocument
page-type: web-api-instance-property
browser-compat: api.NavigationDestination.sameDocument
---

{{APIRef("Navigation API")}}

ویژگی فقط‌خواندنی **`sameDocument`** از رابط {{domxref("NavigationDestination")}} مقدار `true` را برمی‌گرداند اگر پیمایش به همان `document` جاری با مقدار {{domxref("Document")}} باشد، و در غیر این صورت `false` برمی‌گرداند.

این ویژگی برای بررسی اینکه آیا پیمایش در همان سند (same-document) انجام می‌شود یا بین سندها (cross-document) مفید است.

## مقدار

یک مقدار بولی.

## مثال‌ها

```js
navigation.addEventListener("navigate", (event) => {
  console.log(event.destination.sameDocument);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کلاینت: API پیمایش](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح API پیمایش](https://github.com/WICG/navigation-api/blob/main/README.md)