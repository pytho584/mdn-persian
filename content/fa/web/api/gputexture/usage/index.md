---
title: "GPUTexture: usage property"
short-title: usage
slug: Web/API/GPUTexture/usage
page-type: web-api-instance-property
browser-compat: api.GPUTexture.usage
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

خاصیت فقط‌خواندنی **`usage`** در رابط {{domxref("GPUTexture")}}، نشانگرهای بیتی ({{glossary("bitwise flags")}}) است که کاربردهای مجاز `GPUTexture` را مشخص می‌کند.

این مقدار از طریق خاصیت `usage` در شیء توصیفگری که به فراخوانی {{domxref("GPUDevice.createTexture()")}} ارسال می‌شود، تنظیم می‌گردد.

## مقدار

نشانگرهای بیتی که کاربردهای اولیه تنظیم‌شده هنگام ایجاد `GPUTexture` را نشان می‌دهند. عدد بازگشتی، مجموع مقادیر اعشاری متناظر با هر پرچم است، همان‌طور که در جدول زیر مشاهده می‌کنید.

| نشانگر کاربرد                          | توضیح کاربرد                                                                                                                                                                                                                                                                                                                                                                                                                                            | معادل هگز | معادل اعشاری |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | -------------- |
| `GPUTextureUsage.COPY_SRC`             | از این بافت می‌توان به‌عنوان منبع یک عملیات کپی استفاده کرد، برای مثال آرگومان `source` در فراخوانی {{domxref("GPUCommandEncoder.copyTextureToBuffer", "copyTextureToBuffer()")}}.                                                                                                                                                                                                      | 0x01       | 1              |
| `GPUTextureUsage.COPY_DST`             | از این بافت می‌توان به‌عنوان مقصد یک عملیات کپی/نوشتن استفاده کرد، برای مثال آرگومان `destination` در فراخوانی {{domxref("GPUCommandEncoder.copyBufferToTexture", "copyBufferToTexture()")}}.                                                                                                                                                                                          | 0x02       | 2              |
| `GPUTextureUsage.RENDER_ATTACHMENT`    | از این بافت می‌توان به‌عنوان پیوست (attachment) رنگ یا عمق/استنسیل در یک رندر پاس استفاده کرد، برای مثال به‌عنوان خاصیت `view` شیء توصیفگر در فراخوانی {{domxref("GPUCommandEncoder.beginRenderPass", "beginRenderPass()")}}.                                                                                                                                                          | 0x10       | 16             |
| `GPUTextureUsage.STORAGE_BINDING`      | این بافت می‌تواند برای استفاده به‌عنوان بافت ذخیره‌سازی (storage texture) در یک شیدر متصل شود، برای مثال به‌عنوان یک منبع در یک ورودی بایند گروپ هنگام ایجاد {{domxref("GPUBindGroup")}} (از طریق {{domxref("GPUDevice.createBindGroup", "createBindGroup()")}})، که با یک ورودی {{domxref("GPUBindGroupLayout")}} با چیدمان بافت ذخیره‌سازی مشخص مطابقت دارد.                        | 0x08       | 8              |
| `GPUTextureUsage.TEXTURE_BINDING`      | این بافت می‌تواند برای استفاده به‌عنوان بافت نمونه‌برداری‌شده (sampled texture) در یک شیدر متصل شود، برای مثال به‌عنوان یک منبع در یک ورودی بایند گروپ هنگام ایجاد {{domxref("GPUBindGroup")}} (از طریق {{domxref("GPUDevice.createBindGroup", "createBindGroup()")}})، که با یک ورودی {{domxref("GPUBindGroupLayout")}} با چیدمان بافت مشخص مطابقت دارد.                          | 0x04       | 4              |
| `GPUTextureUsage.TRANSIENT_ATTACHMENT` | این بافت به‌عنوان یک راهنمای بهینه‌سازی موقت در نظر گرفته شده است؛ به‌طوری‌که پیوست‌های کارآمد از نظر حافظه ایجاد می‌کند که فقط در رندر پاس جاری استفاده می‌شوند. عملیات‌های رندر پاس مرتبط در حافظه‌ی tile باقی می‌مانند که از ترافیک VRAM جلوگیری کرده و می‌تواند از تخصیص VRAM برای این بافت‌ها جلوگیری کند.                                                                                        | 0x20       | 32             |

## مثال

```js
// …

const depthTexture = device.createTexture({
  size: [canvas.width, canvas.height],
  format: "depth24plus",
  usage: GPUTextureUsage.RENDER_ATTACHMENT,
});

console.log(depthTexture.usage); // 16
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)