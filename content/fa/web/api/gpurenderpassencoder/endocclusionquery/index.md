---
title: "GPURenderPassEncoder: endOcclusionQuery() method"
short-title: endOcclusionQuery()
slug: Web/API/GPURenderPassEncoder/endOcclusionQuery
page-type: web-api-instance-method
browser-compat: api.GPURenderPassEncoder.endOcclusionQuery
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`endOcclusionQuery()`** در رابط {{domxref("GPURenderPassEncoder")}} یک پرس‌وجوی انسداد فعال را که قبلاً با {{domxref("GPURenderPassEncoder.beginOcclusionQuery", "beginOcclusionQuery()")}} شروع شده است، به پایان می‌رساند.

## نحو

```js-nolint
endOcclusionQuery()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### اعتبارسنجی

هنگام فراخوانی **`endOcclusionQuery()`**، معیارهای زیر باید برقرار باشند؛ در غیر این صورت، یک {{domxref("GPUValidationError")}} تولید شده و {{domxref("GPURenderPassEncoder")}} نامعتبر می‌شود:

- یک پرس‌وجوی انسداد برای این گذر رندر فعال باشد (یعنی از طریق فراخوانی قبلی `beginOcclusionQuery()`).

## مثال‌ها

```js
// …

// Create a query set to hold the occlusion queries
const querySet = device.createQuerySet({
  type: "occlusion",
  count: 32,
});

// Render pass descriptor object, including the querySet
const renderPassDescriptor = {
  colorAttachments: [
    {
      clearValue: clearColor,
      loadOp: "clear",
      storeOp: "store",
      view: context.getCurrentTexture().createView(),
    },
  ],
  occlusionQuerySet: querySet,
};

// Begin the render pass
const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);

// Begin an occlusion query at index 0
passEncoder.beginOcclusionQuery(0);

// Run some rendering commands
passEncoder.setPipeline(renderPipeline);
passEncoder.setVertexBuffer(0, vertexBuffer);
passEncoder.draw(3);

// End the occlusion query
passEncoder.endOcclusionQuery();

// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)