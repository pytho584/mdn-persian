---
title: "GPUAdapter: limits property"
short-title: limits
slug: Web/API/GPUAdapter/limits
page-type: web-api-instance-property
browser-compat: api.GPUAdapter.limits
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط خواندنی **`limits`** از رابط {{domxref("GPUAdapter")}} یک شیء {{domxref("GPUSupportedLimits")}} برمی‌گرداند که محدودیت‌های پشتیبانی‌شده توسط آداپتور را توصیف می‌کند.

توجه داشته باشید که مرورگرها به جای گزارش محدودیت‌های دقیق هر GPU، احتمالاً مقادیر رتبه‌بندی (tier) متفاوتی از محدودیت‌های مختلف را گزارش می‌کنند تا اطلاعات منحصربه‌فرد در دسترس برای اثرانگشت‌گیری (fingerprinting) از طریق مرور کاهش یابد. به عنوان مثال، رتبه‌های یک محدودیت خاص ممکن است 2048، 8192 و 32768 باشند. اگر محدودیت واقعی GPU شما 16384 باشد، مرورگر همچنان 8192 را گزارش خواهد داد.

با توجه به اینکه مرورگرهای مختلف این موضوع را به طور متفاوتی مدیریت می‌کنند و مقادیر رتبه‌بندی ممکن است در طول زمان تغییر کنند، ارائه یک گزارش دقیق از مقادیر محدودیت مورد انتظار دشوار است – توصیه می‌شود آزمایش جامعی انجام دهید.

## مقدار

یک نمونه از شیء {{domxref("GPUSupportedLimits")}}.

## مثال‌ها

در کد زیر، ما مقدار `GPUAdapter.limits` از `maxBindGroups` را پرس‌وجو می‌کنیم تا ببینیم آیا برابر یا بزرگتر از 6 است. برنامه نمونه تئوری ما به طور ایده‌آل به 6 گروه اتصال (bind group) نیاز دارد، بنابراین اگر مقدار برگشتی >= 6 باشد، یک محدودیت حداکثر 6 را به شیء `requiredLimits` اضافه می‌کنیم و با استفاده از {{domxref("GPUAdapter.requestDevice()")}} یک دستگاه با آن نیازمندی محدودیت درخواست می‌کنیم.

```js
async function init() {
  if (!navigator.gpu) {
    throw Error("WebGPU not supported.");
  }

  const adapter = await navigator.gpu.requestAdapter();
  if (!adapter) {
    throw Error("Couldn't request WebGPU adapter.");
  }

  const requiredLimits = {};

  // App ideally needs 6 bind groups, so we'll try to request what the app needs
  if (adapter.limits.maxBindGroups >= 6) {
    requiredLimits.maxBindGroups = 6;
  }

  const device = await adapter.requestDevice({
    requiredLimits,
  });

  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)