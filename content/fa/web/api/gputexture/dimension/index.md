---
title: "GPUTexture: dimension property"
short-title: dimension
slug: Web/API/GPUTexture/dimension
page-type: web-api-instance-property
browser-compat: api.GPUTexture.dimension
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

خاصیتِ فقط‌خواندنی **`dimension`** در رابط {{domxref("GPUTexture")}}، ابعاد مجموعه‌ی تکسِل‌ها را برای هر زیرمنبع `GPUTexture` نشان می‌دهد.

این مقدار از طریق خاصیت `dimension` در شیء توصیفگری که به فراخوانِ اصلی {{domxref("GPUDevice.createTexture()")}} داده می‌شود تنظیم می‌گردد؛ اگر این خاصیت حذف شود، مقدار پیش‌فرض آن `"2d"` است.

## مقدار

یک مقدار شمارشی (enumerated value). مقادیر ممکن عبارت‌اند از:

- `"1d"`: یک بافت یک‌بعدی با یک بُعد، یعنی عرض.
- `"2d"`: یک بافت دوبعدی با عرض و ارتفاع، که می‌تواند لایه‌ها نیز داشته باشد. فقط بافت‌های `"2d"` می‌توانند میپ‌مپ (mipmap) داشته باشند، چندنمونه‌ای (multisampled) باشند، از فرمت فشرده یا عمق/قالب استفاده کنند، و به‌عنوان پیوستِ رندر (render attachment) به کار روند.
- `"3d"`: یک بافت سه‌بعدی با عرض، ارتفاع، و عمق.

## مثال‌ها

```js
// …

const depthTexture = device.createTexture({
  size: [canvas.width, canvas.height],
  format: "depth24plus",
  usage: GPUTextureUsage.RENDER_ATTACHMENT,
});

console.log(depthTexture.dimension); // "2d"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)