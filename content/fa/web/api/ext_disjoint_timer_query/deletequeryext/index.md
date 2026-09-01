---
title: "EXT_disjoint_timer_query: deleteQueryEXT() method"
short-title: deleteQueryEXT()
slug: Web/API/EXT_disjoint_timer_query/deleteQueryEXT
page-type: webgl-extension-method
browser-compat: api.EXT_disjoint_timer_query.deleteQueryEXT
---

{{APIRef("WebGL")}}

متد **`EXT_disjoint_timer_query.deleteQueryEXT()`** در [WebGL API](/en-US/docs/Web/API/WebGL_API)، یک شیء {{domxref("WebGLQuery")}} مشخص را حذف می‌کند.

## Syntax

```js-nolint
deleteQueryEXT(query)
```

### پارامترها

- `query`
  - : یک شیء {{domxref("WebGLQuery")}} که باید حذف شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
const ext = gl.getExtension("EXT_disjoint_timer_query");
const query = ext.createQueryEXT();

// …

ext.deleteQueryEXT(query);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLQuery")}}
- {{domxref("EXT_disjoint_timer_query")}}