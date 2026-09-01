---
title: "CSSValueList: item() method"
short-title: item()
slug: Web/API/CSSValueList/item
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.CSSValueList.item
---

{{APIRef("CSSOM")}}{{Deprecated_header}}{{non-standard_header}}

متد **`item()`** از رابط {{domxref("CSSValueList")}} برای دریافت یک {{domxref("CSSValue")}} بر اساس اندیس ترتیبی استفاده می‌شود.

ترتیب در این مجموعه، ترتیب مقادیر را در ویژگی استایل CSS نشان می‌دهد. اگر اندیس بزرگ‌تر یا برابر با تعداد مقادیر در فهرست باشد، این متد `null` برمی‌گرداند.

> [!NOTE]
> این متد بخشی از تلاش برای ایجاد یک مدل شیء CSS تایپ‌شده بود. این تلاش رها شده و اکثر مرورگرها آن را پیاده‌سازی نمی‌کنند.
>
> برای رسیدن به هدف خود می‌توانید از این موارد استفاده کنید:
>
> - [CSS Object Model](/en-US/docs/Web/API/CSS_Object_Model) بدون تایپ، که به‌طور گسترده پشتیبانی می‌شود، یا
> - [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API) مدرن، که پشتیبانی کمتری دارد و آزمایشی در نظر گرفته می‌شود.

## سینتکس

```js-nolint
item(index)
```

### پارامترها

- `index`
  - : یک `unsigned long` که اندیس مقدار CSS را در مجموعه نشان می‌دهد.

### مقدار بازگشتی

یک شیء {{domxref("CSSValue")}} در موقعیت `index` در `CSSValueList`، یا اگر اندیس معتبر نباشد، `null`.

## مشخصات

این ویژگی در اصل در مشخصات [DOM Style Level 2](https://www.w3.org/TR/DOM-Level-2-Style/) تعریف شده بود، اما از آن زمان از هرگونه تلاش برای استانداردسازی حذف شده است.

این ویژگی توسط [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API) مدرن، اما ناسازگار، که اکنون در مسیر استاندارد قرار دارد، جایگزین شده است.

## سازگاری با مرورگر

{{Compat}}