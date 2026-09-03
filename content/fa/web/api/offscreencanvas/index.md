---
title: OffscreenCanvas
slug: Web/API/OffscreenCanvas
page-type: web-api-interface
browser-compat: api.OffscreenCanvas
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

هنگام استفاده از عنصر {{HtmlElement("canvas")}} یا [Canvas API](/en-US/docs/Web/API/Canvas_API)، رندرینگ، انیمیشن و تعامل با کاربر معمولاً در رشته اجرای اصلی یک برنامه وب انجام می‌شود. محاسبات مربوط به انیمیشن‌های بوم و رندرینگ می‌توانند تأثیر چشمگیری بر کارایی برنامه داشته باشند.

رابط **`OffscreenCanvas`** بومی را فراهم می‌کند که می‌توان آن را خارج از صفحه رندر کرد و به این ترتیب DOM و Canvas API را از یکدیگر جدا می‌کند؛ به طوری که عنصر {{HtmlElement("canvas")}} دیگر کاملاً به DOM وابسته نیست. همچنین عملیات رندرینگ را می‌توان درون یک زمینه [worker](/en-US/docs/Web/API/Web_Workers_API) اجرا کرد؛ این امکان به شما می‌دهد برخی وظایف را در یک رشته جداگانه اجرا کنید و از کارهای سنگین روی رشته اصلی جلوگیری کنید.

`OffscreenCanvas` یک [شیء قابل انتقال](/en-US/docs/Web/API/Web_Workers_API/Transferable_objects) است.

{{InheritanceDiagram}}

## سازنده‌ها

- {{domxref("OffscreenCanvas.OffscreenCanvas", "OffscreenCanvas()")}}
  - : سازنده `OffscreenCanvas`. یک شیء جدید `OffscreenCanvas` می‌سازد.

## ویژگی‌های نمونه

- {{domxref("OffscreenCanvas.height")}}
  - : ارتفاع بوم خارج از صفحه.
- {{domxref("OffscreenCanvas.width")}}
  - : عرض بوم خارج از صفحه.

## روش‌های نمونه

- {{domxref("OffscreenCanvas.getContext()")}}
  - : یک زمینه ترسیم برای بوم خارج از صفحه برمی‌گرداند، یا اگر شناسه زمینه پشتیبانی نشود، یا بوم خارج از صفحه از قبل روی حالت زمینه‌ای متفاوت تنظیم شده باشد، [`null`](/en-US/docs/Web/JavaScript/Reference/Operators/null) برمی‌گرداند.
- {{domxref("OffscreenCanvas.convertToBlob()")}}
  - : یک شیء {{domxref("Blob")}} می‌سازد که نمایانگر تصویر موجود در بوم است.
- {{domxref("OffscreenCanvas.transferToImageBitmap()")}}
  - : از آخرین تصویر رندر شده `OffscreenCanvas` یک شیء {{domxref("ImageBitmap")}} می‌سازد. برای نکات مهم درباره مدیریت این {{domxref("ImageBitmap")}} به صفحه مرجع آن مراجعه کنید.

## رویدادها

_رویدادها را از والد خود، {{domxref("EventTarget")}}، به ارث می‌برد._

