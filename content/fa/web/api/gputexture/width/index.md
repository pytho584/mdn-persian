---
title: "GPUTexture: width property"
short-title: width
slug: Web/API/GPUTexture/width
page-type: web-api-instance-property
browser-compat: api.GPUTexture.width
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقطخواندنی **`width`** در رابط {{domxref("GPUTexture")}} نشان‌دهندهٔ عرض آن `GPUTexture` است.

این مقدار بر اساس مقدار ویژگی `size` در شیء توصیفگر (descriptor) که به فراخوانی {{domxref("GPUDevice.createTexture()")}} مبدأ ارسال شده است، تنظیم می‌شود.

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

console.log(depthTexture.width); // 640
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)