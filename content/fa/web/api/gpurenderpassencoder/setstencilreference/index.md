---
title: "GPURenderPassEncoder: setStencilReference() method"
---

---
title: "GPURenderPassEncoder: setStencilReference() method"
short-title: setStencilReference()
slug: Web/API/GPURenderPassEncoder/setStencilReference
page-type: web-api-instance-method
browser-compat: api.GPURenderPassEncoder.setStencilReference
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`setStencilReference()`** از رابط {{domxref("GPURenderPassEncoder")}} مقدار مرجع استنسیل را تنظیم می‌کند که در طول آزمایش‌های استنسیل با عملیات استنسیل `"replace"` (همان‌طور که در توصیف‌گر متد {{domxref("GPUDevice.createRenderPipeline()")}}، در ویژگی‌های تعریف‌کننده عملیات‌های مختلف استنسیل تنظیم شده است) استفاده می‌شود.

## نحو (Syntax)

```js-nolint
setStencilReference(reference)
```

### پارامترها

- `reference`
  - : عددی که مقدار مرجع استنسیل جدید را برای تنظیم در رندرپاس مشخص می‌کند.

> [!NOTE]
> اگر فراخوانی `setStencilReference()` انجام نشود، مقدار مرجع استنسیل برای هر رندرپاس به‌طور پیش‌فرض 0 است.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

```js
// …

const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);

passEncoder.setPipeline(renderPipeline);
passEncoder.setVertexBuffer(0, vertexBuffer);
passEncoder.setStencilReference(1);
passEncoder.draw(3);

passEncoder.end();

// …
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)