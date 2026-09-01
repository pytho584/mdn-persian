---
title: GPUOutOfMemoryError
slug: Web/API/GPUOutOfMemoryError
page-type: web-api-interface
browser-compat: api.GPUOutOfMemoryError
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`GPUOutOfMemoryError`** از {{domxref("WebGPU API", "WebGPU API", "", "nocode")}}، یک خطای کمبود حافظه (OOM) را توصیف می‌کند که نشان می‌دهد حافظه آزاد کافی برای تکمیل عملیات درخواستی وجود نداشته است.

این رابط یکی از انواع خطاهایی است که توسط {{domxref("GPUDevice.popErrorScope")}} و رویداد {{domxref("GPUDevice.uncapturederror_event", "uncapturederror")}} گزارش می‌شوند.

خطاهای کمبود حافظه در یک برنامه‌ی خوش‌رفتار باید نسبتاً نادر باشند، اما نسبت به خطاهای {{domxref("GPUValidationError")}} کمتر قابل پیش‌بینی هستند. دلیل این امر آن است که این خطاها به دستگاهی که برنامه‌ی شما روی آن اجرا می‌شود و همچنین به سایر برنامه‌هایی که در آن زمان از منابع GPU استفاده می‌کنند بستگی دارند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("GPUOutOfMemoryError.GPUOutOfMemoryError", "GPUOutOfMemoryError()")}}
  - : یک نمونه جدید از شیء `GPUOutOfMemoryError` ایجاد می‌کند.

## ویژگی‌های نمونه

ویژگی `message` از والد خود، یعنی {{domxref("GPUError")}}، به ارث رسیده است:

- {{domxref("GPUError.message", "message")}} {{Experimental_Inline}} {{ReadOnlyInline}}
  - : یک رشته که پیامی قابل‌فهم برای انسان ارائه می‌دهد و دلیل رخ دادن خطا را توضیح می‌دهد.

## مثال‌ها

مثال زیر از یک حوزه خطا (error scope) برای دریافت یک خطای کمبود حافظه استفاده می‌کند و آن را در کنسول ثبت می‌کند.

```js
device.pushErrorScope("out-of-memory");

let buffer = device.createBuffer({
  size: 100_000_000_000, // 100GB; far too big
  usage: GPUBufferUsage.COPY_SRC | GPUBufferUsage.MAP_WRITE,
});

device.popErrorScope().then((error) => {
  if (error) {
    // error is a GPUOutOfMemoryError object instance
    buffer = null;
    console.error(`Out of memory, buffer too large. Error: ${error.message}`);
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
- [بهترین روش‌های مدیریت خطا در WebGPU](https://toji.dev/webgpu-best-practices/error-handling)
```