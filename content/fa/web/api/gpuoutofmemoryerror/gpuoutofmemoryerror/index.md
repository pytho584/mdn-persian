---
title: "GPUOutOfMemoryError: GPUOutOfMemoryError() constructor"
short-title: GPUOutOfMemoryError()
slug: Web/API/GPUOutOfMemoryError/GPUOutOfMemoryError
page-type: web-api-constructor
browser-compat: api.GPUOutOfMemoryError.GPUOutOfMemoryError
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

سازندهٔ **`GPUOutOfMemoryError()`** یک نمونهٔ جدید از شیء {{domxref("GPUOutOfMemoryError")}} می‌سازد.

## Syntax

```js-nolint
new GPUOutOfMemoryError(message)
```

### پارامترها

- `message`
  - : رشته‌ای که پیامی قابل‌خواندن برای انسان ارائه می‌دهد و دلیل بروز خطا را توضیح می‌دهد.

## مثال‌ها

یک توسعه‌دهنده معمولاً به‌صورت دستی از سازنده برای ایجاد یک شیء `GPUOutOfMemoryError` استفاده نمی‌کند. عامل کاربر (user agent) از این سازنده برای ایجاد شیء مناسب زمانی استفاده می‌کند که خطای کمبود حافظه توسط {{domxref("GPUDevice.popErrorScope")}} یا رویداد {{domxref("GPUDevice.uncapturederror_event", "uncapturederror")}} نمایان شود.

برای یک مثال خاص که شامل یک نمونهٔ شیء `GPUOutOfMemoryError` است، به صفحهٔ اصلی [`GPUOutOfMemoryError`](/en-US/docs/Web/API/GPUOutOfMemoryError#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
- [بهترین روش‌های مدیریت خطا در WebGPU](https://toji.dev/webgpu-best-practices/error-handling)