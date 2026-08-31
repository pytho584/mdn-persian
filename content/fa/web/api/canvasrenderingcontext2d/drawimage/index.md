---
title: "CanvasRenderingContext2D: drawImage() method"
short-title: drawImage()
slug: Web/API/CanvasRenderingContext2D/drawImage
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.drawImage
---

{{APIRef("Canvas API")}}

متد **`CanvasRenderingContext2D.drawImage()`** از Canvas 2D API راه‌های مختلفی برای رسم یک تصویر روی بوم (canvas) ارائه می‌دهد.

## Syntax

```js-nolint
drawImage(image, dx, dy)
drawImage(image, dx, dy, dWidth, dHeight)
drawImage(image, sx, sy, sWidth, sHeight, dx, dy, dWidth, dHeight)
```

![drawImage](canvas_drawimage.jpg)

### پارامترها

- `image`
  - : عنصری که باید در زمینه (context) رسم شود. مشخصات (specification) هر منبع تصویر بوم را مجاز می‌داند، به طور خاص:
    یک {{domxref("HTMLImageElement")}}،
    یک {{domxref("SVGImageElement")}}،
    یک {{domxref("HTMLVideoElement")}}،
    یک {{domxref("HTMLCanvasElement")}}،
    یک {{domxref("ImageBitmap")}}،
    یک {{domxref("OffscreenCanvas")}}،
    یا یک {{domxref("VideoFrame")}}.
- `sx` {{optional_inline}}
  - : مختصات محور x گوشه بالا-چپ زیر-مستطیل از `image` مبدأ که باید در زمینه مقصد رسم شود. برای حذف این آرگومان از syntax 3 یا 5 آرگومانی استفاده کنید.
- `sy` {{optional_inline}}
  - : مختصات محور y گوشه بالا-چپ زیر-مستطیل از `image` مبدأ که باید در زمینه مقصد رسم شود. برای حذف این آرگومان از syntax 3 یا 5 آرگومانی استفاده کنید.
- `sWidth` {{optional_inline}}
  - : عرض زیر-مستطیل از `image` مبدأ که باید در زمینه مقصد رسم شود. اگر مشخص نشود، کل مستطیل از مختصات مشخص شده توسط `sx` و `sy` تا گوشه پایین-راست تصویر استفاده می‌شود. برای حذف این آرگومان از syntax 3 یا 5 آرگومانی استفاده کنید. مقادیر منفی زیر-مستطیل را در جهت مخالف بزرگ می‌کنند، اما پیکسل‌ها همیشه در جهت اصلی پردازش می‌شوند و تصویر برعکس نمی‌شود.
- `sHeight` {{optional_inline}}
  - : ارتفاع زیر-مستطیل از `image` مبدأ که باید در زمینه مقصد رسم شود. برای حذف این آرگومان از syntax 3 یا 5 آرگومانی استفاده کنید. مقادیر منفی زیر-مستطیل را در جهت مخالف بزرگ می‌کنند، اما پیکسل‌ها همیشه در جهت اصلی پردازش می‌شوند و تصویر برعکس نمی‌شود.
- `dx`
  - : مختصات محور x در بوم مقصد که گوشه بالا-چپ `image` مبدأ در آن قرار می‌گیرد.
- `dy`
  - : مختصات محور y در بوم مقصد که گوشه بالا-چپ `image` مبدأ در آن قرار می‌گیرد.
- `dWidth`
  - : عرضی که `image` در بوم مقصد رسم می‌شود. این امکان مقیاس‌بندی تصویر رسم شده را فراهم می‌کند. اگر مشخص نشود، تصویر هنگام رسم در عرض مقیاس‌بندی نمی‌شود. توجه داشته باشید که این آرگومان در syntax 3 آرگومانی گنجانده نشده است. مقادیر منفی زیر-مستطیل را در جهت مخالف بزرگ می‌کنند، اما پیکسل‌ها همیشه در جهت اصلی پردازش می‌شوند و تصویر برعکس نمی‌شود.
- `dHeight`
  - : ارتفاعی که `image` در بوم مقصد رسم می‌شود. این امکان مقیاس‌بندی تصویر رسم شده را فراهم می‌کند. اگر مشخص نشود، تصویر هنگام رسم در ارتفاع مقیاس‌بندی نمی‌شود. توجه داشته باشید که این آرگومان در syntax 3 آرگومانی گنجانده نشده است. مقادیر منفی زیر-مستطیل را در جهت مخالف بزرگ می‌کنند، اما پیکسل‌ها همیشه در جهت اصلی پردازش می‌شوند و تصویر برعکس نمی‌شود.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- `InvalidStateError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که تصویر داده تصویری نداشته باشد یا عرض یا ارتفاع بوم یا مستطیل مبدأ صفر باشد.
- `TypeMismatchError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که یک تصویر `null` یا `undefined` به عنوان پارامتر ارسال شود.

