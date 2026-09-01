---
title: "GPUCommandEncoder: clearBuffer() method"
short-title: clearBuffer()
slug: Web/API/GPUCommandEncoder/clearBuffer
page-type: web-api-instance-method
browser-compat: api.GPUCommandEncoder.clearBuffer
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`clearBuffer()`** از رابط {{domxref("GPUCommandEncoder")}} دستوری را کدگذاری می‌کند که ناحیه‌ای از یک {{domxref("GPUBuffer")}} را با صفر پر می‌کند.

## نحو

```js-nolint
clearBuffer(buffer)
clearBuffer(buffer, offset)
clearBuffer(buffer, offset, size)
```

### پارامترها

- `buffer`
  - : یک شیء {{domxref("GPUBuffer")}} که نمایانگر بافر مورد نظر برای پاک کردن است.
- `offset` {{optional_inline}}
  - : عددی که نشان‌دهندهٔ offset (به بایت) از ابتدای `buffer` تا زیرناحیه‌ای است که باید پاک شود. اگر حذف شود، `offset` به طور پیش‌فرض ۰ است.
- `size` {{optional_inline}}
  - : عددی که نشان‌دهندهٔ اندازه (به بایت) زیرناحیه‌ای است که باید پاک شود. اگر حذف شود، `size` به طور پیش‌فرض برابر `buffer` size - `offset` است.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### اعتبارسنجی

هنگام فراخوانی **`clearBuffer()`** معیارهای زیر باید رعایت شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و {{domxref("GPUCommandEncoder")}} نامعتبر می‌شود:

- پرچم `GPUBufferUsage.COPY_DST` در {{domxref("GPUBuffer.usage")}} مربوط به `buffer` وجود داشته باشد.
- `offset` و `size` هر دو مضرب ۴ باشند.
- {{domxref("GPUBuffer.size")}} مربوط به `buffer` بزرگتر یا مساوی `offset + size` باشد.

## مثال‌ها

```js
// …

const buffer = device.createBuffer({
  size: 1000,
  usage: GPUBufferUsage.MAP_READ | GPUBufferUsage.COPY_DST,
});

// بعداً

const commandBuffer = device.createCommandEncoder();
commandEncoder.clearBuffer(buffer);

// …
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [API WebGPU](/en-US/docs/Web/API/WebGPU_API)