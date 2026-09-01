---
title: "FileSystemEntry: name property"
short-title: name
slug: Web/API/FileSystemEntry/name
page-type: web-api-instance-property
browser-compat: api.FileSystemEntry.name
---

{{APIRef("File and Directory Entries API")}}

خاصیت فقط-خواندنی **`name`** در رابط {{domxref("FileSystemEntry")}} یک رشته برمی‌گرداند که نام ورودی را مشخص می‌کند؛ این نام، همان ورودی در داخل پوشه‌ی والد آن است (آخرین جزء مسیر که توسط خاصیت {{domxref("FileSystemEntry.fullPath", "fullPath")}} نشان داده می‌شود).

## مقدار

یک رشته که نام ورودی را نشان می‌دهد.

## مثال‌ها

این مثال تابعی به نام `isFileWithExtension()` را نشان می‌دهد که اگر {{domxref("FileSystemEntry")}} داده‌شده هم یک فایل باشد و هم نام فایل به پسوند مشخصی ختم شود، مقدار `true` برمی‌گرداند.

```js
function isFileWithExtension(entry, extension) {
  return entry.isFile && entry.name.endsWith(`.${extension}`);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [رابط API ورودی‌های فایل و پوشه](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("FileSystemEntry")}}
- {{domxref("FileSystemEntry.fullPath")}}