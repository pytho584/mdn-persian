---
title: "ImageData: data property"
short-title: data
slug: Web/API/ImageData/data
page-type: web-api-instance-property
browser-compat: api.ImageData.data
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`ImageData.data`** یک {{jsxref("Uint8ClampedArray")}} یا {{jsxref("Float16Array")}} برمی‌گرداند که شامل داده‌های پیکسلی شیء {{domxref("ImageData")}} است. داده‌ها به‌صورت یک آرایهٔ یک‌بعدی به ترتیب RGBA ذخیره می‌شوند.

## Value

نوع این مقدار به {{domxref("ImageData.pixelFormat")}} استفاده‌شده بستگی دارد:

- اگر `pixelFormat` برابر با `"rgba-unorm8"` باشد، یک {{jsxref("Uint8ClampedArray")}} است.
- اگر `pixelFormat` برابر با `"rgba-float16"` باشد، یک {{jsxref("Float16Array")}} است.

## Examples

### Getting an ImageData object's pixel data

این مثال یک شیء `ImageData` به عرض ۱۰۰ پیکسل و ارتفاع ۱۰۰ پیکسل می‌سازد که در مجموع ۱۰٬۰۰۰ پیکسل می‌شود. آرایهٔ `data` برای هر پیکسل چهار مقدار ذخیره می‌کند؛ بنابراین در مجموع ۴ × ۱۰٬۰۰۰ یا ۴۰٬۰۰۰ مقدار خواهد داشت.

```js
let imageData = new ImageData(100, 100);
console.log(imageData.data); // Uint8ClampedArray[40000]
console.log(imageData.data.length); // 40000
```

اگر شیء `ImageData` برای پیکسل‌های ممیز شناور تنظیم شده باشد — برای مثال، برای تصاویر با محدودهٔ دینامیکی بالا (HDR) — `data` به‌جای آن یک {{jsxref("Float16Array")}} خواهد بود.

```js
let floatArray = new Float16Array(4 * 200 * 200);
let imageData = new ImageData(floatArray, 200, 200, {
  pixelFormat: "rgba-float16",
});
console.log(imageData.data); // Float16Array
```

### Filling a blank ImageData object

این مثال یک شیء جدید `ImageData` می‌سازد و آن را با پیکسل‌های رنگارنگ پر می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

از آنجا که هر پیکسل از چهار مقدار درون آرایهٔ `data` تشکیل شده است، حلقهٔ `for` مضارب چهار را پیمایش می‌کند. مقادیر مرتبط با هر پیکسل به ترتیب R (قرمز)، G (سبز)، B (آبی) و A (آلفا) هستند.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
const imageData = ctx.createImageData(100, 100);

// Fill the array with RGBA values
for (let i = 0; i < imageData.data.length; i += 4) {
  // Percentage in the x direction, times 255
  let x = ((i % 400) / 400) * 255;
  // Percentage in the y direction, times 255
  let y = (Math.ceil(i / 400) / 100) * 255;

  // Modify pixel data
  imageData.data[i + 0] = x; // R value
  imageData.data[i + 1] = y; // G value
  imageData.data[i + 2] = 255 - x; // B value
  imageData.data[i + 3] = 255; // A value
}

// Draw image data to the canvas
ctx.putImageData(imageData, 20, 20);
```

#### Result

{{EmbedLiveSample("Filling_a_blank_ImageData_object", 700, 180)}}

### More examples

برای مثال‌های بیشتر با استفاده از `ImageData.data`، به [Pixel manipulation with canvas](/en-US/docs/Web/API/Canvas_API/Tutorial/Pixel_manipulation_with_canvas)، {{domxref("CanvasRenderingContext2D.createImageData()")}} و {{domxref("CanvasRenderingContext2D.putImageData()")}} مراجعه کنید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("ImageData.height")}}
- {{domxref("ImageData.width")}}
- {{domxref("ImageData")}}
- {{domxref("CanvasRenderingContext2D.createImageData()")}}
- {{domxref("CanvasRenderingContext2D.putImageData()")}}
- [Pixel manipulation with canvas](/en-US/docs/Web/API/Canvas_API/Tutorial/Pixel_manipulation_with_canvas)