---
title: ImageBitmap
slug: Web/API/ImageBitmap
page-type: web-api-interface
browser-compat: api.ImageBitmap
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

رابط **`ImageBitmap`** نمایانگر یک تصویر بیت‌نگاشت است که می‌توان آن را بدون تأخیر غیرضروری روی یک {{HTMLElement("canvas")}} ترسیم کرد. این تصویر را می‌توان با استفاده از متد کارخانه‌ای {{domxref("Window.createImageBitmap()")}} یا {{domxref("WorkerGlobalScope.createImageBitmap()")}} از منابع گوناگونی ایجاد کرد. `ImageBitmap` مسیری ناهمگام و کارآمد از نظر مصرف منابع برای آماده‌سازی بافت‌ها جهت رندرگیری در WebGL فراهم می‌کند.

`ImageBitmap` یک [شیء قابل انتقال](/en-US/docs/Web/API/Web_Workers_API/Transferable_objects) است.

## ویژگی‌های نمونه

- {{domxref("ImageBitmap.height")}} {{ReadOnlyInline}}
  - : یک `unsigned long` که ارتفاع `ImageBitmap` را بر حسب پیکسل CSS نشان می‌دهد.
- {{domxref("ImageBitmap.width")}} {{ReadOnlyInline}}
  - : یک `unsigned long` که عرض `ImageBitmap` را بر حسب پیکسل CSS نشان می‌دهد.

## متدهای نمونه

- {{domxref("ImageBitmap.close()")}}
  - : تمام منابع گرافیکی مرتبط با یک `ImageBitmap` را آزاد می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Window.createImageBitmap")}}
- {{domxref("WorkerGlobalScope.createImageBitmap")}}
- {{domxref("CanvasRenderingContext2D.drawImage()")}}
- {{domxref("WebGLRenderingContext.texImage2D()")}}
- {{domxref("OffscreenCanvas.transferToImageBitmap()")}}