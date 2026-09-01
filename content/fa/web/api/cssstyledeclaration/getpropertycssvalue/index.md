---
title: "CSSStyleDeclaration: getPropertyCSSValue() method"
---

---
title: "CSSStyleDeclaration: getPropertyCSSValue() method"
short-title: getPropertyCSSValue()
slug: Web/API/CSSStyleDeclaration/getPropertyCSSValue
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.CSSStyleDeclaration.getPropertyCSSValue
---

{{ APIRef("CSSOM") }} {{deprecated_header}}{{non-standard_header}}

متد **CSSStyleDeclaration.getPropertyCSSValue()** یک {{domxref('CSSValue')}} شامل مقدار CSS برای یک ویژگی برمی‌گرداند. توجه داشته باشید که اگر نام ویژگی یک ویژگی کوتاه‌نویسی (shorthand) باشد، `null` برمی‌گرداند.

> [!NOTE]
> این رابط بخشی از تلاش برای ایجاد یک CSS Object Model نوع‌دار بود. این تلاش رها شده است و بیشتر مرورگرها آن را پیاده‌سازی نمی‌کنند.
>
> برای رسیدن به هدف خود، می‌توانید از موارد زیر استفاده کنید:
>
> - {{domxref("CSSStyleDeclaration.getPropertyValue()")}} از [CSS Object Model](/en-US/docs/Web/API/CSS_Object_Model) بدون نوع که به‌طور گسترده‌ای پشتیبانی می‌شود، یا
> - {{domxref("Element.computedStyleMap()")}} از [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API) مدرن که پشتیبانی کمتری دارد و تجربی در نظر گرفته می‌شود.

## Syntax

```js-nolint
getPropertyCSSValue(property)
```

### Parameters

- `property`
  - : رشته‌ای که نام ویژگی مورد نظر برای بازیابی را مشخص می‌کند.

### Return value

یک {{domxref('CSSValue')}} شامل مقدار CSS برای یک ویژگی. اگر چنین مقداری وجود نداشته باشد، `null` برمی‌گرداند.

## Examples

کد جاوااسکریپت زیر یک شیء حاوی مقادیر محاسبه‌شده RGB را از ویژگی CSS `color` دریافت می‌کند:

```js
const style = window.getComputedStyle(elem, null);
const rgbObj = style.getPropertyCSSValue("color").getRGBColorValue();
```

## Specifications

این ویژگی در اصل در مشخصات [DOM Style Level 2](https://www.w3.org/TR/DOM-Level-2-Style/) تعریف شده بود، اما از آن زمان از هرگونه تلاش استانداردسازی کنار گذاشته شده است.

این ویژگی با [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API) مدرن، اما ناسازگار، جایگزین شده است که اکنون در مسیر استانداردسازی قرار دارد.

## Browser compatibility

{{Compat}}