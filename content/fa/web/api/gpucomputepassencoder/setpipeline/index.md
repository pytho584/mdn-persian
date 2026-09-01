---
title: "GPUComputePassEncoder: setPipeline() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/GPUComputePassEncoder/setPipeline"
---

---
title: "GPUComputePassEncoder: setPipeline() method"
short-title: setPipeline()
slug: Web/API/GPUComputePassEncoder/setPipeline
page-type: web-api-instance-method
browser-compat: api.GPUComputePassEncoder.setPipeline
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`setPipeline()`** از رابط {{domxref("GPUComputePassEncoder")}}، {{domxref("GPUComputePipeline")}} را برای استفاده در این پاس محاسباتی تنظیم می‌کند.

## Syntax

```js-nolint
setPipeline(pipeline)
```

### پارامترها

- `pipeline`
  - : {{domxref("GPUComputePipeline")}} که قرار است برای این پاس محاسباتی استفاده شود.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

در [نمونه محاسباتی پایه ما](https://mdn.github.io/dom-examples/webgpu-compute-demo/)، چندین دستور از طریق یک {{domxref("GPUCommandEncoder")}} ثبت می‌شوند. بیشتر این دستورها از {{domxref("GPUComputePassEncoder")}} که با `beginComputePass()` ایجاد شده است، سرچشمه می‌گیرند. فراخوانی `setPipeline()` در صورت لزوم برای تنظیم پایپ‌لاین استفاده‌شده در این پاس به کار می‌رود.

```js
const BUFFER_SIZE = 1000;

// …

// ایجاد GPUCommandEncoder برای رمزگذاری دستورهایی که به GPU ارسال می‌شوند
const commandEncoder = device.createCommandEncoder();

// شروع پاس محاسباتی
const passEncoder = commandEncoder.beginComputePass();

// ارسال دستورها
passEncoder.setPipeline(computePipeline);
passEncoder.setBindGroup(0, bindGroup);
passEncoder.dispatchWorkgroups(Math.ceil(BUFFER_SIZE / 64));

// پایان پاس رندر
passEncoder.end();

// کپی بافر خروجی به بافر موقت
commandEncoder.copyBufferToBuffer(
  output,
  0, // افست مبدأ
  stagingBuffer,
  0, // افست مقصد
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