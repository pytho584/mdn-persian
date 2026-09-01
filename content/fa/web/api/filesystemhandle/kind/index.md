---
title: "FileSystemHandle: kind property"
short-title: kind
slug: Web/API/FileSystemHandle/kind
page-type: web-api-instance-property
browser-compat: api.FileSystemHandle.kind
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`kind`** در رابط {{domxref("FileSystemHandle")}} نوع ورودی را برمی‌گرداند. این مقدار اگر ورودی مرتبط یک فایل باشد `'file'` و اگر دایرکتوری باشد `'directory'` است. از این ویژگی برای تشخیص فایل‌ها از دایرکتوری‌ها هنگام پیمایش محتویات یک دایرکتوری استفاده می‌شود.

## مقدار

یک رشته که می‌تواند یکی از موارد زیر باشد:

- `'file'`: اگر هندل یک {{domxref('FileSystemFileHandle')}} باشد.
- `'directory'`: اگر هندل یک {{domxref('FileSystemDirectoryHandle')}} باشد.

## مثال‌ها

تابع زیر به کاربر اجازه می‌دهد یک فایل را از انتخاب‌گر فایل انتخاب کند و سپس بررسی می‌کند که هندل برگشت‌داده‌شده فایل است یا دایرکتوری:

```js
// store a reference to our file handle
let fileHandle;

async function getFile() {
  // open file picker
  [fileHandle] = await window.showOpenFilePicker();

  if (fileHandle.kind === "file") {
    // run file code
  } else if (fileHandle.kind === "directory") {
    // run directory code
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)