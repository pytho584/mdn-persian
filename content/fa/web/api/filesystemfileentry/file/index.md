---
title: "FileSystemFileEntry: file() method"
short-title: file()
slug: Web/API/FileSystemFileEntry/file
page-type: web-api-instance-method
browser-compat: api.FileSystemFileEntry.file
---

{{APIRef("File and Directory Entries API")}}

متد **`file()`** در رابط {{domxref("FileSystemFileEntry")}} یک شیء {{domxref("File")}} برمی‌گرداند که می‌توان از آن برای خواندن داده‌های فایلِ متناظر با این ورودی دایرکتوری استفاده کرد.

## نحو (Syntax)

```js-nolint
file(successCallback)
file(successCallback, errorCallback)
```

### پارامترها

- `successCallback`
  - : یک تابع回调 که وقتی {{domxref("File")}} با موفقیت ساخته شد فراخوانی می‌شود؛ شیء `File` به‌عنوان تنها پارامتر به این تابع回调 ارسال می‌شود.
- `errorCallback` {{optional_inline}}
  - : در صورت ارائه، این باید تابعی باشد که هنگام بروز خطا در تلاش برای ساخت {{domxref("File")}} فراخوانی می‌شود. این تابع回调 یک شیء {{domxref("DOMException")}} شامل شرح خطا را به‌عنوان ورودی دریافت می‌کند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

این مثال یک متد به نام `readFile()` ایجاد می‌کند که یک فایل متنی را می‌خواند و پس از اتمام خواندن، متن دریافتی (به‌صورت رشته) را به یک تابع回调 مشخص‌شده ارسال می‌کند. اگر خطایی رخ دهد، یک تابع خطا (اختیاری) فراخوانی می‌شود.

```js
function readFile(entry, successCallback, errorCallback) {
  entry.file((file) => {
    let reader = new FileReader();

    reader.onload = () => {
      successCallback(reader.result);
    };

    reader.onerror = () => {
      errorCallback(reader.error);
    };

    reader.readAsText(file);
  }, errorCallback);
}
```

این تابع `file()` را فراخوانی می‌کند و به‌عنوان تابع موفقیت، تابعی را مشخص می‌کند که از {{domxref("FileReader")}} برای خواندن فایل به‌صورت متن استفاده می‌کند. رویداد {{domxref("FileReader/load_event", "load")}} مربوط به FileReader طوری تنظیم شده است که رشته بارگذاری‌شده را به `successCallback` که هنگام فراخوانی متد `readFile()` مشخص شده تحویل دهد؛ به همین ترتیب، رویداد {{domxref("FileReader/error_event", "error")}} آن نیز برای فراخوانی `errorCallback` تنظیم شده است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)