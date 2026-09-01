---
title: GPUDeviceLostInfo
slug: Web/API/GPUDeviceLostInfo
page-type: web-api-interface
browser-compat: api.GPUDeviceLostInfo
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`GPUDeviceLostInfo`** از {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} شیءای را نشان می‌دهد که هنگام حل شدن {{jsxref("Promise")}} مربوط به {{domxref("GPUDevice.lost")}} بازگردانده می‌شود. این اطلاعاتی در مورد دلیل از دست رفتن دستگاه ارائه می‌دهد.

برای اطلاعات بیشتر در مورد وضعیت «از دست رفته» به صفحه {{domxref("GPUDevice.lost")}} مراجعه کنید.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("GPUDeviceLostInfo.message", "message")}} {{ReadOnlyInline}}
  - : یک رشته که یک پیام قابل خواندن برای انسان ارائه می‌دهد و دلیل از دست رفتن دستگاه را توضیح می‌دهد.
- {{domxref("GPUDeviceLostInfo.reason", "reason")}} {{ReadOnlyInline}}
  - : یک مقدار شمارشی که دلیل از دست رفتن دستگاه را به شکلی قابل خواندن برای ماشین تعریف می‌کند.

## مثال‌ها

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
  let device = await adapter.requestDevice(descriptor);

  // Use lost to handle lost devices
  device.lost.then((info) => {
    console.error(`WebGPU device was lost: ${info.message}`);
    device = null;
    if (info.reason !== "destroyed") {
      init();
    }
  });
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط [WebGPU API](/en-US/docs/Web/API/WebGPU_API)