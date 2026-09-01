---
title: GPUComputePipeline
slug: Web/API/GPUComputePipeline
page-type: web-api-interface
browser-compat: api.GPUComputePipeline
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`GPUComputePipeline`** از {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} یک pipeline را نشان می‌دهد که مرحله سایه‌زن محاسبه (compute shader) را کنترل می‌کند و می‌تواند در یک {{domxref("GPUComputePassEncoder")}} استفاده شود.

یک نمونه از شیء `GPUComputePipeline` را می‌توان با استفاده از متدهای {{domxref("GPUDevice.createComputePipeline()")}} یا {{domxref("GPUDevice.createComputePipelineAsync()")}} ایجاد کرد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("GPUComputePipeline.label", "label")}}
  - : یک رشته که یک برچسب (label) را ارائه می‌دهد که می‌تواند برای شناسایی شیء استفاده شود، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

## روش‌های نمونه

- {{domxref("GPUComputePipeline.getBindGroupLayout", "getBindGroupLayout()")}}
  - : شیء {{domxref("GPUBindGroupLayout")}} pipeline را با ایندکس داده شده برمی‌گرداند (یعنی ایندکسی که در طرح‌بندی (layout) pipeline اصلی در فراخوانی {{domxref("GPUDevice.createComputePipeline()")}} یا {{domxref("GPUDevice.createComputePipelineAsync()")}} گنجانده شده است).

## مثال‌ها

> [!NOTE] نمونه‌های [WebGPU samples](https://webgpu.github.io/webgpu-samples/) شامل مثال‌های بسیار بیشتری هستند.

### مثال پایه

دموی [محاسبه پایه](https://mdn.github.io/dom-examples/webgpu-compute-demo/) ما فرآیندی را نشان می‌دهد که شامل:

- ایجاد یک طرح‌بندی گروه اتصال (bind group layout) با {{domxref("GPUDevice.createBindGroupLayout()")}}.
- وارد کردن `bindGroupLayout` به {{domxref("GPUDevice.createPipelineLayout()")}} برای ایجاد یک {{domxref("GPUPipelineLayout")}}.
- استفاده مستقیم از آن مقدار در یک فراخوانی `createComputePipeline()` برای ایجاد یک `GPUComputePipeline`.

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

const computePipeline = device.createComputePipeline({
  layout: device.createPipelineLayout({
    bindGroupLayouts: [bindGroupLayout],
  }),
  compute: {
    module: shaderModule,
    entryPoint: "main",
  },
});

// …
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)