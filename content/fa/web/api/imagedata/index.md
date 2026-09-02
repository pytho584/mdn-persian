---
title: ImageData
slug: Web/API/ImageData
page-type: web-api-interface
browser-compat: api.ImageData
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

رابط **`ImageData`** داده‌های پیکسل زیرین یک ناحیه از عنصر {{HTMLElement("canvas")}} را نمایش می‌دهد.

این رابط با استفاده از سازنده {{domxref("ImageData.ImageData", "ImageData()")}} یا روش‌های سازنده روی شی {{domxref("CanvasRenderingContext2D")}} مرتبط با یک بوم (canvas) ایجاد می‌شود: {{domxref("CanvasRenderingContext2D.createImageData", "createImageData()")}} و {{domxref("CanvasRenderingContext2D.getImageData", "getImageData()")}}. همچنین می‌توان از آن برای تنظیم بخشی از بوم با استفاده از {{domxref("CanvasRenderingContext2D.putImageData", "putImageData()")}} استفاده کرد.

## سازنده‌ها

- {{domxref("ImageData.ImageData", "ImageData()")}}
  - : یک شی `ImageData` از یک {{jsxref("Uint8ClampedArray")}} یا {{jsxref("Float16Array")}} داده شده و اندازه تصویر ایجاد می‌کند. اگر آرایه‌ای داده نشود، تصویری از یک مستطیل سیاه شفاف ایجاد می‌کند. توجه داشته باشید که این رایج‌ترین روش ایجاد چنین شیئی در workerها است، زیرا {{domxref("CanvasRenderingContext2D.createImageData", "createImageData()")}} در آنجا در دسترس نیست.

## ویژگی‌های نمونه

- {{domxref("ImageData.data")}} {{ReadOnlyInline}}
  - : یک {{jsxref("Uint8ClampedArray")}} یا {{jsxref("Float16Array")}} که یک آرایه یک‌بعدی شامل داده‌ها به ترتیب RGBA را نمایش می‌دهد. ترتیب به صورت سطر به سطر از پیکسل بالا-چپ تا پایین-راست است.
- {{domxref("ImageData.colorSpace")}} {{ReadOnlyInline}}
  - : یک رشته که فضای رنگی داده‌های تصویر را نشان می‌دهد.
- {{domxref("ImageData.height")}} {{ReadOnlyInline}}
  - : یک `unsigned long` که ارتفاع واقعی `ImageData` را بر حسب پیکسل نمایش می‌دهد.
- {{domxref("ImageData.width")}} {{ReadOnlyInline}}
  - : یک `unsigned long` که عرض واقعی `ImageData` را بر حسب پیکسل نمایش می‌دهد.
- {{domxref("ImageData.pixelFormat")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک رشته که قالب مورد استفاده برای `ImageData` را نشان می‌دهد.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CanvasRenderingContext2D")}}
- عنصر {{HTMLElement("canvas")}} و رابط مرتبط با آن، {{domxref("HTMLCanvasElement")}}.