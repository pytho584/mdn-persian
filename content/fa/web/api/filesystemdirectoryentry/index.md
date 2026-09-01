---
title: FileSystemDirectoryEntry
slug: Web/API/FileSystemDirectoryEntry
page-type: web-api-interface
browser-compat: api.FileSystemDirectoryEntry
---

{{APIRef("File and Directory Entries API")}}

رابطهٔ **`FileSystemDirectoryEntry`** در [API ورودیهای فایل و دایرکتوری](/en-US/docs/Web/API/File_and_Directory_Entries_API) نمایانگر یک دایرکتوری در سیستم فایل است. این رابط روشهایی را فراهم میکند که دسترسی و مدیریت فایلهای داخل یک دایرکتوری و همچنین دسترسی به ورودیهای درون آن دایرکتوری را ممکن میسازد.

{{InheritanceDiagram}}

## مفاهیم پایه

شما میتوانید با فراخوانی {{domxref("FileSystemDirectoryEntry.getDirectory", "getDirectory()")}} یک دایرکتوری جدید بسازید. اگر میخواهید زیردایرکتوریها ایجاد کنید، هر زیردایرکتوری فرزند را به ترتیب بسازید. اگر بخواهید با استفاده از یک مسیر کامل که شامل دایرکتوریهای والد است که هنوز وجود ندارند، دایرکتوری ایجاد کنید، خطا برگردانده میشود. بنابراین سلسلهمراتب را با افزودن بازگشتی یک مسیر جدید پس از ایجاد دایرکتوری والد بسازید.

### مثال

در قطعهکد زیر، دایرکتوریای به نام «Documents» ایجاد میکنیم.

```js
// Taking care of the browser-specific prefixes.
window.requestFileSystem =
  window.requestFileSystem || window.webkitRequestFileSystem;
window.directoryEntry = window.directoryEntry || window.webkitDirectoryEntry;

// …

function onFs(fs) {
  fs.root.getDirectory(
    "Documents",
    { create: true },
    (directoryEntry) => {
      // directoryEntry.isFile === false
      // directoryEntry.isDirectory === true
      // directoryEntry.name === 'Documents'
      // directoryEntry.fullPath === '/Documents'
    },
    onError,
  );
}

// Opening a file system with temporary storage
window.requestFileSystem(TEMPORARY, 1024 * 1024 /* 1MB */, onFs, onError);
```

## ویژگیهای نمونه

_این رابط ویژگی خاص خود را ندارد، اما ویژگیهای رابط والد خود، یعنی {{domxref("FileSystemEntry")}} را به ارث میبرد._

## روشهای نمونه

_این رابط روشهای رابط والد خود، یعنی {{domxref("FileSystemEntry")}} را به ارث میبرد._

- {{domxref("FileSystemDirectoryEntry.createReader", "createReader()")}}
  - : یک شیء {{domxref("FileSystemDirectoryReader")}} میسازد که میتوان از آن برای خواندن ورودیهای این دایرکتوری استفاده کرد.
- {{domxref("FileSystemDirectoryEntry.getDirectory", "getDirectory()")}}
  - : یک شیء `FileSystemDirectoryEntry` برمیگرداند که نمایانگر دایرکتوریای است که در مسیر معین، نسبت به دایرکتوری که روش روی آن فراخوانی شده، قرار دارد.
- {{domxref("FileSystemDirectoryEntry.getFile", "getFile()")}}
  - : یک شیء {{domxref("FileSystemFileEntry")}} برمیگرداند که نمایانگر فایلی در سلسلهمراتب دایرکتوری است، با توجه به مسیری نسبی نسبت به دایرکتوری که روش روی آن فراخوانی شده است.
- {{domxref("FileSystemDirectoryEntry.removeRecursively", "removeRecursively()")}} {{Deprecated_inline}} {{Non-standard_inline}}
  - : دایرکتوری و همچنین تمام محتوای آن را حذف میکند، بهصورت سلسلهمراتبی در تمام زیردرخت فرزندان، فایلها و دایرکتوریها حرکت میکند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [API ورودیهای فایل و دایرکتوری](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("FileSystemDirectoryReader")}}
- {{domxref("FileSystemEntry")}}
- {{domxref("FileSystemFileEntry")}}