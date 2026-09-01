---
title: GPUCompilationMessage
slug: Web/API/GPUCompilationMessage
page-type: web-api-interface
browser-compat: api.GPUCompilationMessage
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط کاربری **`GPUCompilationMessage`** در {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} یک پیام اطلاعاتی، هشدار یا خطای واحد را نشان می‌دهد که توسط کامپایلر ماژول سایه‌زن (Shader Module) GPU تولید شده است.

یک آرایه از اشیاء `GPUCompilationMessage` در ویژگی `messages` شیء {{domxref("GPUCompilationInfo")}} که از طریق {{domxref("GPUShaderModule.getCompilationInfo()")}} قابل دسترسی است، موجود می‌باشد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("GPUCompilationMessage.length", "length")}} {{ReadOnlyInline}}
  - : یک عدد که طول زیررشته‌ای را نشان می‌دهد که پیام به آن مربوط است.
- {{domxref("GPUCompilationMessage.lineNum", "lineNum")}} {{ReadOnlyInline}}
  - : یک عدد که شماره خط در کد سایه‌زن را نشان می‌دهد که پیام به آن مربوط است.
- {{domxref("GPUCompilationMessage.linePos", "linePos")}} {{ReadOnlyInline}}
  - : یک عدد که موقعیت در خط کد را نشان می‌دهد که پیام به آن مربوط است. این می‌تواند یک نقطه دقیق یا شروع زیررشته مرتبط باشد.
- {{domxref("GPUCompilationMessage.message", "message")}} {{ReadOnlyInline}}
  - : یک رشته که متن پیام قابل خواندن برای انسان را نشان می‌دهد.
- {{domxref("GPUCompilationMessage.offset", "offset")}} {{ReadOnlyInline}}
  - : یک عدد که فاصله از شروع کد سایه‌زن تا نقطه دقیق یا شروع زیررشته مرتبط را نشان می‌دهد که پیام به آن مربوط است.
- {{domxref("GPUCompilationMessage.type", "type")}} {{ReadOnlyInline}}
  - : یک مقدار شمارشی که نوع پیام را نشان می‌دهد — `"error"`، `"info"` یا `"warning"`.

## مثال‌ها

برای مشاهده مثال، به صفحه اصلی [`GPUCompilationInfo`](/en-US/docs/Web/API/GPUCompilationInfo#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)