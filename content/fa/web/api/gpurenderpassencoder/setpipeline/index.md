---
title: "GPURenderPassEncoder: setPipeline() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/GPURenderPassEncoder/setPipeline"

---

---
title: "GPURenderPassEncoder: setPipeline() method"
short-title: setPipeline()
slug: Web/API/GPURenderPassEncoder/setPipeline
page-type: web-api-instance-method
browser-compat: api.GPURenderPassEncoder.setPipeline
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`setPipeline()`** از رابط {{domxref("GPURenderPassEncoder")}}، {{domxref("GPURenderPipeline")}} مورد استفاده برای دستورات بعدی رندر پاس را تنظیم می‌کند.

## Syntax

```js-nolint
setPipeline(pipeline)
```

### Parameters

- `pipeline`
  - : {{domxref("GPURenderPipeline")}} که برای دستورات بعدی رندر پاس استفاده می‌شود.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

### Validation

هنگام فراخوانی **`setPipeline()`** باید معیارهای زیر برآورده شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} ایجاد شده و {{domxref("GPURenderPassEncoder")}} نامعتبر می‌شود:

- اگر {{domxref("GPURenderPipeline")}} در مؤلفه عمقِ depth/stencil attachment بنویسد، باید `depthReadOnly` (همان‌طور که در توصیف‌گر فراخوانی {{domxref("GPUCommandEncoder.beginRenderPass()")}} مشخص شده است) برابر با `true` باشد.
- اگر {{domxref("GPURenderPipeline")}} در مؤلفه stencilِ depth/stencil attachment بنویسد، باید `stencilReadOnly` (همان‌طور که در توصیف‌گر فراخوانی {{domxref("GPUCommandEncoder.beginRenderPass()")}} مشخص شده است) برابر با `true` باشد.

## Examples

در [نمونه رندر پایه](https://mdn.github.io/dom-examples/webgpu-render-demo/) ما، چندین دستور از طریق یک {{domxref("GPUCommandEncoder")}} ثبت می‌شوند. بیشتر این دستورات از `GPURenderPassEncoder` که از طریق {{domxref("GPUCommandEncoder.beginRenderPass()")}} ایجاد شده است، سرچشمه می‌گیرند. `setPipeline()` در جای مناسب برای تنظیم پایپ‌لاین رندر فراخوانی می‌شود.

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

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)