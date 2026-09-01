---
title: "GPURenderPassEncoder: end() method"
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`end()`** از رابط {{domxref("GPURenderPassEncoder")}}، ضبط دنباله دستورات رندر پاس جاری را کامل می‌کند.

## Syntax

```js-nolint
end()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### اعتبارسنجی

معیارهای زیر باید هنگام فراخوانی **`end()`** رعایت شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و {{domxref("GPURenderPassEncoder")}} نامعتبر می‌شود:

- {{domxref("GPURenderPassEncoder")}} باز است (یعنی قبلاً با یک فراخوانی `end()` پایان نیافته است).
- هیچ پرس‌وجوی انسداد (occlusion query) فعالی (یعنی با {{domxref("GPURenderPassEncoder.beginOcclusionQuery", "beginOcclusionQuery()")}} شروع شده باشد) روی رندر پاس جاری وجود نداشته باشد.
- پشته اشکال‌زدایی (debug stack) برای رندر پاس جاری خالی است (یعنی هیچ گروه اشکال‌زدایی رندر پاسی در حال حاضر باز نیست، مانند آنچه توسط {{domxref("GPURenderPassEncoder.pushDebugGroup", "pushDebugGroup()")}} باز می‌شود).
- تعداد دستورات رسم (draw commands) کدگذاری شده در این رندر پاس، کمتر یا برابر با ویژگی `maxDrawCount` تعیین شده در توصیف‌گر {{domxref("GPUCommandEncoder.beginRenderPass()")}} باشد.

## مثال‌ها

در [نمایش پایه رندر](https://mdn.github.io/dom-examples/webgpu-render-demo/) ما، چندین دستور از طریق یک {{domxref("GPUCommandEncoder")}} ضبط می‌شوند. بیشتر این دستورات از `GPURenderPassEncoder` ایجاد شده از طریق {{domxref("GPUCommandEncoder.beginRenderPass()")}} سرچشمه می‌گیرند. `end()` در مکان مناسبی برای پایان دادن به رندر پاس فراخوانی می‌شود.

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

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)