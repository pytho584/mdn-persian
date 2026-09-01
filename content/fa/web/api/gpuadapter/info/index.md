---
title: "GPUAdapter: info property"
short-title: info
slug: Web/API/GPUAdapter/info
page-type: web-api-instance-property
browser-compat: api.GPUAdapter.info
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`info`** در رابط {{domxref("GPUAdapter")}} یک شیء {{domxref("GPUAdapterInfo")}} برمی‌گرداند که حاوی اطلاعات شناسایی دربارهٔ آداپتور است.

## مقدار

یک نمونهٔ شیء {{domxref("GPUAdapterInfo")}}.

## مثال‌ها

### استفادهٔ پایه از info

```js
const adapter = await navigator.gpu.requestAdapter();
if (!adapter) {
  throw Error("Couldn't request WebGPU adapter.");
}

const adapterInfo = adapter.info;
console.log(adapterInfo.vendor);
console.log(adapterInfo.architecture);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)