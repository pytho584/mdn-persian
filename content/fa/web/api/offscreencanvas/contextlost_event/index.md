---
title: "OffscreenCanvas: contextlost event"
short-title: contextlost
slug: Web/API/OffscreenCanvas/contextlost_event
page-type: web-api-event
browser-compat: api.OffscreenCanvas.contextlost_event
---

{{APIRef("Canvas API")}}

رویداد **`contextlost`** از رابط {{domxref("OffscreenCanvas")}} زمانی رخ می‌دهد که مرورگر تشخیص دهد زمینه [`OffscreenCanvasRenderingContext2D`](/en-US/docs/Web/API/OffscreenCanvasRenderingContext2D) از بین رفته است. زمینه‌ها می‌توانند به دلایل مختلفی از بین بروند، مانند خراب شدن درایور GPU مرتبط یا تمام شدن حافظه برنامه، و غیره.

به‌طور پیش‌فرض، عامل کاربر تلاش می‌کند زمینه را بازیابی کند و سپس رویداد [`contextrestored`](/en-US/docs/Web/API/OffscreenCanvas/contextrestored_event) را فعال کند. کد کاربر می‌تواند با فراخوانی [`Event.preventDefault()`](/en-US/docs/Web/API/Event/preventDefault) در هنگام پردازش رویداد، از بازیابی زمینه جلوگیری کند.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("contextlost", (event) => { })

oncontextlost = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

قطعه کد زیر رویداد `contextlost` را شناسایی می‌کند.

```js
const canvas = new OffscreenCanvas(256, 256);
const gl = offscreen.getContext("2d");

// انجام ترسیم و ...

canvas.addEventListener("contextlost", (event) => {
  console.log(event);
});
```

برای جلوگیری از بازیابی زمینه، کد کنترل‌کننده رویداد می‌تواند به این شکل باشد:

```js
canvas.addEventListener("contextlost", (event) => {
  event.preventDefault();
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [رویداد `OffScreenCanvas: contextrestored`](/en-US/docs/Web/API/OffscreenCanvas/contextrestored_event)
- [`OffscreenCanvasRenderingContext2D.isContextLost()`](/en-US/docs/Web/API/OffscreenCanvasRenderingContext2D#canvasrenderingcontext2d.iscontextlost)
- [رویداد `HTMLCanvasElement: contextlost`](/en-US/docs/Web/API/HTMLCanvasElement/contextlost_event)