---
title: "GPURenderPassEncoder: drawIndexedIndirect() method"
short-title: drawIndexedIndirect()
slug: Web/API/GPURenderPassEncoder/drawIndexedIndirect
page-type: web-api-instance-method
browser-compat: api.GPURenderPassEncoder.drawIndexedIndirect
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`drawIndexedIndirect()`** از رابط {{domxref("GPURenderPassEncoder")}}، پریمیتیوهای ایندکس‌دار را با استفاده از پارامترهایی که از یک {{domxref("GPUBuffer")}} خوانده می‌شوند، رسم می‌کند.

## نحو (Syntax)

```js-nolint
drawIndexedIndirect(indirectBuffer, indirectOffset)
```

### پارامترها

- `indirectBuffer`
  - : یک {{domxref("GPUBuffer")}} که شامل مقادیر `indexCount`، `instanceCount`، `firstIndex`، `baseVertex` و `firstInstance` مورد نیاز برای اجرای عملیات رسم است. بافر باید حاوی یک بلوک فشرده از پنج مقدار صحیح ۳۲ بیتی بدون علامت (مجموعاً ۲۰ بایت) باشد که به همان ترتیب آرگومان‌های {{domxref("GPURenderPassEncoder.drawIndexed()")}} مرتب شده‌اند. به عنوان مثال:

    ```js
    const uint32 = new Uint32Array(5);
    uint32[0] = 3; // مقدار indexCount
    uint32[1] = 1; // مقدار instanceCount
    uint32[2] = 0; // مقدار firstIndex
    uint32[3] = 0; // مقدار baseVertex
    uint32[4] = 0; // مقدار firstInstance

    // نوشتن مقادیر در یک GPUBuffer
    device.queue.writeBuffer(buffer, 0, uint32, 0, uint32.length);
    ```

    > [!NOTE]
    > برای استفاده از مقادیر غیرصفر `firstInstance`، باید [ویژگی](/en-US/docs/Web/API/GPUSupportedFeatures) `indirect-first-instance` فعال باشد. اگر این ویژگی فعال نباشد و `firstInstance` صفر نباشد، فراخوانی `drawIndexedIndirect()` به عنوان یک عملیات بی‌اثر (no-op) در نظر گرفته می‌شود.

- `indirectOffset`
  - : افست (بر حسب بایت) درون `indirectBuffer` که داده‌های مقادیر از آنجا شروع می‌شوند.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### اعتبارسنجی

هنگام فراخوانی `drawIndexedIndirect()`، معیارهای زیر باید رعایت شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و {{domxref("GPURenderPassEncoder")}} نامعتبر می‌شود:

- پرچم `GPUBufferUsage.INDIRECT` در {{domxref("GPUBuffer.usage")}} بافر `indirectBuffer` وجود داشته باشد.
- مقدار `indirectOffset` + اندازه کل مشخص‌شده توسط پارامترهای مقدار در `indirectBuffer`، کمتر یا برابر با {{domxref("GPUBuffer.size")}} بافر `indirectBuffer` باشد.
- `indirectOffset` مضربی از ۴ باشد.

## مثال‌ها

```js
// …

// ایجاد GPURenderPassEncoder
const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);

// تنظیم pipeline و بافر رأس
passEncoder.setPipeline(renderPipeline);
passEncoder.setVertexBuffer(0, vertexBuffer);
passEncoder.setIndexBuffer(indexBuffer, "uint16");

// ایجاد مقادیر drawIndexedIndirect
const uint32 = new Uint32Array(5);
uint32[0] = 3;
uint32[1] = 1;
uint32[2] = 0;
uint32[3] = 0;
uint32[4] = 0;

// ایجاد یک GPUBuffer و نوشتن مقادیر رسم در آن
const drawValues = device.createBuffer({
  size: 20,
  usage: GPUBufferUsage.COPY_DST | GPUBufferUsage.INDIRECT,
});
device.queue.writeBuffer(drawValues, 0, uint32, 0, uint32.length);

// رسم رأس‌ها
passEncoder.drawIndexedIndirect(drawValues, 0);

// پایان دادن به پاس رندر
passEncoder.end();

// پایان فریم با ارسال آرایه‌ای از GPUCommandBufferها به صف فرمان برای اجرا
device.queue.submit([commandEncoder.finish()]);

// …
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)