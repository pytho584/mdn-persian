---
title: "GPUAdapterInfo: isFallbackAdapter property"
short-title: isFallbackAdapter
slug: Web/API/GPUAdapterInfo/isFallbackAdapter
page-type: web-api-instance-property
browser-compat: api.GPUAdapterInfo.isFallbackAdapter
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`isFallbackAdapter`** از رابط {{domxref("GPUAdapterInfo")}} مقدار `true` را برمی‌گرداند اگر آداپتور یک [آداپتور جایگزین (fallback)](/en-US/docs/Web/API/GPU/requestAdapter#fallback_adapters) باشد و در غیر این صورت مقدار `false` را برمی‌گرداند.

## مقدار

یک مقدار بولین.

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

  const isFallback = adapter.info.isFallbackAdapter;
  console.log(isFallback);

  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
