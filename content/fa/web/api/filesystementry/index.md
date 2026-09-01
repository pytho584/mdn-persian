---
title: "FileSystemEntry"
---

---
title: FileSystemEntry
slug: Web/API/FileSystemEntry
page-type: web-api-interface
browser-compat: api.FileSystemEntry
---

{{APIRef("File and Directory Entries API")}}

رابط **`FileSystemEntry`** در «File and Directory Entries API» یک ورودی واحد در یک سیستم فایل را نشان می‌دهد. این ورودی می‌تواند یک فایل یا یک دایرکتوری باشد (دایرکتوری‌ها توسط رابط {{domxref("FileSystemDirectoryEntry")}} نشان داده می‌شوند). این رابط شامل روش‌هایی برای کار با فایل‌ها—از جمله کپی، جابجایی، حذف و خواندن فایل‌ها—و همچنین اطلاعاتی درباره فایلی که به آن اشاره می‌کند—از جمله نام فایل و مسیر آن از ریشه تا ورودی—است.

## مفاهیم پایه

شما مستقیماً اشیاء `FileSystemEntry` را ایجاد نمی‌کنید. در عوض، از طریق سایر APIها، شیئی بر اساس این رابط دریافت خواهید کرد. این رابط به عنوان کلاس پایه برای رابط‌های {{domxref("FileSystemFileEntry")}} و {{domxref("FileSystemDirectoryEntry")}} عمل می‌کند که به ترتیب ویژگی‌های خاصی را برای ورودی‌های سیستم فایل که نمایانگر فایل‌ها و دایرکتوری‌ها هستند فراهم می‌کنند.

رابط `FileSystemEntry` شامل روش‌هایی است که انتظار دارید برای دستکاری فایل‌ها و دایرکتوری‌ها وجود داشته باشد، اما همچنین شامل یک روش مناسب برای به دست آوردن URL ورودی است: [`toURL()`](/en-US/docs/Web/API/FileSystemEntry/toURL). این رابط همچنین یک طرح URL جدید معرفی می‌کند: `filesystem:`.

می‌توانید از طرح `filesystem:` در گوگل کروم برای مشاهده همه فایل‌ها و پوشه‌هایی که در مبدأ (origin) برنامه‌تان ذخیره شده‌اند استفاده کنید. فقط از طرح `filesystem:` برای دایرکتوری ریشه مبدأ برنامه استفاده کنید. به عنوان مثال، اگر برنامه شما در [`http://www.example.com`](https://www.example.com/) است، `filesystem:http://www.example.com/temporary/` را در یک تب باز کنید. کروم یک فهرست فقط‌خواندنی از همه فایل‌ها و پوشه‌های ذخیره‌شده در مبدأ برنامه شما نشان می‌دهد.

### مثال

برای مشاهده نمونه‌ای از نحوه کارکرد `toURL()`، به [توضیحات روش](/en-US/docs/Web/API/FileSystemEntry/toURL) مراجعه کنید. قطعه کد زیر نشان می‌دهد که چگونه می‌توانید یک فایل را با نام حذف کنید.

```js
// Taking care of the browser-specific prefixes.
window.requestFileSystem =
  window.requestFileSystem || window.webkitRequestFileSystem;

// …

// Opening a file system with temporary storage
window.requestFileSystem(
  TEMPORARY,
  1024 * 1024 /* 1MB */,
  (fs) => {
    fs.root.getFile(
      "log.txt",
      {},
      (fileEntry) => {
        fileEntry.remove(() => {
          console.log("File removed.");
        }, onError);
      },
      onError,
    );
  },
  onError,
);
```

## ویژگی‌های نمونه

_این رابط ویژگی‌های زیر را فراهم می‌کند._

- {{domxref("FileSystemEntry.filesystem", "filesystem")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("FileSystem")}} که نشان‌دهنده سیستم فایلی است که ورودی در آن قرار دارد.
- {{domxref("FileSystemEntry.fullPath", "fullPath")}} {{ReadOnlyInline}}
  - : رشته‌ای که مسیر کامل و مطلق از ریشه سیستم فایل تا ورودی را ارائه می‌دهد؛ همچنین می‌توان آن را به عنوان مسیری نسبی نسبت به دایرکتوری ریشه در نظر گرفت که در ابتدای آن کاراکتر "/" قرار دارد.
- {{domxref("FileSystemEntry.isDirectory", "isDirectory")}} {{ReadOnlyInline}}
  - : یک مقدار بولی که اگر ورودی نشان‌دهنده یک دایرکتوری باشد `true` است؛ در غیر این صورت، `false` است.
- {{domxref("FileSystemEntry.isFile", "isFile")}} {{ReadOnlyInline}}
  - : یک مقدار بولی که اگر ورودی نشان‌دهنده یک فایل باشد `true` است. اگر فایل نباشد، این مقدار `false` است.
- {{domxref("FileSystemEntry.name", "name")}} {{ReadOnlyInline}}
  - : رشته‌ای شامل نام ورودی (بخش پایانی مسیر، بعد از آخرین کاراکتر "/").

## روش‌های نمونه

_این رابط روش‌های زیر را تعریف می‌کند._

- {{domxref("FileSystemEntry.copyTo", "copyTo()")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : فایل یا دایرکتوری را به مکان جدیدی در سیستم فایل کپی می‌کند.
- {{domxref("FileSystemEntry.getMetadata", "getMetadata()")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : فراداده (metadata) مربوط به فایل، مانند تاریخ تغییر و اندازه آن را به دست می‌آورد.
- {{domxref("FileSystemEntry.getParent", "getParent()")}}
  - : یک {{domxref("FileSystemDirectoryEntry")}} که نمایانگر دایرکتوری والد ورودی است را برمی‌گرداند.
- {{domxref("FileSystemEntry.moveTo", "moveTo()")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : فایل یا دایرکتوری را به مکان جدیدی در سیستم فایل منتقل می‌کند، یا فایل یا دایرکتوری را تغییر نام می‌دهد.
- {{domxref("FileSystemEntry.remove", "remove()")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : فایل یا دایرکتوری مشخص‌شده را حذف می‌کند. شما فقط می‌توانید دایرکتوری‌هایی را حذف کنید که خالی هستند.
- {{domxref("FileSystemEntry.toURL", "toURL()")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : یک URL که ورودی را شناسایی می‌کند ایجاد و برمی‌گرداند. این URL از طرح URL `"filesystem:"` استفاده می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("FileSystemFileEntry")}} و {{domxref("FileSystemDirectoryEntry")}} بر اساس `FileSystemEntry` هستند.