---
title: "Document: fullscreen property"
short-title: fullscreen
slug: Web/API/Document/fullscreen
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.Document.fullscreen
---

{{APIRef("Fullscreen API")}}{{Deprecated_Header}}

ویژگی فقط‌خواندنی **`fullscreen`** در رابط منسوخ {{domxref("Document")}} گزارش می‌دهد که آیا سند در حال حاضر محتوایی را در حالت تمام‌صفحه نمایش می‌دهد یا خیر.

اگرچه این ویژگی فقط‌خواندنی است، اما اگر تغییر داده شود (حتی در حالت سخت‌گیرانه) خطایی پرتاب نمی‌کند؛ setter آن یک عملیات بی‌اثر است و نادیده گرفته می‌شود.

> [!NOTE]
> از آنجا که این ویژگی منسوخ شده است، می‌توانید با بررسی اینکه {{DOMxRef("Document.fullscreenElement")}} برابر با `null` نیست، تعیین کنید که حالت تمام‌صفحه روی سند فعال است یا خیر.

## مقدار

یک مقدار بولی است که اگر سند در حال حاضر عنصری را در حالت تمام‌صفحه نمایش دهد، `true` است؛ در غیر این صورت، مقدار `false` است.

## مثال‌ها

این تابع ساده با استفاده از ویژگی منسوخ `fullscreen` گزارش می‌دهد که آیا حالت تمام‌صفحه در حال حاضر فعال است یا خیر.

```js
function isDocumentInFullScreenMode() {
  return document.fullscreen;
}
```

از سوی دیگر، این مثال بعدی از ویژگی فعلی `fullscreenElement` برای تعیین همین موضوع استفاده می‌کند:

```js
function isDocumentInFullScreenMode() {
  return document.fullscreenElement !== null;
}
```

اگر `fullscreenElement` برابر با `null` نباشد، این تابع `true` برمی‌گرداند که نشان می‌دهد حالت تمام‌صفحه فعال است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Fullscreen API](/en-US/docs/Web/API/Fullscreen_API)
- [Guide to the Fullscreen API](/en-US/docs/Web/API/Fullscreen_API/Guide)
- {{DOMxRef("Document.fullscreenEnabled")}}