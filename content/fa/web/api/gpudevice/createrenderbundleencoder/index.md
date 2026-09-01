---
title: "GPUDevice: createRenderBundleEncoder() method"
short-title: createRenderBundleEncoder()
slug: Web/API/GPUDevice/createRenderBundleEncoder
page-type: web-api-instance-method
browser-compat: api.GPUDevice.createRenderBundleEncoder
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`createRenderBundleEncoder()`** از رابط {{domxref("GPUDevice")}} یک {{domxref("GPURenderBundleEncoder")}} ایجاد می‌کند که می‌توان از آن برای ضبط از پیشِ دسته‌ای از دستورات استفاده کرد. این دسته‌ها را می‌توان در {{domxref("GPURenderPassEncoder")}}ها با استفاده از متد {{domxref("GPURenderPassEncoder.executeBundles", "executeBundles()")}}، به تعداد دلخواه، دوباره استفاده کرد.

## نحو (Syntax)

```js-nolint
createRenderBundleEncoder(descriptor)
```

### پارامترها

- `descriptor`
  - : یک شیء حاوی ویژگی‌های زیر:
    - `colorFormats`
      - : آرایه‌ای از مقادیر شمارشی که فرمت‌های رنگی مورد انتظار برای اهداف رندر (render targets) را مشخص می‌کند. برای مقادیر ممکن، به تعریف [`GPUTextureFormat`](https://gpuweb.github.io/gpuweb/#depth-or-stencil-format) در مشخصات فنی مراجعه کنید.
    - `depthReadOnly` {{optional_inline}}
      - : یک مقدار بولی. اگر `true` باشد، مشخص می‌کند که اجرای هر {{domputed("GPURenderBundle")}} ایجاد شده توسط {{domxref("GPURenderBundleEncoder")}}، مؤلفه عمق (depth) `depthStencilFormat` را هنگام اجرا تغییر نخواهد داد. اگر حذف شود، `depthReadOnly` به طور پیش‌فرض `false` خواهد بود.
    - `depthStencilFormat` {{optional_inline}}
      - : یک مقدار شمارشی که فرمت عمق-یا-استنسیل (depth-or-stencil) مورد انتظار برای اهداف رندر را مشخص می‌کند. برای مقادیر ممکن، بخش [فرمت‌های عمق-استنسیل](https://gpuweb.github.io/gpuweb/#depth-or-stencil-format) در مشخصات فنی را ببینید.
    - `label` {{optional_inline}}
      - : رشته‌ای که برچسبی برای شناسایی شیء فراهم می‌کند، برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.
    - `sampleCount` {{optional_inline}}
      - : عددی که تعداد نمونه‌های (sample count) مورد انتظار برای اهداف رندر را مشخص می‌کند.
    - `stencilReadOnly` {{optional_inline}}
      - : یک مقدار بولی. اگر `true` باشد، مشخص می‌کند که اجرای هر {{domputed("GPURenderBundle")}} ایجاد شده توسط {{domxref("GPURenderBundleEncoder")}}، مؤلفه استنسیل (stencil) `depthStencilFormat` را هنگام اجرا تغییر نخواهد داد. اگر حذف شود، `stencilReadOnly` به طور پیش‌فرض `false` خواهد بود.

### مقدار بازگشتی

یک نمونه از شیء {{domxref("GPURenderBundleEncoder")}}.

## مثال‌ها

در نمونه WebGPU با نام [Animometer](https://webgpu.github.io/webgpu-samples/samples/animometer/)، عملیات مشابه متعددی به طور همزمان روی اشیاء مختلف انجام می‌شود. یک دسته از دستورات با استفاده از تابع زیر کدگذاری می‌شود:

```js
function recordRenderPass(
  passEncoder: GPURenderBundleEncoder | GPURenderPassEncoder
) {
  if (settings.dynamicOffsets) {
    passEncoder.setPipeline(dynamicPipeline);
  } else {
    passEncoder.setPipeline(pipeline);
  }
  passEncoder.setVertexBuffer(0, vertexBuffer);
  passEncoder.setBindGroup(0, timeBindGroup);
  const dynamicOffsets = [0];
  for (let i = 0; i < numTriangles; ++i) {
    if (settings.dynamicOffsets) {
      dynamicOffsets[0] = i * alignedUniformBytes;
      passEncoder.setBindGroup(1, dynamicBindGroup, dynamicOffsets);
    } else {
      passEncoder.setBindGroup(1, bindGroups[i]);
    }
    passEncoder.draw(3, 1, 0, 0);
  }
}
```

سپس، یک {{domxref("GPURenderBundleEncoder")}} با استفاده از `createRenderBundleEncoder()` ایجاد می‌شود، تابع فراخوانی می‌شود، و دسته دستورات با استفاده از {{domxref("GPURenderBundleEncoder.finish()")}} در یک {{domxref("GPURenderBundle")}} ضبط می‌شود:

```js
const renderBundleEncoder = device.createRenderBundleEncoder({
  colorFormats: [presentationFormat],
});
recordRenderPass(renderBundleEncoder);
const renderBundle = renderBundleEncoder.finish();
```

سپس از {{domxref("GPURenderPassEncoder.executeBundles()")}} برای استفاده مجدد از کار در چندین پاس رندر (render pass) برای بهبود کارایی استفاده می‌شود. برای زمینه کامل، فهرست کد مثال را مطالعه کنید.

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

## مشخصات فنی

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)