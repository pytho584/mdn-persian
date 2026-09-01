---
title: GPUTextureView
slug: Web/API/GPUTextureView
page-type: web-api-interface
browser-compat: api.GPUTextureView
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`GPUTextureView`** از {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} نمایانگر یک View (نمای) درون زیرمجموعه‌ای از منابع بافت (texture) است که توسط یک {{domxref("GPUTexture")}} خاص تعریف شده‌اند.

یک نمونه از شیء `GPUTextureView` با استفاده از متد {{domxref("GPUTexture.createView()")}} ساخته می‌شود.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("GPUTextureView.label", "label")}}
  - : یک رشته که برچسبی را ارائه می‌دهد که می‌تواند برای شناسایی شیء استفاده شود، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

## مثال‌ها

در [نمونه Cubemap](https://webgpu.github.io/webgpu-samples/samples/cubemap/) از WebGPU Samples، نمونه‌های متعددی از نحوه استفاده از `GPUTextureView` ها (که با فراخوانی‌های {{domxref("GPUTexture.createView()")}} ساخته شده‌اند) را مشاهده خواهید کرد، هم به عنوان `resource` در یک فراخوانی {{domxref("GPUDevice.createBindGroup()")}} و هم به عنوان `view` ارائه‌شده در شیء `depthStencilAttachment` یک توصیف‌گر {{domxref("GPUCommandEncoder.beginRenderPass()")}}.

```js
const uniformBindGroup = device.createBindGroup({
  layout: pipeline.getBindGroupLayout(0),
  entries: [
    {
      binding: 0,
      resource: {
        buffer: uniformBuffer,
        offset: 0,
        size: uniformBufferSize,
      },
    },
    {
      binding: 1,
      resource: sampler,
    },
    {
      binding: 2,
      resource: cubemapTexture.createView({
        dimension: "cube",
      }),
    },
  ],
});

const renderPassDescriptor: GPURenderPassDescriptor = {
  colorAttachments: [
    {
      view: undefined, // Assigned later
      loadOp: "clear",
      storeOp: "store",
    },
  ],
  depthStencilAttachment: {
    view: depthTexture.createView(),
    depthClearValue: 1.0,
    depthLoadOp: "clear",
    depthStoreOp: "store",
  },
};

// …

const commandEncoder = device.createCommandEncoder();
const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);

// …
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)