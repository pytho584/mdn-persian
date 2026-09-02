---
title: "ImageBitmapRenderingContext"
---

---
title: ImageBitmapRenderingContext
slug: Web/API/ImageBitmapRenderingContext
page-type: web-api-interface
browser-compat: api.ImageBitmapRenderingContext
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

رابط **`ImageBitmapRenderingContext`** یک زمینه رندر برای بوم (canvas) است که قابلیت جایگزینی محتویات بوم را با {{domxref("ImageBitmap")}} داده‌شده فراهم می‌کند. شناسه زمینه آن (اولین آرگومان {{domxref("HTMLCanvasElement.getContext()")}} یا {{domxref("OffscreenCanvas.getContext()")}}) برابر با `"bitmaprenderer"` است.

این رابط در هر دو زمینه پنجره (window) و [worker](/en-US/docs/Web/API/Web_Workers_API) در دسترس است.

## ویژگی‌های نمونه

- {{domxref("ImageBitmapRenderingContext.canvas")}} {{ReadOnlyInline}}
  - : یک ارجاع فقط‌خواندنی به شیء {{domxref("HTMLCanvasElement")}} یا {{domxref("OffscreenCanvas")}} که با زمینه داده‌شده مرتبط است.

## روش‌های نمونه

- {{domxref("ImageBitmapRenderingContext.transferFromImageBitmap()")}}
  - : `ImageBitmap` داده‌شده را در بوم مرتبط با این زمینه رندر نمایش می‌دهد. مالکیت `ImageBitmap` به بوم منتقل می‌شود. این متد قبلاً `transferImageBitmap()` نامیده می‌شد، اما در یک تغییر در مشخصات (spec) تغییر نام داد. نام قدیمی به‌عنوان یک نام مستعار برای جلوگیری از شکستن کد حفظ شده است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("OffscreenCanvas")}}