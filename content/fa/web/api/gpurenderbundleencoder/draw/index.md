---
title: "GPURenderBundleEncoder: draw() method"
short-title: draw()
slug: Web/API/GPURenderBundleEncoder/draw
page-type: web-api-instance-method
browser-compat: api.GPURenderBundleEncoder.draw
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`draw()`** از رابط {{domxref("GPURenderBundleEncoder")}}، primitives (اشکال اولیه) را بر اساس بافرهای رأس (vertex buffers) که توسط {{domxref("GPURenderBundleEncoder.setVertexBuffer", "setVertexBuffer()")}} ارائه شده‌اند، رسم می‌کند.

> [!NOTE]
> این متد از نظر عملکردی با معادل خود در {{domxref("GPURenderPassEncoder")}} — {{domxref("GPURenderPassEncoder.draw", "draw()")}} یکسان است.

## نحو (Syntax)

```js-nolint
draw(vertexCount)
draw(vertexCount, instanceCount)
draw(vertexCount, instanceCount, firstVertex)
draw(vertexCount, instanceCount, firstVertex, firstInstance)
```

### پارامترها

- `vertexCount`
  - : عددی که تعداد رئوس (vertices) برای رسم را مشخص می‌کند.
- `instanceCount` {{optional_inline}}
  - : عددی که تعداد نمونه‌ها (instances) برای رسم را مشخص می‌کند. در صورت حذف، `instanceCount` به طور پیش‌فرض ۱ است.
- `firstVertex` {{optional_inline}}
  - : عددی که افست (offset) درون بافرهای رأس، بر حسب رأس، را برای شروع رسم مشخص می‌کند. در صورت حذف، `firstVertex` به طور پیش‌فرض ۰ است.
- `firstInstance` {{optional_inline}}
  - : عددی که اولین نمونه برای رسم را مشخص می‌کند. در صورت حذف، `firstInstance` به طور پیش‌فرض ۰ است.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

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

قطعه کد بالا از نمونه [Animometer](https://webgpu.github.io/webgpu-samples/samples/animometer/) موجود در WebGPU Samples گرفته شده است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)