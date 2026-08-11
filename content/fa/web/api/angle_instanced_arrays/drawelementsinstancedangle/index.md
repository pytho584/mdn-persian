---
title: "ANGLE_instanced_arrays: drawElementsInstancedANGLE() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/ANGLE_instanced_arrays/drawElementsInstancedANGLE"
translated_by: "n8n + AI"
---

متد **`ANGLE_instanced_arrays.drawElementsInstancedANGLE()`** از [WebGL API](/en-US/docs/Web/API/WebGL_API) ابتدایی‌ها (primitives) را از روی داده‌های آرایه‌ای رندر می‌کند، درست مانند متد `gl.drawElements()`. علاوه بر این، می‌تواند چندین نمونه از یک مجموعه عنصر را نیز اجرا کند.

> [!NOTE]
> هنگام استفاده از WebGL2، این متد به‌طور پیش‌فرض با نام `gl.drawElementsInstanced()` در دسترس است.

## نحوه استفاده

```js-nolint
drawElementsInstancedANGLE(mode, count, type, offset, primcount)
```

### پارامترها

- `mode`
  - : یک `GLenum` که نوع اولیه برای ترسیم را مشخص می‌کند. مقادیر قابل قبول:
    - `gl.POINTS`: یک نقطه رسم می‌کند.
    - `gl.LINE_STRIP`: یک خط مستقیم به رأس بعدی رسم می‌کند.
    - `gl.LINE_LOOP`: یک خط مستقیم به رأس بعدی رسم می‌کند و رأس آخر را به رأس اول متصل می‌کند.
    - `gl.LINES`: خطی بین یک جفت رأس رسم می‌کند.
    - [`gl.TRIANGLE_STRIP`](https://en.wikipedia.org/wiki/Triangle_strip)
    - [`gl.TRIANGLE_FAN`](https://en.wikipedia.org/wiki/Triangle_fan)
    - `gl.TRIANGLES`: برای هر گروه سه‌تایی از رئوس یک مثلث رسم می‌کند.

- `count`
  - : یک `GLsizei` که تعداد عناصر برای رندر را مشخص می‌کند.
- `type`
  - : یک `GLenum` که نوع مقادیر موجود در بافر آرایه عناصر را مشخص می‌کند. مقادیر قابل قبول:
    - `gl.UNSIGNED_BYTE`
    - `gl.UNSIGNED_SHORT`
    - `gl.UNSIGNED_INT` (به‌همراه افزونه `OES_element_index_uint`)

- `offset`
  - : یک `GLintptr` که یک offset در بافر آرایه عناصر را مشخص می‌کند. باید مضرب صحیحی از اندازه `type` داده شده باشد.
- `primcount`
  - : یک `GLsizei` که تعداد نمونه‌های مجموعه عناصر برای اجرا را مشخص می‌کند.

### مقدار بازگشتی

هیچ (`undefined`).

### استثناها

- اگر `mode` یکی از مقادیر قابل قبول نباشد، خطای `gl.INVALID_ENUM` رخ می‌دهد.
- اگر `offset` مضرب صحیحی از اندازه نوع داده شده نباشد، خطای `gl.INVALID_OPERATION` رخ می‌دهد.
- اگر `count` یا `primcount` منفی باشند، خطای `gl.INVALID_VALUE` رخ می‌دهد.

## مثال

```js
const ext = gl.getExtension("ANGLE_instanced_arrays");
ext.drawElementsInstancedANGLE(gl.POINTS, 2, gl.UNSIGNED_SHORT, 0, 4);
```

## مشخصات

## سازگاری مرورگر

## جستارهای وابسته

- `ext.drawArraysInstancedANGLE()`
- `ext.vertexAttribDivisorANGLE()`
- `gl.drawArrays()`
- `gl.drawElements()`
- `gl.drawArraysInstanced()`
- `gl.drawElementsInstanced()`
- `gl.vertexAttribDivisor()`
- `multiDrawElementsInstancedWEBGL()`