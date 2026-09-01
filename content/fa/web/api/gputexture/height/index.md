---
title: "GPUTexture: height property"
short-title: height
slug: Web/API/GPUTexture/height
page-type: web-api-instance-property
browser-compat: api.GPUTexture.height
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

خاصیت فقط‑خواندنی **`height`** از رابط {{domxref("GPUTexture")}}، ارتفاع `GPUTexture` را نشان می‌دهد.

این مقدار بر اساس مقدار ویژگی `size` در شیء توصیف‌کننده‌ای که به فراخوانی {{domxref("GPUDevice.createTexture()")}} مبدأ داده شده است، تعیین می‌شود.

## مقدار

یک عدد.

## مثال‌ها

```js
// …

const depthTexture = device.createTexture({
  size: [640, 480],
  format: "depth24plus",
  usage: GPUTextureUsage.RENDER_ATTACHMENT,
});

console.log(depthTexture.height); // 480
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)