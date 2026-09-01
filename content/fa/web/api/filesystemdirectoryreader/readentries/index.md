---
title: "FileSystemDirectoryReader: readEntries() method"
short-title: readEntries()
slug: Web/API/FileSystemDirectoryReader/readEntries
page-type: web-api-instance-method
browser-compat: api.FileSystemDirectoryReader.readEntries
---

{{APIRef("File and Directory Entries API")}}

متد **`readEntries()`** از رابط {{domxref("FileSystemDirectoryReader")}} ورودی‌های دایرکتوریِ در حال خواندن را بازیابی می‌کند و آن‌ها را در قالب یک آرایه به تابع بازگشتیِ داده‌شده تحویل می‌دهد.

اشیاء موجود در آرایه همگی بر پایه {{domxref("FileSystemEntry")}} هستند. به‌طور کلی، آن‌ها یا آبجکت‌های {{domxref("FileSystemFileEntry")}} هستند که فایل‌های استاندارد را نشان می‌دهند، یا آبجکت‌های {{domxref("FileSystemDirectoryEntry")}} که دایرکتوری‌ها را نشان می‌دهند.

## سینتکس

```js-nolint
readEntries(successCallback)
readEntries(successCallback, errorCallback)
```

### پارامترها

- `successCallback`
  - : تابعی که هنگام بازیابی محتویات دایرکتوری فراخوانی می‌شود. این تابع یک پارامتر ورودی دریافت می‌کند: آرایه‌ای از اشیاء ورودیِ سیستم فایل که هر کدام بر پایه {{domxref("FileSystemEntry")}} هستند. به‌طور کلی، آن‌ها یا آبجکت‌های {{domxref("FileSystemFileEntry")}} هستند که فایل‌های استاندارد را نشان می‌دهند، یا آبجکت‌های {{domxref("FileSystemDirectoryEntry")}} که دایرکتوری‌ها را نشان می‌دهند. اگر فایل دیگری باقی نمانده باشد یا قبلاً `readEntries()` را روی این {{domxref("FileSystemDirectoryReader")}} فراخوانی کرده باشید، آرایه خالی خواهد بود.
- `errorCallback` {{optional_inline}}
  - : تابع بازگشتی که در صورت بروز خطا هنگام خواندن از دایرکتوری فراخوانی می‌شود. این تابع یک پارامتر ورودی دریافت می‌کند: یک آبجکت {{domxref("DOMException")}} که خطای رخ‌داده را توصیف می‌کند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

برای نمونه‌کدهای استفاده از این متد، [`DataTransferItem.webkitGetAsEntry()`](/en-US/docs/Web/API/DataTransferItem/webkitGetAsEntry#examples) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

در مرورگرهای مبتنی بر Chromium، `readEntries()` تنها اولین ۱۰۰ نمونه `FileSystemEntry` را برمی‌گرداند. برای دریافت همه نمونه‌ها، باید `readEntries()` چندین بار فراخوانی شود.

## همچنین ببینید

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("FileSystemDirectoryEntry")}}
- {{domxref("FileSystem")}}