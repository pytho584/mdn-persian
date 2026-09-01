---
title: "CSSPrimitiveValue: primitiveType property"
short-title: primitiveType
slug: Web/API/CSSPrimitiveValue/primitiveType
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.CSSPrimitiveValue.primitiveType
---

{{APIRef("CSSOM")}}{{deprecated_header}}{{non-standard_header}}

ویژگی فقط‌خواندنی **`primitiveType`** در رابط {{domxref("CSSPrimitiveValue")}} نوع یک مقدار CSS را نشان می‌دهد.

> [!NOTE]
> این ویژگی بخشی از تلاش برای ایجاد یک مدل شیءِ CSS تایپ‌شده (typed CSS Object Model) بود. این تلاش کنار گذاشته شده است و بیشتر مرورگرها آن را پیاده‌سازی نمی‌کنند.
>
> برای رسیدن به هدف خود می‌توانید از این‌ها استفاده کنید:
>
> - [مدل شیءِ CSS](/en-US/docs/Web/API/CSS_Object_Model) بدون تایپ (untyped) که به‌طور گسترده پشتیبانی می‌شود، یا
> - [API مدل شیءِ CSS تایپ‌شده](/en-US/docs/Web/API/CSS_Typed_OM_API) مدرن که پشتیبانی کمتری دارد و آزمایشی در نظر گرفته می‌شود.

## مقدار

یک `unsigned short` که نوع مقدار را نشان می‌دهد. مقادیر ممکن عبارت‌اند از:

