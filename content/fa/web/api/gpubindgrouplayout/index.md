---
title: GPUBindGroupLayout
slug: Web/API/GPUBindGroupLayout
page-type: web-api-interface
browser-compat: api.GPUBindGroupLayout
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`GPUBindGroupLayout`** در {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} ساختار و هدف منابع مرتبط با GPU مانند بافرهایی که در یک پایپلاین استفاده می‌شوند را تعریف می‌کند و به عنوان یک الگو برای ایجاد {{domxref("GPUBindGroup")}}ها به کار می‌رود.

یک نمونه از شیء `GPUBindGroupLayout` با استفاده از متد {{domxref("GPUDevice.createBindGroupLayout()")}} ایجاد می‌شود.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("GPUBindGroupLayout.label", "label")}}
  - : یک رشته که برچسبی برای شناسایی شیء فراهم می‌کند، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

## مثال‌ها

> [!NOTE]
> [نمونه‌های WebGPU](https://webgpu.github.io/webgpu-samples/) شامل مثال‌های بسیار بیشتری هستند.

### مثال پایه

[نمونه محاسبات پایه](https://mdn.github.io/dom-examples/webgpu-compute-demo/) ما نحوه ایجاد یک طرح بایند گروه و سپس استفاده از آن به عنوان الگو برای ایجاد یک بایند گروه را نشان می‌دهد.

```js
// …

const bindGroupLayout = device.createBindGroupLayout({
  entries: [
    {
      binding: 0,
      visibility: GPUShaderStage.COMPUTE,
      buffer: {
        type: "storage",
      },
    },
  ],
});

const bindGroup = device.createBindGroup({
  layout: bindGroupLayout,
  entries: [
    {
      binding: 0,
      resource: {
        buffer: output,
      },
    },
  ],
});

// …
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)