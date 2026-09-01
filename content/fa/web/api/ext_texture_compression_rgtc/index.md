---
title: EXT_texture_compression_rgtc extension
short-title: EXT_texture_compression_rgtc
slug: Web/API/EXT_texture_compression_rgtc
page-type: webgl-extension
browser-compat: api.EXT_texture_compression_rgtc
---

{{APIRef("WebGL")}}

افزونه `EXT_texture_compression_rgtc` بخشی از [WebGL API](/en-US/docs/Web/API/WebGL_API) است و ۴ فرمت فشرده‌سازی بافت RGTC را در دسترس قرار می‌دهد. RGTC یک فرمت فشرده‌سازی بافت مبتنی بر بلوک است که برای بافت‌های قرمز و قرمز-سبز بدون علامت و با علامت (**R**ed-**G**reen **T**exture **C**ompression) مناسب است.

افزونه‌های WebGL با استفاده از متد {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس هستند. برای اطلاعات بیشتر، به [استفاده از افزونه‌ها](/en-US/docs/Web/API/WebGL_API/Using_Extensions) در [آموزش WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial) مراجعه کنید.

> [!NOTE]
> پشتیبانی به درایور گرافیکی سیستم بستگی دارد. در ویندوز پشتیبانی نمی‌شود.
>
> این افزونه برای هر دو زمینه {{domxref("WebGLRenderingContext", "WebGL1", "", 1)}} و {{domxref("WebGL2RenderingContext", "WebGL2", "", 1)}} در دسترس است.

## ثابت‌ها

فرمت‌های فشرده‌سازی بافت توسط ۴ ثابت ارائه می‌شوند و می‌توان از آنها در دو تابع استفاده کرد: {{domxref("WebGLRenderingContext.compressedTexImage2D", "compressedTexImage2D()")}} و {{domxref("WebGLRenderingContext.compressedTexSubImage2D", "compressedTexSubImage2D()")}}.

- `ext.COMPRESSED_RED_RGTC1_EXT`
  - : هر بلوک ۴×۴ از تکسِل‌ها از ۶۴ بیت داده تصویر قرمز بدون علامت تشکیل شده است. همچنین به [BC4 unsigned](https://learn.microsoft.com/en-us/windows/win32/direct3d10/d3d10-graphics-programming-guide-resources-block-compression#bc4) مراجعه کنید.
- `ext.COMPRESSED_SIGNED_RED_RGTC1_EXT`
  - : هر بلوک ۴×۴ از تکسِل‌ها از ۶۴ بیت داده تصویر قرمز با علامت تشکیل شده است. همچنین به [BC4 signed](https://learn.microsoft.com/en-us/windows/win32/direct3d10/d3d10-graphics-programming-guide-resources-block-compression#bc4) مراجعه کنید.
- `ext.COMPRESSED_RED_GREEN_RGTC2_EXT`
  - : هر بلوک ۴×۴ از تکسِل‌ها از ۶۴ بیت داده تصویر قرمز فشرده‌شده بدون علامت به همراه ۶۴ بیت داده تصویر سبز فشرده‌شده بدون علامت تشکیل شده است. همچنین به [BC5 unsigned](https://learn.microsoft.com/en-us/windows/win32/direct3d10/d3d10-graphics-programming-guide-resources-block-compression#bc5) مراجعه کنید.
- `ext.COMPRESSED_SIGNED_RED_GREEN_RGTC2_EXT`
  - : هر بلوک ۴×۴ از تکسِل‌ها از ۶۴ بیت داده تصویر قرمز فشرده‌شده با علامت به همراه ۶۴ بیت داده تصویر سبز فشرده‌شده با علامت تشکیل شده است. همچنین به [BC5 signed](https://learn.microsoft.com/en-us/windows/win32/direct3d10/d3d10-graphics-programming-guide-resources-block-compression#bc5) مراجعه کنید.

## مثال‌ها

```js
const ext = gl.getExtension("EXT_texture_compression_rgtc");

const texture = gl.createTexture();
gl.bindTexture(gl.TEXTURE_2D, texture);

gl.compressedTexImage2D(
  gl.TEXTURE_2D,
  0,
  ext.COMPRESSED_RED_RGTC1_EXT,
  128,
  128,
  0,
  textureData,
);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLRenderingContext.compressedTexImage2D()")}}
- {{domxref("WebGLRenderingContext.compressedTexSubImage2D()")}}
- {{domxref("WebGLRenderingContext.getParameter()")}}