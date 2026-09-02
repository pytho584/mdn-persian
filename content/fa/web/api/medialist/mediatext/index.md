```
---
title: "MediaList: mediaText property"
short-title: mediaText
slug: Web/API/MediaList/mediaText
page-type: web-api-instance-property
browser-compat: api.MediaList.mediaText
---

{{APIRef("CSSOM")}}

ویژگی **`mediaText`** در رابط {{domxref("MediaList")}} یک {{Glossary("stringifier")}} است که یک رشته شامل نمایش متنی `MediaList` را برمی‌گرداند و همچنین به شما امکان می‌دهد یک `MediaList` جدید تنظیم کنید.

## مقدار

رشته‌ای که رسانه‌های (media queries) یک شیوه‌نامه را نشان می‌دهد. هر کدام با کاما از هم جدا می‌شوند، برای مثال `screen and (width >= 480px), print`.

اگر می‌خواهید رسانه‌های جدیدی روی سند تنظیم کنید، مقدار رشته باید شامل رسانه‌های متفاوت با جداسازی کاما باشد، مثلاً `screen, print`. توجه داشته باشید که `MediaList` یک فهرست زنده است؛ به‌روزرسانی فهرست از طریق `mediaText` بلافاصله رفتار سند را به‌روزرسانی می‌کند.

وقتی مقدار `null` تنظیم شود، آن مقدار `null` به رشته خالی (`""`) تبدیل می‌شود، بنابراین `ml.mediaText = null` معادل `ml.mediaText = ""` است.

## مثال‌ها

در مثال زیر، نمایش متنی `MediaList` اولین شیوه‌نامه اعمال‌شده روی سند فعلی در کنسول ثبت می‌شود.

```js
const stylesheets = document.styleSheets;
let stylesheet = stylesheets[0];
console.log(stylesheet.media.mediaText);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```