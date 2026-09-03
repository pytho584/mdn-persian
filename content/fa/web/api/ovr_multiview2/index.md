---
title: OVR_multiview2 extension
short-title: OVR_multiview2
slug: Web/API/OVR_multiview2
page-type: webgl-extension
browser-compat: api.OVR_multiview2
---

{{APIRef("WebGL")}}

افزونهٔ `OVR_multiview2` بخشی از [WebGL API](/en-US/docs/Web/API/WebGL_API) است و پشتیبانی از رندر همزمان به چند نما (view) را اضافه می‌کند. این قابلیت به‌ویژه برای واقعیت مجازی (VR) و WebXR مفید است.

برای اطلاعات بیشتر، همچنین ببینید:

- [Multiview on WebXR](https://error.ghost.org/)
- [Multiview in babylon.js](https://doc.babylonjs.com/features/featuresDeepDive/cameras/multiViewsPart1)
- [Optimizing Virtual Reality: Understanding Multiview](https://developer.arm.com/community/arm-community-blogs/b/mobile-graphics-and-gaming-blog/posts/optimizing-virtual-reality-understanding-multiview)
- [Multiview WebGL Rendering for Meta Quest](https://developers.meta.com/horizon/documentation/web/web-multiview/)

افزونه‌های WebGL از طریق متد {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس قرار می‌گیرند. برای اطلاعات بیشتر، همچنین به [Using Extensions](/en-US/docs/Web/API/WebGL_API/Using_Extensions) در [WebGL tutorial](/en-US/docs/Web/API/WebGL_API/Tutorial) مراجعه کنید.

> [!NOTE]
> پشتیبانی به درایور گرافیکی سیستم بستگی دارد (Windows+ANGLE و Android پشتیبانی می‌شوند؛ Windows+GL، Mac و Linux پشتیبانی نمی‌شوند).
>
> این افزونه فقط در context‌های {{domxref("WebGL2RenderingContext", "WebGL 2", "", 1)}} در دسترس است، زیرا به GLSL 3.00 و آرایه‌های بافت (texture arrays) نیاز دارد.
>
> در حال حاضر، هیچ راهی برای استفاده از multiview به‌منظور رندر به backbuffer با نمونه‌برداری چندگانه وجود ندارد، بنابراین باید context‌ها را با `antialias: false` ایجاد کنید. با این حال، مرورگر Oculus (نسخهٔ ۶+) همچنین با استفاده از افزونهٔ [`OCULUS_multiview`](https://developers.meta.com/horizon/documentation/web/web-multiview/#using-oculus_multiview-in-webgl-20) از نمونه‌برداری چندگانه پشتیبانی می‌کند. همچنین به [this WebGL issue](https://github.com/KhronosGroup/WebGL/issues/2912) مراجعه کنید.

## ثابت‌ها

این افزونه ۴ ثابت را در دسترس قرار می‌دهد که می‌توانند در [`getParameter()`](/en-US/docs/Web/API/WebGLRenderingContext/getParameter) یا [`getFramebufferAttachmentParameter()`](/en-US/docs/Web/API/WebGLRenderingContext/getFramebufferAttachmentParameter) استفاده شوند.

- `FRAMEBUFFER_ATTACHMENT_TEXTURE_NUM_VIEWS_OVR`
  - : تعداد نماهای (views) پیوستِ شیءِ فریم‌بافر.
- `FRAMEBUFFER_ATTACHMENT_TEXTURE_BASE_VIEW_INDEX_OVR`
  - : شاخص نمای پایه (base view index) پیوستِ شیءِ فریم‌بافر.
- `MAX_VIEWS_OVR`
  - : حداکثر تعداد نماها. اکثر هدست‌های واقعیت مجازی دو نما دارند، اما نمونه‌های اولیه‌ای از هدست‌ها با میدان دید فوق‌عریض (ultra-wide FOV) وجود دارند که از ۴ نما استفاده می‌کنند؛ در حال حاضر ۴ نما حداکثر تعداد پشتیبانی‌شده توسط multiview است.
- `FRAMEBUFFER_INCOMPLETE_VIEW_TARGETS_OVR`
  - : اگر baseViewIndex برای همهٔ نقاط پیوست فریم‌بافر که در آن‌ها مقدار `FRAMEBUFFER_ATTACHMENT_OBJECT_TYPE` برابر با `NONE` نیست یکسان نباشد، فریم‌بافر ناقص (incomplete) در نظر گرفته می‌شود. فراخوانی [`checkFramebufferStatus`](/en-US/docs/Web/API/WebGLRenderingContext/checkFramebufferStatus) برای فریم‌بافری در این حالت، مقدار `FRAMEBUFFER_INCOMPLETE_VIEW_TARGETS_OVR` را برمی‌گرداند.

## متدهای نمونه

- [`framebufferTextureMultiviewOVR()`](/en-US/docs/Web/API/OVR_multiview2/framebufferTextureMultiviewOVR)
  - : به‌طور همزمان به چند عنصر از یک آرایه بافت دوبعدی (2D texture array) رندر می‌کند.

## مثال‌ها

این مثال از [specification](https://registry.khronos.org/webgl/extensions/OVR_multiview2/) گرفته شده است.

```js
const gl = document
  .createElement("canvas")
  .getContext("webgl2", { antialias: false });
const ext = gl.getExtension("OVR_multiview2");
const fb = gl.createFramebuffer();
gl.bindFramebuffer(gl.DRAW_FRAMEBUFFER, fb);

const colorTex = gl.createTexture();
gl.bindTexture(gl.TEXTURE_2D_ARRAY, colorTex);
gl.texStorage3D(gl.TEXTURE_2D_ARRAY, 1, gl.RGBA8, 512, 512, 2);
ext.framebufferTextureMultiviewOVR(
  gl.DRAW_FRAMEBUFFER,
  gl.COLOR_ATTACHMENT0,
  colorTex,
  0,
  0,
  2,
);

const depthStencilTex = gl.createTexture();
gl.bindTexture(gl.TEXTURE_2D_ARRAY, depthStencilTex);
gl.texStorage3D(gl.TEXTURE_2D_ARRAY, 1, gl.DEPTH32F_STENCIL8, 512, 512, 2);

ext.framebufferTextureMultiviewOVR(
  gl.DRAW_FRAMEBUFFER,
  gl.DEPTH_STENCIL_ATTACHMENT,
  depthStencilTex,
  0,
  0,
  2,
);
gl.drawElements(/* … */); // draw will be broadcasted to the layers of colorTex and depthStencilTex.
```

کد شیدر

```glsl
#version 300 es
#extension GL_OVR_multiview2 : require
precision mediump float;
layout (num_views = 2) in;
in vec4 inPos;
uniform mat4 u_viewMatrices[2];
void main() {
  gl_Position = u_viewMatrices[gl_ViewID_OVR] * inPos;
}
```

همچنین، برای مشاهدهٔ یک مثال زنده از multiview، این [three.js](https://threejs.org/examples/?q=mult#webgl_multiple_views) دمو را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLRenderingContext.getParameter()")}}
- [WebXR](/en-US/docs/Web/API/WebXR_Device_API)