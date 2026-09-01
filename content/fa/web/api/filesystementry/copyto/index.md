---
title: "FileSystemEntry: copyTo() method"
short-title: copyTo()
slug: Web/API/FileSystemEntry/copyTo
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.FileSystemEntry.copyTo
---

{{APIRef("File and Directory Entries API")}}{{Deprecated_Header}}{{Non-standard_Header}}

متد **`copyTo()`** در رابط {{domxref("FileSystemEntry")}}، فایل مشخص‌شده توسط ورودی را به مکان جدیدی در سیستم فایل کپی می‌کند.

برخی محدودیت‌های معمول در مورد کارهایی که می‌توان انجام داد وجود دارد:

- یک پوشه نمی‌تواند در خودش کپی شود.
- یک ورودی نمی‌تواند در پوشهٔ والد خود کپی شود، مگر اینکه نام جدیدی مشخص کنید.
- هنگام کپی کردن یک پوشه، کپی همیشه به صورت بازگشتی انجام می‌شود؛ نمی‌توانید زیرپوشه‌ها را حذف کنید.

## نحو (Syntax)

```js-nolint
copyTo(newParent)
copyTo(newParent, newName)
copyTo(newParent, newName, successCallback)
copyTo(newParent, newName, successCallback, errorCallback)
```

### پارامترها

- `newParent`
  - : یک شیء {{domxref("FileSystemDirectoryEntry")}} که پوشهٔ مقصد را برای عملیات کپی مشخص می‌کند.
- `newName` {{optional_inline}}
  - : اگر این پارامتر ارائه شود، کپی با این رشته به عنوان نام جدید فایل یا پوشه نام‌گذاری می‌شود.
- `successCallback` {{optional_inline}}
  - : تابعی که وقتی عملیات کپی با موفقیت کامل شود فراخوانی می‌شود. یک پارامتر ورودی واحد دریافت می‌کند: یک شیء مبتنی بر {{domxref("FileSystemEntry")}} که اطلاعات جدید آیتم کپی‌شده را فراهم می‌کند.
- `errorCallback` {{optional_inline}}
  - : یک تابع برگشت به اختیاری که در صورت بروز خطا هنگام کپی کردن آیتم‌ها اجرا می‌شود. یک پارامتر واحد دارد: یک {{domxref("DOMException")}} که شرح می‌دهد چه چیزی اشتباه رخ داده است.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `DOMException.INVALID_MODIFICATION_ERR`
  - : عملیات درخواستی شامل یک تغییر غیرممکن است، مانند انتقال یک پوشه به داخل خودش یا یکی از زیرپوشه‌های خودش، یا کپی کردن یک آیتم در همان پوشه بدون تغییر نام آن.
- `DOMException.QUOTA_EXCEEDED_ERR`
  - : عملیات از سهمیه ذخیره‌سازی کاربر فراتر رفته است، یا فضای ذخیره‌سازی کافی برای تکمیل عملیات وجود ندارد.

## مثال‌ها

این مثال نشان می‌دهد که چگونه ممکن است یک فایل گزارش موقت به یک پوشه «log» دائمی‌تر منتقل شود.

```js
workingDirectory.getFile(
  "tmp/log.txt",
  {},
  (fileEntry) => {
    workingDirectory.getDirectory(
      "log",
      {},
      (dirEntry) => {
        fileEntry.copyTo(dirEntry);
      },
      handleError,
    );
  },
  handleError,
);
```

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)