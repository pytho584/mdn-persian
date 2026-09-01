```markdown
---
title: "GPUCompilationMessage: type property"
short-title: type
slug: Web/API/GPUCompilationMessage/type
page-type: web-api-instance-property
browser-compat: api.GPUCompilationMessage.type
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`type`** از رابط {{domxref("GPUCompilationMessage")}} یک مقدار شمارشی است که نوع پیام را نشان می‌دهد. هر نوع نشان‌دهنده سطحی از شدت است.

## مقدار

یک مقدار شمارشی. مقادیر ممکن عبارتند از:

- `"error"`
  - : یک خطای ایجاد شیدر که کامپایل موفق را متوقف می‌کند.
- `"info"`
  - : یک پیام صرفاً اطلاعاتی که شدت پایینی دارد.
- `"warning"`
  - : هشداری در مورد یک مشکل که کامپایل موفق را متوقف نمی‌کند اما نیازمند توجه توسعه‌دهنده است. نمونه‌اش استفاده از توابع یا نحو منسوخ است.

## مثال‌ها

```js
const shaderModule = device.createShaderModule({
  code: shaders,
});

const shaderInfo = await shaderModule.getCompilationInfo();
const firstMessage = shaderInfo.messages[0];
console.log(firstMessage.type);
```

برای یک مثال دقیق‌تر به صفحه اصلی [`GPUCompilationInfo`](/en-US/docs/Web/API/GPUCompilationInfo#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- ر[WebGPU API](/en-US/docs/Web/API/WebGPU_API)
```