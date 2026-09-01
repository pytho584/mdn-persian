---
title: "CSSPrimitiveValue: getFloatValue() method"
short-title: getFloatValue()
slug: Web/API/CSSPrimitiveValue/getFloatValue
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.CSSPrimitiveValue.getFloatValue
---

{{APIRef("CSSOM")}}{{deprecated_header}}{{non-standard_header}}

**`getFloatValue()`** متدی از رابط {{domxref("CSSPrimitiveValue")}} است که برای دریافت یک مقدار اعشاری (float) در واحد مشخص‌شده استفاده می‌شود. اگر این مقدار CSS حاوی مقدار اعشاری نباشد یا نتوان آن را به واحد مشخص‌شده تبدیل کرد، یک {{domxref("DOMException")}} پرتاب می‌شود.

> [!NOTE]
> این روش بخشی از تلاشی برای ایجاد یک مدل شیء CSS تایپ‌شده بود. این تلاش کنار گذاشته شده است و اکثر مرورگرها آن را پیاده‌سازی نمی‌کنند.
>
> برای رسیدن به هدف خود، می‌توانید از:
>
> - [مدل شیء CSS](/en-US/docs/Web/API/CSS_Object_Model) بدون تایپ که به‌طور گسترده پشتیبانی می‌شود، یا
> - [API مدل شیء CSS تایپ‌شده](/en-US/docs/Web/API/CSS_Typed_OM_API) مدرن که کمتر پشتیبانی می‌شود و تجربی در نظر گرفته می‌شود، استفاده کنید.

## Syntax

```js-nolint
getFloatValue(unit)
```

### Parameters

- `unit`
  - : یک `unsigned short` که کد نوع واحد را نشان می‌دهد و مقدار باید در آن واحد برگردانده شود. مقادیر معتبر عبارتند از:

    | Constant         | Description                                                                                                            |
    | ---------------- | ---------------------------------------------------------------------------------------------------------------------- |
    | `CSS_CM`         | مقدار یک {{cssxref("&lt;length&gt;")}} بر حسب سانتی‌متر است.                                                           |
    | `CSS_DEG`        | مقدار یک {{cssxref("&lt;angle&gt;")}} بر حسب درجه است.                                                                 |
    | `CSS_DIMENSION`  | مقدار یک {{cssxref("&lt;number&gt;")}} با بُعد ناشناخته است.                                                          |
    | `CSS_EMS`        | مقدار یک {{cssxref("&lt;length&gt;")}} بر حسب واحد em است.                                                             |
    | `CSS_EXS`        | مقدار یک {{cssxref("&lt;length&gt;")}} بر حسب واحد ex است.                                                             |
    | `CSS_GRAD`       | مقدار یک {{cssxref("&lt;angle&gt;")}} بر حسب grad است.                                                                 |
    | `CSS_HZ`         | مقدار یک {{cssxref("&lt;frequency&gt;")}} بر حسب هرتز است. این مقدار را می‌توان با استفاده از متد getFloatValue به دست آورد. |
    | `CSS_IN`         | مقدار یک {{cssxref("&lt;length&gt;")}} بر حسب اینچ است.                                                                |
    | `CSS_KHZ`        | مقدار یک {{cssxref("&lt;frequency&gt;")}} بر حسب کیلوهرتز است.                                                         |
    | `CSS_MM`         | مقدار یک {{cssxref("&lt;length&gt;")}} بر حسب میلی‌متر است.                                                            |
    | `CSS_MS`         | مقدار یک {{cssxref("&lt;time&gt;")}} بر حسب میلی‌ثانیه است.                                                            |
    | `CSS_NUMBER`     | مقدار یک {{cssxref("&lt;number&gt;")}} ساده است.                                                                      |
    | `CSS_PC`         | مقدار یک {{cssxref("&lt;length&gt;")}} بر حسب پیکا است.                                                                |
    | `CSS_PERCENTAGE` | مقدار یک {{cssxref("&lt;percentage&gt;")}} است.                                                                       |
    | `CSS_PT`         | مقدار یک {{cssxref("&lt;length&gt;")}} بر حسب پوینت است.                                                               |
    | `CSS_PX`         | مقدار یک {{cssxref("&lt;length&gt;")}} بر حسب پیکسل است.                                                               |
    | `CSS_RAD`        | مقدار یک {{cssxref("&lt;angle&gt;")}} بر حسب رادیان است.                                                               |
    | `CSS_S`          | مقدار یک {{cssxref("&lt;time&gt;")}} بر حسب ثانیه است.                                                                 |

### Return value

یک مقدار `float` در واحد مشخص‌شده.

### Exceptions

<table class="no-markdown">
  <thead>
    <tr>
      <th scope="col"><strong>نوع</strong></th>
      <th scope="col"><strong>توضیحات</strong></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>DOMException</code></td>
      <td>
        اگر مقدار CSS حاوی مقدار اعشاری نباشد یا اگر مقدار اعشاری نتواند به واحد مشخص‌شده تبدیل شود، یک <code>INVALID_ACCESS_ERR</code> پرتاب می‌شود.
      </td>
    </tr>
  </tbody>
</table>

## Examples

```js
const cs = window.getComputedStyle(document.body);
const cssValue = cs.getPropertyCSSValue("margin-top");
console.log(cssValue.getFloatValue(CSSPrimitiveValue.CSS_CM));
```

## Specifications

این ویژگی در اصل در مشخصات [DOM Style Level 2](https://www.w3.org/TR/DOM-Level-2-Style/) تعریف شده بود، اما از آن زمان از هرگونه تلاش استانداردسازی حذف شده است.

این ویژگی توسط [API مدل شیء CSS تایپ‌شده](/en-US/docs/Web/API/CSS_Typed_OM_API) مدرن، اما ناسازگار، که اکنون در مسیر استاندارد قرار دارد، جایگزین شده است.

## Browser compatibility

{{Compat}}