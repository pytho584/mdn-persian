---
title: "HTMLCanvasElement: contextrestored event"
short-title: contextrestored
slug: Web/API/HTMLCanvasElement/contextrestored_event
page-type: web-api-event
browser-compat: api.HTMLCanvasElement.contextrestored_event
---

{{APIRef("Canvas API")}}

رویداد **`contextrestored`** از [Canvas API](/en-US/docs/Web/API/Canvas_API) زمانی شلیک می‌شود که عامل کاربر فضای ذخیره‌سازی پشتیبان یک [`CanvasRenderingContext2D`](/en-US/docs/Web/API/CanvasRenderingContext2D) را بازیابی کند.

پس از دریافت این رویداد می‌توانید دوباره نقاشی کنید، منابع را مجدداً دریافت کنید و وضعیت زمینه خود را بازنشانی کنید.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا با تنظیم یک ویژگی کنترل‌کننده رویداد استفاده کنید.

```js-nolint
addEventListener("contextrestored", (event) => { })

oncontextrestored = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال

قطعه کد زیر رویداد بازیابی زمینه را شناسایی می‌کند.

```js
const canvas = document.getElementById("canvas");

canvas.addEventListener("contextrestored", (e) => {
  console.log(e);
  // فراخوانی تابع redrawCanvas() یا مشابه آن
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [`HTMLCanvasElement`: رویداد `contextlost`](/en-US/docs/Web/API/HTMLCanvasElement/contextlost_event)
- [`CanvasRenderingContext2D.isContextLost()`](/en-US/docs/Web/API/CanvasRenderingContext2D/isContextLost)
- [`OffscreenCanvas`: رویداد `contextlost`](/en-US/docs/Web/API/OffscreenCanvas/contextlost_event)