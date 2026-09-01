---
title: GPUQueue
slug: Web/API/GPUQueue
page-type: web-api-interface
browser-compat: api.GPUQueue
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`GPUQueue`** از {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} اجرای دستورات رمزگذاری‌شده روی GPU را کنترل می‌کند.

صف اصلی یک دستگاه از طریق ویژگی {{domxref("GPUDevice.queue")}} قابل دسترسی است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("GPUQueue.label", "label")}}
  - : یک رشته که برچسبی برای شناسایی شیء فراهم می‌کند، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

## روش‌های نمونه

- {{domxref("GPUQueue.copyExternalImageToTexture", "copyExternalImageToTexture()")}}
  - : یک عکس فوری گرفته شده از یک تصویر منبع، ویدیو یا بوم را در یک {{domxref("GPUTexture")}} مشخص کپی می‌کند.
- {{domxref("GPUQueue.onSubmittedWorkDone", "onSubmittedWorkDone()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که زمانی حل می‌شود که تمام کارهای ارسال‌شده به GPU از طریق این `GPUQueue` در زمان فراخوانی روش پردازش شده باشند.
- {{domxref("GPUQueue.submit", "submit()")}}
  - : اجرای بافرهای دستوری که توسط یک یا چند شیء {{domxref("GPUCommandBuffer")}} نمایش داده می‌شوند را توسط GPU زمان‌بندی می‌کند.
- {{domxref("GPUQueue.writeBuffer", "writeBuffer()")}}
  - : یک منبع داده ارائه‌شده را در یک {{domxref("GPUBuffer")}} مشخص می‌نویسد.
- {{domxref("GPUQueue.writeTexture", "writeTexture()")}}
  - : یک منبع داده ارائه‌شده را در یک {{domxref("GPUTexture")}} مشخص می‌نویسد.

## مثال‌ها

در [basic render demo](https://mdn.github.io/dom-examples/webgpu-render-demo/) ما، برخی داده‌های رأس را در یک {{jsxref("Float32Array")}} تعریف می‌کنیم که برای رسم یک مثلث استفاده خواهیم کرد:

```js
const vertices = new Float32Array([
  0.0, 0.6, 0, 1, 1, 0, 0, 1, -0.5, -0.6, 0, 1, 0, 1, 0, 1, 0.5, -0.6, 0, 1, 0,
  0, 1, 1,
]);
```

برای استفاده از این داده‌ها در یک خط لوله رندر، باید آن را در یک {{domxref("GPUBuffer")}} قرار دهیم. ابتدا بافر را ایجاد می‌کنیم:

```js
const vertexBuffer = device.createBuffer({
  size: vertices.byteLength, // make it big enough to store vertices in
  usage: GPUBufferUsage.VERTEX | GPUBufferUsage.COPY_DST,
});
```

برای انتقال داده‌ها به بافر می‌توانیم از تابع {{domxref("GPUQueue.writeBuffer", "writeBuffer()")}} استفاده کنیم که به عامل کاربر اجازه می‌دهد کارآمدترین روش را برای کپی داده‌ها تعیین کند:

```js
device.queue.writeBuffer(vertexBuffer, 0, vertices, 0, vertices.length);
```

بعداً، مجموعه‌ای از دستورات با استفاده از روش {{domxref("GPUCommandEncoder.finish()")}} در یک {{domxref("GPUCommandBuffer")}} رمزگذاری می‌شود. سپس بافر دستور از طریق فراخوانی {{domxref("GPUQueue.submit", "submit()")}} به صف ارسال می‌شود تا توسط GPU پردازش شود.

```js
device.queue.submit([commandEncoder.finish()]);
```

> [!NOTE]
> برای یافتن نمونه‌های بیشتر از صف، [WebGPU samples](https://webgpu.github.io/webgpu-samples/) را مطالعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)