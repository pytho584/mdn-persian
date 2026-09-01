---
title: "GPUCanvasContext: getCurrentTexture() method"
short-title: getCurrentTexture()
slug: Web/API/GPUCanvasContext/getCurrentTexture
page-type: web-api-instance-method
browser-compat: api.GPUCanvasContext.getCurrentTexture
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`getCurrentTexture()`** در رابط
{{domxref("GPUCanvasContext")}}، شیء {{domxref("GPUTexture")}} بعدی را که قرار است توسط بافت بوم (canvas) در سند ترکیب شود، برمی‌گرداند.

## نحو (Syntax)

```js-nolint
getCurrentTexture()
```

### پارامترها

هیچ.

### مقدار برگشتی

یک نمونه از شیء {{domxref("GPUTexture")}}.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر `getCurrentTexture()` قبل از پیکربندی بافت بوم (یعنی قبل از فراخوانی {{domxref("GPUCanvasContext.configure()")}}) صدا زده شود، پرتاب می‌شود.

## مثال‌ها

```js
const canvas = document.querySelector("#gpuCanvas");
const context = canvas.getContext("webgpu");

context.configure({
  device,
  format: navigator.gpu.getPreferredCanvasFormat(),
  alphaMode: "premultiplied",
});

// …
// بعداً
const commandEncoder = device.createCommandEncoder();

const renderPassDescriptor = {
  colorAttachments: [
    {
      clearValue: [0, 0, 0, 1], // سیاه مات
      loadOp: "clear",
      storeOp: "store",
      view: context.getCurrentTexture().createView(),
    },
  ],
};

const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)