---
title: "GPUTextureView: label property"
short-title: label
slug: Web/API/GPUTextureView/label
page-type: web-api-instance-property
browser-compat: api.GPUTextureView.label
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی **`label`** در رابط {{domxref("GPUTextureView")}} برچسبی ارائه می‌دهد که می‌توان از آن برای شناسایی شیء استفاده کرد؛ برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

این مقدار را می‌توان هنگام ساخت نمای (view) با قرار دادن ویژگی `label` در شیء توصیفگر (descriptor) که به فراخوانی {{domxref("GPUTexture.createView()")}} ارسال می‌شود تنظیم کرد. همچنین می‌توانید آن را مستقیماً روی شیء `GPUTextureView` بخوانید یا تنظیم کنید.

## مقدار

یک رشته. اگر قبلاً به‌صورت گفته‌شده تنظیم نشده باشد، این مقدار یک رشتهٔ خالی خواهد بود.

## مثال‌ها

تنظیم و خواندن برچسب از طریق `GPUTextureView.label`:

```js
// …

const depthTexture = device.createTexture({
  size: [canvas.width, canvas.height],
  format: "depth24plus",
  usage: GPUTextureUsage.RENDER_ATTACHMENT,
});

const view = depthTexture.createView();

view.label = "my_view";

console.log(view.label); // "my_view"
```

تنظیم برچسب از طریق فراخوانی {{domxref("GPUTexture.createView()")}} و سپس خواندن آن با `GPUTextureView.label`:

```js
// …

const depthTexture = device.createTexture({
  size: [canvas.width, canvas.height],
  format: "depth24plus",
  usage: GPUTextureUsage.RENDER_ATTACHMENT,
});

const view = depthTexture.createView({
  label: "my_view",
});

console.log(view.label); // "my_view"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)