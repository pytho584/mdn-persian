---
title: "EXT_disjoint_timer_query: beginQueryEXT() method"
short-title: beginQueryEXT()
slug: Web/API/EXT_disjoint_timer_query/beginQueryEXT
page-type: webgl-extension-method
browser-compat: api.EXT_disjoint_timer_query.beginQueryEXT
---

{{APIRef("WebGL")}}

متد **`EXT_disjoint_timer_query.beginQueryEXT()`** از [WebGL API](/en-US/docs/Web/API/WebGL_API) یک پرس‌وجوی زمان‌سنجی را آغاز می‌کند.

## Syntax

```js-nolint
beginQueryEXT(target, query)
```

### Parameters

- `target`
  - : یک {{domxref("WebGL_API/Types", "GLenum")}} که هدف پرس‌وجوی زمان را مشخص می‌کند. باید برابر با `ext.TIME_ELAPSED_EXT` باشد.
- `query`
  - : یک شیء {{domxref("WebGLQuery")}} که پرس‌وجوی زمان برای آن شروع می‌شود.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

## Examples

```js
const ext = gl.getExtension("EXT_disjoint_timer_query");
const query = ext.createQueryEXT();
ext.beginQueryEXT(ext.TIME_ELAPSED_EXT, query);

// …
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLQuery")}}
- {{domxref("EXT_disjoint_timer_query")}}