```markdown
---
title: "GPUDevice: adapterInfo property"
short-title: adapterInfo
slug: Web/API/GPUDevice/adapterInfo
page-type: web-api-instance-property
browser-compat: api.GPUDevice.adapterInfo
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط-خواندنی **`adapterInfo`** از رابط {{domxref("GPUDevice")}} یک شیء {{domxref("GPUAdapterInfo")}} برمی‌گرداند که حاوی اطلاعات شناسایی مربوط به آداپتور مبدأ دستگاه است.

## مقدار

یک نمونه از شیء {{domxref("GPUAdapterInfo")}}.

## مثال‌ها

### استفاده پایه از adapterInfo

```js
const adapter = await navigator.gpu.requestAdapter();
if (!adapter) {
  throw Error("Couldn't request WebGPU adapter.");
}

const myDevice = await adapter.requestDevice();

function optimizeForGpuDevice(device) {
  if (device.adapterInfo.vendor === "amd") {
    // Use AMD-specific optimizations
  } else if (device.adapterInfo.architecture.includes("turing")) {
    // Optimize for NVIDIA Turing architecture
  }
}

optimizeForGpuDevice(myDevice);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
```