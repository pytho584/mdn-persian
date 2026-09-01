---
title: "EXT_disjoint_timer_query: queryCounterEXT() method"
short-title: queryCounterEXT()
slug: Web/API/EXT_disjoint_timer_query/queryCounterEXT
page-type: webgl-extension-method
browser-compat: api.EXT_disjoint_timer_query.queryCounterEXT
---

{{APIRef("WebGL")}}

متد **`EXT_disjoint_timer_query.queryCounterEXT()`** در
[WebGL API](/en-US/docs/Web/API/WebGL_API) زمان فعلی را در
شیء پرس‌وجوی متناظر ثبت می‌کند.

## نحو (Syntax)

```js-nolint
queryCounterEXT(query, target)
```

### پارامترها

- `query`
  - : یک شیء {{domxref("WebGLQuery")}} که زمان فعلی برای آن ثبت می‌شود.
- `target`
  - : یک {{domxref("WebGL_API/Types", "GLenum")}} که هدف پرس‌وجوی زمان را مشخص می‌کند. باید
    `ext.TIMESTAMP_EXT` باشد.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
const ext = gl.getExtension("EXT_disjoint_timer_query");
const startQuery = ext.createQueryEXT();
const endQuery = ext.createQueryEXT();
ext.queryCounterEXT(startQuery, ext.TIMESTAMP_EXT);

// …

ext.queryCounterEXT(endQuery, ext.TIMESTAMP_EXT);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLQuery")}}
- {{domxref("EXT_disjoint_timer_query")}}