---
title: "GPUDevice: uncapturederror event"
short-title: uncapturederror
slug: Web/API/GPUDevice/uncapturederror_event
page-type: web-api-event
browser-compat: api.GPUDevice.uncapturederror_event
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رویداد **`uncapturederror`** از رابط {{domxref("GPUDevice")}} زمانی فعال می‌شود که خطایی رخ دهد که توسط یک حوزه خطای GPU (GPU error scope) مشاهده نشده باشد، تا راهی برای گزارش خطاهای غیرمنتظره فراهم کند.

موارد خطای شناخته شده باید با استفاده از {{domxref("GPUDevice.pushErrorScope", "pushErrorScope()")}} و {{domxref("GPUDevice.popErrorScope", "popErrorScope()")}} مدیریت شوند.

## نحو (Syntax)

برای استفاده از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا تنظیم یک ویژگی کنترل‌کننده رویداد (event handler property) استفاده کنید.

```js-nolint
addEventListener("uncapturederror", (event) => { })

onuncapturederror = (event) => { }
```

## نوع رویداد

یک {{domxref("GPUUncapturedErrorEvent")}} که از {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("GPUUncapturedErrorEvent")}}

## مثال‌ها

می‌توانید از چیزی شبیه به موارد زیر به عنوان یک مکانیزم سراسری برای دریافت هر خطایی که توسط حوزه‌های خطا مدیریت نشده و آن‌ها را ضبط کنید، استفاده کنید.

```js
device.addEventListener("uncapturederror", (event) => {
  // نمایش مجدد خطا
  console.error("یک خطای WebGPU ضبط نشد:", event.error);

  reportErrorToServer({
    type: event.error.constructor.name,
    message: event.error.message,
  });
});
```

برای مثال‌ها و اطلاعات بیشتر به [بهترین روش‌های مدیریت خطا در WebGPU](https://toji.dev/webgpu-best-practices/error-handling) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)