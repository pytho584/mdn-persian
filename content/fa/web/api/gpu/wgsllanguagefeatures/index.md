---
title: "GPU: wgslLanguageFeatures property"
short-title: wgslLanguageFeatures
slug: Web/API/GPU/wgslLanguageFeatures
page-type: web-api-instance-property
browser-compat: api.GPU.wgslLanguageFeatures
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‑خواندنی **`wgslLanguageFeatures`** از رابط {{domxref("GPU")}} یک شیء {{domxref("WGSLLanguageFeatures")}} برمی‌گرداند که [افزونه‌های زبان WGSL](https://gpuweb.github.io/gpuweb/wgsl/#language-extension) پشتیبانی‌شده توسط پیاده‌سازی WebGPU را گزارش می‌دهد.

> [!NOTE]
> همه افزونه‌های زبان WGSL در همه مرورگرهایی که از این API پشتیبانی می‌کنند در دسترس نیستند. توصیه می‌کنیم هر افزونه‌ای که تصمیم به استفاده از آن دارید را به دقت آزمایش کنید.

## مقدار

یک نمونه از شیء {{domxref("WGSLLanguageFeatures")}}. این یک شیء [شبه‌مجموعه](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set) است.

## مثال‌ها

```js
if (!navigator.gpu) {
  throw Error("WebGPU not supported.");
}

const wgslFeatures = navigator.gpu.wgslLanguageFeatures;

// Return the size of the set
console.log(wgslFeatures.size);

// Iterate through all the set values using values()
const valueIterator = wgslFeatures.values();
for (const value of valueIterator) {
  console.log(value);
}

// …
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)