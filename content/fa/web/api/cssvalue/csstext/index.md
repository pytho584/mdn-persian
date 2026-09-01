---
title: "CSSValue: cssText property"
short-title: cssText
slug: Web/API/CSSValue/cssText
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.CSSValue.cssText
---

{{APIRef("CSSOM")}}{{Deprecated_header}}{{non-standard_header}}

ویژگی **`cssText`** از واسط {{domxref("CSSValue")}} نشان‌دهندهٔ مقدار جاریِ محاسبه‌شدهٔ ویژگی CSS است.

> [!NOTE]
> این ویژگی بخشی از تلاش برای ایجاد یک CSS Object Model تایپ‌شده (typed CSS Object Model) بود. این تلاش کنار گذاشته شده و بیشتر مرورگرها آن را پیاده‌سازی نمی‌کنند.
>
> برای رسیدن به هدف خود می‌توانید از موارد زیر استفاده کنید:
>
> - [CSS Object Model](/en-US/docs/Web/API/CSS_Object_Model) بدون تایپ که پشتیبانی گسترده‌ای دارد، یا
> - [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API) مدرن که پشتیبانی کمتری دارد و آزمایشی محسوب می‌شود.

## مقدار

یک رشته که مقدار جاری ویژگی CSS را نشان می‌دهد.

## مثال‌ها

```js
const styleDeclaration = document.styleSheets[0].cssRules[0].style;
const cssValue = styleDeclaration.getPropertyCSSValue("color");
console.log(cssValue.cssText);
```

## مشخصات

این ویژگی در ابتدا در مشخصات [DOM Style Level 2](https://www.w3.org/TR/DOM-Level-2-Style/) تعریف شده بود، اما از آن زمان از تمام تلاش‌های استانداردسازی حذف شده است.

این ویژگی با [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API) مدرن، اما ناسازگار، جایگزین شده است که اکنون در مسیر استاندارد قرار دارد.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CSSStyleDeclaration.getPropertyCSSValue()")}}