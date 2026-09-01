---
title: "GPUDevice: lost property"
short-title: lost
slug: Web/API/GPUDevice/lost
page-type: web-api-instance-property
browser-compat: api.GPUDevice.lost
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`lost`** از رابط {{domxref("GPUDevice")}} شامل یک {{jsxref("Promise")}} است که در تمام طول عمر دستگاه در حالت «در انتظار» (pending) باقی می‌ماند و زمانی که دستگاه از دست برود، با یک شیء {{domxref("GPUDeviceLostInfo")}} resolved می‌شود.

{{domxref("GPUAdapter.requestDevice()")}} هرگز `null` برنمی‌گرداند و تنها در صورتی reject می‌کند که درخواست نامعتبر باشد، یعنی فراتر از قابلیت‌های {{domxref("GPUAdapter")}} باشد. با این حال، اگر به دلایلی یک درخواست معتبر دستگاه قابل انجام نباشد، ممکن است به دستگاهی resolve شود که قبلاً از دست رفته است. علاوه بر این، دستگاه‌ها می‌توانند در هر زمانی پس از ایجاد، به دلایل مختلفی (مانند مدیریت منابع مرورگر یا به‌روزرسانی درایور) از دست بروند، بنابراین همیشه بهتر است دستگاه‌های از دست رفته را به‌شکلی مناسب مدیریت کنید.

بسیاری از دلایل از دست رفتن دستگاه گذرا هستند، بنابراین پس از از دست رفتن دستگاه قبلی باید تلاش کنید دستگاه جدیدی به دست آورید، مگر اینکه این از دست رفتن عمداً توسط برنامه و با از بین بردن دستگاه (یعنی با {{domxref("GPUDevice.destroy()")}}) ایجاد شده باشد. توجه داشته باشید که تمام منابع WebGPU ساخته‌شده با دستگاه قبلی (بافرها، بافت‌ها و غیره) باید با دستگاه جدید از نو ساخته شوند.

> [!NOTE]
> همچنین در نظر داشته باشید که یک `GPUAdapter` ممکن است در دسترس نباشد، مثلاً اگر GPU فیزیکی از سیستم جدا شود یا برای صرفه‌جویی در مصرف انرژی غیرفعال شود. از آن به بعد، آداپتور دیگر نمی‌تواند دستگاه‌های معتبر برگرداند و همیشه دستگاه‌هایی را برمی‌گرداند که از قبل از دست رفته‌اند.

## مقدار

یک Promise که وقتی دستگاه از دست برود، با یک شیء {{domxref("GPUDeviceLostInfo")}} resolve می‌شود.

## مثال‌ها

```js
async function init() {
  if (!navigator.gpu) {
    throw Error("WebGPU not supported.");
  }

  const adapter = await navigator.gpu.requestAdapter();
  if (!adapter) {
    throw Error("Couldn't request WebGPU adapter.");
  }

  // Create a GPUDevice
  let device = await adapter.requestDevice(descriptor);

  // Use lost to handle lost devices
  device.lost.then((info) => {
    console.error(`WebGPU device was lost: ${info.message}`);
    device = null;

    if (info.reason !== "destroyed") {
      init();
    }
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