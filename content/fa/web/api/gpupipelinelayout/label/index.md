---
title: "GPUPipelineLayout: label property"
short-title: label
slug: Web/API/GPUPipelineLayout/label
page-type: web-api-instance-property
browser-compat: api.GPUPipelineLayout.label
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی **`label`** در رابط {{domxref("GPUPipelineLayout")}} برچسبی را در اختیار شما قرار می‌دهد که می‌تواند برای شناسایی آن شیء استفاده شود؛ برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

این برچسب را می‌توان با افزودن یک ویژگی `label` به آبجکت توصیف‌گر (descriptor) که در فراخوانی {{domxref("GPUDevice.createPipelineLayout()")}} ارسال می‌شود، تنظیم کرد. همچنین می‌توانید آن را مستقیماً روی خودِ آبجکت `GPUPipelineLayout` بخوانید یا تنظیم کنید.

## مقدار

یک رشته. اگر این مقدار قبلاً به شکلی که در بالا توضیح داده شد تنظیم نشده باشد، یک رشتهٔ خالی خواهد بود.

## مثال‌ها

تنظیم و خواندن برچسب با استفاده از `GPUPipelineLayout.label`:

```js
// …

const pipelineLayout = device.createPipelineLayout({
  bindGroupLayouts: [bindGroupLayout],
});

pipelineLayout.label = "my_pipeline_layout";

console.log(pipelineLayout.label); // "my_pipeline_layout"
```

تنظیم برچسب از طریق فراخوانی {{domxref("GPUDevice.createPipelineLayout()")}} و سپس خواندن آن با استفاده از `GPUPipelineLayout.label`:

```js
// …

const pipelineLayout = device.createPipelineLayout({
  bindGroupLayouts: [bindGroupLayout],
  label: "my_pipeline_layout",
});

console.log(pipelineLayout.label); // "my_pipeline_layout"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)