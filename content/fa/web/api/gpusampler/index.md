---
title: GPUSampler
slug: Web/API/GPUSampler
page-type: web-api-interface
browser-compat: api.GPUSampler
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`GPUSampler`** از {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} شیئی را نشان می‌دهد که می‌تواند نحوه تبدیل و فیلتر کردن داده‌های منابع بافت توسط شیدرها را کنترل کند.

یک نمونه از شیء `GPUSampler` با استفاده از متد {{domxref("GPUDevice.createSampler()")}} ایجاد می‌شود.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("GPUSampler.label", "label")}}
  - : یک رشته که برچسبی برای شناسایی شیء فراهم می‌کند، برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

## مثال‌ها

قطعه کد زیر یک `GPUSampler` ایجاد می‌کند که فیلترینگ سه‌خطی انجام می‌دهد و مختصات بافت را تکرار می‌کند:

```js
// …
const sampler = device.createSampler({
  addressModeU: "repeat",
  addressModeV: "repeat",
  magFilter: "linear",
  minFilter: "linear",
  mipmapFilter: "linear",
});
```

نمونه‌های WebGPU [نمونه نگاشت سایه](https://webgpu.github.io/webgpu-samples/samples/shadowMapping/) از نمونه‌بردارهای مقایسه‌ای برای نمونه‌برداری از یک بافت عمق جهت رندر سایه‌ها استفاده می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)