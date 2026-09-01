---
title: "GPURenderBundleEncoder: pushDebugGroup() method"
short-title: pushDebugGroup()
slug: Web/API/GPURenderBundleEncoder/pushDebugGroup
page-type: web-api-instance-method
browser-compat: api.GPURenderBundleEncoder.pushDebugGroup
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`pushDebugGroup()`** از رابط {{domxref("GPURenderBundleEncoder")}} یک گروه اشکال‌زدایی (debug group) برای بسته رندر (render bundle) آغاز می‌کند. این گروه با یک برچسب مشخص مشخص می‌شود و تمام دستورات رمزگذاری شده بعدی را تا زمانی که متد {{domxref("GPURenderBundleEncoder.popDebugGroup", "popDebugGroup()")}} فراخوانی شود، در بر می‌گیرد.

این قابلیت می‌تواند برای تله‌متری (telemetry) استفاده شود، یا در آینده در پیام‌های {{domxref("GPUError")}}، ابزارهای توسعه‌دهنده مرورگر، یا سایر سرویس‌ها برای کمک به اشکال‌زدایی به کار رود.

> [!NOTE]
> این متد از نظر عملکردی با معادل خود در {{domxref("GPURenderPassEncoder")}} یعنی {{domxref("GPURenderPassEncoder.pushDebugGroup", "pushDebugGroup()")}} یکسان است.

## Syntax

```js-nolint
pushDebugGroup(groupLabel)
```

### پارامترها

- `groupLabel`
  - : یک رشته که برچسب گروه اشکال‌زدایی را مشخص می‌کند.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

```js
// ...

const bundleEncoder = device.createRenderBundleEncoder(renderBundleDescriptor);

bundleEncoder.pushDebugGroup("my_group_marker"); // شروع گروه اشکال‌زدایی با برچسب

bundleEncoder.setPipeline(renderPipeline);
bundleEncoder.setVertexBuffer(0, vertexBuffer);
bundleEncoder.draw(3);

bundleEncoder.popDebugGroup();

// ...
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)