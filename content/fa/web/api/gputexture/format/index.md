---
title: "GPUTexture: format property"
short-title: format
slug: Web/API/GPUTexture/format
page-type: web-api-instance-property
browser-compat: api.GPUTexture.format
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

خاصیت فقط‑خواندنی **`format`** از رابط {{domxref("GPUTexture")}}، فرمت `GPUTexture` را نمایش می‌دهد.

این مقدار از طریق خاصیت `format` در شیء توصیف‌کننده‌ای که به فراخوانی اصلی {{domxref("GPUDevice.createTexture()")}} داده می‌شود، تنظیم می‌گردد.

## مقدار

یک مقدار شمارشی (enumerated value). برای مشاهده تمام مقادیر ممکن، به بخش [Texture formats](https://gpuweb.github.io/gpuweb/#enumdef-gputextureformat) در مشخصات فنی مراجعه کنید. همچنین به [فرمت‌های بافت ردیف ۱ و ردیف ۲](/en-US/docs/Web/API/GPUDevice/createTexture#tier_1_and_tier_2_texture_formats) مراجعه نمایید.

## مثال‌ها

```js
// …

const depthTexture = device.createTexture({
  size: [canvas.width, canvas.height],
  format: "depth24plus",
  usage: GPUTextureUsage.RENDER_ATTACHMENT,
});

console.log(depthTexture.format); // "depth24plus"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)