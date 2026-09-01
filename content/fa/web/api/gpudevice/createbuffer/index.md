---
title: "GPUDevice: createBuffer() method"
---

---
title: "GPUDevice: createBuffer() method"
short-title: createBuffer()
slug: Web/API/GPUDevice/createBuffer
page-type: web-api-instance-method
browser-compat: api.GPUDevice.createBuffer
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`createBuffer()`** از رابط {{domxref("GPUDevice")}} یک {{domxref("GPUBuffer")}} ایجاد می‌کند که داده‌های خام برای استفاده در عملیات‌های GPU در آن ذخیره می‌شوند.

## نحو

```js-nolint
createBuffer(descriptor)
```

### پارامترها

- `descriptor`
  - : شیءای شامل ویژگی‌های زیر:
    - `label` {{optional_inline}}
      - : یک رشته که برچسبی برای شناسایی شیء فراهم می‌کند، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.
    - `mappedAtCreation` {{optional_inline}}
      - : یک مقدار بولی. اگر روی `true` تنظیم شود، بافر در هنگام ایجاد نقشه‌برداری می‌شود؛ یعنی می‌توانید بلافاصله با فراخوانی {{domxref("GPUBuffer.getMappedRange()")}} مقادیر داخل بافر را تنظیم کنید. مقدار پیش‌فرض `false` است.

        توجه داشته باشید که تنظیم `mappedAtCreation: true` معتبر است تا بتوانید داده‌های اولیهٔ بافر را تنظیم کنید، حتی اگر پرچم‌های استفادهٔ `GPUBufferUsage.MAP_READ` یا `GPUBufferUsage.MAP_WRITE` تنظیم نشده باشند.
    - `size`
      - : عددی که اندازهٔ بافر را بر حسب بایت نشان می‌دهد. اگر `mappedAtCreation` روی `true` تنظیم شده باشد، این عدد باید مضربی از `4` باشد.
    - `usage`
      - : {{glossary("Bitwise flags", "bitwise flags")}} نشان‌دهندهٔ استفاده‌های مجاز برای `GPUBuffer`. مقادیر ممکن در [جدول مقادیر `GPUBuffer.usage`](/en-US/docs/Web/API/GPUBuffer/usage#value) آمده است.

        توجه داشته باشید که می‌توان چندین استفادهٔ ممکن را با جدا کردن مقادیر با [OR بیتی](/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_OR) مشخص کرد، برای مثال: `GPUBufferUsage.COPY_SRC | GPUBufferUsage.MAP_WRITE`.

### مقدار بازگشتی

یک نمونهٔ شیء {{domxref("GPUBuffer")}}.

### استثناها

- `RangeError` {{domxref("DOMException")}}
  - : اگر `mappedAtCreation` روی `true` تنظیم شده باشد و `size` مشخص‌شده مضربی از `4` نباشد، این استثنا پرتاب می‌شود.

### اعتبارسنجی

هنگام فراخوانی **`createBuffer()`** معیارهای زیر باید برآورده شوند؛ در غیر این صورت یک {{domxref("GPUValidationError")}} تولید می‌شود و یک شیء نامعتبر {{domxref("GPUBuffer")}} بازگردانده می‌شود:

- یک `usage` معتبر مشخص شده باشد.
- `GPUBufferUsage.MAP_READ` مشخص شده باشد و هیچ پرچم اضافی‌ای غیر از `GPUBufferUsage.COPY_DST` مشخص نشده باشد.
- `GPUBufferUsage.MAP_WRITE` مشخص شده باشد و هیچ پرچم اضافی‌ای غیر از `GPUBufferUsage.COPY_SRC` مشخص نشده باشد.

> [!NOTE]
> اگر تخصیص بافر بدون هیچ اثر جانبی خاصی شکست بخورد، یک شیء {{domxref("GPUOutOfMemoryError")}} تولید می‌شود.

## مثال‌ها

در [دموی محاسباتی پایه](https://mdn.github.io/dom-examples/webgpu-compute-demo/)، ما یک بافر خروجی برای خواندن محاسبات GPU و یک بافر میانی (staging buffer) ایجاد می‌کنیم که برای دسترسی جاوااسکریپت نقشه‌برداری شود.

```js
const output = device.createBuffer({
  size: BUFFER_SIZE,
  usage: GPUBufferUsage.STORAGE | GPUBufferUsage.COPY_SRC,
});

const stagingBuffer = device.createBuffer({
  size: BUFFER_SIZE,
  usage: GPUBufferUsage.MAP_READ | GPUBufferUsage.COPY_DST,
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط [WebGPU API](/en-US/docs/Web/API/WebGPU_API)