---
title: "HTMLCanvasElement: contextlost event"
short-title: contextlost
slug: Web/API/HTMLCanvasElement/contextlost_event
page-type: web-api-event
browser-compat: api.HTMLCanvasElement.contextlost_event
---

{{APIRef("Canvas API")}}

رویداد **`contextlost`** از [Canvas API](/en-US/docs/Web/API/Canvas_API) زمانی شلیک می‌شود که عامل کاربر تشخیص دهد فضای ذخیره‌سازی پشتیبان مرتبط با یک بافت [`CanvasRenderingContext2D`](/en-US/docs/Web/API/CanvasRenderingContext2D) از دست رفته است.
بافت‌ها ممکن است به دلایل مختلفی مانند خراب شدن درایور یا تمام شدن حافظه برنامه از دست بروند.

به طور پیش‌فرض، عامل کاربر سعی در بازگردانی بافت خواهد کرد و سپس رویداد [`contextrestored`](/en-US/docs/Web/API/HTMLCanvasElement/contextrestored_event) را شلیک می‌کند.
کد کاربر می‌تواند با فراخوانی [`Event.preventDefault()`](/en-US/docs/Web/API/Event/preventDefault) در طول مدیریت رویداد، از بازگردانی بافت جلوگیری کند.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("contextlost", (event) => { })

oncontextlost = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال

قطعه کد زیر رویداد `contextlost` را تشخیص می‌دهد.

```js
const canvas = document.getElementById("canvas");

canvas.addEventListener("contextlost", (event) => {
  console.log(event);
});
```

برای جلوگیری از بازگردانی بافت، کد می‌تواند به این شکل باشد:

```js
const canvas = document.getElementById("canvas");

canvas.addEventListener("contextlost", (event) => {
  event.preventDefault();
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [`HTMLCanvasElement: contextrestored` event](/en-US/docs/Web/API/HTMLCanvasElement/contextrestored_event)
- [`CanvasRenderingContext2D.isContextLost()`](/en-US/docs/Web/API/CanvasRenderingContext2D/isContextLost)
- [`OffscreenCanvas: contextlost` event](/en-US/docs/Web/API/OffscreenCanvas/contextlost_event)