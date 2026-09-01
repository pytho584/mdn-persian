---
title: GPUError
slug: Web/API/GPUError
page-type: web-api-interface
browser-compat: api.GPUError
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`GPUError`** در {{domxref("WebGPU API", "WebGPU API", "", "nocode")}}، رابط پایه برای خطاهایی است که توسط {{domxref("GPUDevice.popErrorScope")}} و رویداد {{domxref("GPUDevice.uncapturederror_event", "uncapturederror")}} نمایان می‌شوند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("GPUError.message", "message")}} {{ReadOnlyInline}}
  - : رشته‌ای که پیامی قابل‌خواندن برای انسان ارائه می‌دهد و علت بروز خطا را توضیح می‌دهد.

## مثال‌ها

برای نمونه‌های استفاده از اشیاء خطا که بر اساس `GPUError` هستند، به موارد زیر مراجعه کنید:

- [`GPUDevice.popErrorScope`](/en-US/docs/Web/API/GPUDevice/popErrorScope#examples)
- رویداد [`GPUDevice uncapturederror`](/en-US/docs/Web/API/GPUDevice/uncapturederror_event#examples)
- {{domxref("GPUInternalError")}}، {{domxref("GPUOutOfMemoryError")}} و {{domxref("GPUValidationError")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
- [بهترین روش‌های مدیریت خطا در WebGPU](https://toji.dev/webgpu-best-practices/error-handling)