---
title: "CanvasPattern: setTransform() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/CanvasPattern/setTransform"
translated_by: "n8n + AI"
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

متد **`CanvasPattern.setTransform()`** از یک شی {{domxref("DOMMatrix")}} به عنوان ماتریس تبدیل الگو استفاده می‌کند و آن را روی الگو اعمال می‌کند.

## نحو

```js-nolint
setTransform(matrix)
```

### پارامترها

- `matrix`
  - یک {{domxref("DOMMatrix")}} که به عنوان ماتریس تبدیل الگو استفاده می‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### استفاده از متد `setTransform`

این یک قطعه کد است که از متد `setTransform` برای ایجاد یک {{domxref("CanvasPattern")}} با تبدیل الگوی مشخص شده از یک {{domxref("DOMMatrix")}} استفاده می‌کند. الگو در صورت تنظیم به عنوان {{domxref("CanvasRenderingContext2D.fillStyle", "fillStyle")}} جاری اعمال می‌شود و هنگام استفاده از متد {{domxref("CanvasRenderingContext2D.fillRect", "fillRect()")}} روی بوم کشیده می‌شود، به عنوان مثال.

```html live-sample___canvas
<canvas id="canvas"></canvas>
```

```js live-sample___canvas
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

const matrix = new DOMMatrix([1, 0.2, 0.8, 1, 0, 0]);

const img = new Image();
img.src = "canvas_create_pattern.png";

img.onload = () => {
  const pattern = ctx.createPattern(img, "repeat");
  pattern.setTransform(matrix.rotate(-45).scale(1.5));
  ctx.fillStyle = pattern;
  ctx.fillRect(0, 0, 400, 400);
};
```

{{EmbedLiveSample('canvas', , 250)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این متد: {{domxref("CanvasPattern")}}
- {{domxref("DOMMatrix")}}