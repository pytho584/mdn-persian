---
title: "KHR_parallel_shader_compile extension"
short-title: KHR_parallel_shader_compile
slug: Web/API/KHR_parallel_shader_compile
page-type: webgl-extension
browser-compat: api.KHR_parallel_shader_compile
---

{{APIRef("WebGL")}}

افزونه **`KHR_parallel_shader_compile`** بخشی از [WebGL API](/en-US/docs/Web/API/WebGL_API) است و عملیات نظرسنجی (poll) غیرمسدودکننده را امکان‌پذیر می‌سازد، به طوری که می‌توان وضعیت در دسترس بودن کامپایل/لینک (`COMPLETION_STATUS_KHR`) را بدون ایجاد توقف (stall) پرس‌وجو کرد. به عبارت دیگر، می‌توانید وضعیت کامپایل شدن شیدرهای خود را بدون مسدود کردن زمان اجرا بررسی کنید.

افزونه‌های WebGL با استفاده از متد {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس هستند. برای اطلاعات بیشتر، به بخش [Using Extensions](/en-US/docs/Web/API/WebGL_API/Using_Extensions) در [WebGL tutorial](/en-US/docs/Web/API/WebGL_API/Tutorial) مراجعه کنید.

## ثابت‌ها

- `ext.COMPLETION_STATUS_KHR`
  - : یک GLenum.

## مثال‌ها

فعال‌سازی افزونه:

```js
const ext = gl.getExtension("KHR_parallel_shader_compile");
```

به طور کلی، بهترین روش با یا بدون افزونه به صورت زیر است:

```js
// Assuming lists of `shaders` and `programs`:
for (const x of shaders) gl.compileShader(x); // Never check compile status unless subsequent linking fails.
for (const x of programs) gl.linkProgram(x);
```

با این افزونه، برنامه‌ها می‌توانند بدون ایجاد لرزش (jank) بررسی کنند که آیا برنامه‌ها لینک شده‌اند یا خیر، اما احتمالاً همان زمان کل دیوار (wall time) برای لینک شدن نیاز دارند:

```js
// Generator yielding a progress ratio [0.0, 1.0].
// Without the extension, this will jank and only check one program per generation.
function* linkingProgress(programs) {
  const ext = gl.getExtension("KHR_parallel_shader_compile");
  let todo = programs.slice();
  while (todo.length) {
    if (ext) {
      todo = todo.filter(
        (x) => !gl.getProgramParameter(x, ext.COMPLETION_STATUS_KHR),
      );
    } else {
      const x = todo.pop();
      gl.getProgramParameter(x, gl.LINK_STATUS);
    }
    if (!todo.length) return;
    yield 1.0 - todo.length / programs.length;
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}