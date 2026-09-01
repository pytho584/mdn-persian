---
title: "GPUCommandEncoder: label property"
short-title: label
slug: Web/API/GPUCommandEncoder/label
page-type: web-api-instance-property
browser-compat: api.GPUCommandEncoder.label
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط خواندنی **`label`** در رابط {{domxref("GPUCommandEncoder")}} یک رشته است که برچسبی را برای شناسایی شیء فراهم می‌کند؛ برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

این برچسب می‌تواند با قرار دادن یک ویژگی `label` در شیء توصیف‌کننده‌ای که به فراخوانی اصلی {{domxref("GPUDevice.createCommandEncoder()")}} ارسال می‌شود، تنظیم گردد، یا می‌توانید آن را مستقیماً روی شیء `GPUCommandEncoder` دریافت و تنظیم کنید.

## مقدار

یک رشته. اگر قبلاً هیچ مقداری برای برچسب تنظیم نشده باشد، دریافت برچسب یک رشتهٔ خالی بازمی‌گرداند.

## مثال‌ها

تنظیم و دریافت یک برچسب از طریق `GPUCommandEncoder.label`:

```js
const commandEncoder = device.createCommandEncoder();
commandEncoder.label = "my_command_encoder";
console.log(commandEncoder.label); // "my_command_encoder"
```

تنظیم برچسب از طریق فراخوانی اصلی {{domxref("GPUDevice.createCommandEncoder()")}} و سپس دریافت آن از طریق `GPUCommandEncoder.label`:

```js
const commandEncoder = device.createCommandEncoder({
  label: "my_command_encoder",
});

console.log(commandEncoder.label); // "my_command_encoder"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)