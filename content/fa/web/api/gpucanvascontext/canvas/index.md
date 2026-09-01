---
title: "GPUCanvasContext: canvas property"
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‑خواندنی **`canvas`** از رابط {{domxref("GPUCanvasContext")}} یک ارجاع به canvasای که بافتار (context) از آن ایجاد شده است برمی‌گرداند.

## مقدار

یک نمونه شیء (object instance) از {{domxref("HTMLCanvasElement")}} یا {{domxref("OffscreenCanvas")}}.

## مثال‌ها

```js
const canvas = document.querySelector("#gpuCanvas");
const context = canvas.getContext("webgpu");

// returns an HTMLCanvasElement reference
context.canvas;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)