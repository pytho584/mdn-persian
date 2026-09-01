---
title: "GPUCompilationMessage: length property"
short-title: length
slug: Web/API/GPUCompilationMessage/length
page-type: web-api-instance-property
browser-compat: api.GPUCompilationMessage.length
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‑خواندنی **`length`** در رابط {{domxref("GPUCompilationMessage")}} عددی است که طول زیررشته‌ای را که پیام به آن مربوط می‌شود نشان می‌دهد.

## مقدار

یک عدد.

به طور دقیق، `length` تعداد {{glossary("UTF-16", "واحد کد UTF‑16")}} در زیررشته کد شیدر است که پیام به آن اشاره دارد. اگر پیام به یک نقطهٔ واحد اشاره داشته باشد (نه یک زیررشته)، مقدار `length` صفر خواهد بود.

## مثال‌ها

```js
const shaderModule = device.createShaderModule({
  code: shaders,
});

const shaderInfo = await shaderModule.getCompilationInfo();
const firstMessage = shaderInfo.messages[0];
console.log(firstMessage.length);
```

برای یک مثال کامل‌تر، به صفحه اصلی [`GPUCompilationInfo`](/en-US/docs/Web/API/GPUCompilationInfo#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)