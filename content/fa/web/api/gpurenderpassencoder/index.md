---
title: GPURenderPassEncoder
slug: Web/API/GPURenderPassEncoder
page-type: web-api-interface
browser-compat: api.GPURenderPassEncoder
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`GPURenderPassEncoder`** از {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} دستورات مربوط به کنترل مراحل شیدر رأس و شیدر قطعه را که توسط {{domxref("GPURenderPipeline")}} صادر می‌شوند، رمزگذاری می‌کند. این بخشی از فعالیت کلی رمزگذاری یک {{domxref("GPUCommandEncoder")}} است.

یک خط لوله رندر، گرافیک را به پیوست‌های {{domxref("GPUTexture")}} رندر می‌کند که معمولاً برای نمایش در یک عنصر {{htmlelement("canvas")}} در نظر گرفته شده است، اما می‌تواند به بافت‌هایی که برای اهداف دیگر استفاده می‌شوند و هرگز روی صفحه ظاهر نمی‌شوند نیز رندر کند. این خط لوله دو مرحله اصلی دارد:

- **مرحله رأس**: در این مرحله، یک شیدر رأس داده‌های موقعیت‌دهی وارد شده به GPU را دریافت کرده و با اعمال اثراتی مانند چرخش، انتقال یا پرسپکتیو، از آن برای قرار دادن مجموعه‌ای از رئوس در فضای سه‌بعدی استفاده می‌کند. سپس رئوس به صورت ابتدایی‌هایی مانند مثلث (بلوک ساختمانی اصلی گرافیک رندر شده) مونتاژ شده و توسط GPU شطرنجی می‌شوند تا مشخص شود هر کدام از آن‌ها چه پیکسل‌هایی را روی بوم نقاشی پوشش می‌دهند.
- **مرحله قطعه**: در این مرحله، یک شیدر قطعه رنگ هر پیکسل تحت پوشش ابتدایی‌های تولید شده توسط شیدر رأس را محاسبه می‌کند. این محاسبات اغلب از ورودی‌هایی مانند تصاویر (به صورت بافت) که جزئیات سطح و موقعیت و رنگ نورهای مجازی را فراهم می‌کنند، استفاده می‌کنند.

یک نمونه شیء `GPURenderPassEncoder` از طریق متد {{domxref("GPUCommandEncoder.beginRenderPass()")}} ایجاد می‌شود.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("GPURenderPassEncoder.label", "label")}}
  - : یک رشته که برچسبی را ارائه می‌دهد که می‌تواند برای شناسایی شیء استفاده شود، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

## متدهای نمونه

- {{domxref("GPURenderPassEncoder.beginOcclusionQuery", "beginOcclusionQuery()")}}
  - : یک پرس‌وجوی occlusio را در شاخص مشخص شده از {{domxref("GPUQuerySet")}} مربوطه آغاز می‌کند (که به عنوان مقدار ویژگی توصیف‌کننده `occlusionQuerySet` هنگام فراخوانی {{domxref("GPUCommandEncoder.beginRenderPass()")}} برای اجرای پاس رندر ارائه می‌شود).
- {{domxref("GPURenderPassEncoder.draw", "draw()")}}
  - : ابتدا‌یی‌ها را بر اساس بافرهای رأس ارائه شده توسط {{domxref("GPURenderPassEncoder.setVertexBuffer", "setVertexBuffer()")}} رسم می‌کند.
- {{domxref("GPURenderPassEncoder.drawIndexed", "drawIndexed()")}}
  - : ابتدا‌یی‌های نمایه‌دار را بر اساس بافرهای رأس و نمایه ارائه شده توسط {{domxref("GPURenderPassEncoder.setVertexBuffer", "setVertexBuffer()")}} و {{domxref("GPURenderPassEncoder.setIndexBuffer", "setIndexBuffer()")}} رسم می‌کند.
- {{domxref("GPURenderPassEncoder.drawIndirect", "drawIndirect()")}}
  - : ابتدا‌یی‌ها را با استفاده از پارامترهای خوانده شده از یک {{domxref("GPUBuffer")}} رسم می‌کند.
- {{domxref("GPURenderPassEncoder.drawIndexedIndirect", "drawIndexedIndirect()")}}
  - : ابتدا‌یی‌های نمایه‌دار را با استفاده از پارامترهای خوانده شده از یک {{domxref("GPUBuffer")}} رسم می‌کند.
- {{domxref("GPURenderPassEncoder.end", "end()")}}
  - : ثبت توالی دستورات پاس رندر فعلی را تکمیل می‌کند.
