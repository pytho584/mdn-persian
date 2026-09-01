---
title: "GPUComputePipeline: label property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/GPUComputePipeline/label"
---

---
title: "GPUComputePipeline: label property"
short-title: label
slug: Web/API/GPUComputePipeline/label
page-type: web-api-instance-property
browser-compat: api.GPUComputePipeline.label
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی **`label`** در رابط {{domxref("GPUComputePipeline")}} برچسبی را فراهم می‌کند که می‌توان از آن برای شناسایی شیء استفاده کرد، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

این مقدار را می‌توان با ارائه دادن یک ویژگی `label` در شیء توصیفی که به فراخوانی {{domxref("GPUDevice.createComputePipeline()")}} یا {{domxref("GPUDevice.createComputePipelineAsync()")}} منبع ارسال می‌شود، تنظیم کرد؛ همچنین می‌توانید آن را مستقیماً روی شیء `GPUComputePipeline` بخوانید یا بنویسید.

## مقدار

یک رشته. اگر قبلاً به شکلی که در بالا توضیح داده شد تنظیم نشده باشد، یک رشته خالی خواهد بود.

## مثال‌ها

تنظیم و خواندن یک برچسب از طریق `GPUComputePipeline.label`:

```js
// …

const computePipeline = device.createComputePipeline({
  layout: device.createPipelineLayout({
    bindGroupLayouts: [bindGroupLayout],
  }),
  compute: {
    module: shaderModule,
    entryPoint: "main",
  },
});

computePipeline.label = "my_compute_pipeline";

console.log(computePipeline.label); // "my_compute_pipeline"
```

تنظیم یک برچسب از طریق فراخوانی {{domxref("GPUDevice.createComputePipeline()")}} و سپس خواندن آن از طریق `GPUComputePipeline.label`:

```js
// …

const computePipeline = device.createComputePipeline({
  layout: device.createPipelineLayout({
    bindGroupLayouts: [bindGroupLayout],
  }),
  compute: {
    module: shaderModule,
    entryPoint: "main",
  },
  label: "my_compute_pipeline",
});

console.log(computePipeline.label); // "my_compute_pipeline"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)