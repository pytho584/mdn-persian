---
title: "GPURenderPipeline: getBindGroupLayout() method"
short-title: getBindGroupLayout()
slug: Web/API/GPURenderPipeline/getBindGroupLayout
page-type: web-api-instance-method
browser-compat: api.GPURenderPipeline.getBindGroupLayout
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`getBindGroupLayout()`** از رابط {{domxref("GPURenderPipeline")}}، شیء {{domxref("GPUBindGroupLayout")}} خط لوله را با اندیس داده‌شده برمی‌گرداند (یعنی اندیسی که در طرح خط لولهٔ فراخوانی {{domxref("GPUDevice.createRenderPipeline()")}} یا {{domxref("GPUDevice.createRenderPipelineAsync()")}} مبدأ قرار گرفته است).

اگر {{domxref("GPURenderPipeline")}} با `layout: "auto"` ساخته شده باشد، این متد تنها راه بازیابی {{domxref("GPUBindGroupLayout")}}های تولیدشده توسط خط لوله است.

## سینتکس

```js-nolint
getBindGroupLayout(index)
```

### پارامترها

- `index`
  - : عددی که اندیس {{domxref("GPUBindGroupLayout")}} مورد نظر برای بازگرداندن را نشان می‌دهد.

### مقدار بازگشتی

یک نمونه شیء {{domxref("GPUBindGroupLayout")}}.

### اعتبارسنجی

هنگام فراخوانی **`getBindGroupLayout()`** معیارهای زیر باید برقرار باشند؛ در غیر این صورت یک {{domxref("GPUValidationError")}} ایجاد می‌شود و یک شیء {{domxref("GPUBindGroupLayout")}} نامعتبر بازگردانده می‌شود:

- `index` کمتر از تعداد اشیاء {{domxref("GPUBindGroupLayout")}} استفاده‌شده در طرح خط لوله باشد.

## مثال‌ها

> [!NOTE]
> می‌توانید نمونه‌های کاملی را که در آن‌ها از `getBindGroupLayout()` استفاده شده است، در [نمونه‌های WebGPU](https://webgpu.github.io/webgpu-samples/) ببینید.

```js
// …

// Create a render pipeline using layout: "auto" to automatically generate
// appropriate bind group layouts
const fullscreenQuadPipeline = device.createRenderPipeline({
  layout: "auto",
  vertex: {
    module: device.createShaderModule({
      code: fullscreenTexturedQuadWGSL,
    }),
    entryPoint: "vert_main",
  },
  fragment: {
    module: device.createShaderModule({
      code: fullscreenTexturedQuadWGSL,
    }),
    entryPoint: "frag_main",
    targets: [
      {
        format: presentationFormat,
      },
    ],
  },
  primitive: {
    topology: "triangle-list",
  },
});

// …

// Create a bind group with the auto-generated layout from the render pipeline
const showResultBindGroup = device.createBindGroup({
  layout: fullscreenQuadPipeline.getBindGroupLayout(0),
  entries: [
    {
      binding: 0,
      resource: sampler,
    },
    {
      binding: 1,
      resource: textures[1].createView(),
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