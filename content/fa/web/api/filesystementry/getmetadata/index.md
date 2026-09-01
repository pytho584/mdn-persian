---
title: "FileSystemEntry: getMetadata() method"
short-title: getMetadata()
slug: Web/API/FileSystemEntry/getMetadata
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.FileSystemEntry.getMetadata
---

{{APIRef("File and Directory Entries API")}}{{Deprecated_Header}}{{Non-standard_Header}}

در رابط {{domxref("FileSystemEntry")}}، متد **`getMetadata()`** یک شیء {{domxref("Metadata")}} حاوی اطلاعاتی دربارهٔ ورودی سیستم فایل، مانند تاریخ و زمان آخرین تغییر و اندازهٔ آن، دریافت می‌کند.

## نحو (Syntax)

```js-nolint
getMetadata(successCallback)
getMetadata(successCallback, errorCallback)
```

### پارامترها

- `successCallback`
  - : تابعی که پس از اتمام موفقیت‌آمیز عملیات کپی فراخوانی می‌شود. این تابع یک پارامتر ورودی دریافت می‌کند: یک شیء {{domxref("Metadata")}} حاوی اطلاعات مربوط به فایل.
- `errorCallback` {{optional_inline}}
  - : یک callback اختیاری که در صورت بروز خطا هنگام جستجوی فراداده (metadata) اجرا می‌شود. این تابع یک پارامتر دارد: یک {{domxref("DOMException")}} که نوع خطا را توصیف می‌کند.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- `DOMException.NOT_FOUND_ERR`
  - : {{domxref("FileSystemEntry")}} به یک آیتم اشاره دارد که وجود ندارد.
- `DOMException.SECURITY_ERR`
  - : محدودیت‌های امنیتی از دریافت فرادادهٔ درخواست‌شده جلوگیری می‌کنند.

## مثال

این مثال اندازهٔ یک فایل لاگ را در یک پوشهٔ موقت بررسی می‌کند و اگر از یک مگابایت بزرگ‌تر باشد، آن را به پوشهٔ دیگری منتقل می‌کند.

```js
workingDirectory.getFile(
  "tmp/log.txt",
  {},
  (fileEntry) => {
    fileEntry.getMetadata((metadata) => {
      if (metadata.size > 1048576) {
        workingDirectory.getDirectory(
          "log",
          {},
          (dirEntry) => {
            fileEntry.moveTo(dirEntry);
          },
          handleError,
        );
      }
    });
  },
  handleError,
);
```

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [API ورودی‌های فایل و دایرکتوری](/en-US/docs/Web/API/File_and_Directory_Entries_API)