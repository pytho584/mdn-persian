---
title: "ImageData: ImageData() constructor"
short-title: ImageData()
slug: Web/API/ImageData/ImageData
page-type: web-api-constructor
browser-compat: api.ImageData.ImageData
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

سازندهٔ **`ImageData()`** یک شیء جدید از نوع {{domxref('ImageData')}} برمی‌گرداند که از آرایهٔ تایپ‌شدهٔ داده‌شده ساخته شده و دارای عرض و ارتفاع مشخصی است.

این سازنده، روش ترجیحی برای ایجاد چنین شیئی در یک {{domxref('Worker')}} است.

## نحو

```js-nolint
new ImageData(width, height)
new ImageData(width, height, settings)

new ImageData(dataArray, width)
new ImageData(dataArray, width, height)
new ImageData(dataArray, width, height, settings)
```

### پارامترها

- `width`
  - : یک عدد صحیح بدون علامت (unsigned long) که عرض تصویر را نشان می‌دهد.
- `height`
  - : یک عدد صحیح بدون علامت که ارتفاع تصویر را نشان می‌دهد. اگر آرایه‌ای داده شود، این مقدار اختیاری است: ارتفاع از اندازهٔ آرایه و عرض داده‌شده استنتاج می‌شود.
- `settings` {{optional_inline}}
  - : یک شیء با ویژگی‌های زیر:
    - `colorSpace`
      - : فضای رنگی داده‌های تصویر را مشخص می‌کند. می‌توان آن را برای [فضای رنگی sRGB](https://en.wikipedia.org/wiki/SRGB) روی `"srgb"` یا برای [فضای رنگی display-p3](https://en.wikipedia.org/wiki/DCI-P3) روی `"display-p3"` تنظیم کرد.
    - `pixelFormat`
      - : فرمت پیکسل را مشخص می‌کند. مقادیر ممکن:
        - `"rgba-unorm8"`، برای RGBA با فرمت نرمال‌نشدهٔ بدون علامت ۸ بیتی برای هر مؤلفه، با استفاده از {{jsxref("Uint8ClampedArray")}}. این مقدار پیش‌فرض است.
        - `"rgba-float16"`، برای RGBA با ۱۶ بیت برای هر مؤلفه، با استفاده از {{jsxref("Float16Array")}}. مقادیر پیکسل ممیز شناور (float) امکان نمایش رنگ‌ها در طیف رنگی (gamut) دلخواه و گسترده و محدودهٔ دینامیکی بالا (HDR) را فراهم می‌کنند.

- `dataArray`
  - : یک {{jsxref("Uint8ClampedArray")}} یا {{jsxref("Float16Array")}} که شامل نمایش اصلی پیکسل‌های تصویر است. اگر چنین آرایه‌ای داده نشود، تصویری با یک مستطیل سیاه شفاف با `width` و `height` مشخص‌شده ساخته خواهد شد. نوع `dataArray` باید با `settings.pixelFormat` مطابقت داشته باشد.

### مقدار بازگشتی

یک شیء جدید {{domxref('ImageData')}}.

### استثناها

- `IndexSizeError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که `dataArray` مشخص شده باشد، اما طول آن برابر با `(bytesPerPixel * width * height)` نباشد، یا اگر `height` مشخص نشده باشد، مضربی از `(bytesPerPixel * width)` نباشد. `bytesPerPixel` وقتی `pixelFormat` برابر `"rgba-unorm8"` است، `4` و در غیر این صورت `8` است.
- `InvalidStateError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که `dataArray` از نوع {{jsxref("Uint8ClampedArray")}} باشد و `pixelFormat` روی `"rgba-unorm8"` تنظیم نشده باشد، یا `dataArray` از نوع {{jsxref("Float16Array")}} باشد و `pixelFormat` روی `"rgba-float16"` تنظیم نشده باشد.

## مثال‌ها

### ایجاد یک شیء ImageData خالی

این مثال یک شیء `ImageData` ایجاد می‌کند که ۲۰۰ پیکسل عرض و ۱۰۰ پیکسل ارتفاع دارد و در مجموع شامل ۲۰٬۰۰۰ پیکسل است.

```js
let imageData = new ImageData(200, 100);
// ImageData { width: 200, height: 100, data: Uint8ClampedArray[80000] }
```

### ImageData با استفاده از فضای رنگی display-p3

این مثال یک شیء `ImageData` با [فضای رنگی display-p3](https://en.wikipedia.org/wiki/DCI-P3) ایجاد می‌کند.

```js
let imageData = new ImageData(200, 100, { colorSpace: "display-p3" });
```

### داده‌های پیکسل ممیز شناور برای طیف‌های رنگی گسترده و محدوده دینامیکی بالا (HDR)

مقادیر پیکسل ممیز شناور امکان نمایش رنگ‌ها در طیف‌های رنگی دلخواه و گسترده و محدوده دینامیکی بالا (HDR) را فراهم می‌کنند. می‌توانید گزینهٔ `pixelFormat` را روی `"rgba-float16"` تنظیم کنید تا از مقادیر RGBA با ۱۶ بیت برای هر مؤلفه استفاده کنید. این کار مستلزم آن است که `dataArray` یک {{jsxref("Float16Array")}} باشد.

```js
let floatArray = new Float16Array(4 * 200 * 200);
let imageData = new ImageData(floatArray, 200, 200, {
  pixelFormat: "rgba-float16",
});
console.log(imageData.pixelFormat); // "rgba-float16"
```

### مقداردهی ImageData با یک آرایه

این مثال یک شیء `ImageData` را با رنگ‌های پیکسلی که توسط یک آرایه تعریف شده‌اند، نمونه‌سازی می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

آرایه (`arr`) طولی برابر با `40000` دارد: از ۱۰٬۰۰۰ پیکسل تشکیل شده است که هر کدام با ۴ مقدار تعریف می‌شوند. سازندهٔ `ImageData` عرض `200` را برای شیء جدید مشخص می‌کند، بنابراین `height` به‌طور پیش‌فرض برابر با ۱۰٬۰۰۰ تقسیم بر ۲۰۰، یعنی `50` خواهد بود.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
const arr = new Uint8ClampedArray(40_000);

// Fill the array with the same RGBA values
for (let i = 0; i < arr.length; i += 4) {
  arr[i + 0] = 0; // R value
  arr[i + 1] = 190; // G value
  arr[i + 2] = 0; // B value
  arr[i + 3] = 255; // A value
}

// Initialize a new ImageData object
let imageData = new ImageData(arr, 200);

// Draw image data to the canvas
ctx.putImageData(imageData, 20, 20);
```

#### نتیجه

{{EmbedLiveSample('Initializing_ImageData_with_an_array', 700, 180)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CanvasRenderingContext2D.createImageData()")}}، متد سازنده‌ای که می‌توان در خارج از workerها از آن استفاده کرد.