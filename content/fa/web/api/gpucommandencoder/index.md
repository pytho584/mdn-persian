---
title: GPUCommandEncoder
slug: Web/API/GPUCommandEncoder
page-type: web-api-interface
browser-compat: api.GPUCommandEncoder
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`GPUCommandEncoder`** از {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} نمایانگر یک رمزگذار (encoder) است که دنبالهای از دستورات GPU را برای ارسال به GPU جمعآوری میکند.

یک نمونه از شیء `GPUCommandEncoder` از طریق ویژگی {{domxref("GPUDevice.createCommandEncoder()")}} ساخته میشود.

{{InheritanceDiagram}}

## ویژگیهای نمونه

- {{domxref("GPUCommandEncoder.label", "label")}}
  - : رشته‌ای که برچسبی برای شناسایی شیء فراهم می‌کند، برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

## متدهای نمونه

- {{domxref("GPUCommandEncoder.beginComputePass", "beginComputePass()")}}
  - : شروع به رمزگذاری یک پاس محاسباتی می‌کند و یک {{domxref("GPUComputePassEncoder")}} برمی‌گرداند که می‌تواند برای کنترل محاسبات استفاده شود.
- {{domxref("GPUCommandEncoder.beginRenderPass", "beginRenderPass()")}}
  - : شروع به رمزگذاری یک پاس رندر می‌کند و یک {{domxref("GPURenderPassEncoder")}} برمی‌گرداند که می‌تواند برای کنترل رندر استفاده شود.
- {{domxref("GPUCommandEncoder.clearBuffer", "clearBuffer()")}}
  - : دستوری را رمزگذاری می‌کند که ناحیه‌ای از یک {{domxref("GPUBuffer")}} را با صفر پر می‌کند.
- {{domxref("GPUCommandEncoder.copyBufferToBuffer", "copyBufferToBuffer()")}}
  - : دستوری را رمزگذاری می‌کند که داده‌ها را از یک {{domxref("GPUBuffer")}} به دیگری کپی می‌کند.
- {{domxref("GPUCommandEncoder.copyBufferToTexture", "copyBufferToTexture()")}}
  - : دستوری را رمزگذاری می‌کند که داده‌ها را از یک {{domxref("GPUBuffer")}} به یک {{domxref("GPUTexture")}} کپی می‌کند.
- {{domxref("GPUCommandEncoder.copyTextureToBuffer", "copyTextureToBuffer()")}}
  - : دستوری را رمزگذاری می‌کند که داده‌ها را از یک {{domxref("GPUTexture")}} به یک {{domxref("GPUBuffer")}} کپی می‌کند.
- {{domxref("GPUCommandEncoder.copyTextureToTexture", "copyTextureToTexture()")}}
  - : دستوری را رمزگذاری می‌کند که داده‌ها را از یک {{domxref("GPUTexture")}} به دیگری کپی می‌کند.
- {{domxref("GPUCommandEncoder.finish", "finish()")}}
  - : ضبط توالی دستورات رمزگذاری‌شده روی این `GPUCommandEncoder` را کامل می‌کند و یک {{domxref("GPUCommandBuffer")}} متناظر برمی‌گرداند.
- {{domxref("GPUCommandEncoder.insertDebugMarker", "insertDebugMarker()")}}
  - : نقطه‌ای خاص در یک سری از دستورات رمزگذاری‌شده را با یک برچسب علامت‌گذاری می‌کند.
- {{domxref("GPUCommandEncoder.popDebugGroup", "popDebugGroup()")}}
  - : یک گروه اشکال‌زدایی را پایان می‌دهد که با فراخوانی {{domxref("GPUCommandEncoder.pushDebugGroup", "pushDebugGroup()")}} آغاز شده است.
- {{domxref("GPUCommandEncoder.pushDebugGroup", "pushDebugGroup()")}}
  - : یک گروه اشکال‌زدایی را آغاز می‌کند که با برچسب مشخصی علامت‌گذاری می‌شود و تمام دستورات رمزگذاری‌شده بعدی را تا زمانی که متد {{domxref("GPUCommandEncoder.popDebugGroup", "popDebugGroup()")}} فراخوانی شود، در بر می‌گیرد.
- {{domxref("GPUCommandEncoder.resolveQuerySet", "resolveQuerySet()")}}
  - : دستوری را رمزگذاری می‌کند که یک {{domxref("GPUQuerySet")}} را حل می‌کند و نتایج را در یک {{domxref("GPUBuffer")}} مشخص کپی می‌کند.
- {{domxref("GPUCommandEncoder.writeTimestamp", "writeTimestamp()")}} {{non-standard_inline}} {{deprecated_inline}}
  - : دستوری را رمزگذاری می‌کند که یک برچسب زمانی را در یک {{domxref("GPUQuerySet")}} می‌نویسد، به شرطی که دستورات قبلی ضبط‌شده در همان {{domxref("GPUCommandBuffer")}} در صف توسط GPU اجرا شده باشند.

## مثال‌ها

در [نمایش رندر پایه](https://mdn.github.io/dom-examples/webgpu-render-demo/) ما، چندین دستور از طریق یک `GPUCommandEncoder` ضبط می‌شوند:

```js
// …

// Create GPUCommandEncoder
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

// Draw a triangle

passEncoder.setPipeline(renderPipeline);
passEncoder.setVertexBuffer(0, vertexBuffer);
passEncoder.draw(3);

// End the render pass

passEncoder.end();

// …
```

دستورات رمزگذاری‌شده توسط `GPUCommandEncoder` با استفاده از متد {{domxref("GPUCommandEncoder.finish()")}} در یک {{domxref("GPUCommandBuffer")}} ضبط می‌شوند. سپس بافر فرمان از طریق یک فراخوانی {{domxref("GPUQueue.submit", "submit()")}} به صف ارسال می‌شود و آماده پردازش توسط GPU است.

```js
device.queue.submit([commandEncoder.finish()]);
```

> [!NOTE]
> برای یافتن مثال‌های بیشتر از رمزگذاری دستورات، [نمونه‌های WebGPU](https://webgpu.github.io/webgpu-samples/) را مطالعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)