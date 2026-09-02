---
title: "NavigationHistoryEntry: sameDocument property"
short-title: sameDocument
slug: Web/API/NavigationHistoryEntry/sameDocument
page-type: web-api-instance-property
browser-compat: api.NavigationHistoryEntry.sameDocument
---

{{APIRef("Navigation API")}}

خاصیتِ فقط‌خواندنی **`sameDocument`** در رابط {{domxref("NavigationHistoryEntry")}} مقدار `true` را برمی‌گرداند اگر این ورودی تاریخچه مربوط به همان `document` (سند) با مقدار فعلی {{domxref("Document")}} باشد و سند فعلی کاملاً فعال (fully active) باشد؛ در غیر این صورت `false` برمی‌گرداند.

## مقدار

یک مقدار بولین (boolean).

## مثال‌ها

```js
const current = navigation.currentEntry;
console.log(current.sameDocument);
// Will always return true
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)