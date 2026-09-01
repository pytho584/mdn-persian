---
title: "GPUAdapterInfo: architecture property"
short-title: architecture
slug: Web/API/GPUAdapterInfo/architecture
page-type: web-api-instance-property
browser-compat: api.GPUAdapterInfo.architecture
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`architecture`** در رابط {{domxref("GPUAdapterInfo")}} نام خانواده یا کلاس GPUهایی را که آداپتور به آن تعلق دارد بازمی‌گرداند؛ یا در صورت در دسترس نبودن، یک رشته خالی.

## مقدار

یک رشته.

## نمونه‌ها

```js
const adapter = await navigator.gpu.requestAdapter();
if (!adapter) {
  throw Error("Couldn't request WebGPU adapter.");
}

const adapterInfo = adapter.info;
console.log(adapterInfo.architecture);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)