---
title: "GPUBuffer: usage property"
short-title: usage
slug: Web/API/GPUBuffer/usage
page-type: web-api-instance-property
browser-compat: api.GPBuffer.usage
---

{{APIRef("WebGPU API")}}{SecureContext_Header}}{AvailableInWorkers}}

ویژگی `usage` فقط‑خواندنی از رابط {{domxref("GPUBuffer")}} شامل {{glossary("bitwise flags")}} (پرچم‌ای بیتی) است که کاربرد‌های مجاز `GPUBuffer` را نشان می‌دهد.

`usage` از طریق ویژگی `usage` در شیء توصیف‌کننده‌ای که به فراخوانی {{domxref("GPUDevice.createBuffer()")}} اولیه ارسال می‌شود، تنظیم می‌گردد.

## مقدار

پرچم‌های بیتی که کاربرد‌های اولیه تعیین‌شده در زمان ایجاد `GPUBuffer` را نشان می‌دهند. عدد بازگشتی حاصل جمع مقادیر ده‌دهی نماینده‌های مختلف پرچم‌ها است، همان‌طور که در جدول زیر مشاهده می‌شود.

| پرچم بیتی | توضیح کاربرد | معادل هگزادسیمال | معادل دهمالی |
| ----------- | ------------ | ----------------- | -------------- |
| `GPUBufferUsage.COPY_SRC` | این بافر می‌تواند به عنوان منبع یک عملیات کپی استفاده شود، برای مثال آرگومان منبع در فراخوانی {{domxref("GPUCommandEncoder.copyBufferToBuffer","copyBufferToBuffer()")}}. | 0x0004 | 4 |
| `GPUBufferUsage.COPY_DST` | این بافر می‌تواند به عنوان مقصد یک عملیات کپی/نوشتن استفاده شود، برای مثال آرگومان مقصد در فراخوانی {{domxref("GPUCommandEncoder.copyTextureToBuffer", "copyTextureToBuffer()")}}. | 0x0008 | 8 |
| `GPUBufferUsage.INDEX` | این بافر می‌تواند به عنوان بافر ایندکس استفاده شود، برای مثال به عنوان آرگومان `buffer` که به {{domxref("GPURenderPassEncoder.setIndexBuffer", "setIndexBuffer()")}} ارسال می‌شود. | 0x0010 | 16 |
| `GPUBufferUsage.INDIRECT` | این بافر می‌تواند برای ذخیره آرگومان‌های دستور غیرمستقیم استفاده شود، برای مثال به عنوان آرگومان `indirectBuffer` در فراخوانی {{domxref("GPURenderPassEncoder.drawIndirect", "drawIndirect()")}} یا {{domxref("GPUComputePassEncoder.dispatchWorkgroupsIndirect", "dispatchWorkgroupsIndirect()")}}. | 0x0100 | 256 |
| `GPUBufferUsage.MAP_READ` | این بافر می‌تواند برای خواندن نگاشت شود، برای مثال هنگام فراخوانی {{domxref("GPUBuffer.mapAsync", "mapAsync()")}} با `mode` برابر با `GPUMapMode.READ`. این پرچم فقط می‌تواند با `GPUBufferUsage.COPY_DST` ترکیب شود. | 0x0001 | 1 |
| `GPUBufferUsage.MAP_WRITE` | این بافر می‌تواند برای نوشتن نگاشت شود، برای مثال هنگام فراخوانی {{domxref("GPUBuffer.mapAsync", "mapAsync()")}} با `mode` برابر با `GPUMapMode.WRITE`. این پرچم فقط می‌تواند با `GPUBufferUsage.COPY_SRC` ترکیب شود. | 0x0002 | 2 |
| `GPUBufferUsage.QUERY_RESOLVE` | این بافر می‌تواند برای ضبط نتایج پرس‌وجو استفاده شود، برای مثال به عنوان آرگومان مقصد در فراخوانی {{domxref("GPUCommandEncoder.resolveQuerySet", "resolveQuerySet()")}}. | 0x0200 | 512 |
| `GPUBufferUsage.STORAGE` | این بافر می‌تواند به عنوان بافر ذخیره‌سازی استفاده شود، برای مثال به عنوان یک منبع در یک ورودی گروه اتصال هنگام ایجاد {{domxref("GPUBindGroup")}} (از طریق {{domxref("GPUDevice.createBindGroup", "createBindGroup()")}}، که با یک ورودی از {{domxref("GPUBindGroupLayout")}} با `type` طرح اتصال بافر برابر با `"storage"` یا `"read-only-storage"` مطابقت دارد. | 0x0080 | 128 |
| `GPUBufferUsage.UNIFORM` | این بافر می‌تواند به عنوان بافر یکنواخت استفاده شود، برای مثال به عنوان یک منبع در یک ورودی گروه اتصال هنگام ایجاد {{domxref("GPUBindGroup")}} (از طریق {{domxref("GPUDevice.createBindGroup", "createBindGroup()")}}، که با یک ورودی از {{domxref("GPUBindGroupLayout")}} با `type` طرح اتصال بافر برابر با `"uniform"` مطابقت دارد. | 0x0040 | 64 |
| `GPUBufferUsage.VERTEX` | این بافر می‌تواند به عنوان بافر راس استفاده شود، برای مثال به عنوان آرگومان `buffer` که به {{domxref("GPURenderPassEncoder.setVertexBuffer", "setVertexBuffer()")}} ارسال می‌شود. | 0x0020 | 32 |

## مثال‌ها

```js
const output = device.createBuffer({
  size: BUFFER_SIZE,
  usage: GPUBufferUsage.STORAGE | GPUBufferUsage.COPY_SRC,
});

console.log(output.usage); // 132

const stagingBuffer = device.createBuffer({
  size: BUFFER_SIZE,
  usage: GPUBufferUsage.MAP_READ | GPUBufferUsage.COPY_DST,
});

console.log(stagingBuffer.usage); // 9
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط [WebGPU API](/en-US/docs/Web/API/WebGPU_API)