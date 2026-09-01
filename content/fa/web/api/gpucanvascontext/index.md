---
title: GPUCanvasContext
slug: Web/API/GPUCanvasContext
page-type: web-api-interface
browser-compat: api.GPUCanvasContext
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`GPUCanvasContext`** از {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} نمایانگر زمینه‌ی رندر WebGPU یک عنصر {{htmlelement("canvas")}} است که از طریق فراخوانی {{domxref("HTMLCanvasElement.getContext()")}} با `contextType` برابر با `"webgpu"` بازگردانده می‌شود.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("GPUCanvasContext.canvas", "canvas")}} {{ReadOnlyInline}}
  - : یک ارجاع به بوم‌رنگی (canvas) که زمینه از آن ایجاد شده است را بازمی‌گرداند.

## روش‌های نمونه

- {{domxref("GPUCanvasContext.configure", "configure()")}}
  - : زمینه را برای استفاده در رندرگیری با یک {{domxref("GPUDevice")}} مشخص پیکربندی می‌کند و بوم‌رنگ را به رنگ سیاه شفاف پاک می‌کند.
- {{domxref("GPUCanvasContext.getConfiguration", "getConfiguration()")}}
  - : پیکربندی جاری تنظیم‌شده برای زمینه را بازمی‌گرداند.
- {{domxref("GPUCanvasContext.getCurrentTexture", "getCurrentTexture()")}}
  - : {{domxref("GPUTexture")}} بعدی را که توسط زمینه‌ی بوم‌رنگ به سند ترکیب (composite) خواهد شد، بازمی‌گرداند.
- {{domxref("GPUCanvasContext.unconfigure", "unconfigure()")}}
  - : هر پیکربندی زمینه‌ای که پیشتر تنظیم شده است را حذف می‌کند و تمام بافت‌هایی (textures) را که در هنگام پیکربندی زمینه‌ی بوم‌رنگ تولید شده‌اند، نابود می‌کند.

## مثال‌ها

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

## جستارهای وابسته

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)