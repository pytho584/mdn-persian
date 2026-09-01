---
title: GPUBindGroup
slug: Web/API/GPUBindGroup
page-type: web-api-interface
browser-compat: api.GPUBindGroup
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`GPUBindGroup`** از {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} بر اساس یک {{domxref("GPUBindGroupLayout")}} است و مجموعه‌ای از منابع را تعریف می‌کند که در یک گروه به هم متصل می‌شوند و همچنین نحوه استفاده از این منابع را در مراحل شیدر مشخص می‌کند.

یک نمونه از شیء `GPUBindGroup` با استفاده از متد {{domxref("GPUDevice.createBindGroup()")}} ایجاد می‌شود.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("GPUBindGroup.label", "label")}}
  - : رشته‌ای که برچسبی برای شناسایی شیء فراهم می‌کند؛ برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

## مثال‌ها

> [!NOTE]
> [WebGPU samples](https://webgpu.github.io/webgpu-samples/) شامل مثال‌های بسیار بیشتری هستند.

### مثال پایه

در [دموی محاسبات پایه](https://mdn.github.io/dom-examples/webgpu-compute-demo/) ما، نمونه‌ای از ایجاد چیدمان گروه اتصال و سپس استفاده از آن به‌عنوان قالب برای ساخت یک گروه اتصال نشان داده شده است.

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

// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)