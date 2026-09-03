---
title: "OffscreenCanvas: contextrestored event"
short-title: contextrestored
slug: Web/API/OffscreenCanvas/contextrestored_event
page-type: web-api-event
browser-compat: api.OffscreenCanvas.contextrestored_event
---

{{APIRef("Canvas API")}}

رویداد **`contextrestored`** از رابط {{domxref("OffscreenCanvas")}} زمانی صادر می‌شود که مرورگر زمینه‌ای از [`OffscreenCanvasRenderingContext2D`](/en-US/docs/Web/API/OffscreenCanvasRenderingContext2D) را که [قبلاً از دست رفته بود](/en-US/docs/Web/API/OffscreenCanvas/contextlost_event) بازیابی کند.

پس از دریافت این رویداد، می‌توانید دوباره ترسیم کنید، منابع را دوباره دریافت کنید و وضعیت زمینه خود را مجدداً مقداردهی کنید.

## سینتکس

برای استفاده از این رویداد، نام آن را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا یک ویژگی کنترل‌کننده رویداد (event handler) تنظیم کنید.

```js-nolint
addEventListener("contextrestored", (event) => { })

oncontextrestored = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

قطعه کد زیر رویداد بازیابی‌شدن زمینه را شناسایی می‌کند.

```js
const canvas = new OffscreenCanvas(256, 256);
const gl = offscreen.getContext("2d");

canvas.addEventListener("contextrestored", (e) => {
  console.log(e);
  // call to redrawCanvas() or similar
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [`OffscreenCanvas: contextlost` event](/en-US/docs/Web/API/OffscreenCanvas/contextlost_event)
- [`OffscreenCanvasRenderingContext2D.isContextLost()`](/en-US/docs/Web/API/OffscreenCanvasRenderingContext2D#canvasrenderingcontext2d.iscontextlost)
- [`HTMLCanvasElement: contextrestored` event](/en-US/docs/Web/API/HTMLCanvasElement/contextrestored_event)