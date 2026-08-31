---
title: "CanvasRenderingContext2D: putImageData() method"
short-title: putImageData()
slug: Web/API/CanvasRenderingContext2D/putImageData
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.putImageData
---

{{APIRef("Canvas API")}}

متد **`CanvasRenderingContext2D.putImageData()`** از Canvas 2D API داده‌های موجود در شیء {{domxref("ImageData")}} را روی بوم (canvas) نقاشی می‌کند. اگر یک مستطیل کثیف (dirty rectangle) مشخص شده باشد، فقط پیکسل‌های آن مستطیل نقاشی می‌شوند. این متد تحت تأثیر ماتریس تبدیل بوم قرار نمی‌گیرد.

> **نکته:** داده‌های تصویر را می‌توان با استفاده از متد {{domxref("CanvasRenderingContext2D.getImageData()", "getImageData()")}} از بوم دریافت کرد.

اطلاعات بیشتر درباره `putImageData()` و دستکاری کلی محتوای بوم را در مقاله [Pixel manipulation with canvas](/en-US/docs/Web/API/Canvas_API/Tutorial/Pixel_manipulation_with_canvas) بیابید.

## نحو (Syntax)

```js-nolint
putImageData(imageData, dx, dy)
putImageData(imageData, dx, dy, dirtyX, dirtyY, dirtyWidth, dirtyHeight)
```

### پارامترها

- `imageData`
  - : یک شیء {{domxref("ImageData")}} که شامل آرایه‌ای از مقادیر پیکسل‌ها است.
- `dx`
  - : موقعیت افقی (مختصات x) برای قرار دادن داده‌های تصویر در بوم مقصد.
- `dy`
  - : موقعیت عمودی (مختصات y) برای قرار دادن داده‌های تصویر در بوم مقصد.
- `dirtyX` {{optional_inline}}
  - : موقعیت افقی (مختصات x) گوشه بالا-چپ که داده‌های تصویر از آن استخراج می‌شوند. پیش‌فرض `0` است.
- `dirtyY` {{optional_inline}}
  - : موقعیت عمودی (مختصات y) گوشه بالا-چپ که داده‌های تصویر از آن استخراج می‌شوند. پیش‌فرض `0` است.
- `dirtyWidth` {{optional_inline}}
  - : عرض مستطیلی که باید نقاشی شود. پیش‌فرض برابر عرض داده‌های تصویر است.
- `dirtyHeight` {{optional_inline}}
  - : ارتفاع مستطیلی که باید نقاشی شود. پیش‌فرض برابر ارتفاع داده‌های تصویر است.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر هر یک از آرگومان‌ها بینهایت باشد، پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر داده‌های شیء `ImageData` جدا شده باشند، پرتاب می‌شود.

## مثال‌ها

### درک putImageData

برای درک اینکه این الگوریتم در پشت صحنه چگونه کار می‌کند، در زیر یک پیاده‌سازی بر اساس {{domxref("CanvasRenderingContext2D.fillRect()")}} ارائه شده است.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

function putImageData(
  ctx,
  imageData,
  dx,
  dy,
  dirtyX = 0,
  dirtyY = 0,
  dirtyWidth = imageData.width,
  dirtyHeight = imageData.height,
) {
  const data = imageData.data;
  const height = imageData.height;
  const width = imageData.width;
  const limitBottom = dirtyY + dirtyHeight;
  const limitRight = dirtyX + dirtyWidth;
  for (let y = dirtyY; y < limitBottom; y++) {
    for (let x = dirtyX; x < limitRight; x++) {
      const pos = y * width + x;
      ctx.fillStyle = `rgb(${data[pos * 4 + 0]} ${data[pos * 4 + 1]}
      ${data[pos * 4 + 2]} / ${data[pos * 4 + 3] / 255})`;
      ctx.fillRect(x + dx, y + dy, 1, 1);
    }
  }
}

// Draw content onto the canvas
ctx.fillRect(0, 0, 100, 100);
// Create an ImageData object from it
const imagedata = ctx.getImageData(0, 0, 100, 100);
// use the putImageData function that illustrates how putImageData works
putImageData(ctx, imagedata, 150, 0, 50, 50, 25, 25);
```

#### نتیجه

{{ EmbedLiveSample('Understanding_putImageData', 700, 180) }}

### از دست دادن داده به دلیل بهینه‌سازی مرورگر

> **هشدار:** به دلیل ماهیت اتلافی تبدیل به و از مقادیر رنگ آلفای پیش‌ضرب‌شده (premultiplied alpha)، ممکن است پیکسل‌هایی که به تازگی با استفاده از `putImageData()` تنظیم شده‌اند، در یک فراخوانی معادل `getImageData()` به عنوان مقادیر متفاوت بازگردانده شوند.

#### JavaScript

```js
const canvas = document.createElement("canvas");
canvas.width = 1;
canvas.height = 1;
const context = canvas.getContext("2d");
const imgData = context.getImageData(0, 0, canvas.width, canvas.height);
const pixels = imgData.data;
pixels[0 + 0] = 1;
pixels[0 + 1] = 127;
pixels[0 + 2] = 255;
pixels[0 + 3] = 1;
console.log("before:", pixels);
context.putImageData(imgData, 0, 0);
const imgData2 = context.getImageData(0, 0, canvas.width, canvas.height);
const pixels2 = imgData2.data;
console.log("after:", pixels2);
```

خروجی ممکن است به صورت زیر باشد:

```plain
before: Uint8ClampedArray(4) [ 1, 127, 255, 1 ]
after: Uint8ClampedArray(4) [ 255, 255, 255, 1 ]
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این متد: {{domxref("CanvasRenderingContext2D")}}
- شیء {{domxref("ImageData")}}
- {{domxref("CanvasRenderingContext2D.getImageData()")}}
- [Pixel manipulation with canvas](/en-US/docs/Web/API/Canvas_API/Tutorial/Pixel_manipulation_with_canvas)