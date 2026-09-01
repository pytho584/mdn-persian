---
title: "GPUAdapter: requestAdapterInfo() method"
short-title: requestAdapterInfo()
slug: Web/API/GPUAdapter/requestAdapterInfo
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.GPUAdapter.requestAdapterInfo
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{deprecated_header}}{{non-standard_header}}{{AvailableInWorkers}}

روش **`requestAdapterInfo()`** از رابط {{domxref("GPUAdapter")}} یک {{jsxref("Promise")}} برمی‌گرداند که با یک شیء {{domxref("GPUAdapterInfo")}} حاوی اطلاعات شناسایی درباره یک آداپتور تکمیل می‌شود.

`requestAdapterInfo()` از مشخصات WebGPU حذف شده است. برای دسترسی به اطلاعات آداپتور از {{domxref("GPUAdapter.info")}} استفاده کنید.

## نحو

```js-nolint
requestAdapterInfo()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک نمونه شیء {{domxref("GPUAdapterInfo")}} تکمیل می‌شود.

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

  const adapterInfo = await adapter.requestAdapterInfo();
  console.log(adapterInfo.vendor);
  console.log(adapterInfo.architecture);

  // …
}
```

## مشخصات

دیگر بخشی از [مشخصات WebGPU](https://gpuweb.github.io/gpuweb/) نیست.

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [API WebGPU](/en-US/docs/Web/API/WebGPU_API)