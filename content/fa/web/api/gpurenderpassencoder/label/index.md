---
title: "GPURenderPassEncoder: label property"
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

خاصیت **`label`** (فقط خواندنی) از رابط {{domxref("GPURenderPassEncoder")}} یک رشته است که برچسبی را فراهم می‌کند که می‌توان از آن برای شناسایی شیء استفاده کرد، برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

این مقدار می‌تواند با ارائه یک خاصیت `label` در شیء توصیف‌کننده‌ای که به فراخوانی مبدأ {{domxref("GPUCommandEncoder.beginRenderPass()")}} داده می‌شود، تنظیم گردد، یا می‌توانید آن را مستقیماً روی شیء `GPURenderPassEncoder` دریافت و تنظیم کنید.

## مقدار

یک رشته. اگر قبلاً هیچ مقدار برچسبی تنظیم نشده باشد، دریافت برچسب یک رشته خالی برمی‌گرداند.

## مثال‌ها

تنظیم و دریافت یک برچسب از طریق `GPURenderPassEncoder.label`:

```js
const commandEncoder = device.createCommandEncoder();

const renderPassDescriptor = {
  colorAttachments: [
    {
      clearValue: clearColor,
      loadOp: "clear",
      storeOp: "store",
      view: context.getCurrentTexture().createView(),
    },
  ],
};

const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);
passEncoder.label = "my_render_pass_encoder";

console.log(passEncoder.label); // "my_render_pass_encoder"
```

تنظیم یک برچسب از طریق فراخوانی مبدأ {{domxref("GPUCommandEncoder.beginRenderPass()")}} و سپس دریافت آن از طریق `GPURenderPassEncoder.label`:

```js
const commandEncoder = device.createCommandEncoder();

const renderPassDescriptor = {
  colorAttachments: [
    {
      clearValue: clearColor,
      loadOp: "clear",
      storeOp: "store",
      view: context.getCurrentTexture().createView(),
    },
  ],
  label: "my_render_pass_encoder",
};

const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);

console.log(passEncoder.label); // "my_render_pass_encoder"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)