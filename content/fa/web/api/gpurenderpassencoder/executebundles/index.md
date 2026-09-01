---
title: "GPURenderPassEncoder: executeBundles() method"
---

---
title: "GPURenderPassEncoder: executeBundles() method"
short-title: executeBundles()
slug: Web/API/GPURenderPassEncoder/executeBundles
page-type: web-api-instance-method
browser-compat: api.GPURenderPassEncoder.executeBundles
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`executeBundles()`** از رابط {{domxref("GPURenderPassEncoder")}} دستوراتی را که قبلاً در {{domxref("GPURenderBundle")}}های ارجاع‌شده ضبط شده‌اند، به عنوان بخشی از این رندر پاس اجرا می‌کند.

> [!NOTE]
> پس از فراخوانی `executeBundles()`، بافرهای رأس (vertex buffers)، بافرهای ایندکس (index buffers)، گروه‌های بایند (bind groups) و پایپ‌لاین (pipeline) که در حال حاضر تنظیم شده‌اند، همگی پاک می‌شوند، حتی اگر هیچ باندلی واقعاً اجرا نشود.

## نحو (Syntax)

```js-nolint
executeBundles(bundles)
```

### پارامترها

- `bundles`
  - یک آرایه از اشیاء {{domxref("GPURenderBundle")}} که شامل دستورات از پیش ضبط‌شده برای اجرا هستند.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### اعتبارسنجی

معیارهای زیر باید هنگام فراخوانی **`executeBundles()`** رعایت شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و {{domxref("GPURenderPassEncoder")}} نامعتبر می‌شود.

برای هر {{domxref("GPURenderBundle")}}:

- اگر ویژگی `depthReadOnly` رندر پاس (که در توصیف‌کننده فراخوانی مبدأ {{domxref("GPUCommandEncoder.beginRenderPass()")}} مشخص شده است) `true` باشد، آنگاه ویژگی `depthReadOnly` باندل (که در توصیف‌کننده فراخوانی {{domxref("GPUDevice.createRenderBundleEncoder()")}} که {{domxref("GPURenderBundleEncoder")}} مبدأ را ایجاد کرده است مشخص شده است) نیز `true` است.
- اگر ویژگی `stencilReadOnly` رندر پاس `true` باشد، آنگاه ویژگی `stencilReadOnly` باندل نیز `true` است.
- چیدمان (layout) پایپ‌لاین رندر مشخص‌شده در {{domxref("GPURenderPassEncoder.setPipeline()")}} (که در توصیف‌کننده فراخوانی مبدأ {{domxref("GPUDevice.createRenderPipeline()")}} تعریف شده است) با چیدمان پایپ‌لاین رندر باندل مشخص‌شده در {{domxref("GPURenderBundleEncoder.setPipeline()")}} برابر است.

## مثال‌ها

در مثال Animometer از نمونه‌های WebGPU، عملیات مشابه زیادی به طور همزمان روی اشیاء مختلف انجام می‌شود. از `executeBundles()` برای استفاده مجدد از کار روی چندین رندر پاس به منظور بهبود عملکرد استفاده می‌شود. برای زمینه کامل، فهرست کد مثال را مطالعه کنید.

```js
// …

return function doDraw(timestamp) {
  if (startTime === undefined) {
    startTime = timestamp;
  }
  uniformTime[0] = (timestamp - startTime) / 1000;
  device.queue.writeBuffer(uniformBuffer, timeOffset, uniformTime.buffer);

  renderPassDescriptor.colorAttachments[0].view = context
    .getCurrentTexture()
    .createView();

  const commandEncoder = device.createCommandEncoder();
  const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);

  if (settings.renderBundles) {
    passEncoder.executeBundles([renderBundle]);
  } else {
    recordRenderPass(passEncoder);
  }

  passEncoder.end();
  device.queue.submit([commandEncoder.finish()]);
};

// …
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)