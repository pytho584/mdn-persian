---
title: "GPUAdapter: features property"
short-title: features
slug: Web/API/GPUAdapter/features
page-type: web-api-instance-property
browser-compat: api.GPUAdapter.features
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`features`** در رابط {{domxref("GPUAdapter")}} یک شیء {{domxref("GPUSupportedFeatures")}} برمی‌گرداند که قابلیت‌های اضافی پشتیبانی‌شده توسط آداپتور را توصیف می‌کند.

توجه داشته باشید که همه قابلیت‌ها در همه مرورگرهایی که WebGPU را پشتیبانی می‌کنند در دسترس WebGPU نخواهند بود، حتی اگر آن قابلیت‌ها توسط سخت‌افزار زیرین پشتیبانی شوند. این ممکن است به دلیل محدودیت‌های سیستم عامل، مرورگر، یا آداپتور باشد. برای مثال:

- سیستم عامل ممکن است نتواند تضمین کند که یک قابلیت به شکلی سازگار با مرورگر خاصی در معرض دید قرار می‌گیرد.
- فروشنده مرورگر ممکن است راه‌های امنی برای پیاده‌سازی پشتیبانی از آن قابلیت پیدا نکرده باشد، یا هنوز به آن نرسیده باشد.

اگر امیدوارید از یک قابلیت اضافی خاص در برنامه WebGPU بهره ببرید، تست کامل توصیه می‌شود.

## مقدار

یک نمونه از شیء {{domxref("GPUSupportedFeatures")}}. این یک شیء [مجموعه‌مانند](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set) است.

## مثال‌ها

در کد زیر بررسی می‌کنیم که آیا {{domxref("GPUAdapter")}} دارای قابلیت `texture-compression-astc` است یا خیر. اگر داشته باشد، آن را به آرایه `requiredFeatures` اضافه می‌کنیم و با استفاده از {{domxref("GPUAdapter.requestDevice()")}} دستگاهی با آن نیازمندی درخواست می‌کنیم.

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

  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)