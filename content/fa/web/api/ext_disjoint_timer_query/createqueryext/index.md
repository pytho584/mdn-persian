---
title: "EXT_disjoint_timer_query: createQueryEXT() method"
short-title: createQueryEXT()
slug: Web/API/EXT_disjoint_timer_query/createQueryEXT
page-type: webgl-extension-method
browser-compat: api.EXT_disjoint_timer_query.createQueryEXT
---

{{APIRef("WebGL")}}

متد **`EXT_disjoint_timer_query.createQueryEXT()`** از [WebGL API](/en-US/docs/Web/API/WebGL_API) اشیاء {{domxref("WebGLQuery")}} را ساخته و مقداردهی اولیه می‌کند. این اشیاء زمان لازم برای تکمیل کامل مجموعه‌ای از دستورات GL را پیگیری می‌کنند.

## سینتکس

```js-nolint
createQueryEXT()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک شیء {{domxref("WebGLQuery")}}.

## مثال‌ها

```js
const ext = gl.getExtension("EXT_disjoint_timer_query");
const query = ext.createQueryExt();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLQuery")}}
- {{domxref("EXT_disjoint_timer_query")}}