---
title: "GPUComputePassEncoder: popDebugGroup() method"
short-title: popDebugGroup()
slug: Web/API/GPUComputePassEncoder/popDebugGroup
page-type: web-api-instance-method
browser-compat: api.GPUComputePassEncoder.popDebugGroup
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`popDebugGroup()`** در رابط {{domxref("GPUComputePassEncoder")}} یک گروه اشکال‌زدایی پاس محاسباتی را پایان می‌دهد؛ گروهی که با یک فراخوانی {{domxref("GPUComputePassEncoder.pushDebugGroup", "pushDebugGroup()")}} آغاز شده است.

این می‌تواند برای تله‌متری استفاده شود، یا ممکن است در پیام‌های {{domxref("GPUError")}}، ابزارهای توسعه‌دهندگان مرورگر، یا سایر سرویس‌ها در آینده برای کمک به اشکال‌زدایی به کار رود.

## سینتکس

```js-nolint
popDebugGroup()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### اعتبارسنجی

هنگام فراخوانی **`popDebugGroup()`**، معیارهای زیر باید برقرار باشند؛ در غیر این صورت یک {{domxref("GPUValidationError")}} تولید می‌شود و {{domxref("GPUComputePassEncoder")}} نامعتبر می‌شود:

- پشته اشکال‌زدایی انکودر پاس محاسباتی خالی نباشد (یعنی حداقل یک گروه اشکال‌زدایی پاس محاسباتی قبلاً با {{domxref("GPUComputePassEncoder.pushDebugGroup", "pushDebugGroup()")}} شروع شده باشد).

## مثال‌ها

```js
// …

const passEncoder = commandEncoder.beginComputePass();

passEncoder.pushDebugGroup("my_group_marker"); // Start labeled debug group

passEncoder.setPipeline(computePipeline);
passEncoder.setBindGroup(0, bindGroup);
passEncoder.dispatchWorkgroups(Math.ceil(BUFFER_SIZE / 64));

passEncoder.popDebugGroup();

// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)