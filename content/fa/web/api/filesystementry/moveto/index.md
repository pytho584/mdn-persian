---
title: "FileSystemEntry: moveTo() method"
short-title: moveTo()
slug: Web/API/FileSystemEntry/moveTo
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.FileSystemEntry.moveTo
---

{{APIRef("File and Directory Entries API")}}{{Deprecated_Header}}{{Non-standard_Header}}

متد **`moveTo()`** در رابط {{domxref("FileSystemEntry")}} فایل مشخص‌شده توسط این ورودی را به مکان جدیدی در سیستم فایل منتقل می‌کند، یا اگر دایرکتوری مقصد با دایرکتوری مبدأ یکسان باشد، فایل را تغییر نام می‌دهد.

برخی محدودیت‌های معمول برای کاری که می‌توانید انجام دهید وجود دارد:

- یک دایرکتوری نمی‌تواند به درون خودش منتقل شود.
- یک ورودی نمی‌تواند به دایرکتوری والد خود منتقل شود، مگر اینکه نام جدیدی را مشخص کنید. مشخص کردن نام جدید به `moveTo()` اجازه می‌دهد تا به‌عنوان یک عملیات تغییر نام نیز عمل کند.
- هنگام انتقال یک دایرکتوری، انتقال همیشه به‌صورت بازگشتی انجام می‌شود؛ نمی‌توانید زیرشاخه‌ها را کنار بگذارید.
- نمی‌توانید فایلی را طوری منتقل کنید که جایگزین یک دایرکتوری موجود شود، و همچنین نمی‌توانید دایرکتوری را طوری منتقل کنید که جایگزین یک فایل موجود شود. با این حال، یک فایل می‌تواند جایگزین یک فایل شود و یک دایرکتوری می‌تواند جایگزین یک دایرکتوری شود.
- فقط زمانی می‌توانید یک دایرکتوری را بازنویسی کنید که خالی باشد.

## سینتکس

```js-nolint
moveTo(newParent, newName)
moveTo(newParent, newName, successCallback)
moveTo(newParent, newName, successCallback, errorCallback)
```

### پارامترها

- `newParent`
  - : یک شیء {{domxref("FileSystemDirectoryEntry")}} که دایرکتوری مقصد را برای عملیات انتقال مشخص می‌کند.
- `newName` {{optional_inline}}
  - : اگر این پارامتر ارائه شود، ورودی تغییر نام می‌یابد تا این رشته به‌عنوان نام جدید فایل یا دایرکتوری آن استفاده شود.
- `successCallback` {{optional_inline}}
  - : تابعی که پس از تکمیل موفقیت‌آمیز عملیات انتقال فراخوانی می‌شود. این تابع یک پارامتر ورودی واحد دریافت می‌کند: یک شیء مبتنی بر {{domxref("FileSystemEntry")}} که جزئیات جدید آیتم منتقل‌شده را فراهم می‌کند.
- `errorCallback` {{optional_inline}}
  - : یک callback اختیاری که در صورت بروز خطا هنگام انتقال آیتم‌ها اجرا می‌شود. این تابع یک پارامتر دارد: یک {{domxref("DOMException")}} که خطای رخ‌داده را توصیف می‌کند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `DOMException.INVALID_MODIFICATION_ERR`
  - : عملیات درخواستی شامل یک تغییر غیرممکن است، مانند انتقال یک دایرکتوری به درون خودش یا یکی از دایرکتوری‌های فرزند خودش، یا کپی کردن یک آیتم در همان دایرکتوری بدون تغییر نام آن.
- `DOMException.QUOTA_EXCEEDED_ERR`
  - : عملیات از سهمیه ذخیره‌سازی کاربر فراتر رفته است، یا فضای ذخیره‌سازی کافی برای تکمیل عملیات باقی نمانده است.

### مثال‌ها

این مثال نشان می‌دهد که چگونه ممکن است یک فایل گزارش موقت، زمانی که اندازه‌اش از یک مگابایت فراتر می‌رود، به یک دایرکتوری دائمی‌تر به نام "log" منتقل شود.

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

### سازگاری مرورگر

{{Compat}}

### همچنین ببینید

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("FileSystemEntry.copyTo()")}}