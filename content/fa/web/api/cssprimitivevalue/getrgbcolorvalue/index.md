---
title: "CSSPrimitiveValue: getRGBColorValue() method"
short-title: getRGBColorValue()
slug: Web/API/CSSPrimitiveValue/getRGBColorValue
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.CSSPrimitiveValue.getRGBColorValue
---

{{APIRef("CSSOM")}}{{deprecated_header}}{{non-standard_header}}

متد **`getRGBColorValue()`** از رابط {{domxref("CSSPrimitiveValue")}} برای دریافت یک مقدار رنگ RGB استفاده می‌شود. اگر این مقدار CSS حاوی مقدار رنگ RGB نباشد، یک {{domxref("DOMException")}} پرتاب می‌شود. تغییر در ویژگی سبک متناظر را می‌توان با استفاده از رابط {{domxref("RGBColor")}} انجام داد.

> [!NOTE]
> این متد بخشی از تلاش برای ایجاد یک مدل شیء CSS تایپ‌شده بود. این تلاش رها شده است و بیشتر مرورگرها آن را پیاده‌سازی نمی‌کنند.
>
> برای دستیابی به هدف خود، می‌توانید از:
>
> - مدل شیء CSS بدون تایپ (CSS Object Model) که به طور گسترده پشتیبانی می‌شود، یا
> - API مدرن مدل شیء CSS تایپ‌شده (CSS Typed Object Model API) که کمتر پشتیبانی می‌شود و آزمایشی در نظر گرفته می‌شود، استفاده کنید.

## نحو

```js-nolint
getRGBColorValue()
```

### پارامترها

هیچکدام.

### مقدار برگشتی

یک شیء {{domxref("RGBColor")}} که مقدار رنگ را نمایش می‌دهد.

### استثناها

| نوع            | توضیحات                                                                                                 |
| -------------- | ------------------------------------------------------------------------------------------------------- |
| `DOMException` | یک خطای `INVALID_ACCESS_ERR` پرتاب می‌شود اگر ویژگی متصل نتواند مقدار رنگ RGB برگرداند (یعنی این `CSS_RGBCOLOR` نیست). |

## مثال‌ها

```js
const cs = window.getComputedStyle(document.body);
const cssValue = cs.getPropertyCSSValue("color");
console.log(cssValue.getRGBColorValue());
```

## مشخصات

این ویژگی در ابتدا در مشخصات [DOM Style Level 2](https://www.w3.org/TR/DOM-Level-2-Style/) تعریف شده بود، اما از آن زمان به بعد از هرگونه تلاش استانداردسازی حذف شده است.

این ویژگی با یک API مدرن اما ناسازگار، یعنی [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API) که اکنون در مسیر استاندارد قرار دارد، جایگزین شده است.

## سازگاری با مرورگر

{{Compat}}