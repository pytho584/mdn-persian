---
title: "CanvasRenderingContext2D: createImageData() method"
short-title: createImageData()
slug: Web/API/CanvasRenderingContext2D/createImageData
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.createImageData
---

{{APIRef("Canvas API")}}

متد **`CanvasRenderingContext2D.createImageData()`** در API Canvas 2D یک شیء {{domxref("ImageData")}} جدید و خالی با ابعاد مشخص‌شده ایجاد می‌کند. همهٔ پیکسل‌های موجود در این شیء جدید، سیاه شفاف (transparent black) هستند.

## نحو (Syntax)

```js-nolint
createImageData(width, height)
createImageData(width, height, settings)
createImageData(imagedata)
```

### پارامترها

- `width`
  - : عرض شیء جدید `ImageData`. مقدار منفی باعث قرینه شدن مستطیل حول محور عمودی می‌شود.
- `height`
  - : ارتفاع شیء جدید `ImageData`. مقدار منفی باعث قرینه شدن مستطیل حول محور افقی می‌شود.
- `settings` {{optional_inline}}
  - : یک شیء با ویژگی‌های زیر:
    - `colorSpace`
      - : فضای رنگی داده‌های تصویر را مشخص می‌کند. می‌توان آن را برای [فضای رنگی sRGB](https://en.wikipedia.org/wiki/SRGB) روی `"srgb"` یا برای [فضای رنگی display-p3](https://en.wikipedia.org/wiki/DCI-P3) روی `"display-p3"` تنظیم کرد.
    - `pixelFormat`
      - : فرمت پیکسل را مشخص می‌کند. مقادیر ممکن:
        - `"rgba-unorm8"`، برای RGBA با ۸ بیت در هر مؤلفه، با فرمت نرمال‌شدهٔ بدون علامت (unsigned normalized)، با استفاده از {{jsxref("Uint8ClampedArray")}}.
        - `"rgba-float16"`، برای RGBA با ۱۶ بیت در هر مؤلفه، با استفاده از {{jsxref("Float16Array")}}. مقادیر اعشاری (floating-point) پیکسل‌ها امکان نمایش رنگ‌ها در طیف‌های رنگی به‌خوبی دلخواه و محدودهٔ دینامیکی بالا (HDR) را فراهم می‌کنند.
- `imagedata`
  - : یک شیء `ImageData` موجود که عرض و ارتفاع از آن کپی می‌شود. خود تصویر کپی **نمی‌شود**.

### مقدار بازگشتی

یک شیء جدید {{domxref("ImageData")}} با عرض و ارتفاع مشخص‌شده. این شیء جدید با پیکسل‌های سیاه شفاف پر شده است.

### استثناها

- `IndexSizeError` {{domxref("DOMException")}}
  - : اگر یکی از آرگومان‌های `width` یا `height` صفر باشد، پرتاب می‌شود.

## مثال‌ها

### ایجاد یک شیء ImageData خالی

این قطعه‌کد با استفاده از متد `createImageData()` یک شیء `ImageData` خالی ایجاد می‌کند.

```html
<canvas id="canvas"></canvas>
```

شیء تولیدشده ۱۰۰ پیکسل عرض و ۵۰ پیکسل ارتفاع دارد که در مجموع ۵٬۰۰۰ پیکسل می‌شود. هر پیکسل در یک شیء `ImageData` از چهار مقدار آرایه‌ای تشکیل شده است، بنابراین ویژگی {{domxref("ImageData.data", "data")}} این شیء طولی برابر ۴ × ۵٬۰۰۰ یعنی ۲۰٬۰۰۰ دارد.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

const imageData = ctx.createImageData(100, 50);
console.log(imageData);
// ImageData { width: 100, height: 50, data: Uint8ClampedArray[20000] }
```

### پر کردن یک شیء ImageData خالی

این مثال یک شیء `ImageData` جدید ایجاد می‌کند و آن را با پیکسل‌های بنفش پر می‌کند.

```html
<canvas id="canvas"></canvas>
```

از آنجا که هر پیکسل از چهار مقدار تشکیل شده است، حلقهٔ `for` با مضارب چهار پیمایش می‌کند. مقادیر آرایه مرتبط با هر پیکسل به ترتیب R (قرمز)، G (سبز)، B (آبی) و A (آلفا) هستند.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
const imageData = ctx.createImageData(100, 100);

// Iterate through every pixel
for (let i = 0; i < imageData.data.length; i += 4) {
  // Modify pixel data
  imageData.data[i + 0] = 190; // R value
  imageData.data[i + 1] = 0; // G value
  imageData.data[i + 2] = 210; // B value
  imageData.data[i + 3] = 255; // A value
}

// Draw image data to the canvas
ctx.putImageData(imageData, 20, 20);
```

#### نتیجه

{{EmbedLiveSample("Filling_a_blank_ImageData_object", 700, 180)}}

### مثال‌های بیشتر

برای مثال‌های بیشتر در استفاده از `createImageData()` و شیء `ImageData`، به [دستکاری پیکسل‌ها با canvas](/en-US/docs/Web/API/Canvas_API/Tutorial/Pixel_manipulation_with_canvas) و {{domxref("ImageData.data")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کنندهٔ این متد: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("ImageData")}}
- [دستکاری پیکسل‌ها با canvas](/en-US/docs/Web/API/Canvas_API/Tutorial/Pixel_manipulation_with_canvas)