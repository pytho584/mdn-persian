---
title: "GPUBuffer: mapState property"
short-title: mapState
slug: Web/API/GPUBuffer/mapState
page-type: web-api-instance-property
browser-compat: api.GPUBuffer.mapState
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`mapState`** در رابط {{domxref("GPUBuffer")}}، حالت نگاشت‌شده‌ی `GPUBuffer` را نشان می‌دهد.

## مقدار

یک مقدار شمارشی (enumerated). مقادیر ممکن عبارت‌اند از:

- `unmapped`
  - : بافر نگاشت نشده است. نمی‌توان از {{domxref("GPUBuffer.getMappedRange()")}} برای دسترسی به محتویات `GPUBuffer` در جاوااسکریپت استفاده کرد. این حالت می‌تواند به دلایل زیر باشد:
    - {{domxref("GPUBuffer.mapAsync()")}} هنوز فراخوانی نشده است.
    - `GPUBuffer` قبلاً نگاشت شده بود و سپس با {{domxref("GPUBuffer.unmap()")}} از حالت نگاشت خارج شده است.
- `pending`
  - : بافر هنوز نگاشت نشده است. {{domxref("GPUBuffer.mapAsync()")}} فراخوانی شده، اما {{jsxref("Promise")}} مربوط به آن در حال انتظار است. در حال حاضر نمی‌توان از {{domxref("GPUBuffer.getMappedRange()")}} برای دسترسی به محتویات `GPUBuffer` در جاوااسکریپت استفاده کرد.
- `mapped`
  - : بافر نگاشت شده است. {{jsxref("Promise")}} مربوط به {{domxref("GPUBuffer.mapAsync()")}} با موفقیت انجام شده و اکنون می‌توان از {{domxref("GPUBuffer.getMappedRange()")}} برای دسترسی به محتویات `GPUBuffer` در جاوااسکریپت استفاده کرد.

## مثال‌ها

```js
const stagingBuffer = device.createBuffer({
  size: BUFFER_SIZE,
  usage: GPUBufferUsage.MAP_READ | GPUBufferUsage.COPY_DST,
});

console.log(stagingBuffer.mapState); // "unmapped"

// …

await stagingBuffer.mapAsync(
  GPUMapMode.READ,
  0, // Offset
  BUFFER_SIZE, // Length
);

console.log(stagingBuffer.mapState); // "mapped"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)