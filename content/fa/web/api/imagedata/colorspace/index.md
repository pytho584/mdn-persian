---
title: "ImageData: colorSpace property"
short-title: colorSpace
slug: Web/API/ImageData/colorSpace
page-type: web-api-instance-property
browser-compat: api.ImageData.colorSpace
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

ویژگی فقط خواندنی **`ImageData.colorSpace`** یک رشته است که فضای رنگی داده‌های تصویر را نشان می‌دهد.

فضای رنگی را می‌توان در زمان مقداردهی اولیه `ImageData` با استفاده از سازنده [`ImageData()`](/en-US/docs/Web/API/ImageData/ImageData) یا متد [`createImageData()`](/en-US/docs/Web/API/CanvasRenderingContext2D/createImageData) تنظیم کرد.

## مقدار

این ویژگی می‌تواند مقادیر زیر را داشته باشد:

- `"srgb"` که نشان‌دهنده [فضای رنگی sRGB](https://en.wikipedia.org/wiki/SRGB) است.
- `"display-p3"` که نشان‌دهنده [فضای رنگی display-p3](https://en.wikipedia.org/wiki/DCI-P3) است.

## مثال‌ها

### دریافت فضای رنگی داده‌های تصویر بوم

متد [`getImageData()`](/en-US/docs/Web/API/CanvasRenderingContext2D/getImageData) به شما امکان می‌دهد به صراحت یک فضای رنگی را درخواست کنید. اگر با فضای رنگی که بوم با آن مقداردهی اولیه شده مطابقت نداشته باشد، یک تبدیل انجام می‌شود. از ویژگی `colorSpace` استفاده کنید تا بدانید شیء `ImageData` شما در کدام فضای رنگی قرار دارد.

```js
const context = canvas.getContext("2d", { colorSpace: "display-p3" });
context.fillStyle = "color(display-p3 0.5 0 0)";
context.fillRect(0, 0, 10, 10);

const p3ImageData = context.getImageData(0, 0, 1, 1);
console.log(p3ImageData.colorSpace); // "display-p3"

const srgbImageData = context.getImageData(0, 0, 1, 1, { colorSpace: "srgb" });
console.log(srgbImageData.colorSpace); // "srgb"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [`CanvasRenderingContext2D.createImageData()`](/en-US/docs/Web/API/CanvasRenderingContext2D/createImageData)
- [`CanvasRenderingContext2D.getImageData()`](/en-US/docs/Web/API/CanvasRenderingContext2D/getImageData)
- [`colorSpace` setting in `canvas.getContext()`](/en-US/docs/Web/API/HTMLCanvasElement/getContext#colorspace)
- تنظیم فضای رنگی WebGL:
  - [`WebGLRenderingContext.drawingBufferColorSpace`](/en-US/docs/Web/API/WebGLRenderingContext/drawingBufferColorSpace)
  - [`WebGLRenderingContext.unpackColorSpace`](/en-US/docs/Web/API/WebGLRenderingContext/unpackColorSpace)