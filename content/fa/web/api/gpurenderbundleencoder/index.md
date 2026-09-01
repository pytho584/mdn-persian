---
title: GPURenderBundleEncoder
slug: Web/API/GPURenderBundleEncoder
page-type: web-api-interface
browser-compat: api.GPURenderBundleEncoder
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`GPURenderBundleEncoder`** در {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} برای از پیش ضبط کردن دسته‌ای از دستورات (bundles of commands) استفاده می‌شود.

دسته‌های فرمان با فراخوانی متدهای `GPURenderBundleEncoder` کدگذاری می‌شوند؛ پس از کدگذاری دستورات مورد نظر، آن‌ها با استفاده از متد {{domxref("GPURenderBundleEncoder.finish()")}} در یک نمونه از شیء {{domporf("GPURenderBundle")}} ثبت می‌شوند. این دسته‌های رندر (render bundles) سپس می‌توانند در چندین رندر پاس (render pass) با ارسال اشیاء `GPURenderBundle` به فراخوانی‌های {{domxref("GPURenderPassEncoder.executeBundles()")}} مورد استفاده مجدد قرار گیرند.

در واقع، این مانند یک رندر پاس جزئی است — `GPURenderBundleEncoder`ها تمام عملکردهای مشابه {{domxref("GPURenderPassEncoder")}} را دارند، با این تفاوت که نمی‌توانند کوئری‌های انسداد (occlusion queries) را شروع یا پایان دهند و نمی‌توانند مستطیل برش (scissor rect)، نمای دید (viewport)، ثابت ترکیب (blend constant) و مرجع استنسیل (stencil reference) را تنظیم کنند. `GPURenderBundle` همه این مقادیر را از {{domxref("GPURenderPassEncoder")}} که آن را اجرا می‌کند به ارث می‌برد.

> [!NOTE]
> بافرهای رأس (vertex buffers)، بافرهای ایندکس (index buffers)، گروه‌های اتصال (bind groups) و پایپ‌لاین (pipeline) که در حال حاضر تنظیم شده‌اند، قبل از اجرای یک رندر باندل و پس از پایان اجرای آن، همگی پاک می‌شوند.

استفاده مجدد از دستورات از پیش ضبط‌شده می‌تواند عملکرد برنامه را در شرایطی که سربار فراخوانی‌های رسم جاوااسکریپت (JavaScript draw call overhead) یک گلوگاه است، به‌طور قابل توجهی بهبود بخشد. رندر باندل‌ها در شرایطی بیشترین کارایی را دارند که یک دسته از اشیاء به همان روش در چندین دید یا فریم رسم می‌شوند و تنها تفاوت‌ها در محتوای بافر مورد استفاده است (مانند ماتریس‌های یکنواخت به‌روزرسانی‌شده). یک مثال خوب، رندرینگ واقعیت مجازی (VR) است. ضبط رندر به‌عنوان یک رندر باندل و سپس تنظیم ماتریس دید و پخش مجدد آن برای هر چشم، روشی کارآمدتر برای صدور فراخوانی‌های رسم برای هر دو رندر از صحنه است.

یک نمونه شیء `GPURenderBundleEncoder` از طریق ویژگی {{domxref("GPUDevice.createRenderBundleEncoder()")}} ایجاد می‌شود.

> [!NOTE]
> متدهای `GPURenderBundleEncoder` از نظر عملکردی با معادل‌های موجود در {{domxref("GPURenderPassEncoder")}} یکسان هستند، به جز {{domxref("GPURenderBundleEncoder.finish()")}} که از نظر هدف مشابه {{domxref("GPUCommandEncoder.finish()")}} است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("GPURenderBundleEncoder.label", "label")}}
  - : یک رشته که برچسبی را ارائه می‌دهد که می‌تواند برای شناسایی شیء استفاده شود، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

## روش‌های نمونه

- {{domxref("GPURenderBundleEncoder.draw", "draw()")}}
  - : رسم اولیه‌ها (primitives) بر اساس بافرهای رأس ارائه‌شده توسط {{domxref("GPURenderBundleEncoder.setVertexBuffer", "setVertexBuffer()")}}.
