---
title: "GPUBuffer: mapAsync() method"
---

---
title: "GPUBuffer: mapAsync() method"
short-title: mapAsync()
slug: Web/API/GPUBuffer/mapAsync
page-type: web-api-instance-method
browser-compat: api.GPUBuffer.mapAsync
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`mapAsync()`** از رابط {{domxref("GPUBuffer")}} محدوده مشخص‌شده از `GPUBuffer` را نگاشت می‌کند. این متد یک {{jsxref("Promise")}} برمی‌گرداند که وقتی محتوای `GPUBuffer` آماده دسترسی شد، حل می‌شود. تا زمانی که `GPUBuffer` نگاشت شده است، نمی‌توان از آن در هیچ دستور GPU استفاده کرد.

پس از اینکه بافر با موفقیت نگاشت شد (که می‌توانید با {{domxref("GPUBuffer.mapState")}} بررسی کنید)، فراخوانی‌های {{domxref("GPUBuffer.getMappedRange()")}} یک {{jsxref("ArrayBuffer")}} شامل مقادیر فعلی `GPUBuffer` برمی‌گردانند تا در صورت نیاز توسط جاوااسکریپت خوانده و به‌روزرسانی شوند.

وقتی کارتان با مقادیر `GPUBuffer` تمام شد، متد {{domxref("GPUBuffer.unmap()")}} را فراخوانی کنید تا نگاشت آن لغو شود و دوباره برای GPU در دسترس باشد.

## Syntax

```js-nolint
mapAsync(mode)
mapAsync(mode, offset, size)
```

### Parameters

- `mode`
  - : یک {{glossary("bitwise flags", "bitwise flag")}} که مشخص می‌کند `GPUBuffer` برای خواندن نگاشت شده است یا برای نوشتن. مقادیر ممکن عبارت‌اند از:
    - `GPUMapMode.READ`
      - : `GPUBuffer` برای خواندن نگاشت شده است. مقادیر قابل خواندن هستند، اما هر تغییری که در {{jsxref("ArrayBuffer")}} برگشتی از {{domxref("GPUBuffer.getMappedRange()")}} ایجاد شود، پس از فراخوانی {{domxref("GPUBuffer.unmap()")}} کنار گذاشته خواهد شد.

        نگاشت در حالت خواندن فقط روی `GPUBuffer`هایی قابل استفاده است که usage آن‌ها روی `GPUBufferUsage.MAP_READ` تنظیم شده باشد (یعنی هنگام ایجاد با {{domxref("GPUDevice.createBuffer()")}}).

    - `GPUMapMode.WRITE`
      - : `GPUBuffer` برای نوشتن نگاشت شده است. مقادیر قابل خواندن و به‌روزرسانی هستند — هر تغییری که در {{jsxref("ArrayBuffer")}} برگشتی از {{domxref("GPUBuffer.getMappedRange()")}} ایجاد شود، پس از فراخوانی {{domxref("GPUBuffer.unmap()")}} در `GPUBuffer` ذخیره خواهد شد.

        نگاشت در حالت نوشتن فقط روی `GPUBuffer`هایی قابل استفاده است که usage آن‌ها روی `GPUBufferUsage.MAP_WRITE` تنظیم شده باشد (یعنی هنگام ایجاد با {{domxref("GPUDevice.createBuffer()")}}).

- `offset` {{optional_inline}}
  - : عددی که فاصله را بر حسب بایت از ابتدای بافر تا شروع محدوده مورد نظر برای نگاشت نشان می‌دهد. اگر `offset` حذف شود، پیش‌فرض آن ۰ است.
- `size` {{optional_inline}}
  - : عددی که اندازه محدوده مورد نظر برای نگاشت را بر حسب بایت نشان می‌دهد. اگر `size` حذف شود، محدوده نگاشت شده تا انتهای `GPUBuffer` ادامه می‌یابد.

### Return value

یک {{jsxref("Promise")}} که وقتی محتوای `GPUBuffer` آماده دسترسی شد، به {{jsxref("undefined")}} حل می‌شود.

### Validation

هنگام فراخوانی **`mapAsync()`** باید معیارهای زیر برقرار باشند؛ در غیر این صورت یک `OperationError` {{domxref("DOMException")}} پرتاب می‌شود، پرامیس رد می‌شود و یک {{domxref("GPUValidationError")}} تولید می‌شود:

- `offset` مضربی از ۸ است.
- کل محدوده‌ای که قرار است نگاشت شود (`size` اگر مشخص شده باشد، یا در غیر این صورت {{domxref("GPUBuffer.size")}} - `offset`) مضربی از ۴ است.
- کل محدوده مورد نظر برای نگاشت درون مرزهای `GPUBuffer` قرار دارد.
- اگر حالت `GPUMapMode.READ` باشد، `GPUBuffer` دارای usage با مقدار `GPUBufferUsage.MAP_READ` است.
- اگر حالت `GPUMapMode.WRITE` باشد، `GPUBuffer` دارای usage با مقدار `GPUBufferUsage.MAP_WRITE` است.

## Examples

برای مثال، به [صفحه اصلی `GPUBuffer`](/en-US/docs/Web/API/GPUBuffer#examples) مراجعه کنید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)