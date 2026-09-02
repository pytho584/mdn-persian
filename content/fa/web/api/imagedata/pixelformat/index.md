```yaml
---
title: "ImageData: pixelFormat property"
short-title: pixelFormat
slug: Web/API/ImageData/pixelFormat
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.ImageData.pixelFormat
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}{{SeeCompatTable}}

ویژگی فقط خواندنی **`ImageData.pixelFormat`** رشتهای است که فرمت پیکسل داده‌های تصویر را مشخص می‌کند.

فرمت پیکسل را می‌توان در هنگام مقداردهی اولیه `ImageData` با استفاده از سازنده [`ImageData()`](/en-US/docs/Web/API/ImageData/ImageData) یا متد [`createImageData()`](/en-US/docs/Web/API/CanvasRenderingContext2D/createImageData) تنظیم کرد.

## مقدار

این ویژگی می‌تواند مقادیر زیر را داشته باشد:

- `"rgba-unorm8"` نمایانگر RGBA با ۸ بیت به ازای هر مؤلفه با قالب نرمال‌شده بدون علامت، با استفاده از {{jsxref("Uint8ClampedArray")}}.
- `"rgba-float16"` نمایانگر RGBA با ۱۶ بیت به ازای هر مؤلفه، با استفاده از {{jsxref("Float16Array")}}. مقادیر پیکسل ممیز شناور امکان نمایش رنگ‌ها در طیف‌های رنگی دلخواه وسیع و دامنه دینامیکی بالا (HDR) را فراهم می‌کنند.

## مثال‌ها

### داده‌های پیکسل ممیز شناور برای طیف‌های رنگی وسیع و دامنه دینامیکی بالا (HDR)

مقادیر پیکسل ممیز شناور امکان نمایش رنگ‌ها در طیف‌های رنگی دلخواه وسیع و دامنه دینامیکی بالا (HDR) را فراهم می‌کنند. می‌توانید تنظیم `pixelFormat` را روی `"rgba-float16"` قرار دهید تا از مقادیر RGBA با ۱۶ بیت به ازای هر مؤلفه استفاده کنید. این کار نیاز دارد که `dataArray` یک {{jsxref("Float16Array")}} باشد.

```js
let floatArray = new Float16Array(4 * 200 * 200);
let imageData = new ImageData(floatArray, 200, 200, {
  pixelFormat: "rgba-float16",
});
console.log(imageData.pixelFormat); // "rgba-float16"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ImageData")}}
- {{jsxref("Float16Array")}}
- {{domxref("CanvasRenderingContext2D.createImageData()")}}
- {{domxref("CanvasRenderingContext2D.putImageData()")}}
```