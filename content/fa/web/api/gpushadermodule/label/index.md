---
title: "GPUShaderModule: label property"
short-title: label
slug: Web/API/GPUShaderModule/label
page-type: web-api-instance-property
browser-compat: api.GPUShaderModule.label
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی **`label`** در رابط {{domxref("GPUShaderModule")}} یک برچسب (label) ارائه می‌دهد که می‌توان از آن برای شناسایی شیء استفاده کرد، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

این مقدار را می‌توان با ارائه یک ویژگی `label` در شیء توصیف‌کننده (descriptor) که به فراخوانی اصلی {{domxref("GPUDevice.createShaderModule()")}} داده می‌شود، تنظیم کرد، یا می‌توانید آن را مستقیماً روی شیء `GPUShaderModule` دریافت و تنظیم کنید.

## مقدار

یک رشته (string). اگر قبلاً به‌صورت یادشده تنظیم نشده باشد، یک رشته خالی خواهد بود.

## مثال‌ها

تنظیم و دریافت یک برچسب از طریق `GPUShaderModule.label`:

```js
// ...

const shaderModule = device.createShaderModule({
  code: shaders,
});

shaderModule.label = "my_shader";

console.log(shaderModule.label); // "my_shader"
```

تنظیم یک برچسب از طریق فراخوانی اصلی {{domxref("GPUDevice.createShaderModule()")}} و سپس دریافت آن از طریق `GPUShaderModule.label`:

```js
// ...

const shaderModule = device.createShaderModule({
  code: shaders,
  label: "my_shader",
});

console.log(shaderModule.label); // "my_shader"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)