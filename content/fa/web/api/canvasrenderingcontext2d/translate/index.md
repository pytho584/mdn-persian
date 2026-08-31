---
title: "CanvasRenderingContext2D: translate() method"
short-title: translate()
slug: Web/API/CanvasRenderingContext2D/translate
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.translate
---

{{APIRef("Canvas API")}}

متد **`CanvasRenderingContext2D.translate()`** در Canvas 2D API یک تبدیل انتقال (translation) به ماتریس جاری اضافه می‌کند.

## سینتکس

```js-nolint
translate(x, y)
```

متد `translate()` با جابه‌جایی بوم (canvas) و مبدأ آن روی شبکه به اندازه `x` واحد در جهت افقی و `y` واحد در جهت عمودی، یک تبدیل انتقال به ماتریس جاری اضافه می‌کند.

![مبدأ یک بوم (canvas) بر اساس مقادیر متد translate روی محورهای x و y جابه‌جا شده است.](canvas_grid_translate.png)

### پارامترها

- `x`
  - : مسافت حرکت در جهت افقی. مقادیر مثبت به سمت راست و مقادیر منفی به سمت چپ هستند.
- `y`
  - : مسافت حرکت در جهت عمودی. مقادیر مثبت به سمت پایین و مقادیر منفی به سمت بالا هستند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### جابه‌جایی یک شکل

در این مثال، یک مربع با استفاده از متد `translate()` از موقعیت پیش‌فرض خود جابه‌جا شده است. برای مقایسه، یک مربع هم‌اندازه که جابه‌جا نشده نیز رسم می‌شود.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

متد `translate()` کانتکست را ۱۱۰ واحد در جهت افقی و ۳۰ واحد در جهت عمودی جابه‌جا می‌کند. مربع اول به این اندازه‌ها از موقعیت پیش‌فرض خود منتقل می‌شود.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// Moved square
ctx.translate(110, 30);
ctx.fillStyle = "red";
ctx.fillRect(0, 0, 80, 80);

// Reset current transformation matrix to the identity matrix
ctx.setTransform(1, 0, 0, 1, 0, 0);

// Unmoved square
ctx.fillStyle = "gray";
ctx.fillRect(0, 0, 80, 80);
```

#### نتیجه

مربع جابه‌جاشده قرمز است و مربع بدون جابه‌جایی خاکستری است.

{{ EmbedLiveSample('Moving_a_shape', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این متد: {{domxref("CanvasRenderingContext2D")}}