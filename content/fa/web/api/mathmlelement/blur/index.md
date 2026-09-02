---
title: "MathMLElement: blur() method"
short-title: blur()
slug: Web/API/MathMLElement/blur
page-type: web-api-instance-method
browser-compat: api.MathMLElement.blur
---

{{APIRef("MathML")}}

متد **`blur()`** از رابط {{domxref("MathMLElement")}}، فوکوس صفحه‌کلید را از عنصر MathML جاری حذف می‌کند.

## نحو (Syntax)

```js-nolint
blur()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### حذف فوکوس از یک عنصر MathML

#### HTML

```html
<div>
  <math>
    <msup id="myMath" tabindex="0">
      <mi>x</mi>
      <mn>2</mn>
    </msup>
  </math>
  <button id="focusButton">فوکوس روی Math</button>
  <button id="blurButton">حذف فوکوس از Math</button>
</div>
```

#### JavaScript

```js
const mathElement = document.getElementById("myMath");
const focusButton = document.getElementById("focusButton");
const blurButton = document.getElementById("blurButton");

// فوکوس روی MathMLElement هنگام کلیک روی دکمه "Focus"
focusButton.addEventListener("click", () => {
  mathElement.focus();
});

// حذف فوکوس از MathMLElement هنگام کلیک روی دکمه "Blur"
blurButton.addEventListener("click", () => {
  mathElement.blur();
});
```

### نتیجه

{{EmbedLiveSample("blur",100,100)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("MathMLElement.focus()")}}
- {{domxref("HTMLElement.blur()")}}