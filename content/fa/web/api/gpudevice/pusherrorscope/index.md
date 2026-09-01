---
title: "GPUDevice: pushErrorScope() method"
short-title: pushErrorScope()
slug: Web/API/GPUDevice/pushErrorScope
page-type: web-api-instance-method
browser-compat: api.GPUDevice.pushErrorScope
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`pushErrorScope()`** از رابط {{domxref("GPUDevice")}} یک دامنه خطای GPU جدید را به پشته دامنه خطای دستگاه اضافه می‌کند و به شما امکان می‌دهد خطاهای یک نوع خاص را دریافت کنید.

پس از اتمام دریافت خطاها، می‌توانید با فراخوانی {{domxref("GPUDevice.popErrorScope()")}} به دریافت پایان دهید. این کار دامنه را از پشته حذف می‌کند و یک {{jsxref("Promise")}} برمی‌گرداند که به یک شیء حاوی توضیح اولین خطای دریافت‌شده در آن دامنه، یا `null` در صورت عدم دریافت خطا، تبدیل می‌شود.

## نحو

```js-nolint
pushErrorScope(filter)
```

### پارامترها

- `filter`
  - : یک مقدار شمارشی که نوع خطایی را که در این دامنه خطای خاص دریافت می‌شود مشخص می‌کند. مقادیر ممکن عبارتند از:
    - `"internal"`
      - : دامنه خطا یک {{domxref("GPUInternalError")}} را دریافت می‌کند.
    - `"out-of-memory"`
      - : دامنه خطا یک {{domxref("GPUOutOfMemoryError")}} را دریافت می‌کند.
    - `"validation"`
      - : دامنه خطا یک {{domxref("GPUValidationError")}} را دریافت می‌کند.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

مثال زیر از یک دامنه خطا برای دریافت یک خطای اعتبارسنجی مشکوک استفاده می‌کند و آن را در کنسول ثبت می‌کند.

```js
device.pushErrorScope("validation");

let sampler = device.createSampler({
  maxAnisotropy: 0, // Invalid, maxAnisotropy must be at least 1.
});

device.popErrorScope().then((error) => {
  if (error) {
    sampler = null;
    console.error(`An error occurred while creating sampler: ${error.message}`);
  }
});
```

برای مثال‌ها و اطلاعات بیشتر به [بهترین روش‌های مدیریت خطای WebGPU](https://toji.dev/webgpu-best-practices/error-handling) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)