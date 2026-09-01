---
title: "GPUBindGroupLayout: label property"
short-title: label
slug: Web/API/GPUBindGroupLayout/label
page-type: web-api-instance-property
browser-compat: api.GPUBindGroupLayout.label
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی **`label`** در رابط {{domxref("GPUBindGroupLayout")}} برچسبی را فراهم می‌کند که می‌توان از آن برای شناسایی شیء استفاده کرد، برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

این مقدار را می‌توان با ارائه‌ی یک ویژگی `label` در شیء توصیف‌کننده‌ای که به فراخوانیِ {{domxref("GPUDevice.createBindGroupLayout()")}} ارسال می‌شود تنظیم کرد، یا می‌توانید آن را مستقیماً روی شیء `GPUBindGroupLayout` دریافت و تنظیم کنید.

## مقدار

یک رشته. اگر این ویژگی قبلاً به شکلی که در بالا توضیح داده شد تنظیم نشده باشد، یک رشته‌ی خالی خواهد بود.

## مثال‌ها

تنظیم و دریافت برچسب از طریق `GPUBindGroupLayout.label`:

```js
// …

const bindGroupLayout = device.createBindGroupLayout({
  entries: [
    {
      binding: 0,
      visibility: GPUShaderStage.COMPUTE,
      buffer: {
        type: "storage",
      },
    },
  ],
});

bindGroupLayout.label = "my_bind_group_layout";

console.log(bindGroupLayout.label); // "my_bind_group_layout"
```

تنظیم برچسب از طریق فراخوانیِ {{domxref("GPUDevice.createBindGroupLayout()")}} و سپس دریافت آن از طریق `GPUBindGroupLayout.label`:

```js
// …

const bindGroupLayout = device.createBindGroupLayout({
  entries: [
    {
      binding: 0,
      visibility: GPUShaderStage.COMPUTE,
      buffer: {
        type: "storage",
      },
    },
  ],
  label: "my_bind_group_layout",
});

console.log(bindGroupLayout.label); // "my_bind_group_layout"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)