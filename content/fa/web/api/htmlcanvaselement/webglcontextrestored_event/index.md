---
title: "HTMLCanvasElement: webglcontextrestored event"
---

---
title: "HTMLCanvasElement: webglcontextrestored event"
short-title: webglcontextrestored
slug: Web/API/HTMLCanvasElement/webglcontextrestored_event
page-type: web-api-event
browser-compat: api.HTMLCanvasElement.webglcontextrestored_event
---

{{APIRef("WebGL API")}}

رویداد **`webglcontextrestored`** از [WebGL API](/en-US/docs/Web/API/WebGL_API) زمانی رخ می‌دهد که عامل کاربر (user agent) بافر ترسیم را برای یک شیء {{domxref("WebGLRenderingContext")}} بازیابی کند.

هنگامی که زمینه بازیابی شد، منابع WebGL مانند بافت‌ها و بافرهایی که پیش از از دست رفتن زمینه ساخته شده‌اند، دیگر معتبر نیستند. باید وضعیت برنامهٔ WebGL خود را از نو مقداردهی کنید و منابع را دوباره بسازید.

این رویداد حباب نمی‌زند (bubbling ندارد).

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی event handler تنظیم کنید.

```js-nolint
addEventListener("webglcontextrestored", (event) => { })

onwebglcontextrestored = (event) => { }
```

## Event type

یک {{domxref("WebGLContextEvent")}}. از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("WebGLContextEvent")}}

## Example

با کمک افزونهٔ {{domxref("WEBGL_lose_context")}} می‌توانید رویداد `webglcontextrestored` را شبیه‌سازی کنید:

```js
const canvas = document.getElementById("canvas");
const gl = canvas.getContext("webgl");

canvas.addEventListener("webglcontextrestored", (e) => {
  console.log(e);
});

gl.getExtension("WEBGL_lose_context").restoreContext();

// "webglcontextrestored" event is logged.
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("WebGLContextEvent")}}
- {{domxref("WebGLRenderingContext.isContextLost()")}}
- {{domxref("WEBGL_lose_context")}}, {{domxref("WEBGL_lose_context.loseContext()")}}, {{domxref("WEBGL_lose_context.restoreContext()")}}