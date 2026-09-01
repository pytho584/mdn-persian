---
title: "GPUPipelineError: reason property"
short-title: reason
slug: Web/API/GPUPipelineError/reason
page-type: web-api-instance-property
browser-compat: api.GPUPipelineError.reason
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`reason`** در رابط {{domxref("GPUPipelineError")}} دلیل شکست ایجاد خط لوله (pipeline) را به شکلی قابل‌خواندن برای ماشین مشخص می‌کند.

## مقدار

یک مقدار شمارشی که می‌تواند یکی از موارد زیر باشد:

- `"internal"`
  - : ایجاد خط لوله به دلیل یک خطای داخلی شکست خورده است (برای اطلاعات بیشتر درباره این نوع خطاها به {{domxref("GPUInternalError")}} مراجعه کنید.)
- `"validation"`
  - : ایجاد خط لوله به دلیل یک خطای اعتبارسنجی شکست خورده است (برای اطلاعات بیشتر درباره این نوع خطاها به {{domxref("GPUValidationError")}} مراجعه کنید.)

## مثال‌ها

برای مثالی که شامل یک نمونه شیء `GPUPipelineError` است، به صفحه اصلی [`GPUPipelineError`](/en-US/docs/Web/API/GPUPipelineError#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)