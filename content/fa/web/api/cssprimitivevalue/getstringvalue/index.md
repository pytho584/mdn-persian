---
title: "CSSPrimitiveValue: getStringValue() method"
short-title: getStringValue()
slug: Web/API/CSSPrimitiveValue/getStringValue
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.CSSPrimitiveValue.getStringValue
---

{{APIRef("CSSOM")}}{{deprecated_header}}{{non-standard_header}}

**`getStringValue()`** 方法属于 {{domxref("CSSPrimitiveValue")}} 接口، برای دریافت یک مقدار رشته‌ای استفاده می‌شود. اگر این مقدار CSS حاوی مقدار رشته‌ای نباشد، یک {{domxref("DOMException")}} پرتاب می‌شود.

> [!NOTE]
> این روش بخشی از تلاش برای ایجاد یک مدل شیء CSS تایپ‌شده (Typed CSS Object Model) بود. این تلاش رها شده است و اکثر مرورگرها آن را پیاده‌سازی نمی‌کنند.
>
> برای رسیدن به هدف خود، می‌توانید از موارد زیر استفاده کنید:
>
> - [مدل شیء CSS بدون تایپ](/en-US/docs/Web/API/CSS_Object_Model) که به‌طور گسترده پشتیبانی می‌شود، یا
> - [API مدل شیء CSS تایپ‌شده مدرن](/en-US/docs/Web/API/CSS_Typed_OM_API) که پشتیبانی کمتری دارد و تجربی محسوب می‌شود.

## Syntax

```js-nolint
getStringValue()
```

### Parameters

هیچ.

### Return value

یک مقدار از نوع `string`.

### Exceptions

| **Type**       | **Description**                                                                     |
| -------------- | ----------------------------------------------------------------------------------- |
| `DOMException` | اگر مقدار CSS حاوی مقدار رشته‌ای نباشد، یک خطای `INVALID_ACCESS_ERR` پرتاب می‌شود. |

## Examples

```js
const cs = window.getComputedStyle(document.body);
const cssValue = cs.getPropertyCSSValue("display");
console.log(cssValue.getStringValue());
```

## Specifications

این ویژگی در ابتدا در مشخصات [DOM Style Level 2](https://www.w3.org/TR/DOM-Level-2-Style/) تعریف شده بود، اما از آن زمان از هرگونه تلاش برای استانداردسازی حذف شده است.

اکنون با [API مدل شیء CSS تایپ‌شده](/en-US/docs/Web/API/CSS_Typed_OM_API) مدرن، اما ناسازگار، جایگزین شده است که در مسیر استاندارد قرار دارد.

## Browser compatibility

{{Compat}}