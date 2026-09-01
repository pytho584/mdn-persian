---
title: "FileSystemEntry: filesystem property"
short-title: filesystem
slug: Web/API/FileSystemEntry/filesystem
page-type: web-api-instance-property
browser-compat: api.FileSystemEntry.filesystem
---

{{APIRef("File and Directory Entries API")}}

ویژگی فقط خواندنی **`filesystem`** در رابط {{domxref("FileSystemEntry")}} یک شیء {{domxref("FileSystem")}} را در بر می‌گیرد که نمایانگر سیستم فایلی است که این ورودی (entry) در آن قرار دارد.

## مقدار

یک {{domxref("FileSystem")}} که سیستم فایل حاوی فایل یا دایرکتوری توصیف‌شده توسط `FileSystemEntry` را نشان می‌دهد.

## مثال‌ها

این مثال یک {{domxref("FileSystemDirectoryEntry")}} برای دایرکتوری ریشه سیستم فایل حاوی یک فایل به دست می‌آورد.

```js
let rootDirEntry = fileEntry.filesystem.root;
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [API ورودی‌های فایل و دایرکتوری](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("FileSystemEntry")}}
- {{domxref("FileSystem")}}