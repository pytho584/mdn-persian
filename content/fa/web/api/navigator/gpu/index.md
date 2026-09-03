---
title: "Navigator: gpu property"
short-title: gpu
slug: Web/API/Navigator/gpu
page-type: web-api-instance-property
browser-compat: api.Navigator.gpu
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}

ویژگی فقط‌خواندنی **`Navigator.gpu`** شیء {{domxref("GPU")}} را برای بافت مرورِ جاری (browsing context) برمی‌گرداند؛ این شیء نقطهٔ ورود به {{domxref("WebGPU_API", "WebGPU API", "", "nocode")}} است.

## مقدار

یک شیء {{domxref("GPU")}}.

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

  const device = await adapter.requestDevice();

  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebGPU_API", "WebGPU API", "", "nocode")}}