---
title: "GPUAdapterInfo: device property"
short-title: device
slug: Web/API/GPUAdapterInfo/device
page-type: web-api-instance-property
browser-compat: api.GPUAdapterInfo.device
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

خاصیت فقط‌خواندنی **`device`** از رابط {{domxref("GPUAdapterInfo")}} یک شناسه مخصوص فروشنده برای آداپتور را بازمی‌گرداند، یا اگر در دسترس نباشد، یک رشته خالی.

## مقدار

یک رشته.

## مثال‌ها

```js
const adapter = await navigator.gpu.requestAdapter();
if (!adapter) {
  throw Error("Couldn't request WebGPU adapter.");
}

const adapterInfo = adapter.info;
console.log(adapterInfo.device);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط [WebGPU API](/en-US/docs/Web/API/WebGPU_API)