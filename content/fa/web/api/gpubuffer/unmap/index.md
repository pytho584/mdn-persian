---
title: "GPUBuffer: unmap() method"
short-title: unmap()
slug: Web/API/GPUBuffer/unmap
page-type: web-api-instance-method
browser-compat: api.GPUBuffer.unmap
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`unmap()`** در رابط {{domxref("GPUBuffer")}} محدودهٔ نگاشت‌شدهٔ `GPUBuffer` را از حالت نگاشت خارج می‌کند و محتویات آن را دوباره برای استفاده توسط GPU در دسترس قرار می‌دهد، پس از آنکه قبلاً با {{domxref("GPUBuffer.mapAsync()")}} نگاشت شده باشد (GPU به یک `GPUBuffer` نگاشت‌شده دسترسی ندارد).

هنگامی که `unmap()` فراخوانی می‌شود، هر {{jsxref("ArrayBuffer")}} که از طریق {{domxref("GPUBuffer.getMappedRange()")}} ایجاد شده باشد، جدا (detach) می‌شود.

## Syntax

```js-nolint
unmap()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

برای مشاهدهٔ مثال، به [صفحهٔ اصلی `GPUBuffer`](/en-US/docs/Web/API/GPUBuffer#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)