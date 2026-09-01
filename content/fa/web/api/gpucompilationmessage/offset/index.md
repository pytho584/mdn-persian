```
---
title: "GPUCompilationMessage: offset property"
short-title: offset
slug: Web/API/GPUCompilationMessage/offset
page-type: web-api-instance-property
browser-compat: api.GPUCompilationMessage.offset
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

خصوصیت فقط خواندنی **`offset`** از رابط {{domxref("GPUCompilationMessage")}} یک عدد است که نشان‌دهنده فاصله از ابتدای کد شیدر تا نقطه دقیق یا شروع زیررشته مرتبطی است که پیام به آن اشاره دارد.

## مقدار

یک عدد.

به طور دقیق، `offset` تعداد واحدهای کد UTF-16 ({{glossary("UTF-16", "UTF-16 code units")}}) از ابتدای کد شیدر تا نقطه دقیق یا شروع زیررشته مرتبطی است که پیام به آن اشاره دارد.

اگر پیام با یک موقعیت کد خاص مطابقت نداشته باشد (احتمالاً به کل کد شیدر اشاره دارد)، `offset` برابر 0 خواهد بود.

## مثال‌ها

```js
const shaderModule = device.createShaderModule({
  code: shaders,
});

const shaderInfo = await shaderModule.getCompilationInfo();
const firstMessage = shaderInfo.messages[0];
console.log(firstMessage.offset);
```

برای یک مثال دقیق‌تر، صفحه اصلی [`GPUCompilationInfo`](/en-US/docs/Web/API/GPUCompilationInfo#examples) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
```