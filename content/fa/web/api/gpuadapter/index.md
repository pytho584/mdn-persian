---
title: GPUAdapter
slug: Web/API/GPUAdapter
page-type: web-api-interface
browser-compat: api.GPUAdapter
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابطهٔ **`GPUAdapter`** در {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} یک آداپتور GPU را نشان می‌دهد. از طریق این رابط می‌توانید یک {{domxref("GPUDevice")}}، اطلاعات آداپتور، ویژگی‌ها و محدودیت‌ها را درخواست کنید.

یک شیء `GPUAdapter` با استفاده از روش {{domxref("GPU.requestAdapter()")}} درخواست می‌شود.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("GPUAdapter.features", "features")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("GPUSupportedFeatures")}} که عملکردهای اضافی پشتیبانی‌شده توسط آداپتور را توصیف می‌کند.
- {{domxref("GPUAdapter.info", "info")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("GPUAdapterInfo")}} حاوی اطلاعات شناسایی دربارهٔ آداپتور.
- {{domxref("GPUAdapter.limits", "limits")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("GPUSupportedLimits")}} که محدودیت‌های پشتیبانی‌شده توسط آداپتور را توصیف می‌کند.

### ویژگی‌های منسوخ‌شده

- {{domxref("GPUAdapter.isFallbackAdapter", "isFallbackAdapter")}} {{ReadOnlyInline}} {{deprecated_inline}} {{non-standard_inline}}
  - : یک مقدار بولین. اگر آداپتور یک [آداپتور جایگزین (fallback)](/en-US/docs/Web/API/GPU/requestAdapter#fallback_adapters) باشد، `true` و در غیر این صورت `false` برمی‌گرداند. این ویژگی از پلتفرم وب حذف شده است. به جای آن از {{domxref("GPUAdapterInfo.isFallbackAdapter")}} استفاده کنید.

## روش‌های نمونه

- {{domxref("GPUAdapter.requestAdapterInfo", "requestAdapterInfo()")}} {{deprecated_inline}} {{non-standard_inline}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که با یک شیء {{domxref("GPUAdapterInfo")}} حاوی اطلاعات شناسایی دربارهٔ آداپتور تکمیل می‌شود.
- {{domxref("GPUAdapter.requestDevice", "requestDevice()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که با یک شیء {{domxref("GPUDevice")}} تکمیل می‌شود؛ این شیء رابط اصلی برای ارتباط با GPU است.

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

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)