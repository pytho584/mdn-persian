---
title: "FileSystemEntry: isDirectory property"
short-title: isDirectory
slug: Web/API/FileSystemEntry/isDirectory
page-type: web-api-instance-property
browser-compat: api.FileSystemEntry.isDirectory
---

{{APIRef("File and Directory Entries API")}}

خاصیت فقط خواندنی **`isDirectory`** در رابط {{domxref("FileSystemEntry")}} اگر ورودی یک دایرکتوری باشد (یعنی یک {{domxref("FileSystemDirectoryEntry")}} باشد) مقدار `true` و در غیر این صورت `false` است.

همچنین می‌توانید از {{domxref("FileSystemEntry.isFile", "isFile")}} برای تشخیص فایل بودن ورودی استفاده کنید.

> [!WARNING]
> نباید فرض کنید هر ورودی که دایرکتوری نیست حتماً فایل است یا برعکس. در بسیاری از سیستم‌عامل‌ها انواع دیگری از توصیف‌کننده‌های فایل وجود دارند. حتماً هر دو ویژگی `isDirectory` و `isFile` را در صورت نیاز به‌کار ببرید تا مطمئن شوید ورودی از نوعی است که می‌توانید با آن کار کنید.

## مقدار

یک مقدار بولی (Boolean) که نشان می‌دهد {{domxref("FileSystemEntry")}} یک دایرکتوری است یا خیر.

## مثال‌ها

این مثال نحوه استفاده از این ویژگی را برای تصمیم‌گیری درباره پردازش ورودی به‌عنوان دایرکتوری یا فایل نشان می‌دهد. اگر ورودی هیچ‌کدام نباشد، یک تابع مدیریت خطا با پیام مناسب فراخوانی می‌شود.

```js
if (entry.isDirectory) {
  processSubdirectory(entry);
} else if (entry.isFile) {
  processFile(entry);
} else {
  displayErrorMessage("ورودی سیستم فایل پشتیبانی‌نشده مشخص شده است.");
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [API ورودی‌های فایل و دایرکتوری](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("FileSystemEntry")}}
- {{domxref("FileSystemEntry.isFile")}}
- {{domxref("FileSystemDirectoryEntry")}}