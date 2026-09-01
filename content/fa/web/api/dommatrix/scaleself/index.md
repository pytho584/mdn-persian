---
title: "DOMMatrix: scaleSelf() method"
short-title: scaleSelf()
slug: Web/API/DOMMatrix/scaleSelf
page-type: web-api-instance-method
browser-compat: api.DOMMatrix.scaleSelf
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد **`scaleSelf()`** از رابط {{domxref("DOMMatrix")}} یک متد تبدیل درجا است که با اعمال ضریب مقیاس مشخص‌شده، حول مبدأ داده‌شده (با پیش‌فرض `(0, 0)`) ماتریس را تغییر می‌دهد و ماتریس مقیاس‌شده را برمی‌گرداند.

برای اعمال مقیاس به یک ماتریس بدون تغییر آن، به {{domxref("DOMMatrixReadOnly.scale()")}} مراجعه کنید؛ این متد یک ماتریس مقیاس‌شدهٔ جدید می‌سازد و ماتریس اصلی را بدون تغییر باقی می‌گذارد.

## نحو

```js-nolint
scaleSelf()
scaleSelf(scaleX)
scaleSelf(scaleX, scaleY)
scaleSelf(scaleX, scaleY, scaleZ)
scaleSelf(scaleX, scaleY, scaleZ, originX)
scaleSelf(scaleX, scaleY, scaleZ, originX, originY)
scaleSelf(scaleX, scaleY, scaleZ, originX, originY, originZ)
```

### پارامترها

- `scaleX` {{optional_inline}}
  - : ضریبی برای مقدار مقیاس در محور x. اگر ارائه نشود، به‌طور پیش‌فرض `1` است.
- `scaleY` {{optional_inline}}
  - : ضریبی برای مقدار مقیاس در محور y. اگر ارائه نشود، به‌طور پیش‌فرض برابر با مقدار `scaleX` است.
- `scaleZ` {{optional_inline}}
  - : ضریبی برای مقدار مقیاس در محور z. اگر این مقدار چیزی غیر از 1 باشد، ماتریس حاصل سه‌بعدی خواهد بود.
- `originX` {{optional_inline}}
  - : مختصات x برای مبدأ تبدیل. اگر مبدأ ارائه نشود، به‌طور پیش‌فرض 0 است.
- `originY` {{optional_inline}}
  - : مختصات y برای مبدأ تبدیل. اگر مبدأ ارائه نشود، به‌طور پیش‌فرض 0 است.
- `originZ` {{optional_inline}}
  - : مختصات z برای مبدأ تبدیل. اگر مبدأ ارائه نشود، به‌طور پیش‌فرض 0 است. اگر این مقدار چیزی غیر از 0 باشد، ماتریس حاصل سه‌بعدی خواهد بود.

### مقدار بازگشتی

خود ماتریس را برمی‌گرداند؛ یک {{domxref("DOMMatrix")}}. اگر مقیاس حول محور z اعمال شود، ماتریس یک ماتریس سه‌بعدی 4✕4 خواهد بود.

## مثال‌ها

این SVG شامل دو مربع نیمه‌شفاف، یکی قرمز و یکی آبی است که هر دو در مبدأ سند قرار دارند:

```html
<svg viewBox="0 0 50 50" height="200">
  <rect width="25" height="25" fill="#ff000099" />
  <rect id="transformed" width="25" height="25" fill="#0000ff99" />
</svg>
```

این جاوااسکریپت ابتدا یک ماتریس می‌سازد، سپس با استفاده از متد `scaleSelf()` ماتریس را طوری مقیاس می‌دهد که عرض آن نصف و ارتفاع آن دو برابر شود.

سپس این ماتریس به‌عنوان یک `transform` روی مربع آبی اعمال می‌شود و ابعاد و موقعیت آن تغییر می‌کند. مربع قرمز بدون تغییر باقی می‌ماند.

```js
const matrix = new DOMMatrix();
matrix.scaleSelf(0.5, 2);

document
  .querySelector("#transformed")
  .setAttribute("transform", matrix.toString());
```

{{EmbedLiveSample('Examples', '', '220')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrixReadOnly.scale()")}}
- {{domxref("DOMMatrix.scale3dSelf()")}}
- ویژگی CSS {{cssxref("transform")}} و توابع {{cssxref("transform-function/scale", "scaleSelf()")}} و {{cssxref("transform-function/matrix", "matrix()")}}
- ماژول [تبدیل‌های CSS](/en-US/docs/Web/CSS/Guides/Transforms)
- ویژگی [`transform`](/en-US/docs/Web/SVG/Reference/Attribute/transform) در SVG
- متد {{domxref("CanvasRenderingContext2D.transform()", "transform()")}} از رابط {{domxref("CanvasRenderingContext2D")}}