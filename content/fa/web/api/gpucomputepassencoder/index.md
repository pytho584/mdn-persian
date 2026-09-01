---
title: GPUComputePassEncoder
slug: Web/API/GPUComputePassEncoder
page-type: web-api-interface
browser-compat: api.GPUComputePassEncoder
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

**`GPUComputePassEncoder`** واسطهای از {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} است که دستورات مربوط به کنترل مرحلهٔ سایهزن محاسباتی (compute shader stage) را که توسط {{domxref("GPUComputePipeline")}} صادر میشوند، رمزگذاری میکند. این واسط بخشی از فعالیت کلی رمزگذاری یک {{domxref("GPUCommandEncoder")}} است.

یک خط لولهٔ محاسباتی (compute pipeline) شامل یک مرحلهٔ محاسباتی واحد است که در آن یک سایهزن محاسباتی دادههای عمومی را میگیرد، آنها را به صورت موازی در تعداد مشخصی از گروههای کاری (workgroups) پردازش میکند و سپس نتیجه را در یک یا چند بافر برمیگرداند.

یک نمونه از شیء `GPUComputePassEncoder` از طریق ویژگی {{domxref("GPUCommandEncoder.beginComputePass()")}} ایجاد میشود.

{{InheritanceDiagram}}

## ویژگیهای نمونه

- {{domxref("GPUComputePassEncoder.label", "label")}}
  - : یک رشته که برچسبی برای شناسایی شیء فراهم میکند، برای مثال در پیامهای {{domxref("GPUError")}} یا هشدارهای کنسول.

## روشهای نمونه

- {{domxref("GPUComputePassEncoder.dispatchWorkgroups", "dispatchWorkgroups()")}}
  - : یک شبکهٔ مشخص از گروههای کاری را برای انجام کار جاری {{domxref("GPUComputePipeline")}} توزیع میکند.
- {{domxref("GPUComputePassEncoder.dispatchWorkgroupsIndirect", "dispatchWorkgroupsIndirect()")}}
  - : یک شبکهٔ از گروههای کاری را که توسط پارامترهای یک {{domxref("GPUBuffer")}} تعریف شدهاند، برای انجام کار جاری {{domxref("GPUComputePipeline")}} توزیع میکند.
- {{domxref("GPUComputePassEncoder.end", "end()")}}
  - : ضبط دنبالهٔ دستورات پاس محاسباتی جاری را تکمیل میکند.
- {{domxref("GPUComputePassEncoder.insertDebugMarker", "insertDebugMarker()")}}
  - : نقطهٔ خاصی را در یک سری از دستورات رمزگذاریشده با یک برچسب علامتگذاری میکند.
- {{domxref("GPUComputePassEncoder.popDebugGroup", "popDebugGroup()")}}
  - : یک گروه اشکالزدایی را پایان میدهد که با فراخوانی {{domxref("GPUComputePassEncoder.pushDebugGroup", "pushDebugGroup()")}} شروع شده است.
- {{domxref("GPUComputePassEncoder.pushDebugGroup", "pushDebugGroup()")}}
  - : یک گروه اشکالزدایی را آغاز میکند که با برچسب مشخصی علامتگذاری شده و شامل تمام دستورات رمزگذاریشدهٔ بعدی تا زمان فراخوانی روش {{domxref("GPUComputePassEncoder.popDebugGroup", "popDebugGroup()")}} خواهد بود.
- {{domxref("GPUComputePassEncoder.setBindGroup", "setBindGroup()")}}
  - : {{domxref("GPUBindGroup")}} مورد استفاده برای دستورات محاسباتی بعدی را برای یک شاخص معین تنظیم میکند.
- {{domxref("GPUComputePassEncoder.setPipeline", "setPipeline()")}}
  - : {{domxref("GPUComputePipeline")}} مورد استفاده برای این پاس محاسباتی را تنظیم میکند.

## مثالها

در [نمونهٔ محاسبات پایه](https://mdn.github.io/dom-examples/webgpu-compute-demo/)، چندین دستور از طریق یک {{domxref("GPUCommandEncoder")}} رمزگذاری میشوند. بیشتر این دستورات از `GPUComputePassEncoder` ایجادشده از طریق {{domxref("GPUCommandEncoder.beginComputePass()")}} سرچشمه میگیرند.

```js
// …

// Create GPUCommandEncoder to encode commands to issue to the GPU
const commandEncoder = device.createCommandEncoder();

// Create GPUComputePassEncoder to initiate compute pass
const passEncoder = commandEncoder.beginComputePass();

// Issue commands
passEncoder.setPipeline(computePipeline);
passEncoder.setBindGroup(0, bindGroup);
passEncoder.dispatchWorkgroups(Math.ceil(BUFFER_SIZE / 64));

// End the compute pass
passEncoder.end();

// Copy output buffer to staging buffer
commandEncoder.copyBufferToBuffer(
  output,
  0, // Source offset
  stagingBuffer,
  0, // Destination offset
  BUFFER_SIZE,
);

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