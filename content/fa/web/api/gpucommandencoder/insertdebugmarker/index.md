---
title: "GPUCommandEncoder: insertDebugMarker() method"
short-title: insertDebugMarker()
slug: Web/API/GPUCommandEncoder/insertDebugMarker
page-type: web-api-instance-method
browser-compat: api.GPUCommandEncoder.insertDebugMarker
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`insertDebugMarker()`** از رابط {{domxref("GPUCommandEncoder")}} یک نقطه خاص در یک سری دستورات رمزگذاری شده را با یک برچسب علامت‌گذاری می‌کند.

این می‌تواند برای مخابره (telemetry) استفاده شود، یا ممکن است در پیام‌های {{domxref("GPUError")}}، ابزارهای توسعه‌دهنده مرورگر، یا سایر سرویس‌ها در آینده برای کمک به اشکال‌زدایی (debugging) به کار رود.

## Syntax

```js-nolint
insertDebugMarker(markerLabel)
```

### Parameters

- `markerLabel`
  - : یک رشته که نشان‌دهنده برچسب برای درج است.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

## Examples

```js
// …

commandEncoder.insertDebugMarker("my_marker");

// …
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)