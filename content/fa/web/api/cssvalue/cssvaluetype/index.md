---
title: "CSSValue: cssValueType property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/CSSValue/cssValueType"
---

---
title: "CSSValue: cssValueType property"
short-title: cssValueType
slug: Web/API/CSSValue/cssValueType
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.CSSValue.cssValueType
---

{{APIRef("CSSOM")}}{{Deprecated_header}}{{non-standard_header}}

ویژگی فقط‌خواندنی **`cssValueType`** از رابط {{domxref("CSSValue")}} نوع مقدار محاسبه‌شدهٔ فعلی ویژگی CSS را نشان می‌دهد.

> [!NOTE]
> این ویژگی بخشی از تلاشی برای ایجاد یک مدل شیء CSS تایپ‌شده بود. این تلاش رها شده است و اکثر مرورگرها آن را پیاده‌سازی نمی‌کنند.
>
> برای رسیدن به هدف خود می‌توانید از این‌ها استفاده کنید:
>
> - [مدل شیء CSS](/en-US/docs/Web/API/CSS_Object_Model) بدون تایپ که به‌طور گسترده پشتیبانی می‌شود، یا
> - [API مدل شیء CSS تایپ‌شدهٔ مدرن](/en-US/docs/Web/API/CSS_Typed_OM_API) که پشتیبانی کمتری دارد و آزمایشی در نظر گرفته می‌شود.

## مقدار

یک `unsigned short` که کدی را نشان می‌دهد و نوع مقدار را مشخص می‌کند. مقادیر ممکن عبارت‌اند از:

<table class="no-markdown">
  <thead>
    <tr>
      <th>ثابت</th>
      <th>توضیحات</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>CSS_CUSTOM</code></td>
      <td>مقدار، یک مقدار سفارشی است.</td>
    </tr>
    <tr>
      <td><code>CSS_INHERIT</code></td>
      <td>
        مقدار به ارث رسیده است و <code>cssText</code> شامل
        <code>"inherit"</code> است.
      </td>
    </tr>
    <tr>
      <td><code>CSS_PRIMITIVE_VALUE</code></td>
      <td>
        مقدار یک مقدار ابتدایی است و می‌توان نمونه‌ای از رابط
        {{domxref("CSSPrimitiveValue")}} را با استفاده از روش‌های تبدیل (casting) مختص زبانِ اتصال (binding) روی این نمونه از رابط
        <code>CSSValue</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_VALUE_LIST</code></td>
      <td>
        مقدار یک فهرست <code>CSSValue</code> است و می‌توان نمونه‌ای از رابط
        {{domxref("CSSValueList")}} را با استفاده از روش‌های تبدیل مختص زبانِ اتصال روی این نمونه از رابط
        <code>CSSValue</code> به دست آورد.
      </td>
    </tr>
  </tbody>
</table>

## نمونه‌ها

```js
const styleDeclaration = document.styleSheets[0].cssRules[0].style;
const cssValue = styleDeclaration.getPropertyCSSValue("color");
console.log(cssValue.cssValueType);
```

## مشخصات

این ویژگی در ابتدا در مشخصات [DOM Style Level 2](https://www.w3.org/TR/DOM-Level-2-Style/) تعریف شده بود، اما از آن زمان از هر گونه تلاش استانداردسازی حذف شده است.

اکنون [API مدل شیء CSS تایپ‌شده](/en-US/docs/Web/API/CSS_Typed_OM_API) مدرن، اما ناسازگار، جایگزین آن شده است که در مسیر استاندارد قرار دارد.

## سازگاری مرورگر

{{Compat}}