---
title: "GPURenderPassEncoder: beginOcclusionQuery() method"
short-title: beginOcclusionQuery()
slug: Web/API/GPURenderPassEncoder/beginOcclusionQuery
page-type: web-api-instance-method
browser-compat: api.GPURenderPassEncoder.beginOcclusionQuery
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`beginOcclusionQuery()`** از رابط {{domxref("GPURenderPassEncoder")}} یک پرس‌وجوی محو شدگی (occlusion query) را در ایندکس مشخص شده از {{domxref("GPUQuerySet")}} مرتبط شروع می‌کند (این `GPUQuerySet` به عنوان مقدار ویژگی `occlusionQuerySet` در توصیف‌کننده هنگام فراخوانی {{domxref("GPUCommandEncoder.beginRenderPass()")}} برای اجرای رندرپس ارائه می‌شود).

## نحو (Syntax)

```js-nolint
beginOcclusionQuery(queryIndex)
```

### پارامترها

- `queryIndex`
  - : ایندکس در {{domxref("GPUQuerySet")}} که پرس‌وجوی محو شدگی از آن شروع می‌شود.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### اعتبارسنجی (Validation)

هنگام فراخوانی **`beginOcclusionQuery()`** معیارهای زیر باید برآورده شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} ایجاد می‌شود و {{domxref("GPURenderPassEncoder")}} نامعتبر می‌گردد:

- یک {{domxref("GPUQuerySet")}} در ویژگی `occlusionQuerySet` توصیف‌کننده هنگام فراخوانی {{domxref("GPUCommandEncoder.beginRenderPass()")}} مبدأ مشخص شده باشد.
- `queryIndex` کوچکتر از {{domxref("GPUQuerySet.count")}} باشد.
- `queryIndex` قبلاً در همان رندرپس نوشته نشده باشد.
- هیچ پرس‌وجوی محو شدگی دیگری برای این رندرپس فعال نباشد (یعنی از طریق فراخوانی قبلی `beginOcclusionQuery()`).

## مثال‌ها

```js
// …

// ساخت یک مجموعه پرس‌وجو برای نگهداری پرس‌وجوهای محو شدگی
const querySet = device.createQuerySet({
  type: "occlusion",
  count: 32,
});

// شیء توصیف‌کننده رندرپس، شامل querySet
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

// شروع رندرپس
const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);

// شروع یک پرس‌وجوی محو شدگی در ایندکس 0
passEncoder.beginOcclusionQuery(0);

// اجرای برخی دستورات رندرینگ
passEncoder.setPipeline(renderPipeline);
passEncoder.setVertexBuffer(0, vertexBuffer);
passEncoder.draw(3);

// پایان پرس‌وجوی محو شدگی
passEncoder.endOcclusionQuery();

// …
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)