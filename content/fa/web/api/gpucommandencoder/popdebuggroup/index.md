---
title: "GPUCommandEncoder: popDebugGroup() method"
---

---
title: "GPUCommandEncoder: popDebugGroup() method"
short-title: popDebugGroup()
slug: Web/API/GPUCommandEncoder/popDebugGroup
page-type: web-api-instance-method
browser-compat: api.GPUCommandEncoder.popDebugGroup
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`popDebugGroup()`** از رابط {{domxref("GPUCommandEncoder")}} یک گروه اشکال‌زدایی (debug group) را پایان می‌دهد که با فراخوانی {{domxref("GPUCommandEncoder.pushDebugGroup", "pushDebugGroup()")}} شروع شده است.

این قابلیت می‌تواند برای تله‌متری استفاده شود، یا ممکن است در پیام‌های {{domxref("GPUError")}}، ابزارهای توسعه‌دهنده مرورگر، یا سایر سرویس‌ها در آینده برای کمک به اشکال‌زدایی به کار رود.

## سینتکس

```js-nolint
popDebugGroup()
```

### پارامترها

هیچ پارامتری.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### اعتبارسنجی

هنگام فراخوانی **`popDebugGroup()`** معیارهای زیر باید برآورده شوند؛ در غیر این صورت یک {{domxref("GPUValidationError")}} تولید می‌شود و {{domxref("GPUCommandEncoder")}} نامعتبر می‌شود:

- پشته اشکال‌زدایی (debug stack) رمزگذار فرمان خالی نیست (یعنی حداقل یک گروه اشکال‌زدایی قبلاً با {{domxref("GPUCommandEncoder.pushDebugGroup", "pushDebugGroup()")}} شروع شده است).

## مثال‌ها

```js
// …

commandEncoder.pushDebugGroup("my_group_marker"); // Start labeled debug group

const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);

passEncoder.setPipeline(renderPipeline);
passEncoder.setVertexBuffer(0, vertexBuffer);
passEncoder.draw(3);

passEncoder.end();

commandEncoder.popDebugGroup(); // End labeled debug group

// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)