```
---
title: "GPURenderBundleEncoder: setVertexBuffer() method"
short-title: setVertexBuffer()
slug: Web/API/GPURenderBundleEncoder/setVertexBuffer
page-type: web-api-instance-method
browser-compat: api.GPURenderBundleEncoder.setVertexBuffer
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`setVertexBuffer()`** از رابط {{domxref("GPURenderBundleEncoder")}}، بافر رأس فعلی ({{domxref("GPUBuffer")}}) را برای اسلات داده‌شده تنظیم یا لغو تنظیم می‌کند که داده‌های رأس را برای دستورات ترسیم بعدی فراهم می‌کند.

> [!NOTE]
> این متد از نظر عملکردی با معادل خود در {{domxref("GPURenderPassEncoder")}} — {{domxref("GPURenderPassEncoder.setVertexBuffer", "setVertexBuffer()")}} یکسان است.

## سینتکس

```js-nolint
setVertexBuffer(slot, buffer, offset, size)
```

### پارامترها

- `slot`
  - : عددی که به اسلات بافر رأس اشاره می‌کند تا بافر رأس برای آن تنظیم شود.
- `buffer`
  - : یک {{domxref("GPUBuffer")}} که نشان‌دهنده بافر حاوی داده‌های رأس برای استفاده در دستورات ترسیم بعدی است، یا `null`، که در این صورت هر بافر تنظیم‌شدهٔ قبلی در اسلات داده‌شده، لغو تنظیم می‌شود.
- `offset` {{optional_inline}}
  - : عددی که نشان‌دهنده آفست (offset) بر حسب بایت در `buffer` است که داده‌های رأس از آنجا آغاز می‌شوند. اگر حذف شود، `offset` به‌صورت پیش‌فرض 0 است.
- `size` {{optional_inline}}
  - : عددی که نشان‌دهنده اندازه داده‌های رأس موجود در `buffer` بر حسب بایت است. اگر حذف شود، `size` به‌صورت پیش‌فرض برابر با {{domxref("GPUBuffer.size")}} بافر منهای `offset` است.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### اعتبارسنجی

هنگام فراخوانی **`setVertexBuffer()`** معیارهای زیر باید برقرار باشند؛ در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و {{domxref("GPURenderBundleEncoder")}} نامعتبر می‌شود:

- ویژگی {{domxref("GPUBuffer.usage")}} در `buffer` شامل پرچم `GPUBufferUsage.VERTEX` باشد.
- `slot` کمتر از مقدار `maxVertexBuffers` تعیین‌شده در محدودیت‌های {{domxref("GPUDevice")}} ({{domxref("GPUSupportedLimits", "limit", "", "nocode")}}) باشد.
- `offset` + `size` کمتر یا مساوی با {{domxref("GPUBuffer.size")}} مربوط به `buffer` باشد.
- `offset` مضربی از 4 باشد.

## مثال‌ها

### تنظیم بافر رأس

```js
function recordRenderPass(passEncoder) {
  if (settings.dynamicOffsets) {
    passEncoder.setPipeline(dynamicPipeline);
  } else {
    passEncoder.setPipeline(pipeline);
  }
  passEncoder.setVertexBuffer(0, vertexBuffer);
  passEncoder.setBindGroup(0, timeBindGroup);
  const dynamicOffsets = [0];
  for (let i = 0; i < numTriangles; ++i) {
    if (settings.dynamicOffsets) {
      dynamicOffsets[0] = i * alignedUniformBytes;
      passEncoder.setBindGroup(1, dynamicBindGroup, dynamicOffsets);
    } else {
      passEncoder.setBindGroup(1, bindGroups[i]);
    }
    passEncoder.draw(3, 1, 0, 0);
  }
}
```

قطعه کد بالا از [مثال Animometer](https://webgpu.github.io/webgpu-samples/samples/animometer/) در نمونه‌های WebGPU گرفته شده است.

### لغو تنظیم بافر رأس

```js
// Set vertex buffer in slot 0
passEncoder.setVertexBuffer(0, vertexBuffer);

// Later, unset vertex buffer in slot 0
passEncoder.setVertexBuffer(0, null);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
```