---
title: "CSSPrimitiveValue: setStringValue() method"
short-title: setStringValue()
slug: Web/API/CSSPrimitiveValue/setStringValue
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.CSSPrimitiveValue.setStringValue
---

{{APIRef("CSSOM")}}{{deprecated_header}}{{non-standard_header}}

متد **`setStringValue()`** از رابط {{domxref("CSSPrimitiveValue")}} برای تنظیم یک مقدار رشته‌ای استفاده می‌شود. اگر ویژگی متصل به این مقدار نتواند واحد مشخص‌شده یا مقدار رشته‌ای را بپذیرد، مقدار بدون تغییر باقی می‌ماند و یک {{domxref("DOMException")}} پرتاب می‌شود.

> [!NOTE]
> این متد بخشی از تلاش برای ایجاد یک مدل شیء CSS تایپ‌شده (typed CSS Object Model) بود. این تلاش رها شده است و اکثر مرورگرها آن را پیاده‌سازی نمی‌کنند.
>
> برای دستیابی به هدف خود می‌توانید از موارد زیر استفاده کنید:
>
> - [مدل شیء CSS بدون تایپ (untyped CSS Object Model)](/en-US/docs/Web/API/CSS_Object_Model) که به‌طور گسترده پشتیبانی می‌شود، یا
> - [API مدل شیء CSS تایپ‌شده مدرن (CSS Typed Object Model API)](/en-US/docs/Web/API/CSS_Typed_OM_API) که پشتیبانی کمتری دارد و آزمایشی در نظر گرفته می‌شود.

## نحو

```js-nolint
setStringValue(stringType, stringValue)
```

### پارامترها

- `stringType`
  - : یک `unsigned short` که نوع مقدار را نشان می‌دهد. مقادیر ممکن عبارتند از:

    | ثابت          | توضیحات                                                |
    | ------------- | ------------------------------------------------------ |
    | `CSS_ATTR`    | مقدار یک تابع {{cssxref("attr", "attr()")}} است.       |
    | `CSS_IDENT`   | مقدار یک شناسه (identifier) است.                       |
    | `CSS_STRING`  | مقدار یک {{cssxref("&lt;string&gt;")}} است.             |
    | `CSS_URI`     | مقدار یک {{cssxref("url_value", "&lt;url&gt;")}} است. |

- `stringValue`
  - : یک رشته که مقدار رشته‌ای جدید را نشان می‌دهد.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها

- `InvalidAccessError` {{domxref("DOMException")}}
  - : اگر مقدار CSS حاوی یک مقدار رشته‌ای نباشد یا مقدار رشته‌ای نتواند به واحد مشخص‌شده تبدیل شود، پرتاب می‌شود.
- `NoModificationAllowedError` {{domxref("DOMException")}}
  - : اگر ویژگی فقط خواندنی باشد، پرتاب می‌شود.

## مشخصات

این ویژگی در اصل در مشخصات [DOM Style Level 2](https://www.w3.org/TR/DOM-Level-2-Style/) تعریف شده بود، اما از آن زمان از هرگونه تلاش استانداردسازی حذف شده است.

این ویژگی توسط [API مدل شیء CSS تایپ‌شده (CSS Typed Object Model API)](/en-US/docs/Web/API/CSS_Typed_OM_API) مدرن اما ناسازگار جایگزین شده است که اکنون در مسیر استاندارد قرار دارد.

## سازگاری با مرورگر

{{Compat}}