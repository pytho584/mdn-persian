---
title: "ANGLE_instanced_arrays: vertexAttribDivisorANGLE() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/ANGLE_instanced_arrays/vertexAttribDivisorANGLE"
translated_by: "n8n + AI"
---

متد **`ANGLE_instanced_arrays.vertexAttribDivisorANGLE()`** از [WebGL API](/en-US/docs/Web/API/WebGL_API) نرخ پیشروی generic vertex attributes را هنگام رندر کردن چندین نمونه از primitives با استفاده از {{domxref("ANGLE_instanced_arrays.drawArraysInstancedANGLE()", "ext.drawArraysInstancedANGLE()")}} و {{domxref("ANGLE_instanced_arrays.drawElementsInstancedANGLE()", "ext.drawElementsInstancedANGLE()")}} تغییر می‌دهد.

> [!NOTE]
> هنگام استفاده از {{domxref("WebGL2RenderingContext", "WebGL2")}}، این متد به‌طور پیش‌فرض به‌صورت {{domxref("WebGL2RenderingContext.vertexAttribDivisor()", "gl.vertexAttribDivisor()")}} در دسترس است.

## Syntax

```js-nolint
vertexAttribDivisorANGLE(index, divisor)
```

### Parameters

- `index`
  - : یک {{domxref("WebGL_API/Types", "GLuint")}} که اندیس generic vertex attributes را مشخص می‌کند.
- `divisor`
  - : یک {{domxref("WebGL_API/Types", "GLuint")}} که تعداد نمونه‌هایی را که بین به‌روزرسانی‌های generic attribute عبور می‌کنند مشخص می‌کند.

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

```js
const ext = gl.getExtension("ANGLE_instanced_arrays");
ext.vertexAttribDivisorANGLE(0, 2);
```

## همچنین ببینید

- {{domxref("ANGLE_instanced_arrays.drawArraysInstancedANGLE()", "ext.drawArraysInstancedANGLE()")}}
- {{domxref("ANGLE_instanced_arrays.drawElementsInstancedANGLE()", "ext.drawElementsInstancedANGLE()")}}
- {{domxref("WebGLRenderingContext.drawArrays()")}}
- {{domxref("WebGLRenderingContext.drawElements()")}}
- {{domxref("WebGL2RenderingContext.drawArraysInstanced()")}}
- {{domxref("WebGL2RenderingContext.drawElementsInstanced()")}}
- {{domxref("WebGL2RenderingContext.vertexAttribDivisor()")}}