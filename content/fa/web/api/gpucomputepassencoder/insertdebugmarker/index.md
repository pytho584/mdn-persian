---
title: "GPUComputePassEncoder: insertDebugMarker() method"
---

---
title: "GPUComputePassEncoder: insertDebugMarker() method"
short-title: insertDebugMarker()
slug: Web/API/GPUComputePassEncoder/insertDebugMarker
page-type: web-api-instance-method
browser-compat: api.GPUComputePassEncoder.insertDebugMarker
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`insertDebugMarker()`** از رابط {{domxref("GPUComputePassEncoder")}} یک نقطهٔ مشخص را در مجموعه‌ای از دستورات کدگذاری‌شدهٔ پاس محاسباتی با یک برچسب علامت‌گذاری می‌کند.

این کار می‌تواند برای دورسنجی (تله‌متری) استفاده شود، یا در پیام‌های {{domxref("GPUError")}}، ابزارهای توسعه‌دهندهٔ مرورگر، یا سایر سرویس‌ها در آینده برای کمک به اشکال‌زدایی به کار گرفته شود.

## سینتکس

```js-nolint
insertDebugMarker(markerLabel)
```

### پارامترها

- `markerLabel`
  - : رشته‌ای است که برچسب موردنظر برای درج را نشان می‌دهد.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
// …

passEncoder.insertDebugMarker("my_marker");

// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [رابط برنامه‌نویسی WebGPU](/en-US/docs/Web/API/WebGPU_API)