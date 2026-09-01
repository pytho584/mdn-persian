---
title: "GPUUncapturedErrorEvent: GPUUncapturedErrorEvent() سازنده"
short-title: GPUUncapturedErrorEvent()
slug: Web/API/GPUUncapturedErrorEvent/GPUUncapturedErrorEvent
page-type: web-api-constructor
browser-compat: api.GPUUncapturedErrorEvent.GPUUncapturedErrorEvent
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

سازنده **`GPUUncapturedErrorEvent()`** یک نمونه جدید از شیء {{domxref("GPUUncapturedErrorEvent")}} ایجاد می‌کند.

## نحو

```js-nolint
new GPUUncapturedErrorEvent(type, options)
```

### پارامترها

- `type`
  - : یک مقدار شمارشی که نوع خطا را مشخص می‌کند. مقادیر ممکن عبارتند از:
    - `"internal"`
      - : خطا از نوع {{domxref("GPUInternalError")}} است.
    - `"out-of-memory"`
      - : خطا از نوع {{domxref("GPUOutOfMemoryError")}} است.
    - `"validation"`
      - : خطا از نوع {{domxref("GPUValidationError")}} است.
- `options`
  - : یک شیء که می‌تواند شامل ویژگی‌های زیر باشد:
    - `error`
      - : یک نمونه از شیء {{domxref("GPUError")}} که دسترسی به جزئیات خطا را فراهم می‌کند.

## مثال‌ها

یک توسعه‌دهنده به‌صورت دستی از سازنده برای ایجاد یک شیء `GPUUncapturedErrorEvent` استفاده نمی‌کند. عامل کاربر (user agent) از این سازنده برای ایجاد یک شیء مناسب زمانی که رویداد {{domxref("GPUDevice")}} {{domxref("GPUDevice.uncapturederror_event", "uncapturederror")}} فعال می‌شود استفاده می‌کند تا امکان ضبط یک خطای غیرمنتظره فراهم شود.

برای یک مثال به صفحه اصلی [`GPUUncapturedErrorEvent`](/en-US/docs/Web/API/GPUUncapturedErrorEvent#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
- [بهترین روش‌های مدیریت خطا در WebGPU](https://toji.dev/webgpu-best-practices/error-handling)