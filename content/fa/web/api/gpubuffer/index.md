---
title: GPUBuffer
slug: Web/API/GPUBuffer
page-type: web-api-interface
browser-compat: api.GPUBuffer
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

**`GPUBuffer`** 接口属于 {{domxref("WebGPU API", "WebGPU API", "", "nocode")}}، نشان‌دهنده یک بلوک حافظه است که می‌توان از آن برای ذخیره‌سازی داده‌های خام جهت استفاده در عملیات‌های GPU بهره برد.

یک نمونه از شیء `GPUBuffer` با استفاده از روش {{domxref("GPUDevice.createBuffer()")}} ساخته می‌شود.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("GPUBuffer.label", "label")}}
  - : یک رشته که برچسبی برای شناسایی شیء فراهم می‌کند، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.
- {{domxref("GPUBuffer.mapState", "mapState")}} {{ReadOnlyInline}}
  - : یک مقدار شمارشی که وضعیت نگاشت‌شده `GPUBuffer` را نشان می‌دهد.
- {{domxref("GPUBuffer.size", "size")}} {{ReadOnlyInline}}
  - : عددی که طول تخصیص حافظه `GPUBuffer` را بر حسب بایت نشان می‌دهد.
- {{domxref("GPUBuffer.usage", "usage")}} {{ReadOnlyInline}}
  - : {{glossary("bitwise flags")}} که کاربردهای مجاز `GPUBuffer` را نشان می‌دهد.

## روش‌های نمونه

- {{domxref("GPUBuffer.destroy", "destroy()")}}
  - : `GPUBuffer` را از بین می‌برد.
- {{domxref("GPUBuffer.getMappedRange", "getMappedRange()")}}
  - : یک {{jsxref("ArrayBuffer")}} شامل محتویات نگاشت‌شده `GPUBuffer` در محدوده مشخص‌شده بازمی‌گرداند.
- {{domxref("GPUBuffer.mapAsync", "mapAsync()")}}
  - : محدوده مشخص‌شده از `GPUBuffer` را نگاشت می‌کند. یک {{jsxref("Promise")}} بازمی‌گرداند که وقتی محتوای `GPUBuffer` آماده دسترسی از طریق {{domxref("GPUBuffer.getMappedRange()")}} شد، حل می‌شود.
- {{domxref("GPUBuffer.unmap", "unmap()")}}
  - : محدوده نگاشت‌شده `GPUBuffer` را از حالت نگاشت خارج می‌کند و محتویات آن را دوباره برای استفاده GPU در دسترس قرار می‌دهد.

## مثال‌ها

در [نمونه محاسبات پایه](https://mdn.github.io/dom-examples/webgpu-compute-demo/) ما، یک بافر خروجی برای خواندن محاسبات GPU و یک بافر میانی (staging buffer) برای نگاشت و دسترسی جاوااسکریپت ایجاد می‌کنیم.

```js
const output = device.createBuffer({
  size: BUFFER_SIZE,
  usage: GPUBufferUsage.STORAGE | GPUBufferUsage.COPY_SRC,
});

const stagingBuffer = device.createBuffer({
  size: BUFFER_SIZE,
  usage: GPUBufferUsage.MAP_READ | GPUBufferUsage.COPY_DST,
});
```

بعداً، وقتی `stagingBuffer` حاوی نتایج محاسبات GPU شد، ترکیبی از روش‌های `GPUBuffer` برای خواندن داده‌ها به جاوااسکریپت و سپس ثبت آن در کنسول استفاده می‌شود:

- {{domxref("GPUBuffer.mapAsync()")}} برای نگاشت `GPUBuffer` جهت خواندن استفاده می‌شود.
- {{domxref("GPUBuffer.getMappedRange()")}} برای بازگرداندن یک {{jsxref("ArrayBuffer")}} شامل محتویات `GPUBuffer` استفاده می‌شود.
- {{domxref("GPUBuffer.unmap()")}} برای خارج کردن `GPUBuffer` از حالت نگاشت، پس از خواندن محتوا در جاوااسکریپت، استفاده می‌شود.

```js
// نگاشت بافر میانی برای خواندن نتایج به جاوااسکریپت
await stagingBuffer.mapAsync(
  GPUMapMode.READ,
  0, // Offset
  BUFFER_SIZE, // Length
);

const copyArrayBuffer = stagingBuffer.getMappedRange(0, BUFFER_SIZE);
const data = copyArrayBuffer.slice(0);
stagingBuffer.unmap();
console.log(new Float32Array(data));
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)