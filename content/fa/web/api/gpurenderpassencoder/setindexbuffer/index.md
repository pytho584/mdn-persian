---
title: "GPURenderPassEncoder: setIndexBuffer() method"
short-title: setIndexBuffer()
slug: Web/API/GPURenderPassEncoder/setIndexBuffer
page-type: web-api-instance-method
browser-compat: api.GPURenderPassEncoder.setIndexBuffer
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`setIndexBuffer()`** از رابط {{domxref("GPURenderPassEncoder")}}، {{domxref("GPUBuffer")}} جاری را تنظیم می‌کند که داده‌های ایندکس را برای دستورهای رسم بعدی فراهم می‌کند.

## نحو

```js-nolint
setIndexBuffer(buffer, indexFormat, offset, size)
```

### پارامترها

- `buffer`
  - : یک {{domxref("GPUBuffer")}} که بافر حاوی داده‌های ایندکس مورد استفاده برای دستورهای رسم بعدی را نشان می‌دهد.
- `indexFormat`
  - : یک مقدار شمارشی که قالب داده‌های ایندکس موجود در `buffer` را تعریف می‌کند. مقادیر ممکن عبارت‌اند از:
    - `"uint16"`
    - `"uint32"`
- `offset` {{optional_inline}}
  - : عددی که آفست را بر حسب بایت درون `buffer`، جایی که داده‌های ایندکس آغاز می‌شود، نشان می‌دهد. اگر حذف شود، `offset` به‌صورت پیش‌فرض ۰ است.
- `size` {{optional_inline}}
  - : عددی که اندازه‌ی داده‌های ایندکس موجود در `buffer` را بر حسب بایت نشان می‌دهد. اگر حذف شود، `size` به‌صورت پیش‌فرض برابر با {{domxref("GPUBuffer.size")}} مربوط به `buffer` منهای `offset` است.

#### نکته درباره‌ی indexFormat

`indexFormat` هم نوع داده‌ی مقادیر ایندکس در یک بافر را تعیین می‌کند و هم، زمانی که با پایپلاینی استفاده شود که توپولوژی نوار (`"line-strip"` یا `"triangle-strip"`) را مشخص می‌کند، مقدار «بازآغازی اولیه» (primitive restart) را نیز تعیین می‌کند. مقدار بازآغازی اولیه، یک مقدار ایندکس است که نشان می‌دهد به‌جای ادامه‌ی ساخت نوار با رئوس ایندکس‌شده‌ی قبلی، باید یک اولیه‌ی جدید آغاز شود. این مقدار برای `"uint16"` برابر با `0xFFFF` و برای `"uint32"` برابر با `0xFFFFFFFF` است.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### اعتبارسنجی

هنگام فراخوانی **`setIndexBuffer()`**، معیارهای زیر باید برقرار باشند، در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و {{domxref("GPURenderPassEncoder")}} نامعتبر می‌شود:

- {{domxref("GPUBuffer.usage")}} مربوط به `buffer` شامل پرچم `GPUBufferUsage.INDEX` باشد.
- `offset` + `size` کمتر یا برابر با {{domxref("GPUBuffer.size")}} مربوط به `buffer` باشد.
- `offset` مضربی از اندازه‌ی بایتیِ `indexFormat` باشد (۲ برای `"uint16"`، ۴ برای `"uint32"`).

## مثال‌ها

در مثال [Shadow Mapping](https://webgpu.github.io/webgpu-samples/samples/shadowMapping/) از WebGPU Samples، از `setIndexBuffer()` در دو رندر پاسِ مجزا در هر فریم انیمیشن استفاده می‌شود؛ یکی برای رسم مدل اصلی و دیگری برای رسم سایه‌ی آن. برای دریافت بافت کامل، فهرست کد مثال را مطالعه کنید.

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

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)