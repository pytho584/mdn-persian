---
title: "FileSystemHandle: name property"
short-title: name
slug: Web/API/FileSystemHandle/name
page-type: web-api-instance-property
browser-compat: api.FileSystemHandle.name
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`name`** در رابط {{domxref("FileSystemHandle")}} نام ورودی‌ای را که توسط هندل (handle) نشان داده می‌شود، برمی‌گرداند.

## مقدار

یک رشته (string).

## مثال‌ها

تابع زیر به کاربر اجازه می‌دهد تا یک فایل را از انتخاب‌گر فایل انتخاب کند و ویژگی `name` را بازیابی کند.

```js
// ذخیره ارجاعی به هندل فایل ما
let fileHandle;

async function getFile() {
  // باز کردن انتخاب‌گر فایل
  [fileHandle] = await window.showOpenFilePicker();

  const fileName = fileHandle.name;
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)