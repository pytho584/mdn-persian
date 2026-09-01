---
title: "GPUAdapterInfo: subgroupMaxSize property"
short-title: subgroupMaxSize
slug: Web/API/GPUAdapterInfo/subgroupMaxSize
page-type: web-api-instance-property
browser-compat: api.GPUAdapterInfo.subgroupMaxSize
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط خواندنی **`subgroupMaxSize`** در رابط {{domxref("GPUAdapterInfo")}}، حداکثر [اندازه زیرگروه](https://gpuweb.github.io/gpuweb/wgsl/#subgroup-size) پشتیبانی‌شده برای {{domxref("GPUAdapter")}} را برمی‌گرداند. این ویژگی می‌تواند همراه با [ویژگی](https://developer.mozilla.org/en-US/docs/Web/API/GPUSupportedFeatures) `subgroups` استفاده شود.

## مقدار

یک عدد.

## مثال‌ها

```js
const adapter = await navigator.gpu.requestAdapter();
if (!adapter) {
  throw Error("Couldn't request WebGPU adapter.");
}

const adapterInfo = adapter.info;
console.log(adapterInfo.subgroupMaxSize);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [API WebGPU](/en-US/docs/Web/API/WebGPU_API)