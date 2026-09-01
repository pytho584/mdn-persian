```yaml
---
title: "GPUCanvasContext: unconfigure() method"
short-title: unconfigure()
slug: Web/API/GPUCanvasContext/unconfigure
page-type: web-api-instance-method
browser-compat: api.GPUCanvasContext.unconfigure
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`unconfigure()``** از رابط {{domxref("GPUCanvasContext")}} هر گونه پیکربندی زمینه‌ای که قبلاً تنظیم شده است را حذف کرده و تمام بافت‌هایی را که از طریق {{domxref("GPUCanvasContext.getCurrentTexture", "getCurrentTexture()")}} در حالی که زمینه بوم (canvas context) پیکربندی شده بود، بازگردانده شده‌اند، نابود می‌کند.

## Syntax

```js-nolint
unconfigure()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

هیچ‌کدام (`undefined`).

## مثال‌ها

```js
const canvas = document.querySelector("#gpuCanvas");
const context = canvas.getContext("webgpu");

context.configure({
  device,
  format: navigator.gpu.getPreferredCanvasFormat(),
  alphaMode: "premultiplied",
});

// بعداً
context.unconfigure();
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
```