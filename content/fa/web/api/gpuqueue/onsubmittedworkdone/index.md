---
title: "GPUQueue: onSubmittedWorkDone() method"
short-title: onSubmittedWorkDone()
slug: Web/API/GPUQueue/onSubmittedWorkDone
page-type: web-api-instance-method
browser-compat: api.GPUQueue.onSubmittedWorkDone
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`onSubmittedWorkDone()`** در رابط {{domxref("GPUQueue")}} یک {{jsxref("Promise")}} برمی‌گرداند که زمانی حل می‌شود که تمام کارهایی که در لحظهٔ فراخوانی متد از طریق این `GPUQueue` به GPU ارسال شده‌اند، پردازش شده باشند.

این شامل تکمیل هرگونه فراخوانی {{domxref("GPUBuffer.mapAsync", "mapAsync()")}} روی `GPUBuffer`هایی است که در دستورات ارسال‌شده به صف استفاده شده‌اند، پیش از فراخوانی `onSubmittedWorkDone()`.

توجه: در بیشتر موارد _نیازی_ به فراخوانی `onSubmittedWorkDone()` ندارید. برای نگاشت (mapping) یک بافر نیز **_نیازی_** به فراخوانی آن ندارید. `mapAsync` تضمین می‌کند که کارهای ارسال‌شده به صف قبل از فراخوانی `mapAsync`، پیش از بازگشت `mapAsync` انجام می‌شوند (به [مشخصات WebGPU](https://gpuweb.github.io/gpuweb/#buffer-mapping) مراجعه کنید).

دو کاربرد `onSubmittedWorkDone`:

1. انتظار برای نگاشت چند بافر (کند)

   ```js
   // good
   await Promise.all([
     buffer1.mapAsync(),
     buffer2.mapAsync(),
     buffer3.mapAsync(),
   ]);
   data1 = buffer1.getMappedRange();
   data2 = buffer2.getMappedRange();
   data3 = buffer3.getMappedRange();
   ```

   ```js
   // works but slow
   buffer1.mapAsync();
   buffer2.mapAsync();
   buffer3.mapAsync();
   await device.queue.onSubmittedWorkDone();
   data1 = buffer1.getMappedRange();
   data2 = buffer2.getMappedRange();
   data3 = buffer3.getMappedRange();
   ```

   دلیل کند بودن روش دوم این است که پیاده‌سازی ممکن است بتواند بافرها را قبل از اتمام تمام کارهای ارسال‌شده نگاشت کند. برای مثال، اگر استفاده از همهٔ بافرها تمام شده باشد، اما کارهای بیشتری (نامرتبط با بافرها) از قبل ارسال شده باشند، در این صورت با روش دوم بیشتر از روش اول منتظر می‌مانید.

2. محدود کردن نرخ کار

   اگر در حال انجام کار محاسباتی سنگین هستید و یکباره کار زیادی ارسال کنید، ممکن است مرورگر کار شما را متوقف کند. می‌توانید با ارسال کار بیشتر فقط زمانی که کارهای از قبل ارسال‌شده تمام شده‌اند، نرخ کار را محدود کنید.

## سینتکس

```js-nolint
onSubmittedWorkDone()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با {{jsxref("undefined")}} حل می‌شود.

## مثال‌ها

```js
device.queue.submit([commandEncoder.finish()]);
device.queue.onSubmittedWorkDone().then(() => {
  console.log("All submitted commands processed.");
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)