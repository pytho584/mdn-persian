---
title: "EXT_disjoint_timer_query: endQueryEXT() method"
---

---
title: "EXT_disjoint_timer_query: endQueryEXT() method"
short-title: endQueryEXT()
slug: Web/API/EXT_disjoint_timer_query/endQueryEXT
page-type: webgl-extension-method
browser-compat: api.EXT_disjoint_timer_query.endQueryEXT
---

{{APIRef("WebGL")}}

متد **`EXT_disjoint_timer_query.endQueryEXT()`** در [WebGL API](/en-US/docs/Web/API/WebGL_API) یک پرس‌وجوی زمان‌سنج را پایان می‌دهد.

## Syntax

```js-nolint
endQueryEXT(target)
```

### Parameters

- `target`
  - : یک {{domxref("WebGL_API/Types", "GLenum")}} که هدف پرس‌وجوی زمان را مشخص می‌کند. باید `ext.TIME_ELAPSED_EXT` باشد.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

## Examples

```js
const ext = gl.getExtension("EXT_disjoint_timer_query");
const query = ext.createQueryEXT();
ext.beginQueryEXT(ext.TIME_ELAPSED_EXT, query);

// …

ext.endQueryEXT(ext.TIME_ELAPSED_EXT);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLQuery")}}
- {{domxref("EXT_disjoint_timer_query")}}