---
title: GPUExternalTexture
slug: Web/API/GPUExternalTexture
page-type: web-api-interface
browser-compat: api.GPUExternalTexture
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`GPUExternalTexture`** از {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} یک شیء wrapper (پوشاننده) را نشان می‌دهد که حاوی یک snapshot (عکس فوری) از {{domxref("HTMLVideoElement")}} است و می‌تواند به عنوان یک بافت (texture) در عملیات رندرینگ GPU استفاده شود.

یک نمونه از شیء `GPUExternalTexture` با استفاده از {{domxref("GPUDevice.importExternalTexture()")}} ایجاد می‌شود.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("GPUExternalTexture.label", "label")}}
  - : یک رشته که برچسبی را فراهم می‌کند که می‌توان از آن برای شناسایی شیء استفاده کرد، برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

## مثال‌ها

در نمونه‌های WebGPU، [نمونه بارگذاری ویدیو](https://webgpu.github.io/webgpu-samples/samples/videoUploading/)، یک شیء `GPUExternalTexture` (که با فراخوانی {{domxref("GPUDevice.importExternalTexture()")}} ایجاد شده است) به عنوان مقدار ورودی `resource` در یک گروه bind (bind group) استفاده می‌شود، که هنگام ایجاد یک {{domxref("GPUBindGroup")}} با فراخوانی {{domxref("GPUDevice.createBindGroup()")}} مشخص می‌شود:

```js
// …
const uniformBindGroup = device.createBindGroup({
  layout: pipeline.getBindGroupLayout(0),
  entries: [
    {
      binding: 1,
      resource: sampler,
    },
    {
      binding: 2,
      resource: device.importExternalTexture({
        source: video,
      }),
    },
  ],
});
// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)