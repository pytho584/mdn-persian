---
title: GPURenderPipeline
slug: Web/API/GPURenderPipeline
page-type: web-api-interface
browser-compat: api.GPURenderPipeline
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابطهٔ **`GPURenderPipeline`** در {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} یک پایپلاین را نشان می‌دهد که مراحل شیدر رأس و فرگمنت را کنترل می‌کند و می‌تواند در یک {{domxref("GPURenderPassEncoder")}} یا {{domxref("GPURenderBundleEncoder")}} استفاده شود.

یک نمونه از شیء `GPURenderPipeline` را می‌توان با استفاده از متدهای {{domxref("GPUDevice.createRenderPipeline()")}} یا {{domxref("GPUDevice.createRenderPipelineAsync()")}} ایجاد کرد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("GPURenderPipeline.label", "label")}}
  - : یک رشته که برچسبی برای شناسایی شیء فراهم می‌کند، برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

## روش‌های نمونه

- {{domxref("GPURenderPipeline.getBindGroupLayout", "getBindGroupLayout()")}}
  - : شیء {{domxref("GPUBindGroupLayout")}} پایپلاین را با ایندکس داده‌شده برمی‌گرداند (یعنی آن‌که در چیدمان پایپلاینِ فراخوانیِ {{domxref("GPUDevice.createRenderPipeline()")}} یا {{domxref("GPUDevice.createRenderPipelineAsync()")}} اولیه گنجانده شده است).

## مثال‌ها

> [!NOTE]
> [نمونه‌های WebGPU](https://webgpu.github.io/webgpu-samples/) نمونه‌های بسیار بیشتری را ارائه می‌دهند.

### مثال پایه

[دموی رندر پایه](https://mdn.github.io/dom-examples/webgpu-render-demo/) ما مثالی از ساخت یک شیء توصیف‌گر پایپلاین رندر معتبر ارائه می‌دهد که سپس برای ایجاد یک `GPURenderPipeline` از طریق فراخوانی `createRenderPipeline()` استفاده می‌شود.

```js
// …

const vertexBuffers = [
  {
    attributes: [
      {
        shaderLocation: 0, // position
        offset: 0,
        format: "float32x4",
      },
      {
        shaderLocation: 1, // color
        offset: 16,
        format: "float32x4",
      },
    ],
    arrayStride: 32,
    stepMode: "vertex",
  },
];

const pipelineDescriptor = {
  vertex: {
    module: shaderModule,
    entryPoint: "vertex_main",
    buffers: vertexBuffers,
  },
  fragment: {
    module: shaderModule,
    entryPoint: "fragment_main",
    targets: [
      {
        format: navigator.gpu.getPreferredCanvasFormat(),
      },
    ],
  },
  primitive: {
    topology: "triangle-list",
  },
  layout: "auto",
};

const renderPipeline = device.createRenderPipeline(pipelineDescriptor);

// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)