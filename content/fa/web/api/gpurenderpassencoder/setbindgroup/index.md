---
title: "GPURenderPassEncoder: setBindGroup() method"
short-title: setBindGroup()
slug: Web/API/GPURenderPassEncoder/setBindGroup
page-type: web-api-instance-method
browser-compat: api.GPURenderPassEncoder.setBindGroup
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`setBindGroup()`** در رابط {{domxref("GPURenderPassEncoder")}}، {{domxref("GPUBindGroup")}} مورد استفاده برای دستورهای رندر بعدی را در یک شاخص مشخص تنظیم می‌کند.

## Syntax

```js-nolint
setBindGroup(index, bindGroup)
setBindGroup(index, bindGroup, dynamicOffsets)
setBindGroup(index, bindGroup, dynamicOffsets, dynamicOffsetsStart,
             dynamicOffsetsLength)
```

### Parameters

- `index`
  - : شاخصی که bind group در آن تنظیم می‌شود. این مقدار با شاخص `n` در ویژگی [`@group(n)`](https://gpuweb.github.io/gpuweb/wgsl/#attribute-group) در کد شیدر ({{domxref("GPUShaderModule")}}) که در پایپ‌لاین مربوطه استفاده شده است، مطابقت دارد.
- `bindGroup`
  - : {{domxref("GPUBindGroup")}} مورد استفاده برای دستورهای رندر بعدی، یا `null` که در این صورت هر bind group که قبلاً در این اسلات تنظیم شده بود، لغو می‌شود.
- `dynamicOffsets` {{optional_inline}}
  - : مقداری که افست (به بایت) را برای هر ورودی در `bindGroup` که دارای `hasDynamicOffset: true` است (یعنی در توصیفگر فراخوانی {{domxref("GPUDevice.createBindGroupLayout()")}} که شیء {{domxref("GPUBindGroupLayout")}} را ساخته و `bindGroup` بر اساس آن است) مشخص می‌کند. این مقدار می‌تواند:
    - یک آرایه از اعداد که افست‌های مختلف را مشخص می‌کند.
    - یک {{jsxref("Uint32Array")}} شامل اعدادی که افست‌ها را مشخص می‌کنند.

اگر یک مقدار {{jsxref("Uint32Array")}} برای `dynamicOffsets` مشخص شود، هر دو پارامتر زیر نیز الزامی هستند:

- `dynamicOffsetsStart`
  - : عددی که افست (بر حسب تعداد عناصر آرایه) را در `dynamicOffsetsData` مشخص می‌کند، جایی که داده‌های افست داینامیک شروع می‌شود.
- `dynamicOffsetsLength`
  - : عددی که تعداد مقادیر افست داینامیک را که باید از `dynamicOffsetsData` خوانده شود، مشخص می‌کند.

### Return value

هیچ ({{jsxref("undefined")}}).

### Exceptions

برای فراخوانی‌های `setBindGroup()` که از مقدار {{jsxref("Uint32Array")}} برای `dynamicOffsets` استفاده می‌کنند، فراخوانی با یک `RangeError` {{domxref("DOMException")}} پرتاب می‌شود اگر:

- `dynamicOffsetsStart` کمتر از 0 باشد.
- `dynamicOffsetsStart` + `dynamicOffsetsLength` بزرگ‌تر از `dynamicOffsets.length` باشد.

### Validation

هنگام فراخوانی **`setBindGroup()`** معیارهای زیر باید برآورده شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و {{domxref("GPURenderPassEncoder")}} نامعتبر می‌شود:

- `index` کمتر یا مساوی با `maxBindGroups` در {{domxref("GPUDevice")}} (محدودیت {{domxref("GPUSupportedLimits", "limit", "", "nocode")}}) باشد.
- `dynamicOffsets.length` با تعداد ورودی‌های `bindGroup` که دارای `hasDynamicOffset: true` هستند یکسان باشد.
- برای ورودی‌های `bindGroup` که نوع `buffer` مقیدشده `"uniform"` است (به {{domxref("GPUDevice.createBindGroupLayout()")}} مراجعه کنید)، هر عدد در `dynamicOffsets` مضربی از `minUniformBufferOffsetAlignment` در {{domxref("GPUDevice")}} (محدودیت {{domxref("GPUSupportedLimits", "limit", "", "nocode")}}) باشد.
- برای ورودی‌های `bindGroup` که نوع `buffer` مقیدشده `"storage"` یا `"read-only-storage"` است (به {{domxref("GPUDevice.createBindGroupLayout()")}} مراجعه کنید)، هر عدد در `dynamicOffsets` مضربی از `minStorageBufferOffsetAlignment` در {{domxref("GPUDevice")}} (محدودیت {{domxref("GPUSupportedLimits", "limit", "", "nocode")}}) باشد.
- برای هر ورودی `bindGroup`، مجموع `offset` بافر مقیدشده، به‌علاوه `minBindingSize` ورودی layout مربوطه، به‌علاوه افست داینامیک متناظر که در `dynamicOffsets` مشخص شده، کمتر یا مساوی `size` بافر مقیدشده باشد.

## Examples

### Set bind group

در مثال [Textured Cube](https://webgpu.github.io/webgpu-samples/samples/texturedCube/) از نمونه‌های WebGPU، از `setBindGroup()` برای اتصال `uniformBindGroup` به شاخص 0 استفاده شده است. برای مشاهده کامل مثال به آن مراجعه کنید.

```js
// …

const commandEncoder = device.createCommandEncoder();
const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);
passEncoder.setPipeline(pipeline);
passEncoder.setBindGroup(0, uniformBindGroup);
passEncoder.setVertexBuffer(0, verticesBuffer);
passEncoder.draw(cubeVertexCount, 1, 0, 0);
passEncoder.end();
device.queue.submit([commandEncoder.finish()]);

// …
```

> [!NOTE]
> برای مثال‌های بیشتر از کاربرد `setBindGroup()`، سایر [نمونه‌های WebGPU](https://webgpu.github.io/webgpu-samples/) را بررسی کنید.

### Unset bind group

```js
// تنظیم bind group در اسلات 0
passEncoder.setBindGroup(0, uniformBindGroup);

// بعداً، لغو تنظیم bind group در اسلات 0
passEncoder.setBindGroup(0, null);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)