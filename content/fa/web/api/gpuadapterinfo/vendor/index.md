---
title: "GPUAdapterInfo: vendor property"
short-title: vendor
slug: Web/API/GPUAdapterInfo/vendor
page-type: web-api-instance-property
browser-compat: api.GPUAdapterInfo.vendor
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط-خواندنی **`vendor`** از رابط {{domxref("GPUAdapterInfo")}} نام تولیدکننده آداپتور را برمی‌گرداند، یا اگر در دسترس نباشد یک رشته خالی.

## مقدار

یک رشته.

## مثال‌ها

```js
const adapter = await navigator.gpu.requestAdapter();
if (!adapter) {
  throw Error("Couldn't request WebGPU adapter.");
}

const adapterInfo = adapter.info;
console.log(adapterInfo.vendor);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [The WebGPU API](/en-US/docs/Web/API/WebGPU_API)