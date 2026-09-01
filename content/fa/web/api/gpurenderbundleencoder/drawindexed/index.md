---
title: "GPURenderBundleEncoder: drawIndexed() method"
short-title: drawIndexed()
slug: Web/API/GPURenderBundleEncoder/drawIndexed
page-type: web-api-instance-method
browser-compat: api.GPURenderBundleEncoder.drawIndexed
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`drawIndexed()`** از رابط {{domxref("GPURenderBundleEncoder")}}، primitiveهای نمایه‌دار را بر اساس بافرهای رأس و نمایه رسم می‌کند که توسط {{domxref("GPURenderBundleEncoder.setVertexBuffer", "setVertexBuffer()")}} و {{domxref("GPURenderBundleEncoder.setIndexBuffer", "setIndexBuffer()")}} فراهم شده‌اند.

> [!NOTE]
> این متد از نظر عملکردی با معادل خود در {{domxref("GPURenderPassEncoder")}} یعنی {{domxref("GPURenderPassEncoder.drawIndexed", "drawIndexed()")}} یکسان است.

## نحو

```js-nolint
drawIndexed(indexCount)
drawIndexed(indexCount, instanceCount)
drawIndexed(indexCount, instanceCount, firstIndex)
drawIndexed(indexCount, instanceCount, firstIndex, baseVertex)
drawIndexed(indexCount, instanceCount, firstIndex, baseVertex, firstInstance)
```

### پارامترها

- `indexCount`
  - : عددی که تعداد نمایه‌های موردنظر برای رسم را مشخص می‌کند.
- `instanceCount` {{optional_inline}}
  - : عددی که تعداد نمونه‌های موردنظر برای رسم را مشخص می‌کند. اگر حذف شود، `instanceCount` به‌صورت پیش‌فرض برابر با ۱ است.
- `firstIndex` {{optional_inline}}
  - : عددی که افست در بافر نمایه را بر حسب تعداد نمایه‌ها، برای شروع رسم مشخص می‌کند. اگر حذف شود، `firstIndex` به‌صورت پیش‌فرض برابر با ۰ است.
- `baseVertex` {{optional_inline}}
  - : عددی که پیش از نمایه‌گذاری در بافرهای رأس، به هر مقدار نمایه اضافه می‌شود. اگر حذف شود، `baseVertex` به‌صورت پیش‌فرض برابر با ۰ است.
- `firstInstance` {{optional_inline}}
  - : عددی که اولین نمونه‌ای را که باید رسم شود مشخص می‌کند. اگر حذف شود، `firstInstance` به‌صورت پیش‌فرض برابر با ۰ است.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
// …

const bundleEncoder = device.createRenderBundleEncoder(descriptor);

bundleEncoder.setPipeline(pipeline);
bundleEncoder.setBindGroup(0, sceneBindGroupForRender);
bundleEncoder.setBindGroup(1, modelBindGroup);
bundleEncoder.setVertexBuffer(0, vertexBuffer);
bundleEncoder.setIndexBuffer(indexBuffer, "uint16");
bundleEncoder.drawIndexed(indexCount);

const renderBundle = bundleEncoder.finish();

// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط [WebGPU API](/en-US/docs/Web/API/WebGPU_API)