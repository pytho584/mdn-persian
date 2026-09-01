---
title: "FileReaderSync: readAsArrayBuffer() method"
short-title: readAsArrayBuffer()
slug: Web/API/FileReaderSync/readAsArrayBuffer
page-type: web-api-instance-method
browser-compat: api.FileReaderSync.readAsArrayBuffer
---

{{APIRef("File API")}} {{AvailableInWorkers("worker_except_service")}}

متد **`readAsArrayBuffer()`** از رابط {{DOMxRef("FileReaderSync")}} امکان خواندن همزمان اشیای {{DOMxRef("File")}} یا {{DOMxRef("Blob")}} را به‌صورت یک {{jsxref("ArrayBuffer")}} فراهم می‌کند. این رابط [فقط](/en-US/docs/Web/API/Web_Workers_API/Functions_and_classes_available_to_workers) در [workerها](/en-US/docs/Web/API/Worker) در دسترس است، زیرا عملیات ورودی/خروجی همزمان را فعال می‌کند که به‌طور بالقوه می‌تواند باعث مسدود شدن شود.

## نحو

```js-nolint
readAsArrayBuffer(blob)
```

### پارامترها

- `blob`
  - : شیء {{DOMxRef("File")}} یا {{DOMxRef("Blob")}} که قرار است به‌صورت یک {{jsxref("ArrayBuffer")}} خوانده شود.

### مقدار بازگشتی

یک {{jsxref("ArrayBuffer")}} که داده‌های فایل را نمایش می‌دهد.

### استثناها

متد مذکور می‌تواند استثناهای زیر را ایجاد کند:

- `NotFoundError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که منبع نمایش‌داده‌شده توسط {{DOMxRef("File")}} یا {{DOMxRef("Blob")}} پیدا نشود، مثلاً به این دلیل که پاک شده باشد.
- `SecurityError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که یکی از وضعیت‌های مشکل‌ساز زیر تشخیص داده شود:
    - منبع توسط شخص ثالث تغییر کرده باشد؛
    - همزمان بیش از حد مجاز خواندن انجام شود؛
    - فایلی که منبع به آن اشاره می‌کند برای استفاده از وب ناامن باشد (مانند فایل‌های سیستمی).
- `NotReadableError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که منبع به دلیل مشکل مجوز، مانند قفل همزمان، قابل خواندن نباشد.
- `EncodingError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که منبع یک URL داده‌ای (data URL) باشد و از حد مجاز طول تعیین‌شده توسط هر مرورگر فراتر رود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("File API", "", "", "nocode")}}
- {{DOMxRef("File")}}
- {{DOMxRef("FileReaderSync")}}
- {{DOMxRef("FileReader")}}
- {{DOMxRef("Blob")}}