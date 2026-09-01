---
title: "GPURenderBundleEncoder: setPipeline() method"
short-title: setPipeline()
slug: Web/API/GPURenderBundleEncoder/setPipeline
page-type: web-api-instance-method
browser-compat: api.GPURenderBundleEncoder.setPipeline
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`setPipeline()`** در رابط {{domxref("GPURenderBundleEncoder")}}، {{domxref("GPURenderPipeline")}} را برای استفاده در دستورات بعدی رندر باندل تنظیم می‌کند.

> [!NOTE]
> این متد از نظر عملکردی با معادل خود در {{domxref("GPURenderPassEncoder")}} — {{domxref("GPURenderPassEncoder.setPipeline", "setPipeline()")}} — یکسان است.

## نحو

```js-nolint
setPipeline(pipeline)
```

### پارامترها

- `pipeline`
  - : {{domxref("GPURenderPipeline")}} که برای دستورات بعدی رندر باندل استفاده می‌شود.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### اعتبارسنجی

هنگام فراخوانی `setPipeline()`، معیارهای زیر باید برآورده شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و {{domxref("GPURenderBundleEncoder")}} نامعتبر می‌شود:

- اگر {{domxref("GPURenderPipeline")}} در مؤلفه عمق پیوست depth/stencil بنویسد، `depthReadOnly` (که در توصیف‌گر فراخوانی اصلی {{domxref("GPUCommandEncoder.beginRenderPass()")}} مشخص شده است) باید `true` باشد.
- اگر {{domxref("GPURenderPipeline")}} در مؤلفه استنسیل پیوست depth/stencil بنویسد، `stencilReadOnly` (که در توصیف‌گر فراخوانی اصلی {{domxref("GPUCommandEncoder.beginRenderPass()")}} مشخص شده است) باید `true` باشد.

## مثال‌ها

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

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [API WebGPU](/en-US/docs/Web/API/WebGPU_API)