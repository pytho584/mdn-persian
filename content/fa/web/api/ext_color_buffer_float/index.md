---
title: EXT_color_buffer_float extension
short-title: EXT_color_buffer_float
slug: Web/API/EXT_color_buffer_float
page-type: webgl-extension
browser-compat: api.EXT_color_buffer_float
---

{{APIRef("WebGL")}}

افزونهٔ **`EXT_color_buffer_float`** بخشی از [WebGL](/en-US/docs/Web/API/WebGL_API) است و امکان رندر کردن انواع مختلفی از قالب‌های ممیز شناور را فراهم می‌کند.

افزونه‌های WebGL با استفاده از متد {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس قرار می‌گیرند. برای اطلاعات بیشتر، مقالهٔ [استفاده از افزونه‌ها](/en-US/docs/Web/API/WebGL_API/Using_Extensions) را در [آموزش WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial) ببینید.

> [!NOTE]
> این افزونه فقط در زمینه‌های {{domxref("WebGL2RenderingContext", "WebGL 2", "", 1)}} در دسترس است.
>
> برای {{domxref("WebGLRenderingContext", "WebGL 1", "", 1)}}، افزونه‌های {{domxref("EXT_color_buffer_half_float")}} و {{domxref("WEBGL_color_buffer_float")}} را ببینید.

## متدهای گسترش‌یافته

قالب‌های اندازه‌دار زیر **رندرپذیر رنگی (color-renderable)** می‌شوند:

- `gl.R16F`
- `gl.RG16F`
- `gl.RGBA16F`
- `gl.R32F`
- `gl.RG32F`
- `gl.RGBA32F`
- `gl.R11F_G11F_B10F`

منظور از **رندرپذیر رنگی** این است که:

- متد {{domxref("WebGLRenderingContext.renderbufferStorage()")}} اکنون این قالب‌ها را می‌پذیرد.
- فریم‌بافرهایی که بافت‌هایی با این قالب‌ها به آن‌ها متصل شده‌اند، اکنون می‌توانند وضعیت **FRAMEBUFFER_COMPLETE** داشته باشند.

## مثال‌ها

`gl` باید یک {{domxref("WebGL2RenderingContext")}} باشد. این افزونه در زمینه‌های WebGL 1 کار نمی‌کند.

```js
const ext = gl.getExtension("EXT_color_buffer_float");

gl.renderbufferStorage(gl.RENDERBUFFER, gl.RGBA16F, 256, 256);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLRenderingContext.renderbufferStorage()")}}
- {{domxref("EXT_color_buffer_half_float")}}
- {{domxref("WEBGL_color_buffer_float")}}