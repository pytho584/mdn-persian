---
title: "GPURenderPassEncoder: insertDebugMarker() method"
short-title: insertDebugMarker()
slug: Web/API/GPURenderPassEncoder/insertDebugMarker
page-type: web-api-instance-method
browser-compat: api.GPURenderPassEncoder.insertDebugMarker
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`insertDebugMarker()`** از رابط {{domxref("GPURenderPassEncoder")}} یک نقطهٔ خاص را در یک سری از دستورهای رمزگذاری‌شدهٔ پاس رندر با یک برچسب علامت‌گذاری می‌کند.

این می‌تواند برای سنجش از راه دور (telemetry) استفاده شود، یا ممکن است در پیام‌های {{domxref("GPUError")}}، ابزارهای توسعه‌دهندهٔ مرورگر، یا سایر سرویس‌ها در آینده برای کمک به اشکال‌زدایی به کار رود.

## Syntax

```js-nolint
insertDebugMarker(markerLabel)
```

### Parameters

- `markerLabel`
  - : یک رشته که برچسب مورد نظر برای درج را نشان می‌دهد.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

## Examples

```js
// …

passEncoder.insertDebugMarker("my_marker");

// …
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)