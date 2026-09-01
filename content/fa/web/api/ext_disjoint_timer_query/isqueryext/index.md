```
---
title: "EXT_disjoint_timer_query: isQueryEXT() method"
---

---
title: "EXT_disjoint_timer_query: isQueryEXT() method"
short-title: isQueryEXT()
slug: Web/API/EXT_disjoint_timer_query/isQueryEXT
page-type: webgl-extension-method
browser-compat: api.EXT_disjoint_timer_query.isQueryEXT
---

{{APIRef("WebGL")}}

متد **`EXT_disjoint_timer_query.isQueryEXT()`** از
[WebGL API](/en-US/docs/Web/API/WebGL_API)، اگر شیءِ داده‌شده یک شیء {{domxref("WebGLQuery")}} باشد، مقدار `true` را برمی‌گرداند.

## نحو

```js-nolint
isQueryEXT(query)
```

### پارامترها

- `query`
  - : یک شیء {{domxref("WebGLQuery")}} برای آزمایش.

### مقدار بازگشتی

یک {{domxref("WebGL_API/Types", "GLboolean")}} که نشان می‌دهد آیا شیءِ داده‌شده یک
شیء {{domxref("WebGLQuery")}} است (`true`) یا
نه (`false`).

## مثال‌ها

```js
const ext = gl.getExtension("EXT_disjoint_timer_query");
const query = ext.createQueryEXT();

// …

ext.isQueryEXT(query);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLQuery")}}
- {{domxref("EXT_disjoint_timer_query")}}
```