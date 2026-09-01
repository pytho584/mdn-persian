---
title: "GPUDevice: features property"
---
---
title: "GPUDevice: features property"
short-title: features
slug: Web/API/GPUDevice/features
page-type: web-api-instance-property
browser-compat: api.GPUDevice.features
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

خاصیت فقط خواندنی **`features`** از رابط {{domxref("GPUDevice")}} یک شیء {{domxref("GPUSupportedFeatures")}} را برمی‌گرداند که قابلیت‌های اضافی پشتیبانی‌شده توسط دستگاه را توصیف می‌کند. تنها ویژگی‌هایی که در هنگام ایجاد دستگاه درخواست شده‌اند (یعنی زمانی که {{domxref("GPUAdapter.requestDevice()")}} فراخوانی می‌شود) شامل می‌شوند.

> [!NOTE]
> همه ویژگی‌ها در همه مرورگرهایی که از WebGPU پشتیبانی می‌کنند در دسترس نخواهند بود، حتی اگر آن ویژگی‌ها توسط سخت‌افزار زیرین پشتیبانی شوند. برای جزئیات بیشتر به {{domxref("GPUAdapter.features")}} مراجعه کنید.

## مقدار

یک نمونه از شیء {{domxref("GPUSupportedFeatures")}}. این یک شیء [setlike](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set) است.

## نمونه‌ها

در کد زیر بررسی می‌کنیم که آیا یک {{domxref("GPUAdapter")}} ویژگی `texture-compression-astc` را در دسترس دارد یا خیر. اگر دارد، آن را به آرایه `requiredFeatures` اضافه می‌کنیم و با استفاده از {{domxref("GPUAdapter.requestDevice()")}} دستگاهی با آن ویژگی مورد نیاز درخواست می‌کنیم.

سپس تمام موارد موجود در مجموعه `GPUDevice.features` را در کنسول ثبت می‌کنیم. این مجموعه باید فقط یک مورد داشته باشد — `texture-compression-astc` — زیرا این تنها ویژگی‌ای بود که هنگام ایجاد دستگاه درخواست شده بود.

```js
async function init() {
  if (!navigator.gpu) {
    throw Error("WebGPU not supported.");
  }

  const adapter = await navigator.gpu.requestAdapter();
  if (!adapter) {
    throw Error("Couldn't request WebGPU adapter.");
  }

  const requiredFeatures = [];

  if (adapter.features.has("texture-compression-astc")) {
    requiredFeatures.push("texture-compression-astc");
  }

  const device = await adapter.requestDevice({
    requiredFeatures,
  });

  device.features.forEach((value) => {
    console.log(value);
  });

  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)