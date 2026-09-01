---
title: "GPUDevice: limits property"
short-title: limits
slug: Web/API/GPUDevice/limits
page-type: web-api-instance-property
browser-compat: api.GPUDevice.limits
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنیِ **`limits`** در رابط {{domxref("GPUDevice")}} یک شیء {{domxref("GPUSupportedLimits")}} بازمی‌گرداند که محدودیت‌های پشتیبانی‌شده توسط دستگاه را توصیف می‌کند. همهٔ مقادیر محدودیت‌ها در این شیء گنجانده می‌شوند و محدودیت‌هایی که هنگام ایجاد دستگاه درخواست شده‌اند (یعنی زمانی که {{domxref("GPUAdapter.requestDevice()")}} فراخوانی می‌شود) در این مقادیر منعکس خواهند شد.

> [!NOTE]
> همهٔ محدودیت‌ها لزوماً مطابق انتظار گزارش نمی‌شوند، حتی اگر توسط سخت‌افزار زیرین پشتیبانی شوند. برای جزئیات بیشتر به {{domxref("GPUAdapter.limits")}} مراجعه کنید.

## مقدار

یک نمونهٔ شیء {{domxref("GPUSupportedLimits")}}.

## مثال‌ها

در کد زیر، مقدار `maxBindGroups` را از طریق `GPUAdapter.limits` بررسی می‌کنیم تا ببینیم آیا برابر با ۶ یا بیشتر است. برنامهٔ نمونهٔ فرضی ما در حالت ایده‌آل به ۶ گروه bind نیاز دارد، بنابراین اگر مقدار بازگشتی >= 6 باشد، یک حداکثر محدودیت ۶ را به شیء `requiredLimits` اضافه می‌کنیم.

سپس با چاپ مقدار آن در کنسول، بررسی می‌کنیم که محدودیت مورد انتظار روی دستگاه نهایی اعمال شده است.

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

  console.log(device.limits.maxBindGroups);

  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)