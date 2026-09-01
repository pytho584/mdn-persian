---
title: "GPUPipelineError: GPUPipelineError() سازنده"
short-title: GPUPipelineError()
slug: Web/API/GPUPipelineError/GPUPipelineError
page-type: web-api-constructor
browser-compat: api.GPUPipelineError.GPUPipelineError
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

سازندهٔ **`GPUPipelineError()`** یک نمونهٔ جدید از شیء
{{domxref("GPUPipelineError")}} ایجاد می‌کند.

## نحو (Syntax)

```js-nolint
new GPUPipelineError(message, options)
```

### پارامترها

- `message` {{optional_inline}}
  - : یک رشته که پیامی قابل‌فهم برای انسان فراهم می‌کند و توضیح می‌دهد چرا خطا رخ داده است. اگر مشخص نشود، `message` به طور پیش‌فرض یک رشتهٔ خالی (`""`) خواهد بود.
- `options`
  - : یک شیء که می‌تواند ویژگی‌های زیر را شامل شود:
    - `reason`
      - : یک مقدار شمارشی که دلیل شکست ایجاد پایپ‌لاین را به صورت قابل‌خواندن برای ماشین تعریف می‌کند. مقدار می‌تواند یکی از موارد زیر باشد:
        - `"internal"`: ایجاد پایپ‌لاین به دلیل یک خطای داخلی شکست خورده است (برای اطلاعات بیشتر دربارهٔ این نوع خطاها به {{domxref("GPUInternalError")}} مراجعه کنید).
        - `"validation"`: ایجاد پایپ‌لاین به دلیل یک خطای اعتبارسنجی شکست خورده است (برای اطلاعات بیشتر دربارهٔ این نوع خطاها به {{domxref("GPUValidationError")}} مراجعه کنید).

## مثال‌ها

یک توسعه‌دهنده معمولاً به صورت دستی از سازنده برای ایجاد یک شیء `GPUPipelineError` استفاده نمی‌کند. عامل کاربر (user agent) از این سازنده برای ایجاد یک شیء مناسب زمانی استفاده می‌کند که یک {{jsxref("Promise")}} برگشتی از یک فراخوانی {{domxref("GPUDevice.createComputePipelineAsync()")}} یا {{domxref("GPUDevice.createRenderPipelineAsync()")}} رد (reject) شود و نشان‌دهندهٔ شکست پایپ‌لاین باشد.

برای مشاهدهٔ مثالی شامل یک نمونهٔ شیء `GPUPipelineError`، به صفحهٔ اصلی [`GPUPipelineError`](/en-US/docs/Web/API/GPUPipelineError#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
- [بهترین روش‌های مدیریت خطا در WebGPU](https://toji.dev/webgpu-best-practices/error-handling)