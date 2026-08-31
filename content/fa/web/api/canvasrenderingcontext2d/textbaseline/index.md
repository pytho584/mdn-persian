---
title: "CanvasRenderingContext2D: textBaseline property"
short-title: textBaseline
slug: Web/API/CanvasRenderingContext2D/textBaseline
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.textBaseline
---

{{APIRef("Canvas API")}}

خصوصیت **`CanvasRenderingContext2D.textBaseline`** در Canvas 2D API، baseline متن فعلی را هنگام رسم متن مشخص می‌کند.

## مقدار

مقادیر ممکن:

- `"top"`
  - : خط پایه (baseline) متن در بالای مربع em قرار دارد.
- `"hanging"`
  - : خط پایه متن، baseline آویزان (hanging) است. (مورد استفاده در خط تبتی و دیگر خطوط هندی.)
- `"middle"`
  - : خط پایه متن در وسط مربع em قرار دارد.
- `"alphabetic"`
  - : خط پایه متن، {{glossary("Baseline/Typography", "alphabetic baseline")}} عادی است. مقدار پیش‌فرض.
- `"ideographic"`
  - : خط پایه متن، baseline ایدئوگرافیک (ideographic) است؛ این پایین بدنه کاراکترها است، اگر بدنه اصلی کاراکترها زیر baseline الفبایی بیرون زده باشد. (مورد استفاده در خطوط چینی، ژاپنی و کرهای.)
- `"bottom"`
  - : خط پایه متن، پایین جعبه محدودکننده (bounding box) است. این با baseline ایدئوگرافیک تفاوت دارد زیرا baseline ایدئوگرافیک descenderها (قسمت‌های پایین‌رونده حروف) را در نظر نمی‌گیرد.

مقدار پیش‌فرض `"alphabetic"` است.

## مثال‌ها

### مقایسه مقادیر خصوصیت

این مثال مقادیر مختلف `textBaseline` را نشان می‌دهد.

#### HTML

```html
<canvas id="canvas" width="550" height="500"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

const baselines = [
  "top",
  "hanging",
  "middle",
  "alphabetic",
  "ideographic",
  "bottom",
];
ctx.font = "36px serif";
ctx.strokeStyle = "red";

baselines.forEach((baseline, index) => {
  ctx.textBaseline = baseline;
  const y = 75 + index * 75;
  ctx.beginPath();
  ctx.moveTo(0, y + 0.5);
  ctx.lineTo(550, y + 0.5);
  ctx.stroke();
  ctx.fillText(`Abcdefghijklmnop (${baseline})`, 0, y);
});
```

#### نتیجه

{{ EmbedLiveSample('Comparison_of_property_values', 700, 550) }}

### مقایسه مقادیر خصوصیت روی یک خط

مانند مثال قبلی، این مثال مقادیر مختلف `textBaseline` را نشان می‌دهد، اما این بار همه آنها به صورت افقی روی یک خط قرار گرفته‌اند تا تفاوت‌ها راحت‌تر دیده شود.

#### HTML

```html
<canvas id="canvas" width="724" height="160"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

const baselines = [
  "top",
  "hanging",
  "middle",
  "alphabetic",
  "ideographic",
  "bottom",
];
ctx.font = "20px serif";
ctx.strokeStyle = "red";

ctx.beginPath();
ctx.moveTo(0, 100);
ctx.lineTo(840, 100);
ctx.moveTo(0, 55);
ctx.stroke();

baselines.forEach((baseline, index) => {
  ctx.save();
  ctx.textBaseline = baseline;
  let x = index * 120 + 10;
  ctx.fillText("Abcdefghijk", x, 100);
  ctx.restore();
  ctx.fillText(baseline, x + 5, 50);
});
```

#### نتیجه

{{ EmbedLiveSample('Comparison of property values on the same line', 900, 200) }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این خصوصیت: {{domxref("CanvasRenderingContext2D")}}