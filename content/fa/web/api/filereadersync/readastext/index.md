---
title: "FileReaderSync: readAsText() method"
short-title: readAsText()
slug: Web/API/FileReaderSync/readAsText
page-type: web-api-instance-method
browser-compat: api.FileReaderSync.readAsText
---

{{APIRef("File API")}} {{AvailableInWorkers("worker_except_service")}}

متد **`readAsText()`** از رابط {{DOMxRef("FileReaderSync")}} امکان خواندن اشیاء {{DOMxRef("File")}} یا {{DOMxRef("Blob")}} را به صورت همزمان (synchronous) به یک رشته فراهم می‌کند. این رابط [فقط در workerها](/en-US/docs/Web/API/Web_Workers_API/Functions_and_classes_available_to_workers) در دسترس است زیرا I/O همزمان را فعال می‌کند که می‌تواند بالقوه مسدودکننده باشد.

## Syntax

```js-nolint
readAsText(blob)
readAsText(blob, encoding)
```

### پارامترها

- `blob`
  - : {{DOMxRef("File")}} یا {{DOMxRef("Blob")}} مورد نظر برای خواندن.
- `encoding` {{optional_inline}}
  - : پارامتر اختیاری که رمزگذاری مورد استفاده را مشخص می‌کند (مثلاً `iso-8859-1` یا `UTF-8`). اگر وجود نداشته باشد، متد یک الگوریتم تشخیص برای آن اعمال می‌کند.

### مقدار بازگشتی

یک رشته (string) که داده‌های ورودی را نمایش می‌دهد.

### استثناها (Exceptions)

استثناهای زیر ممکن است توسط این متد ایجاد شوند:

- `NotFoundError` {{domxref("DOMException")}}
  - : اگر منبع نمایش‌داده‌شده توسط {{DOMxRef("File")}} یا {{DOMxRef("Blob")}} DOM یافت نشود، مثلاً به دلیل پاک شدن، پرتاب می‌شود.
- `SecurityError` {{domxref("DOMException")}}
  - : اگر یکی از موقعیت‌های مشکل‌دار زیر تشخیص داده شود، پرتاب می‌شود:
    - منبع توسط شخص ثالث تغییر کرده باشد.
    - تعداد خواندن‌های همزمان بیش از حد باشد.
    - فایل اشاره‌شده توسط منبع برای استفاده از وب ناامن باشد (مانند فایل سیستمی).
- `NotReadableError` {{domxref("DOMException")}}
  - : اگر منبع به دلیل مشکل مجوز، مانند قفل همزمان، قابل خواندن نباشد، پرتاب می‌شود.
- `EncodingError` {{domxref("DOMException")}}
  - : اگر منبع یک URL داده‌ای (data URL) باشد و از حد طول تعیین‌شده توسط هر مرورگر فراتر رود، پرتاب می‌شود.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [File API](/en-US/docs/Web/API/File_API)
- {{DOMxRef("File")}}
- {{DOMxRef("FileReaderSync")}}
- {{DOMxRef("FileReader")}}
- {{ domxref("Blob") }}