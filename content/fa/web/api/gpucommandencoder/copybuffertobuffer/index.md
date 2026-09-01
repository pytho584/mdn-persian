---
title: "GPUCommandEncoder: copyBufferToBuffer() method"
short-title: copyBufferToBuffer()
slug: Web/API/GPUCommandEncoder/copyBufferToBuffer
page-type: web-api-instance-method
browser-compat: api.GPUCommandEncoder.copyBufferToBuffer
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}

متد **`copyBufferToBuffer()`** از رابط {{domxref("GPUCommandEncoder")}} دستوری را کدگذاری می‌کند که داده‌ها را از یک {{domxref("GPUBuffer")}} به GPUBuffer دیگری کپی می‌کند.

## سینتکس

```js-nolint
copyBufferToBuffer(source, destination)
copyBufferToBuffer(source, destination, size)
copyBufferToBuffer(source, sourceOffset, destination, destinationOffset, size)
```

### پارامترها

- `source`
  - : {{domxref("GPUBuffer")}} مبدأ که داده‌ها از آن کپی می‌شوند.
- `sourceOffset` {{optional_inline}}
  - : افست بر حسب بایت در `source` که کپی از آن آغاز می‌شود.
- `destination`
  - : {{domxref("GPUBuffer")}} مقصد که داده‌ها به آن کپی می‌شوند.
- `destinationOffset` {{optional_inline}}
  - : افست بر حسب بایت در `destination` که کپی به آن آغاز می‌شود.
- `size` {{optional_inline}}
  - : تعداد بایت‌هایی که باید کپی شوند.

> [!NOTE]
> اگر در حال کپی کردن بخشی از بافر مبدأ با افست صفر در هر دو بافر مبدأ و مقصد هستید، می‌توانید `sourceOffset` و `destinationOffset` را حذف کنید. اگر کل بافر مبدأ را به بافر مقصد کپی می‌کنید، می‌توانید `sourceOffset`، `destinationOffset` و `size` را حذف کنید.

### مقدار بازگشتی

هیچ مقداری ({{jsxref("undefined")}}).

### اعتبارسنجی

هنگام فراخوانی **`copyBufferToBuffer()`** باید معیارهای زیر برقرار باشند؛ در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و {{domxref("GPUCommandEncoder")}} نامعتبر می‌شود:

- {{domxref("GPUBuffer.usage")}} مربوط به `source` شامل پرچم `GPUBufferUsage.COPY_SRC` باشد.
- {{domxref("GPUBuffer.usage")}} مربوط به `destination` شامل پرچم `GPUBufferUsage.COPY_DST` باشد.
- `size`، `sourceOffset` و `destinationOffset` همگی مضربی از ۴ باشند.
- {{domxref("GPUBuffer.size")}} مربوط به `source` بزرگ‌تر یا مساوی `sourceOffset` + `size` باشد.
- {{domxref("GPUBuffer.size")}} مربوط به `destination` بزرگ‌تر یا مساوی `destinationOffset` + `size` باشد.
- `source` و `destination` دو {{domxref("GPUBuffer")}} متفاوت باشند (نمی‌توان از یک بافر به همان بافر کپی کرد).

## مثال‌ها

در [نمونه محاسبات پایه](https://mdn.github.io/dom-examples/webgpu-compute-demo/)، از `copyBufferToBuffer()` برای کپی کردن محتویات `outputBuffer` به `stagingBuffer` استفاده می‌کنیم.

```js
// …

// Create an output buffer to read GPU calculations to, and a staging buffer to be mapped for JavaScript access

const outputBuffer = device.createBuffer({
  size: BUFFER_SIZE,
  usage: GPUBufferUsage.STORAGE | GPUBufferUsage.COPY_SRC,
});

const stagingBuffer = device.createBuffer({
  size: BUFFER_SIZE,
  usage: GPUBufferUsage.MAP_READ | GPUBufferUsage.COPY_DST,
});

// …

// Create GPUCommandEncoder to encode commands to issue to the GPU
const commandEncoder = device.createCommandEncoder();

// …

// Copy output buffer to staging buffer
commandEncoder.copyBufferToBuffer(
  outputBuffer,
  0, // Source offset
  stagingBuffer,
  0, // Destination offset
  BUFFER_SIZE,
);

// Since we are copying the entire buffer, this can be shortened to
// commandEncoder.copyBufferToBuffer(outputBuffer, stagingBuffer);

// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)