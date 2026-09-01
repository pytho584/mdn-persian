---
title: "GPURenderPassEncoder: draw() method"
short-title: draw()
slug: Web/API/GPURenderPassEncoder/draw
page-type: web-api-instance-method
browser-compat: api.GPURenderPassEncoder.draw
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`draw()`** در رابط {{domxref("GPURenderPassEncoder")}}، primitivesها را بر اساس بافرهای رأس (vertex buffers) که توسط {{domxref("GPURenderPassEncoder.setVertexBuffer", "setVertexBuffer()")}} فراهم شده‌اند، ترسیم می‌کند.

## نحو

```js-nolint
draw(vertexCount)
draw(vertexCount, instanceCount)
draw(vertexCount, instanceCount, firstVertex)
draw(vertexCount, instanceCount, firstVertex, firstInstance)
```

### پارامترها

- `vertexCount`
  - : عددی است که تعداد رأس‌هایی را که باید ترسیم شوند، مشخص می‌کند.
- `instanceCount` {{optional_inline}}
  - : عددی است که تعداد نمونه‌ها (instances) را که باید ترسیم شوند، مشخص می‌کند. اگر حذف شود، `instanceCount` به‌صورت پیش‌فرض برابر 1 است.
- `firstVertex` {{optional_inline}}
  - : عددی که افست (offset) در بافرهای رأس، بر حسب رأس، را برای شروع ترسیم مشخص می‌کند. اگر حذف شود، `firstVertex` به‌صورت پیش‌فرض برابر 0 است.
- `firstInstance` {{optional_inline}}
  - : عددی که اولین نمونه‌ای (instance) را که باید ترسیم شود، مشخص می‌کند. اگر حذف شود، `firstInstance` به‌صورت پیش‌فرض برابر 0 است.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

در [نمایش رندر پایه](https://mdn.github.io/dom-examples/webgpu-render-demo/) ما، چندین دستور از طریق یک {{domxref("GPUCommandEncoder")}} ثبت می‌شوند. بیشتر این دستورها از `GPURenderPassEncoder` که توسط {{domxref("GPUCommandEncoder.beginRenderPass()")}} ساخته شده، منشأ می‌گیرند. از `draw()` برای مشخص کردن اینکه سه رأس برای ایجاد مثلث ما ترسیم شوند استفاده می‌شود.

```js
// …

const renderPipeline = device.createRenderPipeline(pipelineDescriptor);

// Create GPUCommandEncoder to issue commands to the GPU
// Note: render pass descriptor, command encoder, etc. are destroyed after use, fresh one needed for each frame.
const commandEncoder = device.createCommandEncoder();

// Create GPURenderPassDescriptor to tell WebGPU which texture to draw into, then initiate render pass
const renderPassDescriptor = {
  colorAttachments: [
    {
      clearValue: clearColor,
      loadOp: "clear",
      storeOp: "store",
      view: context.getCurrentTexture().createView(),
    },
  ],
};

const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);

// Draw the triangle
passEncoder.setPipeline(renderPipeline);
passEncoder.setVertexBuffer(0, vertexBuffer);
passEncoder.draw(3);

// End the render pass
passEncoder.end();

// End frame by passing array of command buffers to command queue for execution
device.queue.submit([commandEncoder.finish()]);

// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)