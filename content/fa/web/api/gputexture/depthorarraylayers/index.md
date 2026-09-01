---
title: "GPUTexture: depthOrArrayLayers property"
short-title: depthOrArrayLayers
slug: Web/API/GPUTexture/depthOrArrayLayers
page-type: web-api-instance-property
browser-compat: api.GPUTexture.depthOrArrayLayers
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`depthOrArrayLayers`** در رابط {{domxref("GPUTexture")}}، تعداد عمق یا لایه‌های `GPUTexture` را نشان می‌دهد.

این مقدار بر اساس ویژگی `size` در شیء توصیف‌کننده‌ای تنظیم می‌شود که به فراخوانی {{domxref("GPUDevice.createTexture()")}} مبدأ ارسال شده است.

## مقدار

یک عدد. این عدد نشان‌دهنده موارد زیر است:

- عمق بر حسب پیکسل، برای بافت‌هایی با {{domxref("GPUTexture.dimension")}} از نوع `"3d"`.
- تعداد لایه‌ها، برای بافت‌های لایه‌ای با {{domxref("GPUTexture.dimension")}} از نوع `"2d"`.

در مواردی که `GPUTexture` عمق یا لایه ندارد، مقدار این ویژگی برابر با ۱ است.

## نمونه‌ها

```js
// …

const test = device.createTexture({
  size: [128],
  format: "r8uint",
  dimension: "1d",
  usage: GPUTextureUsage.COPY_SRC,
});

console.log(test.depthOrArrayLayers); // 1
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)