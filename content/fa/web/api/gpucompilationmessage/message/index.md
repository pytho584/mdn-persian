```
---
title: "GPUCompilationMessage: message property"
short-title: message
slug: Web/API/GPUCompilationMessage/message
page-type: web-api-instance-property
browser-compat: api.GPUCompilationMessage.message
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقطخواندنی **`message`** در رابط {{domxref("GPUCompilationMessage")}}، رشته‌ای است که متن پیام قابل‌خواندن برای انسان را نمایش می‌دهد.

## مقدار

یک رشته.

## مثال‌ها

```js
const shaderModule = device.createShaderModule({
  code: shaders,
});

const shaderInfo = await shaderModule.getCompilationInfo();
const firstMessage = shaderInfo.messages[0];
console.log(firstMessage.message);
```

برای مثال دقیق‌تر، صفحهٔ اصلی [`GPUCompilationInfo`](/en-US/docs/Web/API/GPUCompilationInfo#examples) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
```