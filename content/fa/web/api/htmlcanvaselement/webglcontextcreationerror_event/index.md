---
title: "HTMLCanvasElement: webglcontextcreationerror event"
short-title: webglcontextcreationerror
slug: Web/API/HTMLCanvasElement/webglcontextcreationerror_event
page-type: web-api-event
browser-compat: api.HTMLCanvasElement.webglcontextcreationerror_event
---

{{APIRef("WebGL API")}}

رویداد **`webglcontextcreationerror`** از [WebGL API](/en-US/docs/Web/API/WebGL_API) زمانی فعال می‌شود که عامل کاربر نتواند یک بافت {{domxref("WebGLRenderingContext")}} ایجاد کند.

این رویداد دارای یک ویژگی {{domxref("WebGLContextEvent.statusMessage")}} است که می‌تواند یک رشته وابسته به پلتفرم با اطلاعات بیشتر در مورد شکست را شامل شود.

این رویداد به بالا منتشر نمی‌شود (bubble نمی‌کند).

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("webglcontextcreationerror", (event) => { })

onwebglcontextcreationerror = (event) => { }
```

## Event type

یک {{domxref("WebGLContextEvent")}}. از {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("WebGLContextEvent")}}

## Example

```js
const canvas = document.getElementById("canvas");

canvas.addEventListener("webglcontextcreationerror", (e) => {
  console.log(e.statusMessage || "Unknown error");
});

const gl = canvas.getContext("webgl");
// logs statusMessage or "Unknown error" if unable to create WebGL context
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLContextEvent")}}
- {{domxref("WebGLRenderingContext.isContextLost()")}}
- {{domxref("WEBGL_lose_context")}}, {{domxref("WEBGL_lose_context.loseContext()")}}, {{domxref("WEBGL_lose_context.restoreContext()")}}