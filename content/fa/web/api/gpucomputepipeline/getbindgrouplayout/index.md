---
title: "GPUComputePipeline: getBindGroupLayout() method"
short-title: getBindGroupLayout()
slug: Web/API/GPUComputePipeline/getBindGroupLayout
page-type: web-api-instance-method
browser-compat: api.GPUComputePipeline.getBindGroupLayout
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`getBindGroupLayout()`** از رابط {{domxref("GPUComputePipeline")}}، شیء {{domxref("GPUBindGroupLayout")}} مربوط به خط لوله را با ایندکس داده‌شده برمی‌گرداند (یعنی ایندکسی که در چیدمان خط لوله فراخوانی اصلی {{domxref("GPUDevice.createComputePipeline()")}} یا {{domxref("GPUDevice.createComputePipelineAsync()")}} گنجانده شده است).

اگر {{domxref("GPUComputePipeline")}} با `layout: "auto"` ساخته شده باشد، این متد تنها راه برای بازیابی {{domxref("GPUBindGroupLayout")}}های تولیدشده توسط خط لوله است.

## Syntax

```js-nolint
getBindGroupLayout(index)
```

### Parameters

- `index`
  - : عددی که ایندکس {{domxref("GPUBindGroupLayout")}} موردنظر برای بازگرداندن را نشان می‌دهد.

### Return value

یک نمونه شیء {{domxref("GPUBindGroupLayout")}}.

### Validation

هنگام فراخوانی **`getBindGroupLayout()`** معیارهای زیر باید برقرار باشند، در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و یک شیء نامعتبر {{domxref("GPUBindGroupLayout")}} بازگردانده می‌شود:

- `index` کمتر از تعداد اشیاء {{domxref("GPUBindGroupLayout")}} استفاده‌شده در چیدمان خط لوله باشد.

## Examples

> [!NOTE]
> شما می‌توانید مثال‌های کاملی را که از `getBindGroupLayout()` استفاده می‌کنند در [نمونه‌های WebGPU](https://webgpu.github.io/webgpu-samples/) مشاهده کنید.

```js
// …

// Create a compute pipeline using layout: "auto" to automatically generate
// appropriate bind group layouts
const computePipeline = device.createComputePipeline({
  layout: "auto",
  compute: {
    module: shaderModule,
    entryPoint: "main",
  },
});

// Create a bind group with the auto-generated layout from the compute pipeline
const computeBindGroup = device.createBindGroup({
  layout: computePipeline.getBindGroupLayout(0),
  entries: [
    {
      binding: 0,
      resource: { buffer: storageBuffer },
    },
  ],
});

// …
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)