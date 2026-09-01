---
title: "EXT_texture_filter_anisotropic extension"
---

---
title: EXT_texture_filter_anisotropic extension
short-title: EXT_texture_filter_anisotropic
slug: Web/API/EXT_texture_filter_anisotropic
page-type: webgl-extension
browser-compat: api.EXT_texture_filter_anisotropic
---

{{APIRef("WebGL")}}

افزونهٔ **`EXT_texture_filter_anisotropic`** بخشی از [WebGL API](/en-US/docs/Web/API/WebGL_API) است و دو ثابت را برای [فیلتر ناهمسانگرد (AF)](https://en.wikipedia.org/wiki/Anisotropic_filtering) در اختیار قرار می‌دهد.

AF کیفیت دسترسی به بافت mipmapped را هنگام مشاهدهٔ یک شیء بافت‌دار در زاویهٔ مورب بهبود می‌بخشد. با استفاده از فقط mipmapping، این دسترسی‌ها تمایل دارند به سمت خاکستری میانگین شوند.

افزونه‌های WebGL با استفاده از روش {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس هستند. برای اطلاعات بیشتر، همچنین [استفاده از افزونه‌ها](/en-US/docs/Web/API/WebGL_API/Using_Extensions) را در [آموزش WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial) ببینید.

> [!NOTE]
> این افزونه برای هر دو زمینهٔ {{domxref("WebGLRenderingContext", "WebGL1", "", 1)}} و {{domxref("WebGL2RenderingContext", "WebGL2", "", 1)}} در دسترس است.

## ثابت‌ها

- `ext.MAX_TEXTURE_MAX_ANISOTROPY_EXT`
  - : این آرگومان `pname` برای فراخوانی {{domxref("WebGLRenderingContext.getParameter", "gl.getParameter()")}} است و حداکثر ناهمسانگردی موجود را برمی‌گرداند.
- `ext.TEXTURE_MAX_ANISOTROPY_EXT`
  - : این آرگومان `pname` برای فراخوانی‌های {{domxref("WebGLRenderingContext.getTexParameter", "gl.getTexParameter()")}} و {{domxref("WebGLRenderingContext.texParameter", "gl.texParameterf()")}} / {{domxref("WebGLRenderingContext.texParameter", "gl.texParameteri()")}} است و حداکثر ناهمسانگردی مورد نظر را برای یک بافت تنظیم می‌کند.

## نمونه‌ها

```js
const texture = gl.createTexture();
gl.bindTexture(gl.TEXTURE_2D, texture);
const ext =
  gl.getExtension("EXT_texture_filter_anisotropic") ||
  gl.getExtension("MOZ_EXT_texture_filter_anisotropic") ||
  gl.getExtension("WEBKIT_EXT_texture_filter_anisotropic");
if (ext) {
  const max = gl.getParameter(ext.MAX_TEXTURE_MAX_ANISOTROPY_EXT);
  gl.texParameterf(gl.TEXTURE_2D, ext.TEXTURE_MAX_ANISOTROPY_EXT, max);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}