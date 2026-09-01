---
title: "GPUQuerySet: destroy() method"
short-title: destroy()
slug: Web/API/GPUQuerySet/destroy
page-type: web-api-instance-method
browser-compat: api.GPUQuerySet.destroy
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`destroy()`** از رابط {{domxref("GPUQuerySet")}}، شیء `GPUQuerySet` را از بین می‌برد.

## نحو (Syntax)

```js-nolint
destroy()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

```js
const querySet = device.createQuerySet({
  type: "occlusion",
  count: 32,
});

// مدتی بعد

querySet.destroy();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)