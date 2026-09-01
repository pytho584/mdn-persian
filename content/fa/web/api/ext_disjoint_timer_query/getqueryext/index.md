---
title: "EXT_disjoint_timer_query: getQueryEXT() method"
short-title: getQueryEXT()
slug: Web/API/EXT_disjoint_timer_query/getQueryEXT
page-type: webgl-extension-method
browser-compat: api.EXT_disjoint_timer_query.getQueryEXT
---

{{APIRef("WebGL")}}

متد **`EXT_disjoint_timer_query.getQueryEXT()`** از
[WebGL API](/en-US/docs/Web/API/WebGL_API) اطلاعاتی را دربارهٔ یک هدف پرس‌وجو بازمی‌گرداند.

## Syntax

```js-nolint
getQueryEXT(target, pname)
```

### Parameters

- `target`
  - : یک {{domxref("WebGL_API/Types", "GLenum")}} که هدف پرس‌وجوی زمان را مشخص می‌کند. باید
    `ext.TIMESTAMP_EXT` یا `ext.TIME_ELAPSED_EXT` باشد.
- `pname`
  - : یک {{domxref("WebGL_API/Types", "GLenum")}} که مشخص می‌کند کدام اطلاعات بازگردانده شود. باید
    `ext.CURRENT_QUERY_EXT` یا `ext.QUERY_COUNTER_BITS_EXT` باشد.

### Return value

مقدار بازگشتی به `pname` بستگی دارد:

- اگر `pname` برابر با `ext.CURRENT_QUERY_EXT` باشد: یک
  شیء {{domxref("WebGLQuery")}} که پرس‌وجوی فعال فعلی برای
  هدف داده‌شده است.
- اگر `pname` برابر با `ext.QUERY_COUNTER_BITS_EXT` باشد: یک
  {{domxref("WebGL_API/Types", "GLint")}} که تعداد بیت‌های استفاده‌شده برای نگهداری نتیجهٔ پرس‌وجو برای
  هدف داده‌شده را نشان می‌دهد.

## Examples

```js
const ext = gl.getExtension("EXT_disjoint_timer_query");
const startQuery = ext.createQueryEXT();
ext.queryCounterEXT(startQuery, ext.TIMESTAMP_EXT);

const currentQuery = ext.getQueryEXT(ext.TIMESTAMP_EXT, ext.CURRENT_QUERY_EXT);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGLQuery")}}
- {{domxref("EXT_disjoint_timer_query")}}