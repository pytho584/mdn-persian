---
title: "GPUComputePassEncoder: setBindGroup() method"
short-title: setBindGroup()
slug: Web/API/GPUComputePassEncoder/setBindGroup
page-type: web-api-instance-method
browser-compat: api.GPUComputePassEncoder.setBindGroup
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`setBindGroup()`** از رابط {{domxref("GPUComputePassEncoder")}}، گروه اتصال ({{domxref("GPUBindGroup")}}) مورد استفاده برای دستورهای محاسباتی بعدی را برای یک شاخص معین تنظیم می‌کند.

## نحو (Syntax)

```js-nolint
setBindGroup(index, bindGroup)
setBindGroup(index, bindGroup, dynamicOffsets)
setBindGroup(index, bindGroup, dynamicOffsets, dynamicOffsetsStart,
             dynamicOffsetsLength)
```

### پارامترها

- `index`
  - : شاخصی که گروه اتصال در آن قرار می‌گیرد. این مقدار با مقدار شاخص `n` در ویژگی [`@group(n)`](https://gpuweb.github.io/gpuweb/wgsl/#attribute-group) در کد شیدر ({{domxref("GPUShaderModule")}}) که در پایپ‌لاین مربوطه استفاده شده است، مطابقت دارد.
- `bindGroup`
  - : شیء {{domxref("GPUBindGroup")}} که برای دستورهای محاسباتی بعدی استفاده می‌شود، یا `null`. در صورت `null`، هر گروه اتصال قبلی که در آن اسلات تنظیم شده بود، حذف می‌شود.
- `dynamicOffsets` {{optional_inline}}
  - : مقداری که افست (به بایت) را برای هر ورودی در `bindGroup` که `hasDynamicOffset: true` دارد مشخص می‌کند (یعنی در توصیفگر فراخوانی {{domxref("GPUDevice.createBindGroupLayout()")}} که شیء {{domxref("GPUBindGroupLayout")}} مبنای `bindGroup` را ایجاد کرده است). این مقدار می‌تواند:
    - آرایه‌ای از اعداد که افست‌های مختلف را مشخص می‌کند.
    - یک {{jsxref("Uint32Array")}} حاوی اعدادی که افست‌ها را مشخص می‌کنند.

اگر مقدار {{jsxref("Uint32Array")}} برای `dynamicOffsets` مشخص شود، هر دو پارامتر زیر نیز الزامی هستند:

- `dynamicOffsetsStart`
  - : عددی که افست شروع داده‌های افست پویا را در `dynamicOffsetsData` بر حسب عناصر آرایه مشخص می‌کند.
- `dynamicOffsetsLength`
  - : عددی که تعداد مقادیر افست پویا را که باید از `dynamicOffsetsData` خوانده شوند، مشخص می‌کند.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها (Exceptions)

برای فراخوانی‌های `setBindGroup()` که از مقدار {{jsxref("Uint32Array")}} برای `dynamicOffsets` استفاده می‌کنند، اگر شرایط زیر برقرار باشد، فراخوانی یک `RangeError` از نوع {{domxref("DOMException")}} پرتاب می‌کند:

- `dynamicOffsetsStart` کمتر از 0 باشد.
- `dynamicOffsetsStart` + `dynamicOffsetsLength` بزرگ‌تر از `dynamicOffsets.length` باشد.

### اعتبارسنجی (Validation)

هنگام فراخوانی **`dispatchWorkgroups()`**، معیارهای زیر باید برآورده شوند؛ در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و {{domxref("GPUComputePassEncoder")}} نامعتبر می‌شود:

- `index` کمتر یا مساوی با `maxBindGroups` از {{domxref("GPUDevice")}} (محدودیت {{domxref("GPUSupportedLimits", "limit", "", "nocode")}}) باشد.
- `dynamicOffsets.length` با تعداد ورودی‌های `bindGroup` که `hasDynamicOffset: true` دارند برابر باشد.
- برای ورودی‌های `bindGroup` که `type` بافر متصل شده `"uniform"` است (به {{domxref("GPUDevice.createBindGroupLayout()")}} مراجعه کنید)، هر عدد در `dynamicOffsets` مضربی از `minUniformBufferOffsetAlignment` از {{domxref("GPUDevice")}} (محدودیت {{domxref("GPUSupportedLimits", "limit", "", "nocode")}}) باشد.
- برای ورودی‌های `bindGroup` که `type` بافر متصل شده `"storage"` یا `"read-only-storage"` است (به {{domxref("GPUDevice.createBindGroupLayout()")}} مراجعه کنید)، هر عدد در `dynamicOffsets` مضربی از `minStorageBufferOffsetAlignment` از {{domxref("GPUDevice")}} (محدودیت {{domxref("GPUSupportedLimits", "limit", "", "nocode")}}) باشد.
- برای هر ورودی `bindGroup`، مقدار `offset` بافر متصل شده، به اضافه `minBindingSize` مربوطه در ورودی layout، به اضافه افست پویای مشخص‌شده در `dynamicOffsets`، کمتر یا مساوی `size` بافر متصل شده باشد.

## مثال‌ها

### تنظیم گروه اتصال

در [نمونه محاسبات پایه](https://mdn.github.io/dom-examples/webgpu-compute-demo/) ما، چندین دستور از طریق یک {{domxref("GPUCommandEncoder")}} ضبط می‌شوند. بیشتر این دستورها از {{domxref("GPUComputePassEncoder")}} که با `beginComputePass()` ایجاد شده، سرچشمه می‌گیرند. فراخوانی `setBindGroup()` که در اینجا استفاده شده، ساده‌ترین شکل است و فقط شاخص و گروه اتصال را مشخص می‌کند.

```js
const BUFFER_SIZE = 1000;

// …

// ایجاد GPUCommandEncoder برای رمزگذاری دستورها و ارسال به GPU
const commandEncoder = device.createCommandEncoder();

// شروع پاس محاسباتی
const passEncoder = commandEncoder.beginComputePass();

// ارسال دستورها
passEncoder.setPipeline(computePipeline);
passEncoder.setBindGroup(0, bindGroup);
passEncoder.dispatchWorkgroups(Math.ceil(BUFFER_SIZE / 64));

// پایان پاس رندر
passEncoder.end();

// کپی بافر خروجی به بافر موقت
commandEncoder.copyBufferToBuffer(
  output,
  0, // افست مبدأ
  stagingBuffer,
  0, // افست مقصد
  BUFFER_SIZE,
);

// پایان فریم با ارسال آرایه‌ای از بافرهای دستور به صف اجرا
device.queue.submit([commandEncoder.finish()]);

// …
```

### حذف گروه اتصال

```js
// تنظیم گروه اتصال در اسلات 0
passEncoder.setBindGroup(0, bindGroup);

// بعداً، حذف گروه اتصال از اسلات 0
passEncoder.setBindGroup(0, null);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)