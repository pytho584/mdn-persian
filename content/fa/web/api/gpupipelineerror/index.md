---
title: "GPUPipelineError"
slug: Web/API/GPUPipelineError
page-type: web-api-interface
browser-compat: api.GPUPipelineError
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`GPUPipelineError`** از {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} یک شکست در خط لوله (pipeline) را توصیف می‌کند. این مقداری است که هنگام رد شدن (reject) یک {{jsxref("Promise")}} بازگردانده شده توسط فراخوانی {{domxref("GPUDevice.createComputePipelineAsync()")}} یا {{domxref("GPUDevice.createRenderPipelineAsync()")}} دریافت می‌شود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("GPUPipelineError.GPUPipelineError", "GPUPipelineError()")}}
  - : یک نمونه جدید از شیء `GPUPipelineError` ایجاد می‌کند.

## ویژگی‌های نمونه

_ویژگی‌های والد خود، {{domxref("DOMException")}} را به ارث می‌برد._

- {{domxref("GPUPipelineError.reason", "reason")}} {{ReadOnlyInline}}
  - : یک مقدار شمارشی که دلیل شکست ایجاد خط لوله را به صورت قابل خواندن برای ماشین مشخص می‌کند.

## مثال‌ها

<!-- cSpell:ignore maijn -->

در قطعه کد زیر، ما در تلاش برای ایجاد یک {{domxref("GPUComputePipeline")}} با استفاده از {{domxref("GPUDevice.createComputePipelineAsync()")}} هستیم. با این حال، `entryPoint` خط لوله محاسباتی خود را به اشتباه `"maijn"` نوشته‌ایم (باید `"main"` باشد)، بنابراین ایجاد خط لوله شکست می‌خورد و بلوک `catch` ما دلیل و پیام خطای حاصل را در کنسول چاپ می‌کند.

```js
// …

let computePipeline;

try {
  computePipeline = await device.createComputePipelineAsync({
    layout: device.createPipelineLayout({
      bindGroupLayouts: [bindGroupLayout],
    }),
    compute: {
      module: shaderModule,
      entryPoint: "maijn",
    },
  });
} catch (error) {
  // error یک نمونه از شیء GPUPipelineError است
  console.error(error.reason);
  console.error(`Pipeline creation failed: ${error.message}`);
}

// …
```

در این مورد، `reason` داده شده `"Validation"` است و `message` عبارت است از `"Entry point "maijn" doesn't exist in the shader module [ShaderModule]."`

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [رابط WebGPU API](/en-US/docs/Web/API/WebGPU_API)
- [بهترین روش‌های مدیریت خطا در WebGPU](https://toji.dev/webgpu-best-practices/error-handling)