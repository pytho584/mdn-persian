---
title: "GPUCanvasContext: getConfiguration() method"
---

---
title: "GPUCanvasContext: getConfiguration() method"
short-title: getConfiguration()
slug: Web/API/GPUCanvasContext/getConfiguration
page-type: web-api-instance-method
browser-compat: api.GPUCanvasContext.getConfiguration
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`getConfiguration()`** از رابط {{domxref("GPUCanvasContext")}}، پیکربندی فعلیِ تنظیم‌شده برای context را برمی‌گرداند.

## نحو

```js-nolint
getConfiguration()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء حاوی گزینه‌های پیکربندیِ تنظیم‌شده روی context (یعنی از طریق متد {{domxref("GPUCanvasContext.configure()")}})، یا `null` اگر هیچ پیکربندی‌ای تنظیم نشده باشد (یا اینکه قبلاً هیچ پیکربندی‌ای تنظیم نشده است، یا پیکربندی تنظیم شده و سپس {{domxref("GPUCanvasContext.unconfigure()")}} روی context فراخوانی شده است).

## مثال‌ها

```js
const canvas = document.querySelector("canvas");
const context = canvas.getContext("webgpu");

if (!navigator.gpu) {
  throw Error("WebGPU not supported.");
}

const adapter = await navigator.gpu.requestAdapter();
if (!adapter) {
  throw Error("Couldn't request WebGPU adapter.");
}

const device = await adapter.requestDevice();

context.configure({
  device,
  format: navigator.gpu.getPreferredCanvasFormat(),
  alphaMode: "premultiplied",
});

console.log(context.getConfiguration());
/* Logs something like:

{
  "alphaMode": "premultiplied",
  "colorSpace": "srgb",
  "device": { ... },
  "format": "bgra8unorm",
  "toneMapping": {
      "mode": "standard"
  },
  "usage": 16,
  "viewFormats": []
}
*/
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("GPUCanvasContext.configure()")}}
- رابط [WebGPU API](/en-US/docs/Web/API/WebGPU_API)