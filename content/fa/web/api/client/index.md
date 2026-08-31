---
title: Client
slug: Web/API/Client
page-type: web-api-interface
browser-compat: api.Client
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

رابط `Client` نمایانگر یک بستر اجرایی مانند {{domxref("Worker")}} یا {{domxref("SharedWorker")}} است. کلاینت‌های {{domxref("Window")}} توسط رابط خاص‌تر {{domxref("WindowClient")}} نمایش داده می‌شوند. می‌توانید اشیاء `Client`/`WindowClient` را از روش‌هایی مانند {{domxref("Clients.matchAll","Clients.matchAll()")}} و {{domxref("Clients.get","Clients.get()")}} دریافت کنید.

## روش‌های نمونه

- {{domxref("Client.postMessage()")}}
  - : یک پیام به کلاینت ارسال می‌کند.

## ویژگی‌های نمونه

- {{domxref("Client.frameType")}} {{ReadOnlyInline}}
  - : نوع قاب کلاینت به‌صورت رشته. می‌تواند `"auxiliary"`، `"top-level"`، `"nested"` یا `"none"` باشد.
- {{domxref("Client.id")}} {{ReadOnlyInline}}
  - : شناسه یکتای همگانی (UUID) کلاینت به‌صورت رشته.
- {{domxref("Client.type")}} {{ReadOnlyInline}}
  - : نوع کلاینت به‌صورت رشته. می‌تواند `"window"`، `"worker"` یا `"sharedworker"` باشد.
- {{domxref("Client.url")}} {{ReadOnlyInline}}
  - : URL کلاینت به‌صورت رشته.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)