- {{domxref("GPURenderBundleEncoder.drawIndexed", "drawIndexed()")}}
  - : رسم اولیه‌های ایندکس‌دار بر اساس بافرهای رأس و ایندکس ارائه‌شده توسط {{domxref("GPURenderBundleEncoder.setVertexBuffer", "setVertexBuffer()")}} و {{domxref("GPURenderBundleEncoder.setIndexBuffer", "setIndexBuffer()")}}.
- {{domxref("GPURenderBundleEncoder.drawIndirect", "drawIndirect()")}}
  - : رسم اولیه‌ها با استفاده از پارامترهایی که از یک {{domxref("GPUBuffer")}} خوانده می‌شوند.
- {{domxref("GPURenderBundleEncoder.drawIndexedIndirect", "drawIndexedIndirect()")}}
  - : رسم اولیه‌های ایندکس‌دار با استفاده از پارامترهایی که از یک {{domxref("GPUBuffer")}} خوانده می‌شوند.

- {{domxref("GPURenderBundleEncoder.finish", "finish()")}}
  - : ضبط توالی دستورات فعلی رندر پاس را تکمیل می‌کند.

- {{domxref("GPURenderBundleEncoder.insertDebugMarker", "insertDebugMarker()")}}
  - : نقطه خاصی را در یک سری از دستورات کدگذاری‌شده با یک برچسب علامت‌گذاری می‌کند.
- {{domxref("GPURenderBundleEncoder.popDebugGroup", "popDebugGroup()")}}
  - : یک گروه اشکال‌زدایی را پایان می‌دهد که با یک فراخوانی {{domxref("GPURenderBundleEncoder.pushDebugGroup", "pushDebugGroup()")}} شروع شده است.
- {{domxref("GPURenderBundleEncoder.pushDebugGroup", "pushDebugGroup()")}}
  - : یک گروه اشکال‌زدایی را شروع می‌کند که با یک برچسب مشخص علامت‌گذاری می‌شود و شامل تمام دستورات کدگذاری‌شده بعدی تا زمانی که متد {{domxref("GPURenderBundleEncoder.popDebugGroup", "popDebugGroup()")}} فراخوانی شود، خواهد بود.
- {{domxref("GPURenderBundleEncoder.setBindGroup", "setBindGroup()")}}
  - : {{domxref("GPUBindGroup")}} را که برای دستورات بعدی رندر باندل استفاده می‌شود، برای یک ایندکس معین تنظیم می‌کند.

- {{domxref("GPURenderBundleEncoder.setIndexBuffer", "setIndexBuffer()")}}
  - : {{domxref("GPUBuffer")}} فعلی را که داده‌های ایندکس را برای دستورات رسم بعدی فراهم می‌کند، تنظیم می‌کند.

- {{domxref("GPURenderBundleEncoder.setPipeline", "setPipeline()")}}
  - : {{domxref("GPURenderPipeline")}} را که برای این رندر باندل استفاده می‌شود تنظیم می‌کند.

- {{domxref("GPURenderBundleEncoder.setVertexBuffer", "setVertexBuffer()")}}
  - : {{domxref("GPUBuffer")}} فعلی را که داده‌های رأس را برای دستورات رسم بعدی فراهم می‌کند، تنظیم یا لغو تنظیم می‌کند.

## مثال‌ها

در نمونه‌های WebGPU، [مثال Animometer](https://webgpu.github.io/webgpu-samples/samples/animometer/)، تعداد زیادی عملیات مشابه به طور همزمان روی اشیاء مختلف انجام می‌شود. یک دسته از دستورات با استفاده از تابع زیر کدگذاری می‌شود:

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

بعداً، یک `GPURenderBundleEncoder` ایجاد می‌شود، تابع فراخوانی می‌شود و دسته فرمان با استفاده از {{domxref("GPURenderBundleEncoder.finish()")}} در یک {{domxref("GPURenderBundle")}} ثبت می‌شود:

```js
const renderBundleEncoder = device.createRenderBundleEncoder({
  colorFormats: [presentationFormat],
});
recordRenderPass(renderBundleEncoder);
const renderBundle = renderBundleEncoder.finish();
```

سپس از {{domxref("GPURenderPassEncoder.executeBundles()")}} برای استفاده مجدد از کار در چندین رندر پاس جهت بهبود عملکرد استفاده می‌شود. برای دریافت متن کامل، به فهرست کد مثال مراجعه کنید.

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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)