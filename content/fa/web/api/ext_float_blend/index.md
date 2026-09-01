---
title: EXT_float_blend extension
short-title: EXT_float_blend
slug: Web/API/EXT_float_blend
page-type: webgl-extension
browser-compat: api.EXT_float_blend
---

{{APIRef("WebGL")}}

افزونهٔ `EXT_float_blend` در [WebGL API](/en-US/docs/Web/API/WebGL_API) امکان ترکیب (blending) و بافرهای ترسیم (draw buffers) با اجزای ممیز شناور ۳۲-بیتی را فراهم می‌کند.

افزونه‌های WebGL با استفاده از متد {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس هستند. برای اطلاعات بیشتر، به [استفاده از افزونه‌ها](/en-US/docs/Web/API/WebGL_API/Using_Extensions) در [آموزش WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial) نیز مراجعه کنید.

> [!NOTE]
> این افزونه برای هر دو زمینه {{domxref("WebGLRenderingContext", "WebGL1", "", 1)}} و {{domxref("WebGL2RenderingContext", "WebGL2", "", 1)}} در دسترس است. با این حال، برای استفاده از آن باید استفاده از بافرهای ترسیم با اجزای ممیز شناور ۳۲-بیتی را فعال کنید؛ این کار از طریق فعال‌کردن افزونهٔ {{domxref("WEBGL_color_buffer_float")}} (برای WebGL1) یا {{domxref("EXT_color_buffer_float")}} (برای WebGL2) انجام می‌شود. انجام این کار به‌طور خودکار `EXT_float_blend` را نیز فعال می‌کند، اگر و تنها اگر `EXT_float_blend` نیز پشتیبانی شود. پشتیبانی از `EXT_color_buffer_float` به معنای پشتیبانی از `EXT_float_blend` نیست.

با فعال بودن این افزونه، فراخوانی {{domxref("WebGLRenderingContext.drawArrays", "drawArrays()")}} یا {{domxref("WebGLRenderingContext.drawElements", "drawElements()")}} با فعال بودن ترکیب و بافر ترسیم با اجزای ممیز شناور ۳۲-بیتی دیگر باعث ایجاد خطای `INVALID_OPERATION` نخواهد شد.

## نکات استفاده

در دستگاه‌هایی که از افزونهٔ `EXT_float_blend` پشتیبانی می‌کنند، این افزونه به‌طور خودکار و ضمنی فعال می‌شود وقتی یک یا چند مورد از {{domxref("EXT_color_buffer_float")}}، {{domxref("OES_texture_float")}} یا {{domxref("WEBGL_color_buffer_float")}} فعال شوند. این تضمین می‌کند محتوایی که پیش از ارائهٔ `EXT_float_blend` توسط WebGL نوشته شده است، همان‌طور که انتظار می‌رود عمل کند.

## مثال‌ها

```js
const gl = canvas.getContext("webgl2");

// enable necessary extensions
gl.getExtension("EXT_color_buffer_float");
gl.getExtension("EXT_float_blend");

const tex = gl.createTexture();
gl.bindTexture(gl.TEXTURE_2D, tex);

// use floating point format
gl.texImage2D(gl.TEXTURE_2D, 0, gl.RGBA32F, 1, 1, 0, gl.RGBA, gl.FLOAT, null);

const fb = gl.createFramebuffer();
gl.bindFramebuffer(gl.FRAMEBUFFER, fb);
gl.framebufferTexture2D(
  gl.FRAMEBUFFER,
  gl.COLOR_ATTACHMENT0,
  gl.TEXTURE_2D,
  tex,
  0,
);

// enable blending
gl.enable(gl.BLEND);

gl.drawArrays(gl.POINTS, 0, 1);
// won't throw gl.INVALID_OPERATION with the extension enabled
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGL API](/en-US/docs/Web/API/WebGL_API)
- [استفاده از افزونه‌های WebGL](/en-US/docs/Web/API/WebGL_API/Using_Extensions)
- [آموزش WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial)
- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("EXT_color_buffer_float")}}
- {{domxref("WEBGL_color_buffer_float")}}
- {{domxref("WebGLRenderingContext.drawArrays()")}}
- {{domxref("WebGLRenderingContext.drawElements()")}}