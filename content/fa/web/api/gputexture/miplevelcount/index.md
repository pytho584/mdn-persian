---
title: "GPUTexture: mipLevelCount property"
short-title: mipLevelCount
slug: Web/API/GPUTexture/mipLevelCount
page-type: web-api-instance-property
browser-compat: api.GPUTexture.mipLevelCount
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‑خواندنی **`mipLevelCount`** از رابط {{domxref("GPUTexture")}} تعداد سطوح mip (`mip level`) را در `GPUTexture` نشان می‌دهد.

این مقدار از طریق ویژگی `mipLevelCount` در شیء توصیف‌کننده‌ای که به فراخوانی {{domxref("GPUDevice.createTexture()")}} اصلی داده می‌شود تنظیم می‌گردد. در صورت حذف، مقدار پیش‌فرض آن `1` است.

## مقدار

یک عدد.

## مثال‌ها

```js
// …
const depthTexture = device.createTexture({
  size: [canvas.width, canvas.height],
  format: "depth24plus",
  usage: GPUTextureUsage.RENDER_ATTACHMENT,
});

console.log(depthTexture.mipLevelCount); // 1
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)