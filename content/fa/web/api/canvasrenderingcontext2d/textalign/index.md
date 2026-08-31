---
title: "CanvasRenderingContext2D: textAlign property"
short-title: textAlign
slug: Web/API/CanvasRenderingContext2D/textAlign
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.textAlign
---

{{APIRef("Canvas API")}}

ویژگی
**`CanvasRenderingContext2D.textAlign`**
در Canvas 2D API، ترازبندی فعلی متن را هنگام رسم متن مشخص می‌کند.

ترازبندی نسبت به مقدار `x` متد
{{domxref("CanvasRenderingContext2D.fillText", "fillText()")}} انجام می‌شود. برای مثال، اگر
`textAlign` برابر با `"center"` باشد، لبه چپ متن در موقعیت
`x - (textWidth / 2)` قرار می‌گیرد.

## مقدار

مقادیر ممکن:

- `"left"`
  - : متن به چپ تراز می‌شود.
- `"right"`
  - : متن به راست تراز می‌شود.
- `"center"`
  - : متن در مرکز قرار می‌گیرد.
- `"start"`
  - : متن در ابتدای عادی خط تراز می‌شود (برای زبان‌های چپ‌به‌راست به چپ و برای زبان‌های راست‌به‌چپ به راست).
- `"end"`
  - : متن در انتهای عادی خط تراز می‌شود (برای زبان‌های چپ‌به‌راست به راست و برای زبان‌های راست‌به‌چپ به چپ).

مقدار پیش‌فرض `"start"` است.

## مثال‌ها

### ترازبندی عمومی متن

این مثال سه مقدار «فیزیکی» ویژگی `textAlign` را نشان می‌دهد:
`"left"`، `"center"` و `"right"`.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
canvas.width = 350;
const ctx = canvas.getContext("2d");
const x = canvas.width / 2;

ctx.beginPath();
ctx.moveTo(x, 0);
ctx.lineTo(x, canvas.height);
ctx.stroke();

ctx.font = "30px serif";

ctx.textAlign = "left";
ctx.fillText("left-aligned", x, 40);

ctx.textAlign = "center";
ctx.fillText("center-aligned", x, 85);

ctx.textAlign = "right";
ctx.fillText("right-aligned", x, 130);
```

#### نتیجه

{{ EmbedLiveSample('General_text_alignment', 700, 180) }}

### ترازبندی متن وابسته به جهت

این مثال دو مقدار وابسته به جهت ویژگی `textAlign` را نشان می‌دهد:
`"start"` و `"end"`. توجه داشته باشید که ویژگی
{{domxref("CanvasRenderingContext2D.direction", "direction")}} به صورت دستی
روی `"ltr"` تنظیم شده است، اگرچه این مقدار برای متن انگلیسی به صورت پیش‌فرض نیز همین است.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.font = "30px serif";
ctx.direction = "ltr";

ctx.textAlign = "start";
ctx.fillText("Start-aligned", 0, 50);

ctx.textAlign = "end";
ctx.fillText("End-aligned", canvas.width, 120);
```

#### نتیجه

{{ EmbedLiveSample('Direction-dependent_text_alignment', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این ویژگی: {{domxref("CanvasRenderingContext2D")}}