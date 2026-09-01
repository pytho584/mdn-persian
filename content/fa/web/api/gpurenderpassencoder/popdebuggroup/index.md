---
title: "GPURenderPassEncoder: popDebugGroup() method"
short-title: popDebugGroup()
slug: Web/API/GPURenderPassEncoder/popDebugGroup
page-type: web-api-instance-method
browser-compat: api.GPURenderPassEncoder.popDebugGroup
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`popDebugGroup()`** از رابط {{domxref("GPURenderPassEncoder")}} یک گروه اشکال‌زدایی رندر پاس را پایان می‌دهد که با فراخوانی {{domxref("GPURenderPassEncoder.pushDebugGroup", "pushDebugGroup()")}} آغاز شده است.

این قابلیت می‌تواند برای تله‌متری (دورسنجی) استفاده شود، یا ممکن است در پیام‌های {{domxref("GPUError")}}، ابزارهای توسعه‌دهنده مرورگر، یا سایر سرویس‌ها در آینده برای کمک به اشکال‌زدایی به کار رود.

## نحو (Syntax)

```js-nolint
popDebugGroup()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### اعتبارسنجی

هنگام فراخوانی **`popDebugGroup()`** معیارهای زیر باید برآورده شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و {{domxref("GPURenderPassEncoder")}} نامعتبر می‌شود:

- پشته اشکال‌زدایی رمزگذار رندر پاس خالی نباشد (یعنی حداقل یک گروه اشکال‌زدایی رندر پاس قبلاً با {{domxref("GPURenderPassEncoder.pushDebugGroup", "pushDebugGroup()")}} شروع شده باشد).

## مثال‌ها

```js
// …

const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);

passEncoder.pushDebugGroup("my_group_marker"); // شروع گروه اشکال‌زدایی برچسب‌دار

passEncoder.setPipeline(renderPipeline);
passEncoder.setVertexBuffer(0, vertexBuffer);
passEncoder.draw(3);

passEncoder.popDebugGroup();

// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)