<table class="no-markdown">
  <thead>
    <tr>
      <th>ثابت</th>
      <th>توضیحات</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>CSS_ATTR</code></td>
      <td>
        مقدار یک تابع {{cssxref("attr", "attr()")}} است. این مقدار را می‌توان با استفاده از روش <code>getStringValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_CM</code></td>
      <td>
        مقدار یک {{cssxref("&lt;length&gt;")}} بر حسب سانتی‌متر است.
        این مقدار را می‌توان با استفاده از روش
        <code>getFloatValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_COUNTER</code></td>
      <td>
        مقدار یک تابع
        <a href="/en-US/docs/Web/CSS/Guides/Counter_styles/Using_counters"
          >counter یا counters</a
        >
        است. این مقدار را می‌توان با استفاده از روش
        <code>getCounterValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_DEG</code></td>
      <td>
        مقدار یک {{cssxref("&lt;angle&gt;")}} بر حسب درجه است. این
        مقدار را می‌توان با استفاده از روش <code>getFloatValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_DIMENSION</code></td>
      <td>
        مقدار یک {{cssxref("&lt;number&gt;")}} با بُعدی نامشخص است. این مقدار را می‌توان با استفاده از روش
        <code>getFloatValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_EMS</code></td>
      <td>
        مقدار یک {{cssxref("&lt;length&gt;")}} بر حسب واحد em است. این
        مقدار را می‌توان با استفاده از روش <code>getFloatValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_EXS</code></td>
      <td>
        مقدار یک {{cssxref("&lt;length&gt;")}} بر حسب واحد ex است. این
        مقدار را می‌توان با استفاده از روش <code>getFloatValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_GRAD</code></td>
      <td>
        مقدار یک {{cssxref("&lt;angle&gt;")}} بر حسب گراد (grad) است. این مقدار
        را می‌توان با استفاده از روش <code>getFloatValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_HZ</code></td>
      <td>
        مقدار یک {{cssxref("&lt;frequency&gt;")}} بر حسب هرتز است.
        این مقدار را می‌توان با استفاده از روش getFloatValue به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_IDENT</code></td>
      <td>
        مقدار یک شناسه (identifier) است. این مقدار را می‌توان با استفاده از روش
        <code>getStringValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_IN</code></td>
      <td>
        مقدار یک {{cssxref("&lt;length&gt;")}} بر حسب اینچ است. این
        مقدار را می‌توان با استفاده از روش <code>getFloatValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_KHZ</code></td>
      <td>
        مقدار یک {{cssxref("&lt;frequency&gt;")}} بر حسب
        کیلوهرتز است. این مقدار را می‌توان با استفاده از روش
        <code>getFloatValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_MM</code></td>
      <td>
        مقدار یک {{cssxref("&lt;length&gt;")}} بر حسب میلی‌متر است.
        این مقدار را می‌توان با استفاده از روش
        <code>getFloatValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_MS</code></td>
      <td>
        مقدار یک {{cssxref("&lt;time&gt;")}} بر حسب میلی‌ثانیه است. این
        مقدار را می‌توان با استفاده از روش <code>getFloatValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_NUMBER</code></td>
      <td>
        مقدار یک {{cssxref("&lt;number&gt;")}} ساده است. این
        مقدار را می‌توان با استفاده از روش <code>getFloatValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_PC</code></td>
      <td>
        مقدار یک {{cssxref("&lt;length&gt;")}} بر حسب پیکا (pica) است. این
        مقدار را می‌توان با استفاده از روش <code>getFloatValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_PERCENTAGE</code></td>
      <td>
        مقدار یک {{cssxref("&lt;percentage&gt;")}} است. این مقدار
        را می‌توان با استفاده از روش <code>getFloatValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_PT</code></td>
      <td>
        مقدار یک {{cssxref("&lt;length&gt;")}} بر حسب پوینت است. این
        مقدار را می‌توان با استفاده از روش <code>getFloatValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_PX</code></td>
      <td>
        مقدار یک {{cssxref("&lt;length&gt;")}} بر حسب پیکسل است. این
        مقدار را می‌توان با استفاده از روش <code>getFloatValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_RAD</code></td>
      <td>
        مقدار یک {{cssxref("&lt;angle&gt;")}} بر حسب رادیان است. این
        مقدار را می‌توان با استفاده از روش <code>getFloatValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_RECT</code></td>
      <td>
        مقدار یک تابع {{cssxref("shape", "rect()", "#Syntax")}}
        است. این مقدار را می‌توان با استفاده از روش
        <code>getRectValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_RGBCOLOR</code></td>
      <td>
        مقدار یک {{cssxref("&lt;color&gt;")}} است. این مقدار را می‌توان
        با استفاده از روش <code>getRGBColorValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_S</code></td>
      <td>
        مقدار یک {{cssxref("&lt;time&gt;")}} بر حسب ثانیه است. این
        مقدار را می‌توان با استفاده از روش <code>getFloatValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_STRING</code></td>
      <td>
        مقدار یک {{cssxref("&lt;string&gt;")}} است. این مقدار را می‌توان
        با استفاده از روش <code>getStringValue()</code> به دست آورد.
      </td>
    </tr>
    <tr>
      <td><code>CSS_UNKNOWN</code></td>
      <td>
        مقدار، یک مقدار CSS2 شناخته‌شده نیست. این مقدار فقط با استفاده از ویژگی {{domxref("CSSValue.cssText", "cssText")}}
        قابل دریافت است.
      </td>
    </tr>
    <tr>
      <td><code>CSS_URI</code></td>
      <td>
        مقدار یک {{cssxref("url_value", "&lt;url&gt;")}} است. این مقدار را می‌توان
        با استفاده از روش <code>getStringValue()</code> به دست آورد.
      </td>
    </tr>
  </tbody>
</table>

## مثال‌ها

```js
const cs = window.getComputedStyle(document.body);
const cssValue = cs.getPropertyCSSValue("color");
console.log(cssValue.primitiveType);
```

## مشخصات

این ویژگی در ابتدا در مشخصات [DOM Style Level 2](https://www.w3.org/TR/DOM-Level-2-Style/) تعریف شده بود، اما از آن زمان از هرگونه تلاش برای استانداردسازی حذف شده است.

این ویژگی با [API مدل شیءِ CSS تایپ‌شده](/en-US/docs/Web/API/CSS_Typed_OM_API) مدرن، اما ناسازگار، جایگزین شده است که اکنون در مسیر استانداردسازی قرار دارد.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CSSStyleDeclaration.getPropertyCSSValue()")}}