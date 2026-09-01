---
title: "EXT_texture_compression_bptc extension"
---

---
title: EXT_texture_compression_bptc extension
short-title: EXT_texture_compression_bptc
slug: Web/API/EXT_texture_compression_bptc
page-type: webgl-extension
browser-compat: api.EXT_texture_compression_bptc
---

{{APIRef("WebGL")}}

افزونهٔ `EXT_texture_compression_bptc` بخشی از [WebGL API](/en-US/docs/Web/API/WebGL_API) است و ۴ قالب فشرده‌سازی بافت BPTC را در دسترس قرار می‌دهد. این قالب‌های فشرده‌سازی در [DirectX API مایکروسافت](https://learn.microsoft.com/en-us/windows/win32/direct3d11/texture-block-compression-in-direct3d-11) با نام‌های [BC7](https://learn.microsoft.com/en-us/windows/win32/direct3d11/bc7-format) و [BC6H](https://learn.microsoft.com/en-us/windows/win32/direct3d11/bc6h-format) شناخته می‌شوند.

افزونه‌های WebGL از طریق متد {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس هستند. برای اطلاعات بیشتر، همچنین [استفاده از افزونه‌ها](/en-US/docs/Web/API/WebGL_API/Using_Extensions) را در [آموزش WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial) ببینید.

> [!NOTE]
> پشتیبانی به درایور گرافیکی سیستم بستگی دارد. در ویندوز پشتیبانی نمی‌شود.
>
> این افزونه برای هر دو زمینه (context) {{domxref("WebGLRenderingContext", "WebGL1", "", 1)}} و {{domxref("WebGL2RenderingContext", "WebGL2", "", 1)}} در دسترس است.

## ثابت‌ها

قالب‌های فشرده‌سازی بافت توسط ۴ ثابت ارائه می‌شوند و می‌توانند در دو تابع استفاده شوند: {{domxref("WebGLRenderingContext.compressedTexImage2D", "compressedTexImage2D()")}} و {{domxref("WebGLRenderingContext.compressedTexSubImage2D", "compressedTexSubImage2D()")}}.

- `ext.COMPRESSED_RGBA_BPTC_UNORM_EXT`
  - : داده‌های ۸ بیتی ممیز ثابت (fixed-point) را فشرده می‌کند. هر بلوک 4x4 تکسِل شامل 128 بیت دادهٔ RGBA یا تصویر است. همچنین ببینید: [قالب BC7](https://learn.microsoft.com/en-us/windows/win32/direct3d11/bc7-format).
- `ext.COMPRESSED_SRGB_ALPHA_BPTC_UNORM_EXT`
  - : داده‌های ۸ بیتی ممیز ثابت را فشرده می‌کند. هر بلوک 4x4 تکسِل شامل 128 بیت دادهٔ SRGB_ALPHA یا تصویر است. همچنین ببینید: [قالب BC7](https://learn.microsoft.com/en-us/windows/win32/direct3d11/bc7-format).
- `ext.COMPRESSED_RGB_BPTC_SIGNED_FLOAT_EXT`
  - : مقادیر ممیز شناور علامت‌دار با دامنهٔ پویای بالا را فشرده می‌کند. هر بلوک 4x4 تکسِل شامل 128 بیت دادهٔ RGB است. این قالب فقط دادهٔ RGB دارد، بنابراین مقدار آلفای بازگشتی 1.0 است. همچنین ببینید: [قالب BC6H](https://learn.microsoft.com/en-us/windows/win32/direct3d11/bc6h-format).
- `ext.COMPRESSED_RGB_BPTC_UNSIGNED_FLOAT_EXT`
  - : مقادیر ممیز شناور بدون علامت با دامنهٔ پویای بالا را فشرده می‌کند. هر بلوک 4x4 تکسِل شامل 128 بیت دادهٔ RGB است. این قالب فقط دادهٔ RGB دارد، بنابراین مقدار آلفای بازگشتی 1.0 است. همچنین ببینید: [قالب BC6H](https://learn.microsoft.com/en-us/windows/win32/direct3d11/bc6h-format).

## مثال‌ها

```js
const ext = gl.getExtension("EXT_texture_compression_bptc");

const texture = gl.createTexture();
gl.bindTexture(gl.TEXTURE_2D, texture);

gl.compressedTexImage2D(
  gl.TEXTURE_2D,
  0,
  ext.COMPRESSED_RGBA_BPTC_UNORM_EXT,
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