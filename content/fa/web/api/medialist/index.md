---
title: MediaList
slug: Web/API/MediaList
page-type: web-api-interface
browser-compat: api.MediaList
---

{{APIRef("CSSOM")}}

رابطِ **`MediaList`** فهرست پرس‌وجوهای رسانه‌ای (media queries) یک شیوه‌نامه (stylesheet) را نمایش می‌دهد؛ برای نمونه، پرس‌وجوهایی که از طریق ویژگیِ `media` عنصر {{htmlelement("link")}} تنظیم شده‌اند.

> [!NOTE]
> `MediaList` فهرستی زنده است؛ به‌روزرسانیِ آن با استفاده از ویژگی‌ها یا متدهای فهرست‌شده در ادامه، بلافاصله رفتار سند را به‌روز می‌کند.

## ویژگی‌های نمونه

- {{domxref("MediaList.mediaText")}}
  - : یک {{Glossary("stringifier")}} که یک رشتهٔ متنیِ نمایش‌دهندهٔ `MediaList` را بازمی‌گرداند و همچنین به شما اجازه می‌دهد یک `MediaList` جدید تنظیم کنید.
- {{domxref("MediaList.length")}} {{ReadOnlyInline}}
  - : تعداد پرس‌وجوهای رسانه‌ای درون `MediaList` را بازمی‌گرداند.

## متدهای نمونه

- {{domxref("MediaList.appendMedium()")}}
  - : یک پرس‌وجوی رسانه‌ای به `MediaList` اضافه می‌کند.
- {{domxref("MediaList.deleteMedium()")}}
  - : یک پرس‌وجوی رسانه‌ای را از `MediaList` حذف می‌کند.
- {{domxref("MediaList.item()")}}
  - : یک getter که با دریافت مقدار اندیسِ یک پرس‌وجوی رسانه‌ای درون `MediaList`، رشته‌ای متنی از آن پرس‌وجو را بازمی‌گرداند. این متد همچنین با استفاده از نحوِ براکت (`[]`) نیز قابل فراخوانی است.
- {{domxref("MediaList.toString()")}}
  - : بازنمود رشت‌ای از این فهرست رسانه را در همان قالبی که ویژگیِ {{domxref("MediaList.mediaText")}} شیء ارائه می‌دهد، بازمی‌گرداند.

## مثال‌ها

مثال زیر، بازنمود متنیِ `MediaList` نخستین شیوه‌نامهٔ اعمال‌شده روی سند فعلی را در کنسول ثبت می‌کند:

```js
const stylesheets = document.styleSheets;
let stylesheet = stylesheets[0];
console.log(stylesheet.media.mediaText);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}