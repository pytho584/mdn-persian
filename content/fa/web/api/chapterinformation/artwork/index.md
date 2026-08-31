---
title: "ChapterInformation: artwork property"
---

---
title: "ChapterInformation: artwork property"
short-title: artwork
slug: Web/API/ChapterInformation/artwork
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.ChapterInformation.artwork
---

{{APIRef("Media Session API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`artwork`** در واسط {{domxref("ChapterInformation")}} یک {{jsxref("Array")}} از اشیاء را بازمی‌گرداند که تصاویر مرتبط با این فصل را نشان می‌دهند.

## مقدار

یک {{jsxref("Array")}} از اشیاء. هر شیء شامل ویژگی‌های زیر است:

- `src`
  - : یک رشته (string) که نشانی اینترنتی (URL) را نشان می‌دهد که عامل کاربر (user agent) داده‌های تصویر را از آن دریافت می‌کند.
- `sizes`
  - : یک رشته که یک یا چند اندازه برای منبع را نشان می‌دهد. مقدار آن می‌تواند کلیدواژه `any` (نشان‌دهنده یک فرمت برداری مقیاس‌پذیر مانند SVG) باشد، یا فهرستی از توکن‌ها با جداکننده فاصله با قالب `<width in pixels>x<height in pixels>` یا `<width in pixels>X<height in pixels>`. اگر چند اندازه ارائه شود، عامل کاربر می‌تواند مناسب‌ترین اندازه را برای زمینه فعلی بارگذاری کند، به شرطی که آن اندازه‌ها در منبع پیوندی موجود باشند.
- `type`
  - : یک رشته که یک راهنمای {{Glossary("MIME type")}} را نشان می‌دهد که به عامل کاربر اجازه می‌دهد انواع تصویری را که پشتیبانی نمی‌کند نادیده بگیرد. با این حال، عامل کاربر ممکن است پس از دانلود تصویر، برای تعیین نوع آن از تشخیص نوع MIME (MIME-type sniffing) استفاده کند.

## مثال‌ها

برای مثال به صفحه اصلی {{domxref("ChapterInformation")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ChapterInformation")}}