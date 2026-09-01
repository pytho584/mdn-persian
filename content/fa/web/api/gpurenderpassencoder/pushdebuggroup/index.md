---
title: "GPURenderPassEncoder: pushDebugGroup() method"
short-title: pushDebugGroup()
slug: Web/API/GPURenderPassEncoder/pushDebugGroup
page-type: web-api-instance-method
browser-compat: api.GPURenderPassEncoder.pushDebugGroup
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`pushDebugGroup()`** از رابط {{domxref("GPURenderPassEncoder")}} یک گروه اشکال‌زدایی رندر پاس را آغاز می‌کند که با برچسب مشخصی علامت‌گذاری می‌شود و تمام دستورات رمزگذاری‌شدهٔ پس از خود را تا زمان فراخوانی متد {{domxref("GPURenderPassEncoder.popDebugGroup", "popDebugGroup()")}} در بر می‌گیرد.

این قابلیت می‌تواند برای تله‌متری استفاده شود، یا ممکن است در پیام‌های {{domxref("GPUError")}}، ابزارهای توسعه‌دهنده مرورگر یا سایر سرویس‌ها در آینده برای کمک به اشکال‌زدایی به کار رود.

## سینتکس

```js-nolint
pushDebugGroup(groupLabel)
```

### پارامترها

- `groupLabel`
  - : یک رشته (string) که برچسب گروه اشکال‌زدایی را نشان می‌دهد.

### مقدار بازگشتی

هیچ مقداری ({{jsxref("undefined")}}).

## مثال‌ها

```js
// …

const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);

passEncoder.pushDebugGroup("my_group_marker"); // Start labeled debug group

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