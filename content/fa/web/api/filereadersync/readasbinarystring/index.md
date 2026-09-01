---
title: "FileReaderSync: readAsBinaryString() method"
short-title: readAsBinaryString()
slug: Web/API/FileReaderSync/readAsBinaryString
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.FileReaderSync.readAsBinaryString
---

{{APIRef("File API")}}{{deprecated_header}} {{AvailableInWorkers("worker_except_service")}}

> [!NOTE]
> این روش به‌نفع {{DOMxRef("FileReaderSync.readAsArrayBuffer","readAsArrayBuffer()")}} منسوخ شده است.

متد **`readAsBinaryString()`** از رابط {{DOMxRef("FileReaderSync")}} امکان خواندن همزمان اشیاء {{DOMxRef("File")}} یا {{DOMxRef("Blob")}} را به‌صورت یک رشته فراهم می‌کند. این رابط در [workerها](/en-US/docs/Web/API/Worker) [فقط در دسترس است](/en-US/docs/Web/API/Web_Workers_API/Functions_and_classes_available_to_workers)، زیرا ورودی/خروجی همزمان را فعال می‌کند که بالقوه می‌تواند مسدودکننده باشد.

## سینتکس

```js-nolint
readAsBinaryString(blob)
```

### پارامترها

- `blob`
  - : شیء {{DOMxRef("File")}} یا {{DOMxRef("Blob")}} برای خواندن.

### مقدار بازگشتی

یک رشته که نشان‌دهنده داده‌های ورودی است.

### استثناها

- `NotFoundError` {{domxref("DOMException")}}
  - : اگر منبع نمایش‌داده‌شده توسط DOM {{DOMxRef("File")}} یا {{DOMxRef("Blob")}} پیدا نشود، مثلاً به دلیل پاک شدن، پرتاب می‌شود.
- `SecurityError` {{domxref("DOMException")}}
  - : اگر یکی از شرایط مشکل‌ساز زیر تشخیص داده شود، پرتاب می‌شود:
    - منبع توسط شخص ثالث تغییر کرده باشد؛
    - بیش از حد مجاز خوانش همزمان انجام شده باشد؛
    - فایلی که منبع به آن اشاره می‌کند برای استفاده در وب امن نباشد (مانند فایل سیستمی).
- `NotReadableError` {{domxref("DOMException")}}
  - : اگر به دلیل مشکل مجوز، مانند قفل همزمان، امکان خواندن منبع وجود نداشته باشد، پرتاب می‌شود.
- `EncodingError` {{domxref("DOMException")}}
  - : اگر منبع یک data URL باشد و از حداکثر طول تعیین‌شده توسط هر مرورگر فراتر رود، پرتاب می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File API](/en-US/docs/Web/API/File_API)
- {{DOMxRef("File")}}
- {{DOMxRef("FileReaderSync")}}
- {{DOMxRef("FileReader")}}
- {{ domxref("Blob") }}