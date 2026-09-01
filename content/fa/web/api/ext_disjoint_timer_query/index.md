---
title: EXT_disjoint_timer_query extension
short-title: EXT_disjoint_timer_query
slug: Web/API/EXT_disjoint_timer_query
page-type: webgl-extension
browser-compat: api.EXT_disjoint_timer_query
---

{{APIRef("WebGL")}}

افزونه **EXT_disjoint_timer_query** بخشی از [WebGL API](/en-US/docs/Web/API/WebGL_API) است و راهی برای اندازه‌گیری مدت زمان اجرای مجموعه‌ای از دستورات GL فراهم می‌کند، بدون اینکه خط لوله رندر را متوقف کند.

افزونه‌های WebGL از طریق متد {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس هستند. برای اطلاعات بیشتر، به [استفاده از افزونه‌ها](/en-US/docs/Web/API/WebGL_API/Using_Extensions) در [آموزش WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial) مراجعه کنید.

> [!NOTE]
> این افزونه فقط در بسترهای {{domxref("WebGLRenderingContext", "WebGL1", "", 1)}} در دسترس است. {{domxref("EXT_disjoint_timer_query_webgl2")}} در بسترهای {{domxref("WebGL2RenderingContext", "WebGL 2", "", 1)}} در دسترس است.
>
> در WebGL 2، متد OpenGL `getQueryObject()` به {{domxref("WebGL2RenderingContext.getQueryParameter")}} تغییر نام داده است.
> در WebGL 2، پرس‌وجوهای دیگر (مانند پرس‌وجوهای occlusion و پرس‌وجوهای اولیه) با استفاده از اشیاء {{domxref("WebGLQuery")}} امکان‌پذیر است.

## انواع

این افزونه یک نوع جدید را معرفی می‌کند:

- `GLuint64EXT`
  - : عدد صحیح ۶۴ بیتی بدون علامت.

## ثابت‌ها

این افزونه هفت ثابت جدید را معرفی می‌کند.

- `ext.QUERY_COUNTER_BITS_EXT`
  - : یک {{domxref("WebGL_API/Types", "GLint")}} که تعداد بیت‌های استفاده‌شده برای نگهداری نتیجه پرس‌وجو برای هدف داده شده را نشان می‌دهد.
- `ext.CURRENT_QUERY_EXT`
  - : یک شیء {{domxref("WebGLQuery")}} که پرس‌وجوی فعال فعلی برای هدف داده شده است.
- `ext.QUERY_RESULT_EXT`
  - : یک {{domxref("WebGL_API/Types", "GLuint64EXT")}} شامل نتیجه پرس‌وجو.
- `ext.QUERY_RESULT_AVAILABLE_EXT`
  - : یک {{domxref("WebGL_API/Types", "GLboolean")}} که نشان می‌دهد آیا نتیجه پرس‌وجو در دسترس است یا خیر.
- `ext.TIME_ELAPSED_EXT`
  - : زمان سپری شده (به نانوثانیه).
- `ext.TIMESTAMP_EXT`
  - : زمان فعلی.
- `ext.GPU_DISJOINT_EXT`
  - : یک {{domxref("WebGL_API/Types", "GLboolean")}} که نشان می‌دهد آیا GPU هرگونه عملیات ناپیوسته (disjoint) انجام داده است یا خیر.

## متدهای نمونه

این افزونه هشت متد جدید را معرفی می‌کند.

- {{domxref("EXT_disjoint_timer_query.createQueryEXT()", "ext.createQueryEXT()")}}
  - : یک {{domxref("WebGLQuery")}} جدید ایجاد می‌کند.
- {{domxref("EXT_disjoint_timer_query.deleteQueryEXT()", "ext.deleteQueryEXT()")}}
  - : یک {{domxref("WebGLQuery")}} داده شده را حذف می‌کند.
- {{domxref("EXT_disjoint_timer_query.isQueryEXT()", "ext.isQueryEXT()")}}
  - : اگر یک شیء داده شده یک {{domxref("WebGLQuery")}} معتبر باشد، `true` برمی‌گرداند.
- {{domxref("EXT_disjoint_timer_query.beginQueryEXT()", "ext.beginQueryEXT()")}}
  - : تایمر زمانی شروع می‌شود که تمام دستورات قبل از `beginQueryEXT` به طور کامل اجرا شده باشند.
- {{domxref("EXT_disjoint_timer_query.endQueryEXT()", "ext.endQueryEXT()")}}
  - : تایمر زمانی متوقف می‌شود که تمام دستورات قبل از `endQueryEXT` به طور کامل اجرا شده باشند.
- {{domxref("EXT_disjoint_timer_query.queryCounterEXT()", "ext.queryCounterEXT()")}}
  - : زمان فعلی را در شیء پرس‌وجوی مربوطه ثبت می‌کند.
- {{domxref("EXT_disjoint_timer_query.getQueryEXT()", "ext.getQueryEXT()")}}
  - : اطلاعاتی درباره یک هدف پرس‌وجو برمی‌گرداند.
- {{domxref("EXT_disjoint_timer_query.getQueryObjectEXT()", "ext.getQueryObjectEXT()")}}
  - : وضعیت یک شیء پرس‌وجو را برمی‌گرداند.

## مثال‌ها

```js
const ext = gl.getExtension("EXT_disjoint_timer_query");
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}