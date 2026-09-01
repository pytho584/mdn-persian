---
title: "EXT_frag_depth extension"
short-title: EXT_frag_depth
slug: Web/API/EXT_frag_depth
page-type: webgl-extension
browser-compat: api.EXT_frag_depth
---

{{APIRef("WebGL")}}

افزونهٔ **`EXT_frag_depth`** بخشی از [WebGL API](/en-US/docs/Web/API/WebGL_API) است و امکان تنظیم مقدار عمق یک فرگمنت را از درون شیدر فرگمنت فراهم می‌کند.

افزونه‌های WebGL با استفاده از روش {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس هستند. برای اطلاعات بیشتر، به [استفاده از افزونه‌ها](/en-US/docs/Web/API/WebGL_API/Using_Extensions) در [آموزش WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial) مراجعه کنید.

> [!NOTE]
> این افزونه تنها در بافت‌های {{domxref("WebGLRenderingContext", "WebGL1", "", 1)}} قابل استفاده است. در {{domxref("WebGL2RenderingContext", "WebGL2", "", 1)}}، عملکرد این افزونه به‌طور پیش‌فرض در بافت WebGL2 در دسترس است. نیاز به GLSL `#version 300 es` دارد.

## مثال‌ها

فعال‌سازی افزونه:

```js
gl.getExtension("EXT_frag_depth");
```

اکنون متغیر خروجی `gl_FragDepthEXT` در دسترس است تا بتوانید مقدار عمق یک فرگمنت را از درون شیدر فرگمنت تنظیم کنید:

```html
<script type="x-shader/x-fragment">
  void main() {
    gl_FragColor = vec4(1.0, 0.0, 1.0, 1.0);
    gl_FragDepthEXT = 0.5;
  }
</script>
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}