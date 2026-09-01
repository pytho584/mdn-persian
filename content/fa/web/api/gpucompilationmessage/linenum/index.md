---
title: "GPUCompilationMessage: lineNum property"
---

---
title: "GPUCompilationMessage: lineNum property"
short-title: lineNum
slug: Web/API/GPUCompilationMessage/lineNum
page-type: web-api-instance-property
browser-compat: api.GPUCompilationMessage.lineNum
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

خاصیت فقط‌خواندنی **`lineNum`** از رابط {{domxref("GPUCompilationMessage")}} عددی است که شماره خط در کد شیدر را نشان می‌دهد که پیام به آن مربوط می‌شود.

## مقدار

یک عدد.

توجه داشته باشید که:

- اگر پیام به یک زیررشته مربوط باشد، `lineNum` به شماره خطی اشاره می‌کند که زیررشته از آنجا شروع می‌شود.
- اگر پیام به خط مشخصی از کد مربوط نباشد (مثلاً به کل کد شیدر اشاره داشته باشد)، `lineNum` برابر با ۰ خواهد بود.
- مقادیر یک‌پایه هستند — مقدار ۱ به اولین خط کد اشاره دارد.
- خط‌ها با شکست خط از هم جدا می‌شوند. در WGSL، [فهرست خاصی از کاراکترها](https://gpuweb.github.io/gpuweb/wgsl/#line-break) به‌عنوان شکست خط تعریف شده است.

## مثال‌ها

```js
const shaderModule = device.createShaderModule({
  code: shaders,
});

const shaderInfo = await shaderModule.getCompilationInfo();
const firstMessage = shaderInfo.messages[0];
console.log(firstMessage.lineNum);
```

برای مثال دقیق‌تر، به صفحهٔ اصلی [`GPUCompilationInfo`](/en-US/docs/Web/API/GPUCompilationInfo#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)