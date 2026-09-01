---
title: "CSSPrimitiveValue: getRectValue() method"
short-title: getRectValue()
slug: Web/API/CSSPrimitiveValue/getRectValue
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.CSSPrimitiveValue.getRectValue
---

{{APIRef("CSSOM")}}{{deprecated_header}}{{non-standard_header}}

متد **`getRectValue()`** از رابط {{domxref("CSSPrimitiveValue")}} برای دریافت یک مقدار rect استفاده می‌شود. اگر این مقدار CSS حاوی یک مقدار rect نباشد، یک {{domxref("DOMException")}} پرتاب می‌شود. تغییر در ویژگی استایل متناظر را می‌توان با استفاده از رابط {{domxref("Rect")}} انجام داد.

> [!NOTE]
> این متد بخشی از تلاش برای ایجاد یک مدل شیء CSS تایپ‌شده بود. این تلاش رها شده است و بیشتر مرورگرها آن را پیاده‌سازی نمی‌کنند.
>
> برای دستیابی به هدف خود، می‌توانید از:
>
> - [CSS Object Model](/en-US/docs/Web/API/CSS_Object_Model) بدون تایپ، که به‌طور گسترده پشتیبانی می‌شود، یا
> - [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API) مدرن، که کمتر پشتیبانی می‌شود و تجربی در نظر گرفته می‌شود، استفاده کنید.

## Syntax

```js-nolint
getRectValue()
```

### Parameters

هیچ.

### Return value

یک شیء {{domxref("Rect")}} که مقدار rect را نشان می‌دهد.

### Exceptions

| **Type**       | **Description**                                                                                                  |
| -------------- | ---------------------------------------------------------------------------------------------------------------- |
| `DOMException` | اگر مقدار CSS حاوی یک مقدار Rect نباشد (یعنی `CSS_RECT` نباشد)، خطای `INVALID_ACCESS_ERR` پرتاب می‌شود. |

## Examples

```js
const cs = window.getComputedStyle(document.getElementById("clippedDiv"));
const cssValue = cs.getPropertyCSSValue("clip");
console.log(cssValue.getRectValue());
```

## Specifications

این ویژگی در ابتدا در مشخصات [DOM Style Level 2](https://www.w3.org/TR/DOM-Level-2-Style/) تعریف شده بود، اما از آن زمان از هرگونه تلاش برای استانداردسازی حذف شده است.

این ویژگی با [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API) مدرن، اما ناسازگار، جایگزین شده است که اکنون در مسیر استاندارد قرار دارد.

## Browser compatibility

{{Compat}}