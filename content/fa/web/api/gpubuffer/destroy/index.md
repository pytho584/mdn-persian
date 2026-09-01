---
title: "GPUBuffer: destroy() method"
---

---
title: "GPUBuffer: destroy() method"
short-title: destroy()
slug: Web/API/GPUBuffer/destroy
page-type: web-api-instance-method
browser-compat: api.GPUBuffer.destroy
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`destroy()`** از رابط {{domxref("GPUBuffer")}}، شیء `GPUBuffer` را از بین می‌برد.

## نحو

```js-nolint
destroy()
```

### پارامترها

هیچ پارامتری.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
const output = device.createBuffer({
  size: 1000,
  usage: GPUBufferUsage.STORAGE | GPUBufferUsage.COPY_SRC,
});

// some time later

output.destroy();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)