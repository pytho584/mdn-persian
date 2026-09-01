---
title: "EXT_sRGB extension"
short-title: EXT_sRGB
slug: Web/API/EXT_sRGB
page-type: webgl-extension
browser-compat: api.EXT_sRGB
---

{{APIRef("WebGL")}}

افزونه **`EXT_sRGB`** بخشی از [WebGL API](/en-US/docs/Web/API/WebGL_API) است و پشتیبانی از sRGB را به بافت‌ها و اشیاء فریم‌بافر اضافه می‌کند.

افزونه‌های WebGL با استفاده از متد {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس هستند. برای اطلاعات بیشتر، به [استفاده از افزونه‌ها](/en-US/docs/Web/API/WebGL_API/Using_Extensions) در [آموزش WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial) مراجعه کنید.

> [!NOTE]
> این افزونه فقط برای زمینه‌های {{domxref("WebGLRenderingContext", "WebGL1", "", 1)}} در دسترس است. در {{domxref("WebGL2RenderingContext", "WebGL2", "", 1)}}، عملکرد این افزونه به طور پیش‌فرض در زمینه WebGL2 موجود است. ثابت‌های WebGL2 عبارتند از: `gl.SRGB`، `gl.SRGB8`، `gl.SRGB8_ALPHA8` و `gl.FRAMEBUFFER_ATTACHMENT_COLOR_ENCODING`.

## ثابت‌ها

این افزونه ثابت‌های زیر را ارائه می‌دهد که می‌توان در متدهای {{domxref("WebGLRenderingContext.texImage2D()", "texImage2D()")}}، {{domxref("WebGLRenderingContext.texSubImage2D()", "texSubImage2D()")}}، {{domxref("WebGLRenderingContext.renderbufferStorage()", "renderbufferStorage()")}} و {{domxref("WebGLRenderingContext.getFramebufferAttachmentParameter()", "getFramebufferAttachmentParameter()")}} استفاده کرد.

- `ext.SRGB_EXT`
  - فرمت sRGB بدون اندازه‌گذاری که دقت را به درایور واگذار می‌کند.
- `ext.SRGB_ALPHA_EXT`
  - فرمت sRGB بدون اندازه‌گذاری با مؤلفه آلفای بدون اندازه‌گذاری.
- `ext.SRGB8_ALPHA8_EXT`
  - فرمت‌های sRGB و آلفای دارای اندازه (8-بیت).
- `ext.FRAMEBUFFER_ATTACHMENT_COLOR_ENCODING_EXT`
  - کدگذاری رنگ فریم‌بافر را برمی‌گرداند (`gl.LINEAR` یا `ext.SRGB_EXT`).

## مثال‌ها

```js
const ext = gl.getExtension("EXT_sRGB");

const texture = gl.createTexture();
gl.bindTexture(gl.TEXTURE_2D, texture);

gl.texImage2D(
  gl.TEXTURE_2D,
  0,
  ext.SRGB_EXT,
  512,
  512,
  0,
  ext.SRGB_EXT,
  gl.UNSIGNED_BYTE,
  image,
);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLRenderingContext.texImage2D()")}}
- {{domxref("WebGLRenderingContext.texSubImage2D()")}}
- {{domxref("WebGLRenderingContext.renderbufferStorage()")}}
- {{domxref("WebGLRenderingContext.getFramebufferAttachmentParameter()")}}