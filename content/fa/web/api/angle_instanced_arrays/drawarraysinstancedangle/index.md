---
title: "ANGLE_instanced_arrays: drawArraysInstancedANGLE() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/ANGLE_instanced_arrays/drawArraysInstancedANGLE"
translated_by: "n8n + AI"
---

# متد drawArraysInstancedANGLE()

متد **`ANGLE_instanced_arrays.drawArraysInstancedANGLE()`** در [WebGL API](/en-US/docs/Web/API/WebGL_API)، مانند متد [`gl.drawArrays()`](/en-US/docs/Web/API/WebGLRenderingContext/drawArrays)، اشکال هندسی (primitives) را از روی داده‌های آرایه‌ای رندر می‌کند. علاوه بر این، می‌تواند چندین instance از بازهٔ عناصر را اجرا کند.

> [!NOTE]
> در [WebGL2](/en-US/docs/Web/API/WebGL2RenderingContext)، این متد به‌طور پیش‌فرض با نام [`gl.drawArraysInstanced()`](/en-US/docs/Web/API/WebGL2RenderingContext/drawArraysInstanced) در دسترس است.

## Syntax

```js-nolint
drawArraysInstancedANGLE(mode, first, count, primcount)
```

### پارامترها

- `mode`
  - : یک [`GLenum`](/en-US/docs/Web/API/WebGL_API/Types) که نوع primitive برای رندر را مشخص می‌کند. مقادیر ممکن:
    - `gl.POINTS`: یک نقطه رسم می‌کند.
    - `gl.LINE_STRIP`: یک خط راست به رأس بعدی رسم می‌کند.
    - `gl.LINE_LOOP`: یک خط راست به رأس بعدی رسم کرده و رأس آخر را به رأس اول وصل می‌کند.
    - `gl.LINES`: یک خط بین دو رأس رسم می‌کند.
    - [`gl.TRIANGLE_STRIP`](https://en.wikipedia.org/wiki/Triangle_strip)
    - [`gl.TRIANGLE_FAN`](https://en.wikipedia.org/wiki/Triangle_fan)
    - `gl.TRIANGLES`: برای هر گروه سه‌تایی از رأس‌ها، یک مثلث رسم می‌کند.

- `first`
  - : یک [`GLint`](/en-US/docs/Web/API/WebGL_API/Types) که شاخص شروع در آرایهٔ نقاط برداری را مشخص می‌کند.
- `count`
  - : یک [`GLsizei`](/en-US/docs/Web/API/WebGL_API/Types) که تعداد شاخص‌هایی که باید رندر شوند را مشخص می‌کند.
- `primcount`
  - : یک [`GLsizei`](/en-US/docs/Web/API/WebGL_API/Types) که تعداد instanceهای بازهٔ عناصر برای اجرا را مشخص می‌کند.

### مقدار بازگشتی

مقداری بازگردانده نمی‌شود (`undefined`).

### استثناها

- اگر `mode` یکی از مقادیر مجاز نباشد، خطای `gl.INVALID_ENUM` صادر می‌شود.
- اگر `first`، `count` یا `primcount` منفی باشند، خطای `gl.INVALID_VALUE` صادر می‌شود.
- اگر `gl.CURRENT_PROGRAM` برابر با [`null`](/en-US/docs/Web/JavaScript/Reference/Operators/null) باشد، خطای `gl.INVALID_OPERATION` صادر می‌شود.

## مثال

```js
const ext = gl.getExtension("ANGLE_instanced_arrays");
ext.drawArraysInstancedANGLE(gl.POINTS, 0, 8, 4);
```

## جستارهای وابسته

- [`ext.drawElementsInstancedANGLE()`](/en-US/docs/Web/API/ANGLE_instanced_arrays/drawElementsInstancedANGLE)
- [`ext.vertexAttribDivisorANGLE()`](/en-US/docs/Web/API/ANGLE_instanced_arrays/vertexAttribDivisorANGLE)
- [`gl.drawArrays()`](/en-US/docs/Web/API/WebGLRenderingContext/drawArrays)
- [`gl.drawElements()`](/en-US/docs/Web/API/WebGLRenderingContext/drawElements)
- [`gl.drawArraysInstanced()`](/en-US/docs/Web/API/WebGL2RenderingContext/drawArraysInstanced)
- [`gl.drawElementsInstanced()`](/en-US/docs/Web/API/WebGL2RenderingContext/drawElementsInstanced)
- [`gl.vertexAttribDivisor()`](/en-US/docs/Web/API/WebGL2RenderingContext/vertexAttribDivisor)
- [`multiDrawArraysInstancedWEBGL()`](/en-US/docs/Web/API/WEBGL_multi_draw/multiDrawArraysInstancedWEBGL)