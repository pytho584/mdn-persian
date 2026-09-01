---
title: "CSSValueList: length property"
short-title: length
slug: Web/API/CSSValueList/length
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.CSSValueList.length
---

{{APIRef("CSSOM")}}{{Deprecated_header}}{{non-standard_header}}

ویژگی فقط‌خواندنی **`length`** در رابط {{domxref("CSSValueList")}} تعداد {{domxref("CSSValue")}}‌های موجود در فهرست را نشان می‌دهد. محدودهٔ مقادیر معتبر شاخص‌ها، بازه‌ای بسته از `0` تا `length-1` است.

> [!NOTE]
> این ویژگی بخشی از تلاشی برای ایجاد یک CSS Object Model تایپ‌شده بود. این تلاش رها شده است و بیشتر مرورگرها آن را پیاده‌سازی نمی‌کنند.
>
> برای دستیابی به هدف خود، می‌توانید از موارد زیر استفاده کنید:
>
> - [CSS Object Model](/en-US/docs/Web/API/CSS_Object_Model) بدون تایپ، که پشتیبانی گسترده‌ای دارد، یا
> - [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API) مدرن، که پشتیبانی کمتری دارد و آزمایشی در نظر گرفته می‌شود.

## مقدار

یک `unsigned long` که تعداد {{domxref("CSSValue")}}‌ها را نشان می‌دهد.

## مشخصات

این ویژگی در اصل در مشخصات [DOM Style Level 2](https://www.w3.org/TR/DOM-Level-2-Style/) تعریف شده بود، اما از آن زمان از هرگونه تلاش برای استانداردسازی حذف شده است.

این ویژگی با [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API) مدرن، اما ناسازگار، جایگزین شده است؛ این API اکنون در مسیر استانداردسازی قرار دارد.

## سازگاری مرورگر

{{Compat}}