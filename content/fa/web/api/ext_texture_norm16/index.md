---
title: EXT_texture_norm16 extension
short-title: EXT_texture_norm16
slug: Web/API/EXT_texture_norm16
page-type: webgl-extension
browser-compat: api.EXT_texture_norm16
---

{{APIRef("WebGL")}}

افزونه **`EXT_texture_norm16`** بخشی از [WebGL API](/en-US/docs/Web/API/WebGL_API) است و مجموعه‌ای از فرمت‌های نرمال‌سازی‌شده با علامت (signed) و بدون علامت (unsigned) ۱۶ بیتی جدید (بافت نقطه‌ثابت، رندر بافر و بافت بافر) را ارائه می‌دهد.

هنگامی که این افزونه فعال باشد:

- متدهای {{domxref("WebGLRenderingContext.texImage2D()")}} و {{domxref("WebGLRenderingContext.texSubImage2D()")}} فرمت‌های جدید ارائه‌شده توسط این افزونه را می‌پذیرند.
- انواع نقطه‌ثابت نرمال‌سازی‌شده ۱۶ بیتی `ext.R16_EXT`، `ext.RG16_EXT` و `ext.RGBA16_EXT` به عنوان فرمت‌های قابل رندر رنگ در دسترس قرار می‌گیرند و رندر بافرها می‌توانند در این فرمت‌ها ایجاد شوند.

افزونه‌های WebGL با استفاده از متد {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس هستند. برای اطلاعات بیشتر، به [استفاده از افزونه‌ها](/en-US/docs/Web/API/WebGL_API/Using_Extensions) در [آموزش WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial) مراجعه کنید.

> [!NOTE]
> این افزونه فقط در زمینه‌های (context) {{domxref("WebGL2RenderingContext", "WebGL 2", "", 1)}} قابل استفاده است.

## ثابت‌ها

- `ext.R16_EXT`
  - : فرمت قرمز ۱۶ بیتی بدون علامت. قابل رندر رنگ.
- `ext.RG16_EXT`
  - : فرمت RG ۱۶ بیتی بدون علامت. قابل رندر رنگ.
- `ext.RGB16_EXT`
  - : فرمت RGB ۱۶ بیتی بدون علامت.
- `ext.RGBA16_EXT`
  - : فرمت RGBA ۱۶ بیتی بدون علامت. قابل رندر رنگ.
- `ext.R16_SNORM_EXT`
  - : فرمت قرمز ۱۶ بیتی نرمال‌سازی‌شده با علامت.
- `ext.RG16_SNORM_EXT`
  - : فرمت RG ۱۶ بیتی نرمال‌سازی‌شده با علامت.
- `ext.RGB16_SNORM_EXT`
  - : فرمت RGB ۱۶ بیتی نرمال‌سازی‌شده با علامت.
- `ext.RGBA16_SNORM_EXT`
  - : فرمت RGBA ۱۶ بیتی نرمال‌سازی‌شده با علامت.

## مثال‌ها

### فعال کردن افزونه

```js
let ext = gl.getExtension("EXT_texture_norm16");
```

### فرمت‌های بافت

متد {{domxref("WebGLRenderingContext.texImage2D()")}} هنگامی که `EXT_texture_norm16` فعال است، فرمت‌های جدیدی را می‌پذیرد. نمونه فراخوانی‌ها:

```js-nolint
// imageData = Uint16Array
gl.texImage2D(gl.TEXTURE_2D, 0, ext.R16_EXT, 1, 1, 0, gl.RED, gl.UNSIGNED_SHORT, imageData);
gl.texImage2D(gl.TEXTURE_2D, 0, ext.RG16_EXT, 1, 1, 0, gl.RG, gl.UNSIGNED_SHORT, imageData);
gl.texImage2D(gl.TEXTURE_2D, 0, ext.RGB16_EXT, 1, 1, 0, gl.RGB, gl.UNSIGNED_SHORT, imageData);
gl.texImage2D(gl.TEXTURE_2D, 0, ext.RGBA16_EXT, 1, 1, 0, gl.RGBA, gl.UNSIGNED_SHORT, imageData);

// imageData = Int16Array
gl.texImage2D(gl.TEXTURE_2D, 0, ext.R16_SNORM_EXT, 1, 1, 0, gl.RED, gl.SHORT, imageData);
gl.texImage2D(gl.TEXTURE_2D, 0, ext.RG16_SNORM_EXT, 1, 1, 0, gl.RG, gl.SHORT, imageData);
gl.texImage2D(gl.TEXTURE_2D, 0, ext.RGB16_SNORM_EXT, 1, 1, 0, gl.RGB, gl.SHORT, imageData);
gl.texImage2D(gl.TEXTURE_2D, 0, ext.RGBA16_SNORM_EXT, 1, 1, 0, gl.RGBA, gl.SHORT, imageData);
```

### فرمت‌های رندر بافر

متد {{domxref("WebGLRenderingContext.renderbufferStorage()")}} مقادیر `ext.R16_EXT`،
`ext.RG16_EXT` و `ext.RGBA16_EXT` را به عنوان فرمت‌های داخلی برای ایجاد رندر بافرها در این فرمت‌ها می‌پذیرد. نمونه فراخوانی‌ها:

```js
gl.renderbufferStorage(gl.RENDERBUFFER, ext.R16_EXT, 1, 1);
gl.renderbufferStorage(gl.RENDERBUFFER, ext.RG16_EXT, 1, 1);
gl.renderbufferStorage(gl.RENDERBUFFER, ext.RGBA16_EXT, 1, 1);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLRenderingContext.texImage2D()")}}
- {{domxref("WebGLRenderingContext.renderbufferStorage()")}}