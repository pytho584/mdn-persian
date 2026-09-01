---
title: "GPUCommandBuffer: label property"
---

---
title: "GPUCommandBuffer: label property"
short-title: label
slug: Web/API/GPUCommandBuffer/label
page-type: web-api-instance-property
browser-compat: api.GPUCommandBuffer.label
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی **`label`** از رابط {{domxref("GPUCommandBuffer")}} که فقط‌خواندنی است، رشته‌ای است که برچسبی را برای شناسایی شیء فراهم می‌کند؛ برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

این برچسب را می‌توان با ارائه‌ی یک ویژگی `label` در شیء توصیفگری که به فراخوانی {{domxref("GPUCommandEncoder.finish()")}} اصلی ارسال می‌شود تنظیم کرد، یا می‌توانید آن را مستقیماً روی شیء `GPUCommandBuffer` دریافت و تنظیم کنید.

## مقدار

یک رشته. اگر قبلاً هیچ مقدار برچسبی تنظیم نشده باشد، دریافت برچسب یک رشته‌ی خالی برمی‌گرداند.

## مثال‌ها

تنظیم و دریافت یک برچسب از طریق `GPUCommandBuffer.label`:

```js
const commandBuffer = commandEncoder.finish();
commandBuffer.label = "my_command_buffer";
console.log(commandBuffer.label); // "my_command_buffer"
```

تنظیم یک برچسب از طریق فراخوانی {{domxref("GPUCommandEncoder.finish()")}} اصلی و سپس دریافت آن از طریق `GPUCommandBuffer.label`:

```js
const commandBuffer = commandEncoder.finish({
  label: "my_command_buffer",
});

console.log(commandBuffer.label); // "my_command_buffer"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)