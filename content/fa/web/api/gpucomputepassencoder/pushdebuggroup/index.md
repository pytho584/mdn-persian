---
title: "GPUComputePassEncoder: pushDebugGroup() method"
short-title: pushDebugGroup()
slug: Web/API/GPUComputePassEncoder/pushDebugGroup
page-type: web-api-instance-method
browser-compat: api.GPUComputePassEncoder.pushDebugGroup
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`pushDebugGroup()`** از رابط {{domxref("GPUComputePassEncoder")}} یک گروه اشکال‌زدایی (debug group) برای عبور محاسباتی (compute pass) آغاز می‌کند که با یک برچسب مشخص مشخص می‌شود و تمام دستورات رمزگذاری شده بعدی را تا زمانی که متد {{domxref("GPUComputePassEncoder.popDebugGroup", "popDebugGroup()")}} فراخوانی شود، در خود جای می‌دهد.

این می‌تواند برای تله‌متری (telemetry) استفاده شود، یا ممکن است در پیام‌های {{domxref("GPUError")}}، ابزارهای توسعه‌دهنده مرورگر، یا سایر سرویس‌ها در آینده برای کمک به اشکال‌زدایی به کار گرفته شود.

## Syntax

```js-nolint
pushDebugGroup(groupLabel)
```

### Parameters

- `groupLabel`
  - : یک رشته که برچسب گروه اشکال‌زدایی را مشخص می‌کند.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

## Examples

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

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- The [WebGPU API](/en-US/docs/Web/API/WebGPU_API)