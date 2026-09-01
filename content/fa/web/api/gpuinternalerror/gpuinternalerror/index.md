---
title: "GPUInternalError: GPUInternalError() constructor"
short-title: GPUInternalError()
slug: Web/API/GPUInternalError/GPUInternalError
page-type: web-api-constructor
browser-compat: api.GPUInternalError.GPUInternalError
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

سازندهٔ **`GPUInternalError()`** یک نمونهٔ شیء جدید از {{domxref("GPUInternalError")}} ایجاد می‌کند.

## سینتکس

```js-nolint
new GPUInternalError(message)
```

### پارامترها

- `message`
  - : رشته‌ای که یک پیام قابل فهم برای انسان فراهم می‌کند و دلیل رخ دادن خطا را توضیح می‌دهد.

## مثال‌ها

یک توسعه‌دهنده معمولاً به‌صورت دستی از این سازنده برای ایجاد یک شیء `GPUInternalError` استفاده نمی‌کند. عامل کاربر (user agent) از این سازنده برای ایجاد شیء مناسب استفاده می‌کند، زمانی که یک خطای داخلی توسط {{domxref("GPUDevice.popErrorScope")}} یا رویداد {{domxref("GPUDevice.uncapturederror_event", "uncapturederror")}} نمایان می‌شود.

برای نمونه‌ای که شامل یک نمونهٔ شیء `GPUInternalError` است، به صفحهٔ اصلی [`GPUInternalError`](/en-US/docs/Web/API/GPUInternalError#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
- [WebGPU Error Handling best practices](https://toji.dev/webgpu-best-practices/error-handling)