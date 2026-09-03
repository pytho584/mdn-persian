---
title: "Navigator: mimeTypes property"
short-title: mimeTypes
slug: Web/API/Navigator/mimeTypes
page-type: web-api-instance-property
browser-compat: api.Navigator.mimeTypes
---

{{ ApiRef("HTML DOM") }}

یک شیء {{domxref("MimeTypeArray")}} را برمی‌گرداند که شامل فهرستی از اشیاء {{domxref("MimeType")}} است و نشان‌دهندهٔ انواع MIME است که توسط مرورگر شناسایی و پشتیبانی می‌شوند. می‌توان از این آرایه برای دریافت اطلاعات دربارهٔ افزونهٔ فعال (plugin) استفاده کرد که برای مدیریت یک فایل از نوع مشخص به کار می‌رود. ویژگی‌های نام‌دار شیء بازگشتی قابل شمارش نیستند (به جز در نسخه‌های بسیار قدیمی مرورگر).

نسخه‌های اخیر مشخصات، مجموعهٔ بازگشتی از انواع MIME را به صورت ثابت (hard-coded) تعیین می‌کنند. اگر فایل‌های PDF بتوانند به صورت درون‌خطی (inline) نمایش داده شوند، مقادیر `application/pdf` و `text/pdf` در فهرست قرار می‌گیرند. در غیر این صورت یک فهرست خالی بازگردانده می‌شود.

> [!NOTE]
> برای تعیین اینکه آیا نمایش درون‌خطی فایل‌های PDF پشتیبانی می‌شود، از {{domxref("Navigator.pdfViewerEnabled")}} استفاده کنید. این ویژگی را از این خاصیت استنباط نکنید.

نسخه‌های قدیمی مرورگر فهرست بازگشتی را به صورت ثابت تعیین نمی‌کنند و ممکن است انواع MIME دیگری را برگردانند.

## مقدار

یک شیء `MimeTypeArray` که دارای خاصیت `length` و همچنین متدهای `item(index)` و `namedItem(name)` است. اگر نمایش درون‌خطی PDF پشتیبانی شود، این شیء شامل ورودی‌هایی برای انواع MIME `application/pdf` و `text/pdf` است. در غیر این صورت یک `MimeTypeArray` خالی بازگردانده می‌شود. توضیحات و پسوندهای فایل پشتیبانی‌شده توسط افزونه‌های فعال به ترتیب به صورت `'pdf'` و `'Portable Document Format'` ثابت شده‌اند.

## مثال‌ها

کد زیر بررسی می‌کند که آیا فایل‌های PDF می‌توانند به صورت درون‌خطی نمایش داده شوند و سپس توضیحات افزونه و پسوندهای فایل پشتیبانی‌شده را چاپ می‌کند.

```js
if ("application/pdf" in navigator.mimeTypes) {
  // مرورگر از نمایش درون‌خطی فایل‌های PDF پشتیبانی می‌کند.

  const { description, suffixes } = navigator.mimeTypes["application/pdf"];
  console.log(`Description: ${description}, Suffix: ${suffixes}`);
  // خروجی مورد انتظار: Description: Portable Document Format, Suffix: pdf
}
```

توجه کنید که در کد بالا برای `application/pdf` بررسی شده است، اما می‌توانستید به همان اندازه `text/pdf` را نیز بررسی کنید. (هر دو نوع MIME یا هر دو درست هستند یا هیچ‌کدام.) علاوه بر این، در مرورگرهای فعلی نیازی به دریافت توضیحات و پسوندهای افزونه نیست، زیرا این اطلاعات نیز ثابت شده‌اند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}