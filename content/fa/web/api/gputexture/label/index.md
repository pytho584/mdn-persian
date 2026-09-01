---
title: "GPUTexture: label property"
short-title: label
slug: Web/API/GPUTexture/label
page-type: web-api-instance-property
browser-compat: api.GPUTexture.label
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

خصوصیت **`label`** در رابط {{domxref("GPUTexture")}} برچسبی را فراهم می‌کند که می‌توان از آن برای شناسایی شیء استفاده کرد، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

این مقدار را می‌توان با ارائه‌ی یک خصوصیت `label` در شیء توصیف‌گر (descriptor) که به فراخوانی {{domxref("GPUDevice.createTexture()")}} مبدأ ارسال می‌شود تنظیم کرد، یا می‌توانید آن را مستقیماً روی شیء `GPUTexture` بخوانید و بنویسید.

## مقدار

یک رشته. اگر این مقدار قبلاً همان‌طور که در بالا توضیح داده شد تنظیم نشده باشد، یک رشته‌ی خالی خواهد بود.

## مثال‌ها

تنظیم و خواندن یک برچسب از طریق `GPUTexture.label`:

```js
// …

const depthTexture = device.createTexture({
  size: [canvas.width, canvas.height],
  format: "depth24plus",
  usage: GPUTextureUsage.RENDER_ATTACHMENT,
});

depthTexture.label = "my_texture";

console.log(depthTexture.label); // "my_texture"
```

تنظیم یک برچسب از طریق فراخوانی {{domxref("GPUDevice.createTexture()")}} مبدأ و سپس خواندن آن از طریق `GPUTexture.label`:

```js
// …

const depthTexture = device.createTexture({
  size: [canvas.width, canvas.height],
  format: "depth24plus",
  usage: GPUTextureUsage.RENDER_ATTACHMENT,
  label: "my_texture",
});

console.log(depthTexture.label); // "my_texture"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [رابط WebGPU API](/en-US/docs/Web/API/WebGPU_API)