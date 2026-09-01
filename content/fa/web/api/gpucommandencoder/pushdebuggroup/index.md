---
title: "GPUCommandEncoder: pushDebugGroup() method"
short-title: pushDebugGroup()
slug: Web/API/GPUCommandEncoder/pushDebugGroup
page-type: web-api-instance-method
browser-compat: api.GPUCommandEncoder.pushDebugGroup
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`pushDebugGroup()`** از رابط {{domxref("GPUCommandEncoder")}} یک گروه اشکال‌زدایی را شروع می‌کند که با یک برچسب مشخص علامت‌گذاری می‌شود و تمام دستورات رمزگذاری‌شدهٔ بعدی را تا زمانی که متد {{domxref("GPUCommandEncoder.popDebugGroup", "popDebugGroup()")}} فراخوانی شود، در بر می‌گیرد.

این می‌تواند برای تله‌متری استفاده شود، یا ممکن است در پیام‌های {{domxref("GPUError")}}، ابزارهای توسعه‌دهندهٔ مرورگر، یا سایر سرویس‌ها در آینده برای کمک به اشکال‌زدایی به کار رود.

## نحو

```js-nolint
pushDebugGroup(groupLabel)
```

### پارامترها

- `groupLabel`
  - : یک رشته که برچسب گروه اشکال‌زدایی را نشان می‌دهد.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

```js
// …

commandEncoder.pushDebugGroup("my_group_marker"); // شروع گروه اشکال‌زدایی برچسب‌دار

const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);

passEncoder.setPipeline(renderPipeline);
passEncoder.setVertexBuffer(0, vertexBuffer);
passEncoder.draw(3);

passEncoder.end();

commandEncoder.popDebugGroup(); // پایان گروه اشکال‌زدایی برچسب‌دار

// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)