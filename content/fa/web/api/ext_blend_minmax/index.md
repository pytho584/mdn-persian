---
title: "EXT_blend_minmax extension"
short-title: EXT_blend_minmax
slug: Web/API/EXT_blend_minmax
page-type: webgl-extension
browser-compat: api.EXT_blend_minmax
---

{{APIRef("WebGL")}}

افزونهٔ **`EXT_blend_minmax`** بخشی از [WebGL API](/en-US/docs/Web/API/WebGL_API) است و قابلیت‌های ترکیب رنگ (blending) را با افزودن دو معادلهٔ ترکیب جدید گسترش می‌دهد: کمینه یا بیشینه‌ی اجزای رنگ منبع و مقصد.

افزونه‌های WebGL از طریق متد {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس هستند. برای اطلاعات بیشتر، بخش [استفاده از افزونه‌ها](/en-US/docs/Web/API/WebGL_API/Using_Extensions) را در [آموزش WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial) ببینید.

> [!NOTE]
> این افزونه فقط در دسترس بافت‌های {{domxref("WebGLRenderingContext", "WebGL1", "", 1)}} است. در {{domxref("WebGL2RenderingContext", "WebGL2", "", 1)}}، عملکرد این افزونه به‌طور پیش‌فرض در بافت WebGL2 موجود است. ثابت‌های مربوطه در WebGL2 عبارت‌اند از `gl.MIN` و `gl.MAX`.

## ثابت‌ها

این افزونه دو ثابت جدید اضافه می‌کند که می‌توانند در {{domxref("WebGLRenderingContext.blendEquation()")}} و {{domxref("WebGLRenderingContext.blendEquationSeparate()")}} استفاده شوند:

- `ext.MIN_EXT`
  - : کمینه‌ی اجزای رنگ منبع و مقصد را تولید می‌کند.
- `ext.MAX_EXT`
  - : بیشینه‌ی اجزای رنگ منبع و مقصد را تولید می‌کند.

## مثال‌ها

```js
const ext = gl.getExtension("EXT_blend_minmax");

gl.blendEquation(ext.MIN_EXT);
gl.blendEquation(ext.MAX_EXT);

gl.blendEquationSeparate(ext.MIN_EXT, ext.MAX_EXT);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLRenderingContext.blendEquation()")}}
- {{domxref("WebGLRenderingContext.blendEquationSeparate()")}}