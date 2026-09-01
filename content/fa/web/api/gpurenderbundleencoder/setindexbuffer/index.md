---
title: "GPURenderBundleEncoder: setIndexBuffer() method"
short-title: setIndexBuffer()
slug: Web/API/GPURenderBundleEncoder/setIndexBuffer
page-type: web-api-instance-method
browser-compat: api.GPURenderBundleEncoder.setIndexBuffer
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`setIndexBuffer()`** از واسط {{domxref("GPURenderBundleEncoder")}}، بافر جاری {{domxref("GPUBuffer")}} را تنظیم می‌کند که داده‌های شاخص را برای دستورات ترسیم بعدی فراهم می‌کند.

> [!NOTE]
> این متد از نظر عملکردی با معادل خود در {{domxref("GPURenderPassEncoder")}} یعنی {{domxref("GPURenderPassEncoder.setIndexBuffer", "setIndexBuffer()")}} یکسان است.

## نحو

```js-nolint
setIndexBuffer(buffer, indexFormat, offset, size)
```

### پارامترها

- `buffer`
  - : یک {{domxref("GPUBuffer")}} که بافر حاوی داده‌های شاخص برای استفاده در دستورات ترسیم بعدی را نشان می‌دهد.
- `indexFormat`
  - : یک مقدار شمارشی که قالب داده‌های شاخص موجود در `buffer` را تعریف می‌کند. مقادیر ممکن عبارتند از:
    - `"uint16"`
    - `"uint32"`
- `offset` {{optional_inline}}
  - : عددی که نشان‌دهنده افست (بر حسب بایت) درون `buffer` است که داده‌های شاخص از آنجا شروع می‌شود. اگر حذف شود، `offset` به طور پیش‌فرض 0 است.
- `size` {{optional_inline}}
  - : عددی که نشان‌دهنده اندازه (بر حسب بایت) داده‌های شاخص موجود در `buffer` است. اگر حذف شود، `size` به طور پیش‌فرض برابر با `buffer`'s {{domxref("GPUBuffer.size")}} - `offset` است.

#### نکته‌ای در مورد indexFormat

`indexFormat` هم نوع داده مقادیر شاخص در یک بافر را تعیین می‌کند و هم، هنگامی که با یک پایپ‌لاین که توپولوژی اولیه نواری (مانند `"line-strip"` یا `"triangle-strip"`) را مشخص می‌کند استفاده شود، مقدار restart اولیه را نیز تعیین می‌کند. مقدار restart اولیه یک مقدار شاخص است که نشان می‌دهد یک اولیه جدید باید شروع شود، نه اینکه ساخت نوار با رئوس شاخص‌گذاری شده قبلی ادامه یابد. این مقدار برای `"uint16"` برابر با `0xFFFF` و برای `"uint32"` برابر با `0xFFFFFFFF` است.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### اعتبارسنجی

معیارهای زیر باید هنگام فراخوانی **`setIndexBuffer()`** رعایت شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} تولید می‌شود و {{domxref("GPURenderBundleEncoder")}} نامعتبر می‌شود:

- `buffer`'s {{domxref("GPUBuffer.usage")}} شامل پرچم `GPUBufferUsage.INDEX` باشد.
- `offset` + `size` کمتر یا مساوی `buffer`'s {{domxref("GPUBuffer.size")}} باشد.
- `offset` مضربی از اندازه بایت `indexFormat` باشد (2 برای `"uint16"`، 4 برای `"uint32"`).

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

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)