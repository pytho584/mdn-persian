---
title: "GPUDevice: queue property"
short-title: queue
slug: Web/API/GPUDevice/queue
page-type: web-api-instance-property
browser-compat: api.GPUDevice.queue
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژصیت فقط‌خواندنی **`queue`** در رابط {{domxref("GPUDevice")}}، صف اصلی {{domxref("GPUQueue")}} مربوط به دستگاه را برمی‌گرداند.

## مقدار

یک نمونه از شیء {{domxref("GPUQueue")}}.

## مثال‌ها

دسترسی پایه به {{domxref("GPUQueue")}}:

```js
async function init() {
  if (!navigator.gpu) {
    throw Error("WebGPU not supported.");
  }

  const adapter = await navigator.gpu.requestAdapter();
  if (!adapter) {
    throw Error("Couldn't request WebGPU adapter.");
  }

  // Create a GPUDevice
  const device = await adapter.requestDevice();

  // …

  // Common queue use — end current frame by passing array of
  // command buffers to queue for execution
  device.queue.submit([commandEncoder.finish()]);

  // …
}
```

> [!NOTE]
> برای مشاهده مثال‌های بیشتر درباره صف، به صفحات مرجع {{domxref("GPUQueue")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)