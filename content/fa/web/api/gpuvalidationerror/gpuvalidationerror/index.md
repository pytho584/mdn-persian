---
title: "GPUValidationError: GPUValidationError() constructor"
---

---
title: "GPUValidationError: GPUValidationError() constructor"
short-title: GPUValidationError()
slug: Web/API/GPUValidationError/GPUValidationError
page-type: web-api-constructor
browser-compat: api.GPUValidationError.GPUValidationError
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

سازندهٔ **`GPUValidationError()`** یک نمونهٔ جدید از شیء {{domxref("GPUValidationError")}} ایجاد می‌کند.

## سینتکس

```js-nolint
new GPUValidationError(message)
```

### پارامترها

- `message`
  - : رشته‌ای که پیامی قابل‌خواندن برای انسان فراهم می‌کند و دلیل رخ دادن خطا را توضیح می‌دهد.

## مثال‌ها

یک توسعه‌دهنده به‌صورت دستی از این سازنده برای ایجاد یک شیء `GPUValidationError` استفاده نمی‌کند. عامل کاربر (user agent) هنگام بروز خطای اعتبارسنجی، از این سازنده برای ایجاد شیء مناسب استفاده می‌کند؛ این خطا از طریق {{domxref("GPUDevice.popErrorScope")}} یا رویداد {{domxref("GPUDevice.uncapturederror_event", "uncapturederror")}} نمایان می‌شود.

برای نمونه‌ای خاص که شامل یک نمونهٔ شیء `GPUValidationError` است، به صفحهٔ اصلی [`GPUValidationError`](/en-US/docs/Web/API/GPUValidationError#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
- [بهترین روش‌های مدیریت خطا در WebGPU](https://toji.dev/webgpu-best-practices/error-handling)