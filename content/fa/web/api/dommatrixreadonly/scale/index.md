---
title: "DOMMatrixReadOnly: scale() method"
short-title: scale()
slug: Web/API/DOMMatrixReadOnly/scale
page-type: web-api-instance-method
browser-compat: api.DOMMatrixReadOnly.scale
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد **`scale()`** در رابط {{domxref("DOMMatrixReadOnly")}} یک ماتریس جدید می‌سازد که نتیجهٔ اعمال یک تبدیل مقیاس (scale) بر ماتریس اصلی است.

## Syntax

```js-nolint
scale(scaleX)
scale(scaleX, scaleY)
scale(scaleX, scaleY, scaleZ)
scale(scaleX, scaleY, scaleZ, originX)
scale(scaleX, scaleY, scaleZ, originX, originY)
scale(scaleX, scaleY, scaleZ, originX, originY, originZ)
```

### پارامترها

- `scaleX`
  - : ضریب مقیاس در امتداد محور x.
- `scaleY` {{optional_inline}}
  - : ضریب مقیاس در امتداد محور y. اگر مقداردهی نشود، به‌طور پیش‌فرض برابر با مقدار `scaleX` خواهد بود.
- `scaleZ` {{optional_inline}}
  - : ضریب مقیاس در امتداد محور z. اگر این مقدار چیزی غیر از 1 باشد، ماتریس حاصل سه‌بعدی (3D) خواهد بود.
- `originX` {{optional_inline}}
  - : مختصات x برای مبدأ تبدیل. اگر مبدأ مشخص نشود، به‌طور پیش‌فرض برابر با 0 است.
- `originY` {{optional_inline}}
  - : مختصات y برای مبدأ تبدیل. اگر مبدأ مشخص نشود، به‌طور پیش‌فرض برابر با 0 است.
- `originZ` {{optional_inline}}
  - : مختصات z برای مبدأ تبدیل. اگر مبدأ مشخص نشود، به‌طور پیش‌فرض برابر با 0 است. اگر این مقدار چیزی غیر از 0 باشد، ماتریس حاصل سه‌بعدی (3D) خواهد بود.

### مقدار بازگشتی

یک [`DOMMatrix`](/en-US/docs/Web/API/DOMMatrix) برمی‌گرداند که شامل ماتریس جدیدی است و نتیجهٔ اعمال ضریب مقیاس داده‌شده بر ابعاد x و y ماتریس اصلی، حول مبدأ مشخص‌شده است. ماتریس اصلی تغییر نمی‌کند.

اگر مقیاس حول محور z اعمال شود، ماتریس حاصل یک ماتریس سه‌بعدی 4✕4 خواهد بود.

## مثال‌ها

این SVG شامل سه مربع — یکی قرمز، یکی آبی و یکی سبز — است که همگی در مبدأ سند قرار دارند:

```html
<svg width="250" height="250" viewBox="0 0 25 25">
  <rect width="25" height="25" fill="red" />
  <rect id="transformed" width="25" height="25" fill="blue" />
  <rect id="transformedOrigin" width="25" height="25" fill="green" />
</svg>
```

این جاوااسکریپت ابتدا یک ماتریس همانی (identity matrix) می‌سازد و سپس با استفاده از متد `scale()` یک ماتریس جدید با یک پارامتر ایجاد می‌کند.

ما با ساختن یک ماتریس جدید با سه پارامتر و بررسی ویژگی `is2D` آن، بررسی می‌کنیم که آیا مرورگر از متد `scale()` با شش پارامتر پشتیبانی می‌کند یا نه. اگر این مقدار `false` باشد، یعنی مرورگر پارامتر سوم را به‌عنوان `scaleZ` پذیرفته و این ماتریس سه‌بعدی شده است.

سپس بسته به پشتیبانی مرورگر، با سه یا شش پارامتر، ماتریس جدیدی می‌سازیم که حول یک مبدأ مشخص مقیاس‌دهی شده است.

این ماتریس‌های جدید به‌عنوان `transform` روی مربع آبی و سبز اعمال می‌شوند و ابعاد و موقعیت آن‌ها را تغییر می‌دهند. مربع قرمز در جای خود باقی می‌ماند.

```js
const matrix = new DOMMatrixReadOnly();
const scaledMatrix = matrix.scale(0.5);

let scaledMatrixWithOrigin = matrix.scale(0.5, 25, 25);

// اگر مرورگر این پارامترها را به‌عنوان scaleX، scaleY و scaleZ تفسیر کرده باشد، ماتریس حاصل سه‌بعدی است
const browserExpectsSixParamScale = !scaledMatrixWithOrigin.is2D;
if (browserExpectsSixParamScale) {
  scaledMatrixWithOrigin = matrix.scale(0.5, 0.5, 1, 25, 25, 0);
}

document
  .querySelector("#transformed")
  .setAttribute("transform", scaledMatrix.toString());
document
  .querySelector("#transformedOrigin")
  .setAttribute("transform", scaledMatrixWithOrigin.toString());
```

{{EmbedLiveSample('Examples', '250', '250')}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}