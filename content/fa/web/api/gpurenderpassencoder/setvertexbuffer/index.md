---
title: "GPURenderPassEncoder: setVertexBuffer() method"
short-title: setVertexBuffer()
slug: Web/API/GPURenderPassEncoder/setVertexBuffer
page-type: web-api-instance-method
browser-compat: api.GPURenderPassEncoder.setVertexBuffer
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`setVertexBuffer()`** از رابط {{domxref("GPURenderPassEncoder")}}، {{domxref("GPUBuffer")}} فعلی را برای اسلات (slot) مشخص‌شده تنظیم یا لغو می‌کند. این بافر داده‌های رأس (vertex data) را برای دستورات ترسیم بعدی فراهم می‌کند.

## نحو (Syntax)

```js-nolint
setVertexBuffer(slot, buffer, offset, size)
```

### پارامترها

- `slot`
  - : عددی که اسلات بافر رأس را مشخص می‌کند تا بافر رأس برای آن تنظیم شود.
- `buffer`
  - : یک {{domxref("GPUBuffer")}} که نشان‌دهندهٔ بافر حاوی داده‌های رأس برای استفاده در دستورات ترسیم بعدی است، یا `null` که در این صورت هر بافر قبلاً تنظیم‌شده در اسلات داده‌شده لغو می‌شود.
- `offset` {{optional_inline}}
  - : عددی که افست (offset) را بر حسب بایت، درون `buffer` مشخص می‌کند که داده‌های رأس از آنجا شروع می‌شوند. اگر حذف شود، `offset` به طور پیش‌فرض ۰ است.
- `size` {{optional_inline}}
  - : عددی که اندازهٔ داده‌های رأس موجود در `buffer` را بر حسب بایت مشخص می‌کند. اگر حذف شود، `size` به طور پیش‌فرض برابر با `buffer`'s {{domxref("GPUBuffer.size")}} - `offset` است.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### اعتبارسنجی (Validation)

هنگام فراخوانی **`setVertexBuffer()`** معیارهای زیر باید برآورده شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} ایجاد می‌شود و {{domxref("GPURenderPassEncoder")}} نامعتبر می‌شود:

- `buffer`'s {{domxref("GPUBuffer.usage")}} شامل پرچم `GPUBufferUsage.VERTEX` باشد.
- `slot` کمتر از `maxVertexBuffers` {{domxref("GPUSupportedLimits", "limit", "", "nocode")}} دستگاه {{domxref("GPUDevice")}} باشد.
- `offset` + `size` کمتر یا مساوی `buffer`'s {{domxref("GPUBuffer.size")}} باشد.
- `offset` مضرب ۴ باشد.

## مثال‌ها

### تنظیم بافر رأس

در [نمایش رندر پایه](https://mdn.github.io/dom-examples/webgpu-render-demo/) ما، چندین دستور از طریق یک {{domxref("GPUCommandEncoder")}} ثبت می‌شوند. بیشتر این دستورات از `GPURenderPassEncoder` که از طریق {{domxref("GPUCommandEncoder.beginRenderPass()")}} ایجاد شده است، می‌آیند. `setVertexBuffer()` به‌طور مناسب برای تنظیم منبع داده‌های رأس استفاده می‌شود.

```js
// …

const renderPipeline = device.createRenderPipeline(pipelineDescriptor);

// ایجاد GPUCommandEncoder برای ارسال دستورات به GPU
// توجه: توصیف‌کنندهٔ رندر پاس، encoder دستورات و غیره پس از استفاده نابود می‌شوند، برای هر فریم به یک نمونهٔ جدید نیاز است.
const commandEncoder = device.createCommandEncoder();

// ایجاد GPURenderPassDescriptor برای گفتن به WebGPU که به کدام بافت (texture) ترسیم کند، سپس شروع رندر پاس
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

// ترسیم مثلث
passEncoder.setPipeline(renderPipeline);
passEncoder.setVertexBuffer(0, vertexBuffer);
passEncoder.draw(3);

// پایان رندر پاس
passEncoder.end();

// پایان فریم با ارسال آرایه‌ای از command bufferها به صف فرمان برای اجرا
device.queue.submit([commandEncoder.finish()]);

// …
```

### لغو تنظیم بافر رأس

```js
// تنظیم بافر رأس در اسلات ۰
passEncoder.setVertexBuffer(0, vertexBuffer);

// بعداً، لغو تنظیم بافر رأس در اسلات ۰
passEncoder.setVertexBuffer(0, null);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)