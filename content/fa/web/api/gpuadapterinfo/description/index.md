---
title: "GPUAdapterInfo: description property"
short-title: description
slug: Web/API/GPUAdapterInfo/description
page-type: web-api-instance-property
browser-compat: api.GPUAdapterInfo.description
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`description`** در رابط {{domxref("GPUAdapterInfo")}} یک رشته قابل‌خواندن برای انسان برمی‌گرداند که آداپتور را توصیف می‌کند، یا اگر در دسترس نباشد، یک رشته خالی.

## مقدار

یک رشته.

## مثال‌ها

```js
const adapter = await navigator.gpu.requestAdapter();
if (!adapter) {
  throw Error("Couldn't request WebGPU adapter.");
}

const adapterInfo = adapter.info;
console.log(adapterInfo.description);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)