- {{domxref("GPURenderPassEncoder.endOcclusionQuery", "endOcclusionQuery()")}}
  - : یک پرس‌وجوی occlusio فعال را که قبلاً با {{domxref("GPURenderPassEncoder.beginOcclusionQuery", "beginOcclusionQuery()")}} شروع شده بود، پایان می‌دهد.
- {{domxref("GPURenderPassEncoder.executeBundles", "executeBundles()")}}
  - : دستوراتی را که قبلاً در {{domxref("GPURenderBundle")}}های ارجاع داده شده ثبت شده‌اند، به عنوان بخشی از این پاس رندر اجرا می‌کند.
- {{domxref("GPURenderPassEncoder.insertDebugMarker", "insertDebugMarker()")}}
  - : یک نقطه خاص در یک سری از دستورات رمزگذاری شده را با یک برچسب علامت‌گذاری می‌کند.
- {{domxref("GPURenderPassEncoder.popDebugGroup", "popDebugGroup()")}}
  - : یک گروه دیباگ را که با فراخوانی {{domxref("GPURenderPassEncoder.pushDebugGroup", "pushDebugGroup()")}} شروع شده است، پایان می‌دهد.
- {{domxref("GPURenderPassEncoder.pushDebugGroup", "pushDebugGroup()")}}
  - : یک گروه دیباگ را شروع می‌کند که با یک برچسب مشخص علامت‌گذاری شده است و تمام دستورات رمزگذاری شده بعدی را تا زمانی که متد {{domxref("GPURenderPassEncoder.popDebugGroup", "popDebugGroup()")}} فراخوانی شود، در خود جای می‌دهد.
- {{domxref("GPURenderPassEncoder.setBindGroup", "setBindGroup()")}}
  - : {{domxref("GPUBindGroup")}} را برای استفاده در دستورات رندر بعدی، برای یک شاخص معین تنظیم می‌کند.
- {{domxref("GPURenderPassEncoder.setBlendConstant", "setBlendConstant()")}}
  - : رنگ ثابت blend و مقادیر آلفا را که با فاکتورهای blend `"constant"` و `"one-minus-constant"` استفاده می‌شوند، تنظیم می‌کند (همانطور که در توصیف‌کننده متد {{domxref("GPUDevice.createRenderPipeline()")}}، در ویژگی `blend` تنظیم شده است).
- {{domxref("GPURenderPassEncoder.setIndexBuffer", "setIndexBuffer()")}}
  - : {{domxref("GPUBuffer")}} فعلی را که داده‌های نمایه را برای دستورات رسم بعدی فراهم می‌کند، تنظیم می‌کند.
- {{domxref("GPURenderPassEncoder.setPipeline", "setPipeline()")}}
  - : {{domxref("GPURenderPipeline")}} را برای استفاده در این پاس رندر تنظیم می‌کند.
- {{domxref("GPURenderPassEncoder.setScissorRect", "setScissorRect()")}}
  - : مستطیل قیچی (scissor) را که در مرحله شطرنجی‌سازی استفاده می‌شود، تنظیم می‌کند. پس از تبدیل به مختصات viewport، هر قطعه‌ای که خارج از مستطیل قیچی قرار گیرد، دور انداخته می‌شود.
- {{domxref("GPURenderPassEncoder.setStencilReference", "setStencilReference()")}}
  - : مقدار مرجع stencil را که در طول تست‌های stencil با عملیات stencil `"replace"` استفاده می‌شود، تنظیم می‌کند (همانطور که در توصیف‌کننده متد {{domxref("GPUDevice.createRenderPipeline()")}}، در ویژگی‌های تعریف‌کننده عملیات مختلف stencil تنظیم شده است).
- {{domxref("GPURenderPassEncoder.setVertexBuffer", "setVertexBuffer()")}}
  - : {{domxref("GPUBuffer")}} فعلی را که داده‌های رأس را برای دستورات رسم بعدی فراهم می‌کند، تنظیم یا لغو تنظیم می‌کند.
- {{domxref("GPURenderPassEncoder.setViewport", "setViewport()")}}
  - : viewport مورد استفاده در مرحله شطرنجی‌سازی را برای نگاشت خطی از مختصات دستگاه نرمال‌شده به مختصات viewport تنظیم می‌کند.

## مثال‌ها

در [نمایش رندر پایه](https://mdn.github.io/dom-examples/webgpu-render-demo/) ما، چندین دستور از طریق یک {{domxref("GPUCommandEncoder")}} ثبت می‌شوند. بیشتر این دستورات از `GPURenderPassEncoder` ایجاد شده از طریق {{domxref("GPUCommandEncoder.beginRenderPass()")}} نشأت می‌گیرند.

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

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)