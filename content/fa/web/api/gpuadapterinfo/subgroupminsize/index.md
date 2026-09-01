---
title: "GPUAdapterInfo: subgroupMinSize property"
short-title: subgroupMinSize
slug: Web/API/GPUAdapterInfo/subgroupMinSize
page-type: web-api-instance-property
browser-compat: api.GPUAdapterInfo.subgroupMinSize
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

خاصیت فقط‌خواندنی **`subgroupMinSize`** در رابط {{domxref("GPUAdapterInfo")}}، حداقل [اندازه زیرگروه](https://gpuweb.github.io/gpuweb/wgsl/#subgroup-size) پشتیبانی‌شده را برای {{domxref("GPUAdapter")}} برمی‌گرداند. می‌توان از آن همراه با [ویژگی](/en-US/docs/Web/API/GPUSupportedFeatures) `subgroups` استفاده کرد.

## مقدار

یک عدد.

## مثال‌ها

```js
const adapter = await navigator.gpu.requestAdapter();
if (!adapter) {
  throw Error("Couldn't request WebGPU adapter.");
}

const adapterInfo = adapter.info;
console.log(adapterInfo.subgroupMinSize);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)