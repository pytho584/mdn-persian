---
title: "GPURenderPipeline: label property"
short-title: label
slug: Web/API/GPURenderPipeline/label
page-type: web-api-instance-property
browser-compat: api.GPURenderPipeline.label
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

خاصیت **`label`** از رابط {{domxref("GPURenderPipeline")}} یک برچسب (label) فراهم می‌کند که می‌توان از آن برای شناسایی شیء استفاده کرد، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

این مقدار می‌تواند با ارائه یک خاصیت `label` در شیء توصیف‌گر (descriptor) که به فراخوانی {{domxref("GPUDevice.createRenderPipeline()")}} یا {{domxref("GPUDevice.createRenderPipelineAsync()")}} اصلی ارسال می‌شود، تنظیم گردد، یا می‌توانید آن را مستقیماً روی شیء `GPURenderPipeline` دریافت و تنظیم کنید.

## Value

یک رشته. اگر این مقدار قبلاً به‌صورت فوق تنظیم نشده باشد، یک رشته خالی خواهد بود.

## Examples

تنظیم و دریافت یک برچسب از طریق `GPURenderPipeline.label`:

```js
// …

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

renderPipeline.label = "my_render_pipeline";

console.log(renderPipeline.label); // "my_render_pipeline"
```

تنظیم یک برچسب از طریق فراخوانی {{domxref("GPUDevice.createRenderPipeline()")}} و سپس دریافت آن از طریق `GPURenderPipeline.label`:

```js
// …

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
  label: "my_render_pipeline",
};

const renderPipeline = device.createRenderPipeline(pipelineDescriptor);

console.log(renderPipeline.label); // "my_render_pipeline"
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [The WebGPU API](/en-US/docs/Web/API/WebGPU_API)