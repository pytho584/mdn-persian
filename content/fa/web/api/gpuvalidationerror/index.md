---
title: "GPUValidationError"
---

---
title: GPUValidationError
slug: Web/API/GPUValidationError
page-type: web-api-interface
browser-compat: api.GPUValidationError
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابطهٔ **`GPUValidationError`** در {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} خطایی مربوط به برنامه را توصیف می‌کند که نشان می‌دهد یک عملیات از محدودیت‌های اعتبارسنجی API وب‌GPU عبور نکرده است.

این رابط یکی از انواع خطاهایی است که توسط {{domxref("GPUDevice.popErrorScope")}} و رویداد {{domxref("GPUDevice.uncapturederror_event", "uncapturederror")}} نمایان می‌شود.

خطاهای اعتبارسنجی هر زمان که ورودی‌های نامعتبر به یک فراخوانی WebGPU داده شوند رخ می‌دهند. این خطاها سازگار و قابل پیش‌بینی هستند و تا زمانی که برنامهٔ شما به‌درستی نوشته شده باشد نباید رخ دهند. آن‌ها در هر دستگاهی که کد شما روی آن اجرا می‌شود به همان شکل رخ می‌دهند، بنابراین پس از رفع هر خطایی که در طول توسعه ظاهر می‌شود، معمولاً نیازی به مشاهدهٔ مستقیم آن‌ها ندارید. یک استثنا در این قاعده زمانی است که از دارایی‌ها، شیدرها و موارد مشابه ارائه‌شده توسط کاربر استفاده می‌کنید؛ در این صورت، بررسی خطاهای اعتبارسنجی در هنگام بارگذاری می‌تواند مفید باشد.

> [!NOTE]
> ما سعی کرده‌ایم اطلاعات مفیدی برای کمک به درک دلیل رخ دادن خطاهای اعتبارسنجی در کد WebGPU شما در بخش‌های «Validation» (اعتبارسنجی) ارائه دهیم، که معیارهایی برای جلوگیری از خطاهای اعتبارسنجی فهرست می‌کنند. برای مثال، به [بخش اعتبارسنجی `GPUDevice.createBindGroup()`](/en-US/docs/Web/API/GPUDevice/createBindGroup#validation) مراجعه کنید.

{{InheritanceDiagram}}

## سازنده

- {{domxref("GPUValidationError.GPUValidationError", "GPUValidationError()")}}
  - : یک نمونهٔ جدید از شیء `GPUValidationError` می‌سازد.

## ویژگی‌های نمونه

ویژگی `message` از والد خود، {{domxref("GPUError")}}، به ارث رسیده است:

- {{domxref("GPUError.message", "message")}} {{Experimental_Inline}} {{ReadOnlyInline}}
  - : یک رشته که پیامی قابل خواندن برای انسان ارائه می‌دهد و دلیل رخ دادن خطا را توضیح می‌دهد.

## مثال‌ها

مثال زیر از یک scope خطا برای ثبت یک خطای اعتبارسنجی مشکوک استفاده می‌کند و آن را در کنسول ثبت می‌کند.

```js
device.pushErrorScope("validation");

let sampler = device.createSampler({
  maxAnisotropy: 0, // Invalid, maxAnisotropy must be at least 1.
});

device.popErrorScope().then((error) => {
  if (error) {
    // error is a GPUValidationError object instance
    sampler = null;
    console.error(`An error occurred while creating sampler: ${error.message}`);
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
- [بهترین روش‌های مدیریت خطا در WebGPU](https://toji.dev/webgpu-best-practices/error-handling)