برای گوش دادن به این رویدادها از {{DOMxRef("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید یا یک شنونده رویداد را به ویژگی `oneventname` این رابط نسبت دهید.

- [`contextlost`](/en-US/docs/Web/API/OffscreenCanvas/contextlost_event)
  - : اگر مرورگر تشخیص دهد که یک زمینه [`OffscreenCanvasRenderingContext2D`](/en-US/docs/Web/API/OffscreenCanvasRenderingContext2D) از دست رفته است، این رویداد صادر می‌شود.
- [`contextrestored`](/en-US/docs/Web/API/OffscreenCanvas/contextrestored_event)
  - : اگر مرورگر با موفقیت یک زمینه [`OffscreenCanvasRenderingContext2D`](/en-US/docs/Web/API/OffscreenCanvasRenderingContext2D) را بازیابی کند، این رویداد صادر می‌شود.

## مثال‌ها

### نمایش همزمان فریم‌های تولیدشده توسط یک `OffscreenCanvas`

یکی از راه‌های استفاده از API `OffscreenCanvas` این است که از یک زمینه رندر که از یک شیء `OffscreenCanvas` به دست آمده برای تولید فریم‌های جدید استفاده کنید. پس از اینکه رندر یک فریم جدید در این زمینه به پایان رسید، می‌توان متد {{domxref("OffscreenCanvas.transferToImageBitmap", "transferToImageBitmap()")}} را برای ذخیره آخرین تصویر رندر شده فراخوانی کرد. این متد یک شیء {{domxref("ImageBitmap")}} برمی‌گرداند که می‌توان از آن در انواع Web APIها و همچنین در یک بوم دوم بدون ایجاد یک کپی انتقالی استفاده کرد.

برای نمایش `ImageBitmap` می‌توانید از یک زمینه {{domxref("ImageBitmapRenderingContext")}} استفاده کنید که با فراخوانی `canvas.getContext("bitmaprenderer")` روی یک عنصر بوم (نمایان) ایجاد می‌شود. این زمینه فقط قابلیت جایگزینی محتوای بوم با `ImageBitmap` داده‌شده را فراهم می‌کند. فراخوانی {{domxref("ImageBitmapRenderingContext.transferFromImageBitmap()")}} همراه با `ImageBitmap` رندر شده و ذخیره‌شده قبلی از `OffscreenCanvas`، باعث نمایش `ImageBitmap` روی بوم و انتقال مالکیت آن به بوم می‌شود. یک `OffscreenCanvas` واحد می‌تواند فریم‌ها را به هر تعداد دلخواهی از اشیاء `ImageBitmapRenderingContext` دیگر منتقل کند.

با این دو عنصر {{HTMLElement("canvas")}}:

```html
<canvas id="one"></canvas> <canvas id="two"></canvas>
```

کد زیر رندرگیری را با استفاده از `OffscreenCanvas` همانطور که در بالا توضیح داده شد فراهم می‌کند.

```js
const one = document.getElementById("one").getContext("bitmaprenderer");
const two = document.getElementById("two").getContext("bitmaprenderer");

const offscreen = new OffscreenCanvas(256, 256);
const gl = offscreen.getContext("webgl");

// Perform some drawing for the first canvas using the gl context
const bitmapOne = offscreen.transferToImageBitmap();
one.transferFromImageBitmap(bitmapOne);

// Perform some more drawing for the second canvas
const bitmapTwo = offscreen.transferToImageBitmap();
two.transferFromImageBitmap(bitmapTwo);
```

### نمایش ناهمزمان فریم‌های تولیدشده توسط یک `OffscreenCanvas`

راه دیگر استفاده از API `OffscreenCanvas` این است که {{domxref("HTMLCanvasElement.transferControlToOffscreen", "transferControlToOffscreen()")}} را روی یک عنصر {{HTMLElement("canvas")}} فراخوانی کنید؛ چه روی یک [worker](/en-US/docs/Web/API/Web_Workers_API) و چه روی رشته اصلی. این متد از روی یک شیء {{domxref("HTMLCanvasElement")}} در رشته اصلی، یک شیء `OffscreenCanvas` برمی‌گرداند. سپس با فراخوانی {{domxref("OffscreenCanvas.getContext", "getContext()")}} یک زمینه رندرگیری از آن `OffscreenCanvas` دریافت می‌کنید.

اسکریپت `main.js` (رشته اصلی) ممکن است به این شکل باشد:

```js
const htmlCanvas = document.getElementById("canvas");
const offscreen = htmlCanvas.transferControlToOffscreen();

const worker = new Worker("offscreen-canvas.js");
worker.postMessage({ canvas: offscreen }, [offscreen]);
```

اسکریپت `offscreen-canvas.js` (رشته worker) می‌تواند به این شکل باشد:

```js
onmessage = (evt) => {
  const canvas = evt.data.canvas;
  const gl = canvas.getContext("webgl");
  // Perform some drawing using the gl context
};
```

همچنین می‌توان از {{domxref("Window.requestAnimationFrame", "requestAnimationFrame()")}} در workerها استفاده کرد:

```js
onmessage = (evt) => {
  const canvas = evt.data.canvas;
  const gl = canvas.getContext("webgl");

  function render(time) {
    // Perform some drawing using the gl context
    requestAnimationFrame(render);
  }
  requestAnimationFrame(render);
};
```

برای یک مثال کامل، [سورس مثال OffscreenCanvas](https://github.com/mdn/dom-examples/tree/main/web-workers/offscreen-canvas-worker) را در GitHub ببینید یا [مثال زنده OffscreenCanvas](https://mdn.github.io/dom-examples/web-workers/offscreen-canvas-worker/) را اجرا کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("CanvasRenderingContext2D")}}
- {{domxref("OffscreenCanvasRenderingContext2D")}}
- {{domxref("ImageBitmap")}}
- {{domxref("ImageBitmapRenderingContext")}}
- {{domxref("HTMLCanvasElement.transferControlToOffscreen()")}}
- {{domxref("Window.requestAnimationFrame()", "requestAnimationFrame()")}}
- [WebGL Off the Main Thread – Mozilla Hacks](https://hacks.mozilla.org/2016/01/webgl-off-the-main-thread/) (2016)