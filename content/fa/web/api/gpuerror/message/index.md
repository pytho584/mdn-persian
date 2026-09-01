---
title: "GPUError: message property"
---

---
title: "GPUError: message property"
short-title: message
slug: Web/API/GPUError/message
page-type: web-api-instance-property
browser-compat: api.GPUError.message
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقطخواندنی **`message`** در رابط {{domxref("GPUError")}} پیامی قابلخواندن برای انسان فراهم میکند که دلیل وقوع خطا را توضیح میدهد.

## مقدار

یک رشته.

## مثالها

برای مثال‌های کاربرد آبجکت‌های خطا بر اساس `GPUError`، به موارد زیر مراجعه کنید:

- [`GPUDevice.popErrorScope`](/en-US/docs/Web/API/GPUDevice/popErrorScope#examples)
- [The `GPUDevice uncapturederror` event](/en-US/docs/Web/API/GPUDevice/uncapturederror_event#examples)
- {{domxref("GPUInternalError")}}، {{domxref("GPUOutOfMemoryError")}}، و {{domxref("GPUValidationError")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- The [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
- [WebGPU Error Handling best practices](https://toji.dev/webgpu-best-practices/error-handling)