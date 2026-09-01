---
title: "GPURenderBundleEncoder: insertDebugMarker() method"
short-title: insertDebugMarker()
slug: Web/API/GPURenderBundleEncoder/insertDebugMarker
page-type: web-api-instance-method
browser-compat: api.GPURenderBundleEncoder.insertDebugMarker
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`insertDebugMarker()`** از رابط {{domxref("GPURenderBundleEncoder")}} نقطهٔ مشخصی را در مجموعه‌ای از دستورات رمزگذاری‌شدهٔ پاس رندر باند (render bundle pass) با یک برچسب علامت‌گذاری می‌کند.

این می‌تواند برای تله‌متری (telemetry) استفاده شود، یا ممکن است در پیام‌های {{domxref("GPUError")}}، ابزارهای توسعه‌دهندهٔ مرورگر، یا سایر سرویس‌ها در آینده برای کمک به اشکال‌زدایی به کار رود.

> [!NOTE]
> این روش از نظر عملکردی با معادل آن در {{domxref("GPURenderPassEncoder")}} — {{domxref("GPURenderPassEncoder.InsertDebugMarker", "InsertDebugMarker()")}} یکسان است.

## Syntax

```js-nolint
insertDebugMarker(markerLabel)
```

### Parameters

- `markerLabel`
  - : رشته‌ای که برچسب مورد نظر برای درج را نشان می‌دهد.

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

```js
// …

bundleEncoder.insertDebugMarker("my_marker");

// …
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- The [WebGPU API](/en-US/docs/Web/API/WebGPU_API)