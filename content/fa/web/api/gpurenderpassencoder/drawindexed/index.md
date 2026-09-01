---
title: "GPURenderPassEncoder: drawIndexed() method"
short-title: drawIndexed()
slug: Web/API/GPURenderPassEncoder/drawIndexed
page-type: web-api-instance-method
browser-compat: api.GPURenderPassEncoder.drawIndexed
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`drawIndexed()`** از رابط {{domxref("GPURenderPassEncoder")}} اولیه‌های شاخص‌دار را بر اساس بافرهای رأس و شاخص که توسط {{domxref("GPURenderPassEncoder.setVertexBuffer", "setVertexBuffer()")}} و {{domxref("GPURenderPassEncoder.setIndexBuffer", "setIndexBuffer()")}} فراهم شده‌اند، ترسیم می‌کند.

## سینتکس

```js-nolint
drawIndexed(indexCount)
drawIndexed(indexCount, instanceCount)
drawIndexed(indexCount, instanceCount, firstIndex)
drawIndexed(indexCount, instanceCount, firstIndex, baseVertex)
drawIndexed(indexCount, instanceCount, firstIndex, baseVertex, firstInstance)
```

### پارامترها

- `indexCount`
  - : عددی که تعداد شاخص‌هایی که باید ترسیم شوند را مشخص می‌کند.
- `instanceCount` {{optional_inline}}
  - : عددی که تعداد نمونه‌ها (instance) را برای ترسیم مشخص می‌کند. اگر حذف شود، `instanceCount` به‌صورت پیش‌فرض 1 است.
- `firstIndex` {{optional_inline}}
  - : عددی که افست (offset) در بافر شاخص را، بر حسب شاخص، برای شروع ترسیم مشخص می‌کند. اگر حذف شود، `firstIndex` به‌صورت پیش‌فرض 0 است.
- `baseVertex` {{optional_inline}}
  - : عددی که پیش از شاخص‌گذاری در بافرهای رأس، به هر مقدار شاخص اضافه می‌شود. اگر حذف شود، `baseVertex` به‌صورت پیش‌فرض 0 است.
- `firstInstance` {{optional_inline}}
  - : عددی که اولین نمونه (instance) را برای ترسیم مشخص می‌کند. اگر حذف شود، `firstInstance` به‌صورت پیش‌فرض 0 است.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

در مثال [Shadow Mapping](https://webgpu.github.io/webgpu-samples/samples/shadowMapping/) از WebGPU Samples، متد `drawIndexed()` در هر فریم انیمیشن در دو رندر پاس مجزا استفاده می‌شود؛ یکی برای پر کردن بافر سایه و دیگری برای ترسیم نمای اصلی صحنه. برای دریافت زمینه کامل، فهرست کد مثال را بررسی کنید.

```js
// …

const commandEncoder = device.createCommandEncoder();
{
  const shadowPass = commandEncoder.beginRenderPass(shadowPassDescriptor);
  shadowPass.setPipeline(shadowPipeline);
  shadowPass.setBindGroup(0, sceneBindGroupForShadow);
  shadowPass.setBindGroup(1, modelBindGroup);
  shadowPass.setVertexBuffer(0, vertexBuffer);
  shadowPass.setIndexBuffer(indexBuffer, "uint16");
  shadowPass.drawIndexed(indexCount);

  shadowPass.end();
}
{
  const renderPass = commandEncoder.beginRenderPass(renderPassDescriptor);
  renderPass.setPipeline(pipeline);
  renderPass.setBindGroup(0, sceneBindGroupForRender);
  renderPass.setBindGroup(1, modelBindGroup);
  renderPass.setVertexBuffer(0, vertexBuffer);
  renderPass.setIndexBuffer(indexBuffer, "uint16");
  renderPass.drawIndexed(indexCount);

  renderPass.end();
}

// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [رابط برنامه‌نویسی WebGPU](/en-US/docs/Web/API/WebGPU_API)