---
title: "HTMLCanvasElement: webglcontextlost event"
short-title: webglcontextlost
slug: Web/API/HTMLCanvasElement/webglcontextlost_event
page-type: web-api-event
browser-compat: api.HTMLCanvasElement.webglcontextlost_event
---

{{APIRef("WebGL API")}}

رویداد **`webglcontextlost`** از [WebGL API](/en-US/docs/Web/API/WebGL_API) زمانی رخ می‌دهد که عامل کاربر تشخیص دهد بافر ترسیم مرتبط با یک شیء {{domxref("WebGLRenderingContext")}} از دست رفته است.

این رویداد به بالا انتشار نمی‌یابد.

## نحو

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی handler رویداد تنظیم نمایید.

```js-nolint
addEventListener("webglcontextlost", (event) => { })

onwebglcontextlost = (event) => { }
```

## نوع رویداد

یک {{domxref("WebGLContextEvent")}} که از {{domxref("Event")}} ارث می‌برد.

{{InheritanceDiagram("WebGLContextEvent")}}

## مثال

با کمک افزونه {{domxref("WEBGL_lose_context")}} می‌توانید رویداد `webglcontextlost` را شبیه‌سازی کنید:

```js
const canvas = document.getElementById("canvas");
const gl = canvas.getContext("webgl");

canvas.addEventListener("webglcontextlost", (event) => {
  console.log(event);
});

gl.getExtension("WEBGL_lose_context").loseContext();

// رویداد "webglcontextlost" ثبت می‌شود.
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLContextEvent")}}
- {{domxref("WebGLRenderingContext.isContextLost()")}}
- {{domxref("WEBGL_lose_context")}}، {{domxref("WEBGL_lose_context.loseContext()")}}، {{domxref("WEBGL_lose_context.restoreContext()")}}