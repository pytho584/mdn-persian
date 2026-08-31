---
title: "CanvasRenderingContext2D: rotate() method"
---

---
title: "CanvasRenderingContext2D: rotate() method"
short-title: rotate()
slug: Web/API/CanvasRenderingContext2D/rotate
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.rotate
---

{{APIRef("Canvas API")}}

روش **`CanvasRenderingContext2D.rotate()`** از Canvas 2D API، چرخشی به ماتریس تبدیل اضافه می‌کند.

## نحو

```js-nolint
rotate(angle)
```

![Rectangular coordinate system with the rotation of the abscissa axis by the alpha angle](canvas_grid_rotate.png)

### پارامترها

- `angle`
  - : زاویهٔ چرخش، در جهت عقربه‌های ساعت و بر حسب رادیان. برای محاسبهٔ رادیان از روی درجه، می‌توانید از
    `degree * Math.PI / 180` استفاده کنید.

نقطهٔ مرکز چرخش همیشه مبدأ بوم است. برای تغییر نقطهٔ مرکز، باید بوم را با استفاده از روش
{{domxref("CanvasRenderingContext2D.translate", "translate()")}} جابه‌جا کنید.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### چرخاندن یک شکل

در این مثال، یک مستطیل به اندازهٔ ۴۵ درجه چرخانده می‌شود. توجه داشته باشید که مرکز چرخش، گوشهٔ بالا-چپ بوم است، نه مکانی که نسبت به یک شکل تعریف شده باشد.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// Point of transform origin
ctx.arc(0, 0, 5, 0, 2 * Math.PI);
ctx.fillStyle = "blue";
ctx.fill();

// Non-rotated rectangle
ctx.fillStyle = "gray";
ctx.fillRect(100, 0, 80, 20);

// Rotated rectangle
ctx.rotate((45 * Math.PI) / 180);
ctx.fillStyle = "red";
ctx.fillRect(100, 0, 80, 20);

// Reset transformation matrix to the identity matrix
ctx.setTransform(1, 0, 0, 1, 0, 0);
```

#### نتیجه

مرکز چرخش آبی است. مستطیل چرخانده‌نشده خاکستری و مستطیل چرخانده‌شده قرمز است.

{{ EmbedLiveSample('Rotating_a_shape', 700, 180) }}

### چرخاندن یک شکل حول مرکز آن

در این مثال، یک شکل حول نقطهٔ مرکزی خودش چرخانده می‌شود. برای این کار، مراحل زیر به ماتریس اعمال می‌شوند:

1. ابتدا، {{domxref("CanvasRenderingContext2D.translate()", "translate()")}} مبدأ ماتریس را به مرکز شکل منتقل می‌کند.
2. `rotate()` ماتریس را به اندازهٔ دلخواه می‌چرخاند.
3. در پایان، `translate()` مبدأ ماتریس را به نقطهٔ شروع بازمی‌گرداند. این کار با اعمال مقادیر منفی مختصات مرکز شکل انجام می‌شود.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

شکل یک مستطیل است که گوشهٔ آن در (۸۰، ۶۰) قرار دارد، عرض آن ۱۴۰ و ارتفاع آن ۳۰ است. مرکز افقی آن در (۸۰ + ۱۴۰ / ۲)، یعنی ۱۵۰ قرار دارد. مرکز عمودی آن در (۶۰ + ۳۰ / ۲)، یعنی ۷۵ قرار دارد. بنابراین، نقطهٔ مرکز در (۱۵۰، ۷۵) است.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// Non-rotated rectangle
ctx.fillStyle = "gray";
ctx.fillRect(80, 60, 140, 30);

// Matrix transformation
ctx.translate(150, 75);
ctx.rotate(Math.PI / 2);
ctx.translate(-150, -75);

// Rotated rectangle
ctx.fillStyle = "red";
ctx.fillRect(80, 60, 140, 30);
```

#### نتیجه

مستطیل چرخانده‌نشده خاکستری و مستطیل چرخانده‌شده قرمز است.

{{ EmbedLiveSample('Rotating_a_shape_around_its_center', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- واسطی که این روش را تعریف می‌کند: {{domxref("CanvasRenderingContext2D")}}