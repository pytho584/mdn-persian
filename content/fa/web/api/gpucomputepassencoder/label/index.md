---
title: "GPUComputePassEncoder: label property"
---

---
title: "GPUComputePassEncoder: label property"
short-title: label
slug: Web/API/GPUComputePassEncoder/label
page-type: web-api-instance-property
browser-compat: api.GPUComputePassEncoder.label
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی **`label`** فقط‌خواندنی در رابط {{domxref("GPUComputePassEncoder")}}، رشته‌ای است که برچسبی برای شناسایی شیء فراهم می‌کند؛ برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

این برچسب را می‌توان با ارائه‌ی یک ویژگی `label` در آبجکت توصیفگری که به فراخوانی مبدأ {{domxref("GPUCommandEncoder.beginComputePass()")}} ارسال می‌شود، تنظیم کرد؛ همچنین می‌توانید آن را مستقیماً روی شیء `GPUComputePassEncoder` بخوانید یا تنظیم کنید.

## مقدار

یک رشته. اگر قبلاً هیچ مقدار برچسبی تنظیم نشده باشد، خواندن برچسب، یک رشته‌ی خالی برمی‌گرداند.

## مثال‌ها

تنظیم و خواندن یک برچسب از طریق `GPUComputePassEncoder.label`:

```js
const commandEncoder = device.createCommandEncoder();
const passEncoder = commandEncoder.beginComputePass();

passEncoder.label = "my_compute_pass_encoder";
console.log(passEncoder.label); // "my_compute_pass_encoder"
```

تنظیم یک برچسب از طریق فراخوانی مبدأ {{domxref("GPUCommandEncoder.beginComputePass()")}} و سپس خواندن آن از طریق `GPUComputePassEncoder.label`:

```js
const commandEncoder = device.createCommandEncoder();
const passEncoder = commandEncoder.beginComputePass({
  label: "my_compute_pass_encoder",
});

console.log(passEncoder.label); // "my_compute_pass_encoder"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)