---
title: "OffscreenCanvas: transferToImageBitmap() method"
short-title: transferToImageBitmap()
slug: Web/API/OffscreenCanvas/transferToImageBitmap
page-type: web-api-instance-method
browser-compat: api.OffscreenCanvas.transferToImageBitmap
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

متد **`transferToImageBitmap()`** از رابط {{domxref("OffscreenCanvas")}} یک شیء {{domxref("ImageBitmap")}} از آخرین تصویر رندر شده‌ی `OffscreenCanvas` ایجاد می‌کند. تصویر درون `OffscreenCanvas` با یک تصویر خالی جدید برای رندرهای بعدی جایگزین می‌شود.

اگر فقط نیاز به کپی کردن محتوای فعلی `OffscreenCanvas` در یک بوم‌نقاشی دیگر دارید، از متد {{domxref("CanvasRenderingContext2D.drawImage()")}} آن بافت با ورودی `OffscreenCanvas` استفاده کنید.

## دستور زبان

```js-nolint
transferToImageBitmap()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{domxref("ImageBitmap")}} تازه تخصیص‌یافته.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود:
    - بوم‌نقاشی به محدوده‌ی بافت دیگری (مانند یک worker) منتقل شده باشد.
    - حالت بافت بوم‌نقاشی با فراخوانی {{domxref("OffscreenCanvas.getContext()")}} تنظیم نشده باشد.

## توضیحات

این `ImageBitmap` به یک منبع گرافیکی بالقوه بزرگ ارجاع می‌دهد. برای اطمینان از استحکام برنامه‌ی وب، مهم است که از تخصیص تعداد زیادی از این منابع در هر لحظه خودداری کنید. به همین دلیل، ضروری است که اطمینان حاصل شود `ImageBitmap` یا _مصرف_ می‌شود یا _بسته_ می‌شود.

همانطور که در مثال‌های {{domxref("OffscreenCanvas")}} توضیح داده شده، ارسال این `ImageBitmap` به {{domxref("ImageBitmapRenderingContext.transferFromImageBitmap()")}} باعث _مصرف_ شیء `ImageBitmap` می‌شود؛ دیگر به منبع گرافیکی زیرین ارجاع نمی‌دهد و نمی‌توان آن را به هیچ API وب دیگری منتقل کرد.

اگر هدف شما ارسال `ImageBitmap` به APIهای وب دیگری است که آن را مصرف نمی‌کنند - مثلاً {{domxref("CanvasRenderingContext2D.drawImage()")}} - پس باید پس از اتمام کار آن را با فراخوانی {{domxref("ImageBitmap.close()")}} _ببندید_. صرفاً رها کردن ارجاع جاوااسکریپتی به `ImageBitmap` کافی نیست؛ این کار منبع گرافیکی آن را تا اجرای بعدی زباله‌روب (garbage collector) زنده نگه می‌دارد.

اگر `transferToImageBitmap()` را فراخوانی می‌کنید و قصد ارسال آن به {{domxref("ImageBitmapRenderingContext.transferFromImageBitmap()")}} را ندارید، در نظر بگیرید که آیا اصلاً نیاز به فراخوانی `transferToImageBitmap()` دارید یا خیر. بسیاری از APIهای وب که `ImageBitmap` را می‌پذیرند، `OffscreenCanvas` را نیز به عنوان آرگومان قبول می‌کنند، از جمله {{domxref("CanvasRenderingContext2D.drawImage()")}}.

## مثال‌ها

```js
const offscreen = new OffscreenCanvas(256, 256);
const gl = offscreen.getContext("webgl");

// انجام ترسیم با استفاده از بافت gl

offscreen.transferToImageBitmap();
// ImageBitmap { width: 256, height: 256 }

// یا:
// این `ImageBitmap` را به `ImageBitmapRenderingContext.transferFromImageBitmap` ارسال کنید
// یا:
// از `ImageBitmap` با سایر APIهای وب استفاده کنید و `ImageBitmap.close()` را فراخوانی کنید!
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده‌ی این متد، {{domxref("OffscreenCanvas")}}
- {{domxref("ImageBitmapRenderingContext.transferFromImageBitmap")}}