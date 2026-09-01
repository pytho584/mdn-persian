---
title: HTMLCanvasElement
slug: Web/API/HTMLCanvasElement
page-type: web-api-interface
browser-compat: api.HTMLCanvasElement
---

{{APIRef("Canvas API")}}

رابطهٔ **`HTMLCanvasElement`** ویژگی‌ها و روش‌هایی را برای دستکاری چیدمان و نمایش عناصر {{HtmlElement("canvas")}} فراهم می‌کند. رابطهِٔ `HTMLCanvasElement` همچنین ویژگی‌ها و روش‌های رابطهِٔ {{domxref("HTMLElement")}} را به ارث می‌برد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{domxref("HTMLElement")}} به ارث می‌برد._

- {{domxref("HTMLCanvasElement.height")}}
  - : ویژگی HTML [`height`](/en-US/docs/Web/HTML/Reference/Elements/canvas#height) عنصر {{HTMLElement("canvas")}} یک `integer` غیرمنفی است که تعداد پیکسل‌های منطقی (یا مقادیر RGBA) را در یک ستون از بوم نشان می‌دهد. وقتی این ویژگی مشخص نشده باشد، یا اگر روی مقدار نامعتبری مانند عدد منفی تنظیم شود، مقدار پیش‌فرض `150` استفاده می‌شود. اگر ارتفاع CSS جداگانه‌ای به {{HTMLElement("canvas")}} اختصاص داده نشود، این مقدار به‌عنوان ارتفاع بوم در واحد پیکسل CSS استفاده خواهد شد.
- {{domxref("HTMLCanvasElement.width")}}
  - : ویژگی HTML [`width`](/en-US/docs/Web/HTML/Reference/Elements/canvas#width) عنصر {{HTMLElement("canvas")}} یک `integer` غیرمنفی است که تعداد پیکسل‌های منطقی (یا مقادیر RGBA) را در یک ردیف از بوم نشان می‌دهد. وقتی این ویژگی مشخص نشده باشد، یا اگر روی مقدار نامعتبری مانند عدد منفی تنظیم شود، مقدار پیش‌فرض `300` استفاده می‌شود. اگر عرض CSS جداگانه‌ای به {{HTMLElement("canvas")}} اختصاص داده نشود، این مقدار به‌عنوان عرض بوم در واحد پیکسل CSS استفاده خواهد شد.
- {{domxref("HTMLCanvasElement.mozOpaque")}} {{non-standard_inline}} {{deprecated_inline}}
  - : یک مقدار بولی که ویژگی HTML [`moz-opaque`](/en-US/docs/Web/HTML/Reference/Elements/canvas#moz-opaque) عنصر {{HTMLElement("canvas")}} را بازتاب می‌دهد. این ویژگی به بوم اعلام می‌کند که آیا شفافیت عاملی خواهد بود یا خیر. اگر بوم بداند که شفافیتی وجود ندارد، می‌توان عملکرد نقاشی را بهینه کرد. این ویژگی فقط در مرورگرهای مبتنی بر موزیلا پشتیبانی می‌شود؛ به‌جای آن از روش استاندارد {{domxref("HTMLCanvasElement.getContext()", "canvas.getContext('2d', { alpha: false })")}} استفاده کنید.
- {{domxref("HTMLCanvasElement.mozPrintCallback")}} {{non-standard_inline}}
  - : یک `function` که در ابتدا `null` است. محتوای وب می‌تواند آن را به تابع جاوااسکریپتی تنظیم کند که هنگام چاپ صفحه، وقتی بوم باید دوباره ترسیم شود، فراخوانی می‌شود. هنگام فراخوانی، یک شیء «printState» به تابع برگشتی داده می‌شود که رابطهِٔ [MozCanvasPrintState](https://searchfox.org/firefox-main/search?q=interface%20MozCanvasPrintState&path=HTMLCanvasElement.webidl) را پیاده‌سازی می‌کند. تابع برگشتی می‌تواند از شیء printState بافت مورد نظر برای رسم را دریافت کند و پس از اتمام کار باید متد `done()` را روی آن صدا بزند. هدف `mozPrintCallback` به دست آوردن رندر با وضوح بالاتر از بوم با وضوح چاپگری است که در حال استفاده است. [این پست وبلاگ را ببینید.](https://blog.mozilla.org/labs/2012/09/a-new-way-to-control-printing-output/)

## روش‌های نمونه

_روش‌ها را از والد خود، {{domxref("HTMLElement")}} به ارث می‌برد._

- {{domxref("HTMLCanvasElement.captureStream()")}}
  - : یک {{domxref("CanvasCaptureMediaStreamTrack")}} برمی‌گرداند که ویدیوی بلادرنگ از سطح بوم است.
- {{domxref("HTMLCanvasElement.getContext()")}}
  - : یک بافت رسم روی بوم برمی‌گرداند، یا اگر شناسهٔ بافت پشتیبانی نشود یا بوم قبلاً روی حالت بافت متفاوتی تنظیم شده باشد، [`null`](/en-US/docs/Web/JavaScript/Reference/Operators/null) برمی‌گرداند.
- {{domxref("HTMLCanvasElement.toDataURL()")}}
  - : یک داده-URL شامل نمایشی از تصویر در قالبی که پارامتر `type` مشخص می‌کند (پیش‌فرض `png`) برمی‌گرداند. تصویر برگشتی دارای وضوح 96dpi است.
- {{domxref("HTMLCanvasElement.toBlob()")}}
  - : یک شیء {{domxref("Blob")}} ایجاد می‌کند که تصویر موجود در بوم را نشان می‌دهد؛ این فایل ممکن است بنا به صلاحدید عامل کاربر روی دیسک ذخیره شود یا در حافظه نگهداری شود.
- {{domxref("HTMLCanvasElement.transferControlToOffscreen()")}}
  - : کنترل را به یک شیء {{domxref("OffscreenCanvas")}} منتقل می‌کند، چه در رشتهٔ اصلی (main thread) و چه در یک worker.

## رویدادها

_رویدادها را از والد خود، {{domxref("HTMLElement")}} به ارث می‌برد._

به این رویدادها با استفاده از {{DOMxRef("EventTarget.addEventListener", "addEventListener()")}} یا با انتساب یک شنوندهٔ رویداد به ویژگی `oneventname` این رابط گوش دهید.

- [`contextlost`](/en-US/docs/Web/API/HTMLCanvasElement/contextlost_event)
  - : اگر مرورگر تشخیص دهد که بافت `CanvasRenderingContext2D` از بین رفته است، فعال می‌شود.
- [`contextrestored`](/en-US/docs/Web/API/HTMLCanvasElement/contextrestored_event)
  - : اگر مرورگر با موفقیت بافت `CanvasRenderingContext2D` را بازیابی کند، فعال می‌شود.
- [`webglcontextcreationerror`](/en-US/docs/Web/API/HTMLCanvasElement/webglcontextcreationerror_event)
  - : اگر عامل کاربر نتواند بافت `WebGLRenderingContext` یا `WebGL2RenderingContext` ایجاد کند، فعال می‌شود.
- [`webglcontextlost`](/en-US/docs/Web/API/HTMLCanvasElement/webglcontextlost_event)
  - : اگر عامل کاربر تشخیص دهد که بافر رسم مرتبط با یک شیء `WebGLRenderingContext` یا `WebGL2RenderingContext` از بین رفته است، فعال می‌شود.
- [`webglcontextrestored`](/en-US/docs/Web/API/HTMLCanvasElement/webglcontextrestored_event)
  - : اگر عامل کاربر بافر رسم را برای یک شیء `WebGLRenderingContext` یا `WebGL2RenderingContext` بازیابی کند، فعال می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- عنصر HTML که این رابط را پیاده‌سازی می‌کند: {{HTMLElement("canvas")}}