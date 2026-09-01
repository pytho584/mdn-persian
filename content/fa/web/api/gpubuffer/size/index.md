---
title: "GPUBuffer: size property"
short-title: size
slug: Web/API/GPUBuffer/size
page-type: web-api-instance-property
browser-compat: api.GPUBuffer.size
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`size`** در رابط {{domxref("GPUBuffer")}}، طول تخصیص حافظهٔ `GPUBuffer` را بر حسب بایت نشان می‌دهد.

مقدار `size` از طریق ویژگی `size` در شیء توصیفگری که به فراخوانی {{domxref("GPUDevice.createBuffer()")}} مربوطه داده می‌شود، تنظیم می‌گردد.

## مقدار

یک عدد.

## مثال‌ها

```js
// Define global buffer size
const BUFFER_SIZE = 1000;

// …

const output = device.createBuffer({
  size: BUFFER_SIZE,
  usage: GPUBufferUsage.STORAGE | GPUBufferUsage.COPY_SRC,
});

console.log(output.size); // 1000
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)