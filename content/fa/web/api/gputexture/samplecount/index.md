---
title: "GPUTexture: sampleCount property"
---

---
title: "GPUTexture: sampleCount property"
short-title: sampleCount
slug: Web/API/GPUTexture/sampleCount
page-type: web-api-instance-property
browser-compat: api.GPUTexture.sampleCount
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`sampleCount`** در رابط {{domxref("GPUTexture")}}، تعداد نمونه (sample count) آن `GPUTexture` را نشان می‌دهد.

این مقدار از طریق ویژگی `sampleCount` در شیء توصیف‌گر (descriptor) که به فراخوانی متناظر {{domxref("GPUDevice.createTexture()")}} ارسال می‌شود، تنظیم می‌گردد. اگر این ویژگی حذف شود، مقدار پیش‌فرض آن ۱ است.

## مقدار

یک عدد. مقادیر ممکن عبارت‌اند از:

- ۱
- ۴، که نشان‌دهندهٔ یک بافت چندنمونه‌ای (multi-sampled texture) است.

## مثال‌ها

```js
// …

const depthTexture = device.createTexture({
  size: [canvas.width, canvas.height],
  format: "depth24plus",
  usage: GPUTextureUsage.RENDER_ATTACHMENT,
});

console.log(depthTexture.sampleCount); // 1
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)