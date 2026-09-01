---
title: "GPUBuffer: label property"
---

---
title: "GPUBuffer: label property"
short-title: label
slug: Web/API/GPUBuffer/label
page-type: web-api-instance-property
browser-compat: api.GPUBuffer.label
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی **`label`** از رابط {{domxref("GPUBuffer")}} برچسبی را فراهم می‌کند که می‌توان از آن برای شناسایی شیء استفاده کرد؛ برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

این برچسب را می‌توان با قرار دادن یک ویژگی `label` در شیء توصیف‌گر (descriptor) که به فراخوانی {{domxref("GPUDevice.createBuffer()")}} برای ایجاد بافر ارسال می‌شود، تنظیم کرد؛ یا می‌توانید آن را مستقیماً روی شیء `GPUBuffer` بخوانید یا تنظیم کنید.

## مقدار

یک رشته. اگر این مقدار قبلاً به شکلی که در بالا توضیح داده شد تنظیم نشده باشد، یک رشتهٔ خالی خواهد بود.

## مثال‌ها

تنظیم و خواندن یک برچسب از طریق `GPUBuffer.label`:

```js
const output = device.createBuffer({
  size: BUFFER_SIZE,
  usage: GPUBufferUsage.STORAGE | GPUBufferUsage.COPY_SRC,
});

output.label = "my_buffer";

console.log(output.label); // "my_buffer"
```

تنظیم یک برچسب از طریق فراخوانی {{domxref("GPUDevice.createBuffer()")}} و سپس خواندن آن با استفاده از `GPUBuffer.label`:

```js
const output = device.createBuffer({
  size: BUFFER_SIZE,
  usage: GPUBufferUsage.STORAGE | GPUBufferUsage.COPY_SRC,
  label: "my_buffer",
});

console.log(output.label); // "my_buffer"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [رابط WebGPU](/en-US/docs/Web/API/WebGPU_API)