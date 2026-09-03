---
title: OES_standard_derivatives extension
short-title: OES_standard_derivatives
slug: Web/API/OES_standard_derivatives
page-type: webgl-extension
browser-compat: api.OES_standard_derivatives
---

{{APIRef("WebGL")}}

افزونهٔ **`OES_standard_derivatives`** بخشی از [WebGL API](/en-US/docs/Web/API/WebGL_API) است و توابع مشتق GLSL یعنی `dFdx`، `dFdy` و `fwidth` را اضافه می‌کند.

افزونه‌های WebGL از طریق متد {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس قرار می‌گیرند. برای اطلاعات بیشتر، به [استفاده از افزونه‌ها](/en-US/docs/Web/API/WebGL_API/Using_Extensions) در [آموزش WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial) نیز مراجعه کنید.

> [!NOTE]
> این افزونه فقط در دسترس زمینه‌های {{domxref("WebGLRenderingContext", "WebGL1", "", 1)}} است. در {{domxref("WebGL2RenderingContext", "WebGL2", "", 1)}}، عملکرد این افزونه به‌صورت پیش‌فرض در زمینهٔ WebGL2 در دسترس است. در WebGL 2 این ثابت با نام `gl.FRAGMENT_SHADER_DERIVATIVE_HINT` در دسترس است و استفاده از آن به GLSL با `#version 300 es` نیاز دارد.

## ثابت‌ها

این افزونه یک ثابت جدید ارائه می‌کند که می‌توان از آن در متدهای {{domxref("WebGLRenderingContext.hint()", "hint()")}} و {{domxref("WebGLRenderingContext.getParameter()", "getParameter()")}} استفاده کرد.

- `ext.FRAGMENT_SHADER_DERIVATIVE_HINT_OES`
  - : یک {{domxref("WebGL_API.Types", "GLenum")}} که دقت محاسبهٔ مشتق را برای توابع توکار GLSL مشخص می‌کند: `dFdx`، `dFdy` و `fwidth`.

## توابع توکار GLSL

اگر این افزونه فعال شده باشد، می‌توان از توابع جدید زیر در کد شیدر GLSL استفاده کرد:

```c
genType dFdx(genType p)
genType dFdy(genType p)
genType fwidth(genType p)
```

- `dFdx()`
  - : مشتق نسبت به `x` را با استفاده از تفاضل محلی برای آرگومان ورودی `p` برمی‌گرداند.
- `dFdy()`
  - : مشتق نسبت به `y` را با استفاده از تفاضل محلی برای آرگومان ورودی `p` برمی‌گرداند.
- `fwidth()`
  - : مجموع قدر مطلق مشتق نسبت به `x` و `y` را با استفاده از تفاضل محلی برای آرگومان ورودی `p` برمی‌گرداند. یعنی `abs(dFdx(p)) + abs(dFdy(p))`.

`dFdx()` و `dFdy()` معمولاً برای تخمین پهنای فیلتر مورد استفاده در ضدآلیاسینگ بافت‌های رویه‌ای (procedural textures) به کار می‌روند.

## مثال‌ها

فعال‌کردن افزونه‌ها:

```js
gl.getExtension("OES_standard_derivatives");
gl.getExtension("EXT_shader_texture_lod");
```

کد شیدری که هنگام پیچیدن (wrapping) مختصات بافت از بروز مصنوعات جلوگیری می‌کند:

```html
<script type="x-shader/x-fragment">
  #extension GL_EXT_shader_texture_lod : enable
  #extension GL_OES_standard_derivatives : enable

  uniform sampler2D myTexture;
  varying vec2 texCoord;

  void main(){
    gl_FragColor = texture2DGradEXT(myTexture, mod(texCoord, vec2(0.1, 0.5)),
                                    dFdx(texCoord), dFdy(texCoord));
  }
</script>
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("EXT_shader_texture_lod")}}