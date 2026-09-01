---
title: "FileReaderSync: readAsDataURL() method"
short-title: readAsDataURL()
slug: Web/API/FileReaderSync/readAsDataURL
page-type: web-api-instance-method
browser-compat: api.FileReaderSync.readAsDataURL
---

{{APIRef("File API")}} {{AvailableInWorkers("worker_except_service")}}

متد **`readAsDataURL()`** از رابط {{DOMxRef("FileReaderSync")}} امکان خواندن همزمان اشیاء {{DOMxRef("File")}} یا {{DOMxRef("Blob")}} را به صورت یک رشته که یک داده URL را نشان می‌دهد، فراهم می‌کند. این رابط [فقط در workerها](/en-US/docs/Web/API/Web_Workers_API/Functions_and_classes_available_to_workers) [در دسترس](/en-US/docs/Web/API/Worker) است، زیرا ورودی/خروجی همزمان را فعال می‌کند که به طور بالقوه می‌تواند مسدودکننده باشد.

## نحو

```js-nolint
readAsDataURL(blob)
```

### پارامترها

- `blob`
  - : شیء {{DOMxRef("File")}} یا {{DOMxRef("Blob")}} که باید خوانده شود.

### مقدار بازگشتی

رشته‌ای که داده ورودی را به صورت یک داده URL نشان می‌دهد.

### استثناها

استثناهای زیر می‌توانند توسط این متد ایجاد شوند:

- `NotFoundError` {{domxref("DOMException")}}
  - : اگر منبعی که توسط {{DOMxRef("File")}} یا {{DOMxRef("Blob")}} نمایش داده می‌شود پیدا نشود، مثلاً به دلیل پاک شدن، پرتاب می‌شود.
- `SecurityError` {{domxref("DOMException")}}
  - : اگر یکی از وضعیت‌های مشکل‌ساز زیر شناسایی شود، پرتاب می‌شود:
    - منبع توسط شخص ثالث تغییر کرده باشد؛
    - عملیات خواندن بیش از حد به طور همزمان انجام شود؛
    - فایلی که منبع به آن اشاره می‌کند برای استفاده از وب امن نباشد (مانند فایل‌های سیستم).
- `NotReadableError` {{domxref("DOMException")}}
  - : اگر منبع به دلیل مشکل مجوز مانند قفل همزمان قابل خواندن نباشد، پرتاب می‌شود.
- `EncodingError` {{domxref("DOMException")}}
  - : اگر منبع یک داده URL باشد و از حداکثر طول تعیین‌شده توسط هر مرورگر فراتر رود، پرتاب می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{DOMxRef("File")}}
- {{DOMxRef("FileReaderSync")}}
- {{DOMxRef("FileReader")}}
- {{ domxref("Blob") }}