---
title: "CanvasRenderingContext2D: getImageData() method"
short-title: getImageData()
slug: Web/API/CanvasRenderingContext2D/getImageData
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.getImageData
---

{{APIRef("Canvas API")}}

متد **`getImageData()`** از {{domxref("CanvasRenderingContext2D")}} در Canvas 2D API یک شیء {{domxref("ImageData")}} را برمی‌گرداند که داده‌های پیکسلی زیرین را برای یک بخش مشخص از canvas نشان می‌دهد.

این متد تحت تأثیر ماتریس تبدیل canvas قرار نمی‌گیرد. اگر مستطیل مشخص‌شده از مرزهای canvas خارج شود، پیکسل‌های خارج از canvas در شیء `ImageData` برگشتی به‌صورت سیاه شفاف (transparent black) هستند.

> [!NOTE]
> داده‌های تصویر را می‌توان با استفاده از متد {{domxref("CanvasRenderingContext2D.putImageData()", "putImageData()")}} روی canvas نقاشی کرد.

اطلاعات بیشتر درباره `getImageData()` و دستکاری کلی محتوای canvas را در [Pixel manipulation with canvas](/en-US/docs/Web/API/Canvas_API/Tutorial/Pixel_manipulation_with_canvas) بیابید.

## Syntax

```js-nolint
getImageData(sx, sy, sw, sh)
getImageData(sx, sy, sw, sh, settings)
```

### Parameters

- `sx`
  - : مختصات محور x گوشه بالا-چپ مستطیلی که `ImageData` از آن استخراج خواهد شد.
- `sy`
  - : مختصات محور y گوشه بالا-چپ مستطیلی که `ImageData` از آن استخراج خواهد شد.
- `sw`
  - : عرض مستطیلی که `ImageData` از آن استخراج خواهد شد. مقادیر مثبت به سمت راست و مقادیر منفی به سمت چپ هستند.
- `sh`
  - : ارتفاع مستطیلی که `ImageData` از آن استخراج خواهد شد. مقادیر مثبت به سمت پایین و مقادیر منفی به سمت بالا هستند.
- `settings` {{optional_inline}}
  - : یک شیء با ویژگی‌های زیر:
    - `colorSpace`
      - : فضای رنگی داده‌های تصویر را مشخص می‌کند. می‌تواند به `"srgb"` برای [فضای رنگی sRGB](https://en.wikipedia.org/wiki/SRGB) یا `"display-p3"` برای [فضای رنگی display-p3](https://en.wikipedia.org/wiki/DCI-P3) تنظیم شود.
    - `pixelFormat`
      - : فرمت پیکسل را مشخص می‌کند. مقادیر ممکن:
        - `"rgba-unorm8"`، برای RGBA با فرمت unsigned normalized 8 بیت به ازای هر مؤلفه، با استفاده از {{jsxref("Uint8ClampedArray")}}.
        - `"rgba-float16"`، برای RGBA با 16 بیت به ازای هر مؤلفه، با استفاده از {{jsxref("Float16Array")}}. مقادیر پیکسل ممیز-شناور امکان نمایش رنگ‌ها در طیف‌های رنگی دلخواه و دامنه دینامیک بالا (HDR) را فراهم می‌کنند.

### Return value

یک شیء {{domxref("ImageData")}} شامل داده‌های تصویر برای مستطیل مشخص‌شده از canvas. مختصات گوشه بالا-چپ مستطیل `(sx, sy)` و مختصات گوشه پایین-راست `(sx + sw - 1, sy + sh - 1)` هستند.

> [!NOTE]
> با برخی تنظیمات حریم خصوصی (مانند محافظت در برابر اثر انگشت‌گذاری (fingerprinting))، نویز تصادفی ظریفی به نتیجه `getImageData()` اضافه می‌شود تا از استنباط دستگاه رندر کاربر توسط وب‌سایت جلوگیری شود. بنابراین، `putImageData()` و `getImageData()` ممکن است رفت و برگشت کاملی نداشته باشند.

### Exceptions

- `IndexSizeError` {{domxref("DOMException")}}
  - : اگر `sw` یا `sh` صفر باشند، پرتاب می‌شود.
- `SecurityError` {{domxref("DOMException")}}
  - : canvas حاوی یا ممکن است حاوی پیکسل‌هایی باشد که از یک مبدأ (origin) غیر از مبدأ بارگذاری سند بارگذاری شده‌اند. برای جلوگیری از پرتاب شدن `SecurityError` {{domxref("DOMException")}} در این شرایط، CORS را به‌گونه‌ای پیکربندی کنید که استفاده از تصویر منبع به این روش مجاز باشد. به [Allowing cross-origin use of images and canvas](/en-US/docs/Web/HTML/How_to/CORS_enabled_image) مراجعه کنید.

## Examples

### دریافت داده‌های تصویر از یک canvas

این مثال یک تصویر را رسم می‌کند و سپس از `getImageData()` برای گرفتن بخشی از canvas استفاده می‌کند.

ما از `getImageData()` برای استخراج یک برش از تصویر استفاده می‌کنیم، که از `(10, 20)` شروع می‌شود، با عرض `80` و ارتفاع `230`. سپس این برش را سه بار رسم می‌کنیم و برش‌ها را به‌ترتیب در پایین و سمت راست برش قبلی قرار می‌دهیم.

#### HTML

```html
<canvas id="canvas" width="700" height="400"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

const image = new Image();
image.src = "plumeria.jpg";
image.addEventListener("load", () => {
  ctx.drawImage(image, 0, 0, 233, 320);

  const imageData = ctx.getImageData(10, 20, 80, 230);
  ctx.putImageData(imageData, 260, 0);
  ctx.putImageData(imageData, 380, 50);
  ctx.putImageData(imageData, 500, 100);
});
```

#### Result

{{EmbedLiveSample("Getting_image_data_from_a_canvas", "", 420)}}

### تبدیل فضای رنگی

تنظیم اختیاری `colorSpace` به شما امکان می‌دهد داده‌های تصویر را در قالب دلخواه دریافت کنید.

```js
const context = canvas.getContext("2d", { colorSpace: "display-p3" });
context.fillStyle = "color(display-p3 0.5 0 0)";
context.fillRect(0, 0, 10, 10);

// Get ImageData converted to sRGB
const imageData = context.getImageData(0, 0, 1, 1, { colorSpace: "srgb" });
console.log(imageData.colorSpace); // "srgb"
```

### دریافت داده در قالب‌های پیکسل مختلف

تنظیم اختیاری `pixelFormat` به شما امکان می‌دهد داده‌های تصویر را در قالب پیکسل دلخواه دریافت کنید.

```js
const context = canvas.getContext("2d");

const defaultImageData = context.getImageData(0, 0, 1, 1);
console.log(defaultImageData.pixelFormat); // "rgba-unorm8"

const float16ImageData = context.getImageData(0, 0, 1, 1, {
  pixelFormat: "rgba-float16",
});
console.log(float16ImageData.pixelFormat); // "rgba-float16"
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- رابط تعریف‌کننده این متد: {{domxref("CanvasRenderingContext2D")}}
- شیء {{domxref("ImageData")}}
- {{domxref("CanvasRenderingContext2D.putImageData()")}}
- [Pixel manipulation with canvas](/en-US/docs/Web/API/Canvas_API/Tutorial/Pixel_manipulation_with_canvas)