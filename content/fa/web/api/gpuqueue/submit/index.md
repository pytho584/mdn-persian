---
title: "GPUQueue: submit() method"
---

---
title: "GPUQueue: submit() method"
short-title: submit()
slug: Web/API/GPUQueue/submit
page-type: web-api-instance-method
browser-compat: api.GPUQueue.submit
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متود **`submit()`** از رابط {{domxref("GPUQueue")}} اجرای بافرهای فرمان را که توسط یک یا چند شیء {{domacro("GPUCommandBuffer")}} نمایش داده می‌شوند، توسط GPU زمان‌بندی می‌کند.

## نحو (Syntax)

```js-nolint
submit(commandBuffers)
```

### پارامترها

- `commandBuffers`
  - : آرایه‌ای از اشیاء {{domxref("GPUCommandBuffer")}} شامل فرمان‌هایی که باید برای پردازش توسط GPU در صف قرار گیرند. این آرایه نباید حاوی اشیاء تکراری `GPUCommandBuffer` باشد — هر یک فقط می‌تواند یک بار در هر فراخوانی `submit()` ارسال شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### اعتبارسنجی

هنگام فراخوانی **`submit()`** معیارهای زیر باید برآورده شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} ایجاد شده و {{domxref("GPUQueue")}} نامعتبر می‌شود:

- آرایه‌ای از اشیاء {{domxref("GPUCommandBuffer")}} که در فراخوانی `submit()` ارجاع شده‌اند، حاوی موارد تکراری نباشد.
- هر شیء {{domxref("GPUBuffer")}}، {{domxref("GPUTexture")}} و {{domxref("GPUQuerySet")}} که در فرمان‌های رمزگذاری‌شده استفاده شده‌اند، برای استفاده در دسترس باشند؛ یعنی در دسترس نبودن‌ (عدم دسترسی `GPUBuffer` زمانی است که در حال {{domxref("GPUBuffer.mapAsync", "mapped", "", "nocode")}} هستند یا با متود `destroy()` نابود شده‌اند) وجود نداشته باشد.
- هر شیء {{domxref("GPUExternalTexture")}} که در فرمان‌های رمزگذاری‌شده استفاده شده‌اند منقضی نشده باشند (آن‌ها به طور خودکار مدت کوتاهی پس از وارد شدن از طریق {{domxref("GPUDevice.importExternalTexture", "importExternalTexture()")}} منقضی می‌شوند).
- اگر شیء {{domxref("GPUQuerySet")}} مورد استفاده در یک فرمان رمزگذاری‌شده از نوع query `"occlusion"` باشد، قبلاً استفاده نشده باشد، به جز توسط {{domxref("GPURenderPassEncoder.beginOcclusionQuery()")}}.

## مثال‌ها

در [نمونه‌ی رندر پایه](https://mdn.github.io/dom-examples/webgpu-render-demo/) ما، تعدادی فرمان از طریق یک {{domxref("GPUCommandEncoder")}} ثبت می‌شوند:

```js
// …

// ایجاد GPUCommandEncoder
const commandEncoder = device.createCommandEncoder();

// ایجاد GPURenderPassDescriptor برای تعیین اینکه WebGPU به کدام بافت رسم کند، سپس شروع رندر پاس

const renderPassDescriptor = {
  colorAttachments: [
    {
      clearValue: clearColor,
      loadOp: "clear",
      storeOp: "store",
      view: context.getCurrentTexture().createView(),
    },
  ],
};

const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);

// رسم یک مثلث

passEncoder.setPipeline(renderPipeline);
passEncoder.setVertexBuffer(0, vertexBuffer);
passEncoder.draw(3);

// پایان رندر پاس

passEncoder.end();

// …
```

فرمان‌های رمزگذاری‌شده توسط {{domxref("GPUCommandEncoder")}} با استفاده از متود {{domxref("GPUCommandEncoder.finish()")}} در یک {{domxref("GPUCommandBuffer")}} بازنویسی می‌شوند. سپس بافر فرمان از طریق یک فراخوانی `submit()` به صف ارسال می‌شود، آماده برای پردازش توسط GPU.

```js
device.queue.submit([commandEncoder.finish()]);
```

> [!NOTE]
> برای دیدن نمونه‌های بیشتر از صف، به [نمونه‌های WebGPU](https://webgpu.github.io/webgpu-samples/) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)