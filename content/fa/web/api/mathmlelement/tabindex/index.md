---
title: "MathMLElement: tabIndex property"
short-title: tabIndex
slug: Web/API/MathMLElement/tabIndex
page-type: web-api-instance-property
browser-compat: api.MathMLElement.tabIndex
---

{{APIRef("MathML")}}

ویژگی **`tabIndex`** در رابط {{DOMxRef("MathMLElement")}} ترتیب پیمایش با کلید Tab را برای عنصر MathML فعلی مشخص می‌کند.

ترتیب پیمایش با Tab به صورت زیر است:

1. عناصر دارای `tabIndex` مثبت. عناصری که مقادیر `tabIndex` یکسانی دارند باید به ترتیب ظاهرشدن پیمایش شوند. پیمایش از کمترین `tabIndex` به بیشترین آن انجام می‌شود.
2. عناصری که از ویژگی `tabIndex` پشتیبانی نمی‌کنند، یا از آن پشتیبانی کرده و `tabIndex` را برابر `0` قرار می‌دهند، به ترتیب ظاهرشدن پیمایش می‌شوند.

عناصر غیرفعال در ترتیب پیمایش با Tab شرکت نمی‌کنند. مقادیر نیازی به ترتیب پیوسته ندارند و نباید با مقدار خاصی شروع شوند. حتی می‌توانند منفی باشند، البته هر مرورگر مقادیر بسیار بزرگ را کوتاه می‌کند.

## مقدار

یک عدد صحیح.

## نمونه‌ها

### استفاده از ویژگی tabIndex

```html
<math id="math1" tabindex="2">
  <msup>
    <mi>a</mi>
    <mn>2</mn>
  </msup>
</math>

<math id="math2">
  <mfrac>
    <mn>1</mn>
    <mn>2</mn>
  </mfrac>
</math>
```

```js
const math1 = document.getElementById("math1");
const math2 = document.getElementById("math2");

// Access and modify the tabIndex
console.log(math1.tabIndex); // 2
math2.tabIndex = 1; // Add math2 to the tab order before math1

// Programmatically focus on an element with negative tabIndex
math1.tabIndex = -1;
math1.focus(); // Works, even though it is not in the tabbing order
```

### نتیجه

{{EmbedLiveSample("tabindex",100,100)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLElement.tabIndex")}}
- [دسترس‌پذیری ویجت‌های جاوااسکریپت قابل پیمایش با صفحه‌کلید](/en-US/docs/Web/Accessibility/Guides/Keyboard-navigable_JavaScript_widgets)
- [`tabindex`](/en-US/docs/Web/MathML/Reference/Global_attributes/tabindex)