---
title: "FileSystemEntry: isFile property"
---

---
title: "FileSystemEntry: isFile property"
short-title: isFile
slug: Web/API/FileSystemEntry/isFile
page-type: web-api-instance-property
browser-compat: api.FileSystemEntry.isFile
---

{{APIRef("File and Directory Entries API")}}

ویژگی فقط‌خواندنی **`isFile`** از رابط {{domxref("FileSystemEntry")}}، اگر ورودی (entry) یک فایل را نشان دهد (یعنی یک {{domxref("FileSystemFileEntry")}} باشد)، مقدار `true` و در غیر این صورت مقدار `false` را دارد.

همچنین می‌توانید از {{domxref("FileSystemEntry.isDirectory", "isDirectory")}} برای تعیین اینکه آیا ورودی یک پوشه (دایرکتوری) است استفاده کنید.

> [!WARNING]
> نباید فرض کنید که هر ورودی‌ای که فایل نیست، پوشه است یا برعکس. در بسیاری از سیستم‌عامل‌ها انواع دیگری از توصیفگرهای فایل (file descriptors) نیز وجود دارند. حتماً در صورت نیاز از هر دو `isDirectory` و `isFile` استفاده کنید تا مطمئن شوید ورودی موردنظر از نوعی است که می‌دانید چگونه با آن کار کنید.

## مقدار

یک مقدار بولین (Boolean) که نشان می‌دهد آیا {{domxref("FileSystemEntry")}} یک فایل است یا خیر.

## مثال‌ها

این مثال نشان می‌دهد که چگونه می‌توان از این ویژگی برای تعیین اینکه ورودی باید به‌عنوان پوشه پردازش شود یا فایل استفاده کرد. اگر ورودی هیچ‌کدام نباشد، یک مدیریت‌کننده خطا (error handler) با پیام مناسب فراخوانی می‌شود.

```js
if (entry.isDirectory) {
  processSubdirectory(entry);
} else if (entry.isFile) {
  processFile(entry);
} else {
  displayErrorMessage("Unsupported file system entry specified.");
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("FileSystemEntry")}}
- {{domxref("FileSystemEntry.isDirectory")}}
- {{domxref("FileSystemFileEntry")}}