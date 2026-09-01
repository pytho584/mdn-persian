---
title: "GPUBuffer: getMappedRange() method"
short-title: getMappedRange()
slug: Web/API/GPUBuffer/getMappedRange
page-type: web-api-instance-method
browser-compat: api.GPUBuffer.getMappedRange
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`getMappedRange()`** از رابط {{domxref("GPUBuffer")}} یک {{jsxref("ArrayBuffer")}} شامل محتویات نگاشت‌شدهٔ `GPUBuffer` را در محدودهٔ مشخص‌شده بازمی‌گرداند.

این کار تنها پس از آن امکان‌پذیر است که `GPUBuffer` با موفقیت با استفاده از {{domxref("GPUBuffer.mapAsync()")}} نگاشت شده باشد (می‌توان این موضوع را با {{domxref("GPUBuffer.mapState")}} بررسی کرد). در حالی که `GPUBuffer` نگاشت شده است، نمی‌توان از آن در هیچ دستور GPU استفاده کرد.

هنگامی که کار با مقادیر `GPUBuffer` به پایان رسید، با فراخوانی {{domxref("GPUBuffer.unmap()")}} آن را از نگاشت خارج کنید تا دوباره در دسترس GPU قرار گیرد. اگر تلاش شود که {{jsxref("ArrayBuffer")}} به هر طریقی غیر از {{domxref("GPUBuffer.unmap()")}} جدا شود (مثلاً با فراخوانی {{jsxref("ArrayBuffer/transfer", "transfer()")}})، یک `TypeError` پرتاب می‌شود.

## Syntax

```js-nolint
getMappedRange()
getMappedRange(offset)
getMappedRange(offset, size)
```

### پارامترها

- `offset` {{optional_inline}}
  - : عددی که نشان‌دهندهٔ offset (بر حسب بایت) از ابتدای محدودهٔ نگاشت‌شدهٔ `GPUBuffer` تا ابتدای محدوده‌ای است که باید در {{jsxref("ArrayBuffer")}} برگردانده شود. اگر `offset` حذف شود، مقدار پیش‌فرض آن 0 است.
- `size` {{optional_inline}}
  - : عددی که اندازهٔ (بر حسب بایت) {{jsxref("ArrayBuffer")}} مورد نظر برای بازگرداندن را مشخص می‌کند. اگر `size` حذف شود، محدوده تا انتهای محدودهٔ نگاشت‌شدهٔ `GPUBuffer` ادامه می‌یابد.

### مقدار بازگشتی

یک {{jsxref("ArrayBuffer")}}.

### اعتبارسنجی

هنگام فراخوانی **`getMappedRange()`** معیارهای زیر باید رعایت شوند، در غیر این صورت یک `OperationError` {{domxref("DOMException")}} پرتاب می‌شود:

- `offset` مضربی از 8 است.
- کل محدوده‌ای که باید نگاشت شود (اگر `size` مشخص شده باشد، همان `size`؛ در غیر این صورت طول محدودهٔ نگاشت‌شده منهای `offset`) مضربی از 4 است.
- کل محدوده درون مرزهای محدودهٔ نگاشت‌شده قرار دارد و با محدوده‌های {{jsxref("ArrayBuffer")}} مشخص‌شده توسط سایر فراخوانی‌های فعال `getMappedRange()` همپوشانی ندارد.

## مثال‌ها

برای مشاهدهٔ مثال به [صفحهٔ اصلی `GPUBuffer`](/en-US/docs/Web/API/GPUBuffer#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)