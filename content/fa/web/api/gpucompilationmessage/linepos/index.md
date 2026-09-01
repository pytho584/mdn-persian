---
title: "GPUCompilationMessage: linePos property"
---

---
title: "GPUCompilationMessage: linePos property"
short-title: linePos
slug: Web/API/GPUCompilationMessage/linePos
page-type: web-api-instance-property
browser-compat: api.GPUCompilationMessage.linePos
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`linePos`** از رابط {{domxref("GPUCompilationMessage")}} عددی است که موقعیت را در خط کد نشان می‌دهد؛ موقعیتی که پیام به آن مربوط می‌شود. این موقعیت می‌تواند یک نقطهٔ دقیق یا شروع زیررشتهٔ مرتبط باشد.

## مقدار

یک عدد.

به بیان دقیق‌تر، `linePos` تعداد {{glossary("UTF-16", "واحدهای کد UTF-16")}} از ابتدای خط تا نقطهٔ دقیق یا شروع زیررشتهٔ مرتبط با پیام است.

توجه داشته باشید که:

- اگر پیام به یک زیررشته مربوط باشد، `linePos` به اولین واحد کد UTF-16 آن زیررشته اشاره می‌کند.
- اگر پیام به موقعیت کد خاصی مربوط نباشد (مثلاً به کل کد شیدر اشاره کند)، `linePos` برابر 0 خواهد بود.
- مقادیر یک‌پایه هستند — مقدار 1 به اولین واحد کد خط اشاره می‌کند.

## مثال

```js
const shaderModule = device.createShaderModule({
  code: shaders,
});

const shaderInfo = await shaderModule.getCompilationInfo();
const firstMessage = shaderInfo.messages[0];
console.log(firstMessage.linePos);
```

برای یک مثال دقیق‌تر، صفحهٔ اصلی [`GPUCompilationInfo` page](/en-US/docs/Web/API/GPUCompilationInfo#examples) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- The [WebGPU API](/en-US/docs/Web/API/WebGPU_API)