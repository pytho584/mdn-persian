---
title: "EXT_shader_texture_lod extension"
short-title: EXT_shader_texture_lod
slug: Web/API/EXT_shader_texture_lod
page-type: webgl-extension
browser-compat: api.EXT_shader_texture_lod
---

{{APIRef("WebGL")}}

افزونهٔ **`EXT_shader_texture_lod`** بخشی از [WebGL API](/en-US/docs/Web/API/WebGL_API) است و توابع بافت اضافی‌ای را به زبان سایه‌زن OpenGL ES می‌افزاید که به نویسندهٔ سایه‌زن کنترل صریح بر LOD ([جزئیات سطح](https://en.wikipedia.org/wiki/Level_of_detail)) می‌دهد.

افزونه‌های WebGL از طریق متد {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس هستند. برای اطلاعات بیشتر، همچنین به [استفاده از افزونه‌ها](/en-US/docs/Web/API/WebGL_API/Using_Extensions) در [آموزش WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial) مراجعه کنید.

> [!NOTE]
> این افزونه فقط برای زمینه‌های (context) {{domxref("WebGLRenderingContext", "WebGL1", "", 1)}} در دسترس است. در {{domxref("WebGL2RenderingContext", "WebGL2", "", 1)}}، عملکرد این افزونه به‌طور پیش‌فرض در زمینهٔ WebGL2 موجود است. این افزونه به GLSL `#version 300 es` نیاز دارد.

## توابع داخلی GLSL

اگر این افزونه فعال باشد، توابع جدید زیر را می‌توان در کد سایه‌زن GLSL استفاده کرد:

```c
vec4 texture2DLodEXT(sampler2D sampler, vec2 coord, float lod)
vec4 texture2DProjLodEXT(sampler2D sampler, vec3 coord, float lod)
vec4 texture2DProjLodEXT(sampler2D sampler, vec4 coord, float lod)
vec4 textureCubeLodEXT(samplerCube sampler, vec3 coord, float lod)
vec4 texture2DGradEXT(sampler2D sampler, vec2 P, vec2 dPdx, vec2 dPdy)
vec4 texture2DProjGradEXT(sampler2D sampler, vec3 P, vec2 dPdx, vec2 dPdy)
vec4 texture2DProjGradEXT(sampler2D sampler, vec4 P, vec2 dPdx, vec2 dPdy)
vec4 textureCubeGradEXT(samplerCube sampler, vec3 P, vec3 dPdx, vec3 dPdy)
```

## مثال‌ها

فعال‌سازی افزونه:

```js
gl.getExtension("EXT_shader_texture_lod");
```

کد سایه‌زنی که هنگام پیچیدن مختصات بافت از ایجاد مصنوعات (artifacts) جلوگیری می‌کند:

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
- {{domxref("OES_standard_derivatives")}}