---
title: "CSSPrimitiveValue: getCounterValue() method"
---

---
title: "CSSPrimitiveValue: getCounterValue() method"
short-title: getCounterValue()
slug: Web/API/CSSPrimitiveValue/getCounterValue
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.CSSPrimitiveValue.getCounterValue
---

{{APIRef("CSSOM")}}{{deprecated_header}}{{non-standard_header}}

متد **`getCounterValue()`** از رابط {{domxref("CSSPrimitiveValue")}} برای دریافت مقدار [counter](/en-US/docs/Web/CSS/Guides/Counter_styles/Using_counters) استفاده می‌شود. اگر این مقدار CSS حاوی مقدار counter نباشد، یک {{domxref("DOMException")}} برانگیخته می‌شود. اصلاح ویژگی استایل مربوطه را می‌توان از طریق رابط {{domxref("Counter")}} انجام داد.

> [!NOTE]
> این روش بخشی از تلاش برای ایجاد یک مدل شیء CSS تایپ‌شده بود. این تلاش رها شده است و بیشتر مرورگرها آن را پیاده‌سازی نمی‌کنند.
>
> برای رسیدن به هدف خود می‌توانید از موارد زیر استفاده کنید:
>
> - [مدل شیء CSS](/en-US/docs/Web/API/CSS_Object_Model) بدون تایپ که به‌طور گسترده پشتیبانی می‌شود، یا
> - [API مدل شیء تایپ‌شده CSS](/en-US/docs/Web/API/CSS_Typed_OM_API) مدرن که کمتر پشتیبانی می‌شود و آزمایشی در نظر گرفته می‌شود.

## Syntax

```js-nolint
getCounterValue()
```

### Parameters

هیچ.

### Return value

یک شیء {{domxref("Counter")}} که مقدار counter را نشان می‌دهد.

### Exceptions

| **Type**       | **Description**                                                                                                         |
| -------------- | ----------------------------------------------------------------------------------------------------------------------- |
| `DOMException` | اگر مقدار CSS حاوی مقدار `Counter` نباشد (مثلاً `CSS_COUNTER` نباشد)، خطای `INVALID_ACCESS_ERR` برانگیخته می‌شود. |

## Specifications

این ویژگی در ابتدا در مشخصات [DOM Style Level 2](https://www.w3.org/TR/DOM-Level-2-Style/) تعریف شده بود، اما از آن زمان از هرگونه تلاش استانداردسازی حذف شده است.

با [API مدل شیء تایپ‌شده CSS](/en-US/docs/Web/API/CSS_Typed_OM_API) مدرن اما ناسازگار جایگزین شده است که اکنون در مسیر استاندارد قرار دارد.

## Browser compatibility

{{Compat}}