## مثال‌ها

### رسم یک تصویر روی بوم

این مثال یک تصویر را با استفاده از متد `drawImage()` روی بوم رسم می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
<div class="hidden">
  <img
    id="source"
    src="https://mdn.github.io/shared-assets/images/examples/rhino.jpg"
    width="300"
    height="227" />
</div>
```

```css hidden
.hidden {
  display: none;
}
```

#### JavaScript

تصویر مبدأ از مختصات (33, 71) با عرض 104 و ارتفاع 124 گرفته شده است. روی بوم در (21, 20) رسم می‌شود و در آنجا عرض 87 و ارتفاع 104 به آن داده می‌شود.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
const image = document.getElementById("source");

image.addEventListener("load", (e) => {
  ctx.drawImage(image, 33, 71, 104, 124, 21, 20, 87, 104);
});
```

#### نتیجه

{{ EmbedLiveSample('Drawing_an_image_to_the_canvas', 700, 180) }}

### درک اندازه عنصر مبدأ

متد `drawImage()` هنگام رسم از _اندازه ذاتی (intrinsic size) عنصر مبدأ بر حسب پیکسل CSS_ استفاده می‌کند.

برای مثال، اگر یک `Image` بارگذاری کنید و پارامترهای اندازه اختیاری را در [سازنده (constructor)](/en-US/docs/Web/API/HTMLImageElement/Image) آن مشخص کنید، باید از ویژگی‌های `naturalWidth` و `naturalHeight` نمونه ایجاد شده برای محاسبه صحیح مواردی مانند مناطق برش و مقیاس استفاده کنید، نه از `element.width` و `element.height`. همین موضوع برای `videoWidth` و `videoHeight` اگر عنصر یک {{htmlelement("video")}} باشد و غیره صادق است.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

const image = new Image(60, 45); // استفاده از اندازه اختیاری برای تصویر
image.onload = drawImageActualSize; // هنگام بارگذاری تصویر رسم کن

// بارگذاری تصویری با اندازه ذاتی 300x227 پیکسل CSS
image.src = "https://mdn.github.io/shared-assets/images/examples/rhino.jpg";

function drawImageActualSize() {
  // استفاده از اندازه ذاتی تصویر بر حسب پیکسل CSS برای عنصر بوم
  canvas.width = this.naturalWidth;
  canvas.height = this.naturalHeight;

  // تصویر را به صورت 300x227 رسم می‌کند و اندازه سفارشی 60x45 داده شده
  // در سازنده را نادیده می‌گیرد
  ctx.drawImage(this, 0, 0);

  // برای استفاده از اندازه سفارشی باید پارامترهای مقیاس را با استفاده از
  // ویژگی‌های width و height عنصر مشخص کنیم - بیایید یکی را در گوشه روی آن رسم کنیم:
  ctx.drawImage(this, 0, 0, this.width, this.height);
}
```

#### نتیجه

{{EmbedLiveSample('Understanding_source_element_size', 700, 260)}}

## مشخصات (Specifications)

{{Specifications}}

## سازگاری مرورگر (Browser compatibility)

{{Compat}}

## نکات

- `drawImage()` تنها زمانی روی یک {{domxref("HTMLVideoElement")}} به درستی کار می‌کند که {{domxref("HTMLMediaElement.readyState")}} آن بزرگتر از 1 باشد (یعنی رویداد **seek** پس از تنظیم خاصیت `currentTime` فعال شده باشد).
- `drawImage()` همیشه از _اندازه ذاتی عنصر مبدأ بر حسب پیکسل CSS_ هنگام رسم، برش و/یا مقیاس‌بندی استفاده می‌کند.
- در برخی نسخه‌های قدیمی مرورگر، `drawImage()` تمام متاداده‌های EXIF در تصاویر، از جمله جهت‌گیری (Orientation) را نادیده می‌گیرد. این رفتار به ویژه در دستگاه‌های iOS مشکل‌ساز است. شما باید خودتان جهت‌گیری را تشخیص دهید و از `rotate()` برای اصلاح آن استفاده کنید.

## همچنین ببینید

- رابط تعریف‌کننده این متد: {{domxref("CanvasRenderingContext2D")}}