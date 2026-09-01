---
title: "GPUCommandBuffer"
---

---
title: GPUCommandBuffer
slug: Web/API/GPUCommandBuffer
page-type: web-api-interface
browser-compat: api.GPUCommandBuffer
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`GPUCommandBuffer`** در {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} نمایانگر فهرستی از پیش ضبط‌شده از دستورات GPU است که می‌توان برای اجرا به یک {{domxref("GPUQueue")}} ارسال کرد.

یک `GPUCommandBuffer` از طریق متد {{domxref("GPUCommandEncoder.finish()")}} ایجاد می‌شود؛ دستورات GPU ثبت‌شده در آن با ارسال `GPUCommandBuffer` به‌عنوان پارامتر فراخوانی {{domxref("GPUQueue.submit()")}} برای اجرا ارسال می‌شوند.

> [!NOTE]
> وقتی یک شیء `GPUCommandBuffer` ارسال شد، دیگر نمی‌توان از آن استفاده کرد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("GPUCommandBuffer.label", "label")}}
  - : رشته‌ای که برچسبی برای شناسایی شیء فراهم می‌کند، برای مثال در پیام‌های {{domxref("GPUError")}} یا اخطارهای کنسول.

## مثال‌ها

```js
// …

const commandBuffer = commandEncoder.finish();
device.queue.submit([commandBuffer]);
```

> [!NOTE]
> برای مشاهدهٔ مثال‌های کامل، [نمونه‌های WebGPU](https://webgpu.github.io/webgpu-samples/) را مطالعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)