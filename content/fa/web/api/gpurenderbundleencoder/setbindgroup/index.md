---
title: "GPURenderBundleEncoder: setBindGroup() method"
short-title: setBindGroup()
slug: Web/API/GPURenderBundleEncoder/setBindGroup
page-type: web-api-instance-method
browser-compat: api.GPURenderBundleEncoder.setBindGroup
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`setBindGroup()`** از رابط {{domxref("GPURenderBundleEncoder")}}، {{domxref("GPUBindGroup")}} را برای استفاده در دستورات بعدی باندل رندر، برای یک ایندکس معین، تنظیم می‌کند.

> [!NOTE]
> این متد از نظر عملکردی با معادل خود در {{domxref("GPURenderPassEncoder")}} — {{domxref("GPURenderPassEncoder.setBindGroup", "setBindGroup()")}} یکسان است.

## نحو

```js-nolint
setBindGroup(index, bindGroup)
setBindGroup(index, bindGroup, dynamicOffsets)
setBindGroup(index, bindGroup, dynamicOffsets, dynamicOffsetsStart,
             dynamicOffsetsLength)
```

### پارامترها

- `index`
  - : ایندکسی که بایند گروه در آن تنظیم می‌شود. این مقدار با مقدار ایندکس `n` ویژگی [`@group(n)`](https://gpuweb.github.io/gpuweb/wgsl/#attribute-group) متناظر در کد شیدر ({{domxref("GPUShaderModule")}}) مورد استفاده در پایپلاین مرتبط مطابقت دارد.
- `bindGroup`
  - : {{domxref("GPUBindGroup")}} ای که برای دستورات بعدی باندل رندر استفاده می‌شود، یا `null`، که در این صورت هر بایند گروه قبلی تنظیم‌شده در اسلات داده‌شده لغو می‌شود.
- `dynamicOffsets` {{optional_inline}}
  - : مقداری که آفست (برحسب بایت) را برای هر ورودی در `bindGroup` که `hasDynamicOffset: true` دارد مشخص می‌کند (یعنی در توصیفگر فراخوانی {{domxref("GPUDevice.createBindGroupLayout()")}} که شیء {{domxref("GPUBindGroupLayout")}} مبنای `bindGroup` را ایجاد کرده است). این مقدار می‌تواند یکی از موارد زیر باشد:
    - آرایه‌ای از اعداد که آفست‌های مختلف را مشخص می‌کنند.
    - یک {{jsxref("Uint32Array")}} حاوی اعدادی که آفست‌ها را مشخص می‌کنند.

اگر مقدار {{jsxref("Uint32Array")}} برای `dynamicOffsets` مشخص شده باشد، هر دو پارامتر زیر نیز الزامی هستند:

- `dynamicOffsetsStart`
  - : عددی که آفست (برحسب عناصر آرایه) را در `dynamicOffsetsData` مشخص می‌کند، جایی که داده‌های آفست پویا آغاز می‌شود.
- `dynamicOffsetsLength`
  - : عددی که تعداد مقادیر آفست پویایی را که باید از `dynamicOffsetsData` خوانده شوند، مشخص می‌کند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

برای فراخوانی‌های `setBindGroup()` که از مقدار {{jsxref("Uint32Array")}} برای `dynamicOffsets` استفاده می‌کنند، در صورت برقراری شرایط زیر، فراخوانی یک `RangeError` {{domxref("DOMException")}} پرتاب می‌کند:

- `dynamicOffsetsStart` کمتر از 0 باشد.
- `dynamicOffsetsStart` + `dynamicOffsetsLength` بزرگ‌تر از `dynamicOffsets.length` باشد.

### اعتبارسنجی

هنگام فراخوانی **`setBindGroup()`** معیارهای زیر باید برقرار باشند؛ در غیر این صورت یک {{domxref("GPUValidationError")}} تولید می‌شود و {{domxref("GPURenderBundleEncoder")}} نامعتبر می‌شود:

- `index` کمتر یا مساوی `maxBindGroups` متعلق به {{domxref("GPUDevice")}} ({{domxref("GPUSupportedLimits", "limit", "", "nocode")}}) باشد.
- `dynamicOffsets.length` با تعداد ورودی‌های `bindGroup` که `hasDynamicOffset: true` دارند یکسان باشد.
- برای ورودی‌های `bindGroup` که در آن‌ها `type` بافر متصل‌شده `"uniform"` است (به {{domxref("GPUDevice.createBindGroupLayout()")}} مراجعه کنید)، هر عدد در `dynamicOffsets` مضربی از `minUniformBufferOffsetAlignment` متعلق به {{domxref("GPUDevice")}} ({{domxref("GPUSupportedLimits", "limit", "", "nocode")}}) باشد.
- برای ورودی‌های `bindGroup` که در آن‌ها `type` بافر متصل‌شده `"storage"` یا `"read-only-storage"` است (به {{domxref("GPUDevice.createBindGroupLayout()")}} مراجعه کنید)، هر عدد در `dynamicOffsets` مضربی از `minStorageBufferOffsetAlignment` متعلق به {{domxref("GPUDevice")}} ({{domxref("GPUSupportedLimits", "limit", "", "nocode")}}) باشد.
- برای هر ورودی `bindGroup`، مجموع `offset` بافر متصل‌شده، به‌علاوه `minBindingSize` ورودی layout متناظر، به‌علاوه آفست پویای متناظر مشخص‌شده در `dynamicOffsets`، کمتر یا مساوی `size` بافر متصل‌شده باشد.

## مثال‌ها

### تنظیم بایند گروه

```js
function recordRenderPass(passEncoder) {
  if (settings.dynamicOffsets) {
    passEncoder.setPipeline(dynamicPipeline);
  } else {
    passEncoder.setPipeline(pipeline);
  }
  passEncoder.setVertexBuffer(0, vertexBuffer);
  passEncoder.setBindGroup(0, timeBindGroup);
  const dynamicOffsets = [0];
  for (let i = 0; i < numTriangles; ++i) {
    if (settings.dynamicOffsets) {
      dynamicOffsets[0] = i * alignedUniformBytes;
      passEncoder.setBindGroup(1, dynamicBindGroup, dynamicOffsets);
    } else {
      passEncoder.setBindGroup(1, bindGroups[i]);
    }
    passEncoder.draw(3, 1, 0, 0);
  }
}
```

قطعه کد بالا از [مثال Animometer](https://webgpu.github.io/webgpu-samples/samples/animometer/) در نمونه‌های WebGPU گرفته شده است.

### لغو تنظیم بایند گروه

```js
// Set bind group in slot 0
passEncoder.setBindGroup(0, timeBindGroup);

// Later, unset bind group in slot 0
passEncoder.setBindGroup(0, null);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)