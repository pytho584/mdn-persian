---
title: "EXT_disjoint_timer_query: getQueryObjectEXT() method"
short-title: getQueryObjectEXT()
slug: Web/API/EXT_disjoint_timer_query/getQueryObjectEXT
page-type: webgl-extension-method
browser-compat: api.EXT_disjoint_timer_query.getQueryObjectEXT
---

{{APIRef("WebGL")}}

متد **`EXT_disjoint_timer_query.getQueryObjectEXT()`** در [WebGL API](/en-US/docs/Web/API/WebGL_API) وضعیت یک شیء پرس‌وجو (query object) را برمی‌گرداند.

## Syntax

```js-nolint
getQueryObjectEXT(query, pname)
```

### پارامترها

- `query`
  - : یک شیء {{domxref("WebGLQuery")}} که اطلاعات از آن گرفته می‌شود.
- `pname`
  - : یک {{domxref("WebGL_API/Types", "GLenum")}} که مشخص می‌کند کدام اطلاعات برگردانده شود. باید یکی از مقادیر `ext.QUERY_RESULT_EXT` یا `ext.QUERY_RESULT_AVAILABLE_EXT` باشد.

### مقدار بازگشتی

بستگی به `pname` دارد:

- اگر `pname` برابر `ext.QUERY_RESULT_EXT` باشد: یک {{domxref("WebGL_API/Types", "GLuint64EXT")}} حاوی نتیجه پرس‌وجو.
- اگر `pname` برابر `ext.QUERY_RESULT_AVAILABLE_EXT` باشد: یک {{domxref("WebGL_API/Types", "GLboolean")}} که نشان می‌دهد آیا نتیجه پرس‌وجو در دسترس است یا خیر.

## مثال‌ها

```js
const ext = gl.getExtension("EXT_disjoint_timer_query");
const query = ext.createQueryEXT();
ext.beginQueryEXT(ext.TIME_ELAPSED_EXT, query);

// رسم
ext.endQueryEXT(ext.TIME_ELAPSED_EXT);

// در آینده و پس از بازگشت کنترل به مرورگر
const available = ext.getQueryObjectEXT(query, ext.QUERY_RESULT_AVAILABLE_EXT);
const disjoint = gl.getParameter(ext.GPU_DISJOINT_EXT);

if (available && !disjoint) {
  // مشاهده مدت زمان رندر شدن شیء بر حسب نانوثانیه
  const timeElapsed = ext.getQueryObjectEXT(query, ext.QUERY_RESULT_EXT);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLQuery")}}
- {{domxref("EXT_disjoint_timer_query")}}