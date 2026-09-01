---
title: "GPU"
page-type: web-api-interface
browser-compat: api.GPU
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`GPU`** در {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} نقطه شروع استفاده از WebGPU است. از این رابط می‌توان برای برگرداندن یک {{domxref("GPUAdapter")}} استفاده کرد که از طریق آن می‌توانید دستگاه‌ها را درخواست کنید، ویژگی‌ها و محدودیت‌ها را پیکربندی کنید و موارد دیگر را انجام دهید.

شیء `GPU` برای زمینه جاری از طریق ویژگی‌های {{domxref("Navigator.gpu")}} یا {{domxref("WorkerNavigator.gpu")}} قابل دسترسی است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("GPU.wgslLanguageFeatures", "wgslLanguageFeatures")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("WGSLLanguageFeatures")}} که [افزونه‌های زبان WGSL](https://gpuweb.github.io/gpuweb/wgsl/#language-extension) پشتیبانی‌شده توسط پیاده‌سازی WebGPU را گزارش می‌دهد.

## روش‌های نمونه

- {{domxref("GPU.requestAdapter", "requestAdapter()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که با یک نمونه از شیء {{domxref("GPUAdapter")}} تکمیل می‌شود. از این طریق می‌توانید یک {{domxref("GPUDevice")}} درخواست کنید که رابط اصلی برای استفاده از قابلیت‌های WebGPU است.
- {{domxref("GPU.getPreferredCanvasFormat", "getPreferredCanvasFormat()")}}
  - : فرمت بافت بهینه بوم را برای نمایش محتوای ۸‐بیتی با عمق رنگ استاندارد در سیستم جاری برمی‌گرداند.

## مثال‌ها

### درخواست یک آداپتر و یک دستگاه

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

### پیکربندی GPUCanvasContext با فرمت بافت بهینه

```js
const canvas = document.querySelector("#gpuCanvas");
const context = canvas.getContext("webgpu");

context.configure({
  device,
  format: navigator.gpu.getPreferredCanvasFormat(),
  alphaMode: "premultiplied",
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)