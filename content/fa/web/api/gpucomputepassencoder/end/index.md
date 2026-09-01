---
title: "GPUComputePassEncoder: end() method"
short-title: end()
slug: Web/API/GPUComputePassEncoder/end
page-type: web-api-instance-method
browser-compat: api.GPUComputePassEncoder.end
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`end()`** در رابط {{domxref("GPUComputePassEncoder")}} ضبط دنباله دستوراتِ پاس محاسباتی جاری را تکمیل می‌کند.

## نحو (Syntax)

```js-nolint
end()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### اعتبارسنجی

هنگام فراخوانی **`end()`** معیارهای زیر باید برآورده شوند؛ در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و {{domxref("GPUComputePassEncoder")}} نامعتبر می‌شود:

- {{domxref("GPUComputePassEncoder")}} باز باشد (یعنی قبلاً با یک فراخوانی `end()` پایان نیافته باشد).
- هر فراخوانی {{domxref("GPUComputePassEncoder.pushDebugGroup", "pushDebugGroup()")}} که روی این انکودر انجام شده باشد، پیش از فراخوانی `end()` یک فراخوانی متناظر {{domxref("GPUComputePassEncoder.popDebugGroup", "popDebugGroup()")}} داشته باشد.

## مثال‌ها

در [نمونه محاسبات پایه](https://mdn.github.io/dom-examples/webgpu-compute-demo/)، چندین دستور از طریق یک {{domxref("GPUCommandEncoder")}} ضبط می‌شوند. بیشتر این دستورها از {{domxref("GPUComputePassEncoder")}} می‌آیند که از طریق {{domxref("GPUCommandEncoder.beginComputePass()")}} ساخته شده است.

```js
const BUFFER_SIZE = 1000;

// …

// ساخت GPUCommandEncoder برای رمزگذاری دستورهایی که به GPU ارسال می‌شوند
const commandEncoder = device.createCommandEncoder();

// شروع پاس محاسباتی
const passEncoder = commandEncoder.beginComputePass();

// صدور دستورها
passEncoder.setPipeline(computePipeline);
passEncoder.setBindGroup(0, bindGroup);
passEncoder.dispatchWorkgroups(Math.ceil(BUFFER_SIZE / 64));

// پایان دادن به پاس رندر
passEncoder.end();

// کپی کردن بافر خروجی به بافر موقت
commandEncoder.copyBufferToBuffer(
  output,
  0, // آفست مبدأ
  stagingBuffer,
  0, // آفست مقصد
  BUFFER_SIZE,
);

// پایان فریم با ارسال آرایه‌ای از بافرهای فرمان به صف فرمان برای اجرا
device.queue.submit([commandEncoder.finish()]);

// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)