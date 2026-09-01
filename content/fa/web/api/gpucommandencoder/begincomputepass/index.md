---
title: "GPUCommandEncoder: beginComputePass() method"
short-title: beginComputePass()
slug: Web/API/GPUCommandEncoder/beginComputePass
page-type: web-api-instance-method
browser-compat: api.GPUCommandEncoder.beginComputePass
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

**`beginComputePass()`** متدی از رابط {{domxref("GPUCommandEncoder")}} است که رمزگذاری یک پاس محاسباتی (compute pass) را آغاز می‌کند و یک {{domxref("GPUComputePassEncoder")}} برمی‌گرداند که می‌تواند برای کنترل محاسبات استفاده شود.

## Syntax

```js-nolint
beginComputePass()
beginComputePass(descriptor)
```

### Parameters

- `descriptor` {{optional_inline}}
  - : یک شیء حاوی ویژگی‌های زیر:
    - `label` {{optional_inline}}
      - : رشته‌ای که برچسبی برای شناسایی شیء فراهم می‌کند، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.
    - `timestampWrites` {{optional_inline}}
      - : آرایه‌ای از اشیاء که مکان و زمان نوشته‌شدن مقادیر پرس‌وجوی timestamp را برای این پاس مشخص می‌کنند. این اشیاء دارای ویژگی‌های زیر هستند:
        - `querySet`
          - : یک {{domxref("GPUQuerySet")}} از نوع `"timestamp"` که نتایج پرس‌وجوی timestamp در آن نوشته خواهد شد.
        - `beginningOfPassWriteIndex`
          - : عددی که ایندکس کوئری در `querySet` را مشخص می‌کند که timestamp ابتدای پاس رندر در آن نوشته می‌شود. این ویژگی اختیاری است — اگر تعریف نشود، هیچ timestamپی برای ابتدای پاس نوشته نخواهد شد.
        - `endOfPassWriteIndex`
          - : عددی که ایندکس کوئری در `querySet` را مشخص می‌کند که timestamp انتهای پاس رندر در آن نوشته می‌شود. این ویژگی اختیاری است — اگر تعریف نشود، هیچ timestamپی برای انتهای پاس نوشته نخواهد شد.

        > [!NOTE]
        > برای استفاده از پرس‌وجوهای timestamp باید [feature](/en-US/docs/Web/API/GPUSupportedFeatures) به نام `timestamp-query` فعال باشد. مقادیر پرس‌وجوی timestamp بر حسب نانوثانیه نوشته می‌شوند، اما نحوه تعیین این مقدار به پیاده‌سازی بستگی دارد.

### Return value

یک نمونه از شیء {{domxref("GPUComputePassEncoder")}}.

### Validation

برای فراخوانی **`beginComputePass()`** معیارهای زیر باید برآورده شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} ایجاد شده و یک {{domxref("GPUComputePassEncoder")}} نامعتبر بازگردانده می‌شود:

- ویژگی {{domxref("GPUSupportedFeatures", "feature", "", "nocode")}} به نام `timestamp-query` در {{domxref("GPUDevice")}} فعال باشد.

## Examples

در [نمونه محاسبات پایه](https://mdn.github.io/dom-examples/webgpu-compute-demo/) ما، چندین دستور از طریق یک {{domxref("GPUCommandEncoder")}} ثبت می‌شوند. بیشتر این دستورات از {{domxref("GPUComputePassEncoder")}} که از طریق `beginComputePass()` ایجاد شده است، سرچشمه می‌گیرند.

```js
// …

// Create GPUCommandEncoder to encode commands to issue to the GPU
const commandEncoder = device.createCommandEncoder();

// Initiate compute pass
const passEncoder = commandEncoder.beginComputePass();

// Issue commands
passEncoder.setPipeline(computePipeline);
passEncoder.setBindGroup(0, bindGroup);
passEncoder.dispatchWorkgroups(Math.ceil(BUFFER_SIZE / 64));

// End the render pass
passEncoder.end();

// Copy output buffer to staging buffer
commandEncoder.copyBufferToBuffer(
  output,
  0, // Source offset
  stagingBuffer,
  0, // Destination offset
  BUFFER_SIZE,
);

// End frame by passing array of command buffers to command queue for execution
device.queue.submit([commandEncoder.finish()]);

// …
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)