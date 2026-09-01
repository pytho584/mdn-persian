---
title: "GPUBindGroup: label property"
short-title: label
slug: Web/API/GPUBindGroup/label
page-type: web-api-instance-property
browser-compat: api.GPUBindGroup.label
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی **`label`** در رابط {{domxref("GPUBindGroup")}} برچسبی را فراهم می‌کند که می‌توان از آن برای شناسایی شیء استفاده کرد، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

این مقدار را می‌توان با ارائه یک ویژگی `label` در شیء توصیف‌کننده‌ای که به فراخوانی مبدأ {{domxref("GPUDevice.createBindGroup()")}} منتقل می‌شود تنظیم کرد، یا می‌توانید آن را مستقیماً روی شیء `GPUBindGroup` بخوانید و بنویسید.

## مقدار

یک رشته. اگر قبلاً به صورت فوق تنظیم نشده باشد، یک رشته خالی خواهد بود.

## مثال‌ها

تنظیم و خواندن برچسب از طریق `GPUBindGroup.label`:

```js
// …

const bindGroup = device.createBindGroup({
  layout: bindGroupLayout,
  entries: [
    {
      binding: 0,
      resource: {
        buffer: output,
      },
    },
  ],
});

bindGroup.label = "my_bind_group";

console.log(bindGroup.label); // "my_bind_group"
```

تنظیم برچسب از طریق فراخوانی مبدأ {{domxref("GPUDevice.createBindGroup()")}} و سپس خواندن آن از طریق `GPUBindGroup.label`:

```js
// …

const bindGroup = device.createBindGroup({
  layout: bindGroupLayout,
  entries: [
    {
      binding: 0,
      resource: {
        buffer: output,
      },
    },
  ],
  label: "my_bind_group",
});

console.log(bindGroup.label); // "my_bind_group"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)