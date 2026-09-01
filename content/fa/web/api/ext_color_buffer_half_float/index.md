```yaml
---
title: "EXT_color_buffer_half_float extension"
short-title: EXT_color_buffer_half_float
slug: Web/API/EXT_color_buffer_half_float
page-type: webgl-extension
browser-compat: api.EXT_color_buffer_half_float
---

{{APIRef("WebGL")}}

افزونهٔ **`EXT_color_buffer_half_float`** بخشی از [WebGL API](/en-US/docs/Web/API/WebGL_API) است و امکان رندر کردن به بافرهای رنگی ۱۶-بیتی ممیز شناور (floating-point) را اضافه می‌کند.

افزونه‌های WebGL با استفاده از متد {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس هستند. برای اطلاعات بیشتر، همچنین به [استفاده از افزونه‌ها](/en-US/docs/Web/API/WebGL_API/Using_Extensions) در [آموزش WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial) مراجعه کنید.

> [!NOTE]
> این افزونه برای هر دو زمینه (context) {{domxref("WebGLRenderingContext", "WebGL1", "", 1)}} و {{domxref("WebGL2RenderingContext", "WebGL2", "", 1)}} در دسترس است. در WebGL 2، این یک جایگزین برای استفاده از افزونهٔ {{domxref("EXT_color_buffer_float")}} در پلتفرم‌هایی است که از اهداف رندر ۱۶-بیتی ممیز شناور پشتیبانی می‌کنند اما از اهداف رندر ۳۲-بیتی ممیز شناور پشتیبانی نمی‌کنند.
>
> افزونهٔ {{domxref("OES_texture_half_float")}} به طور ضمنی این افزونه را فعال می‌کند.

## ثابت‌ها

- `ext.RGBA16F_EXT`
  - : فرمت RGBA ۱۶-بیتی ممیز شناور قابل رندر کردن به رنگ.
- `ext.RGB16F_EXT`
  - : فرمت RGB ۱۶-بیتی ممیز شناور. در WebGL 1.0، این ممکن است قابل رندر کردن به رنگ باشد (وابسته به پیاده‌سازی). در WebGL 2.0، این فرمت قابل رندر کردن به رنگ نیست.
- `ext.FRAMEBUFFER_ATTACHMENT_COMPONENT_TYPE_EXT`
  - : به متد {{domxref("WebGLRenderingContext.getFramebufferAttachmentParameter()")}} داده می‌شود تا نوع فریم‌بافر را دریافت کند.
- `ext.UNSIGNED_NORMALIZED_EXT`
  - : فریم‌بافر شامل مؤلفه‌های نقطه ثابت بدون علامت (unsigned fixed-point) است.

## متدهای گسترش‌یافته

این افزونه متد {{domxref("WebGLRenderingContext.renderbufferStorage()")}} را گسترش می‌دهد:

- در زمینه‌های WebGL 1.0، پارامتر `internalFormat` اکنون مقادیر `ext.RGBA16F_EXT` و `ext.RGB16F_EXT` را می‌پذیرد. با این حال، پشتیبانی از `ext.RGB16F_EXT` اختیاری است و برنامه‌ها باید کامل بودن فریم‌بافر را بررسی کنند تا مشخص شود آیا پشتیبانی می‌شود یا خیر.
- در زمینه‌های WebGL 2.0، پارامتر `internalFormat` اکنون `ext.RGBA16F_EXT` را می‌پذیرد. فرمت `RGB16F` در WebGL 2.0 قابل رندر کردن به رنگ نیست.

همچنین متد {{domxref("WebGLRenderingContext.getFramebufferAttachmentParameter()")}} را گسترش می‌دهد:

- در زمینه‌های WebGL 1.0، پارامتر `pname` اکنون `ext.FRAMEBUFFER_ATTACHMENT_COMPONENT_TYPE_EXT` را می‌پذیرد. اگر `attachment` برابر `DEPTH_STENCIL_ATTACHMENT` و `pname` برابر `FRAMEBUFFER_ATTACHMENT_COMPONENT_TYPE_EXT` باشد، خطای `INVALID_OPERATION` تولید می‌شود. وقتی `pname` برابر `ext.FRAMEBUFFER_ATTACHMENT_COMPONENT_TYPE_EXT` است، `getFramebufferAttachmentParameter()` به ترتیب برای مؤلفه‌های ممیز شناور یا نقطه ثابت بدون علامت، `gl.FLOAT` یا `gl.UNSIGNED_NORMALIZED_EXT` را برمی‌گرداند.

## مثال

```js
const ext = gl.getExtension("EXT_color_buffer_half_float");

gl.renderbufferStorage(gl.RENDERBUFFER, ext.RGBA16F_EXT, 256, 256);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLRenderingContext.renderbufferStorage()")}}
- {{domxref("OES_texture_half_float")}}
```