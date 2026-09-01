---
title: "GPUTexture: destroy() method"
short-title: destroy()
slug: Web/API/GPUTexture/destroy
page-type: web-api-instance-method
browser-compat: api.GPUTexture.destroy
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`destroy()`** در رابط {{domxref("GPUTexture")}}، شیء `GPUTexture` را از بین می‌برد.

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
// …

const depthTexture = device.createTexture({
  size: [canvas.width, canvas.height],
  format: "depth24plus",
  usage: GPUTextureUsage.RENDER_ATTACHMENT,
});

// مدتی بعد

depthTexture.destroy();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)