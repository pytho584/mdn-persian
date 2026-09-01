---
title: "GPUPipelineLayout"
---

---
title: GPUPipelineLayout
slug: Web/API/GPUPipelineLayout
page-type: web-api-interface
browser-compat: api.GPUPipelineLayout
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

**`GPUPipelineLayout`** واسطهای در {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} است که {{domxref("GPUBindGroupLayout")}} های مورد استفاده توسط یک پایپلاین را تعریف میکند. {{domxref("GPUBindGroup")}} هایی که در طول رمزگذاری دستورات با پایپلاین استفاده میشوند، باید دارای {{domxref("GPUBindGroupLayout")}} سازگار باشند.

یک نمونه شیء `GPUPipelineLayout` با استفاده از روش {{domxref("GPUDevice.createPipelineLayout()")}} ایجاد میشود.

{{InheritanceDiagram}}

## ویژگیهای نمونه

- {{domxref("GPUPipelineLayout.label", "label")}}
  - : یک رشته که برچسبی برای شناسایی شیء فراهم میکند، مثلاً در پیامهای {{domxref("GPUError")}} یا هشدارهای کنسول.

## مثالها

> [!NOTE]
> [نمونههای WebGPU](https://webgpu.github.io/webgpu-samples/) شامل مثالهای بسیار بیشتری هستند.

### مثال پایه چیدمان پایپلاین

قطعه زیر:

- یک {{domxref("GPUBindGroupLayout")}} ایجاد میکند که یک اتصال با یک بافر، یک بافت و یک سمپلر را توصیف میکند.
- یک `GPUPipelineLayout` بر اساس {{domxref("GPUBindGroupLayout")}} ایجاد میکند.

```js
// …

const bindGroupLayout = device.createBindGroupLayout({
  entries: [
    {
      binding: 0,
      visibility: GPUShaderStage.VERTEX | GPUShaderStage.FRAGMENT,
      buffer: {},
    },
    {
      binding: 1,
      visibility: GPUShaderStage.FRAGMENT,
      texture: {},
    },
    {
      binding: 2,
      visibility: GPUShaderStage.FRAGMENT,
      sampler: {},
    },
  ],
});

const pipelineLayout = device.createPipelineLayout({
  bindGroupLayouts: [bindGroupLayout],
});

// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)