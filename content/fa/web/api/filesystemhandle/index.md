---
title: FileSystemHandle
slug: Web/API/FileSystemHandle
page-type: web-api-interface
browser-compat: api.FileSystemHandle
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}

رابط **`FileSystemHandle`** در {{domxref('File System API', '', '', 'nocode')}} یک شیء است که یک ورودی (entry) فایل یا دایرکتوری را نمایش می‌دهد. چندین handle می‌توانند نمایانگر یک ورودی یکسان باشند. در بیشتر موارد، به‌طور مستقیم با `FileSystemHandle` کار نمی‌کنید، بلکه با رابط‌های فرزند آن یعنی {{domxref('FileSystemFileHandle')}} و {{domxref('FileSystemDirectoryHandle')}} سروکار دارید.

## رابط‌های مبتنی بر FileSystemHandle

در ادامه فهرستی از رابط‌های مبتنی بر رابط `FileSystemHandle` آورده شده است.

- {{domxref("FileSystemFileHandle")}}
  - : نمایانگر یک handle به یک ورودی فایل است.
- {{domxref("FileSystemDirectoryHandle")}}
  - : یک handle به یک ورودی دایرکتوری فراهم می‌کند.

## ویژگی‌های نمونه

- {{domxref('FileSystemHandle.kind','kind')}} {{ReadOnlyInline}}
  - : نوع ورودی را بازمی‌گرداند. اگر ورودی مرتبط یک فایل باشد، مقدار `'file'` و اگر دایرکتوری باشد، مقدار `'directory'` است.
- {{domxref('FileSystemHandle.name', 'name')}} {{ReadOnlyInline}}
  - : نام ورودی مرتبط را بازمی‌گرداند.

## روش‌های نمونه

- {{domxref('FileSystemHandle.isSameEntry()', 'isSameEntry()')}}
  - : دو handle را با هم مقایسه می‌کند تا ببیند آیا ورودی‌های مرتبط (فایل یا دایرکتوری) یکسان هستند یا نه.
- {{domxref('FileSystemHandle.queryPermission()', 'queryPermission()')}} {{Experimental_Inline}}
  - : وضعیت فعلی مجوزِ handle جاری را پرس‌وجو می‌کند.
- {{domxref('FileSystemHandle.remove', 'remove()')}} {{Experimental_Inline}} {{Non-standard_Inline}}
  - : درخواست حذف ورودیِ نمایش‌داده‌شده توسط handle را از سیستم فایل زیرین می‌دهد.
- {{domxref('FileSystemHandle.requestPermission', 'requestPermission()')}} {{Experimental_Inline}}
  - : برای handle فایل، مجوز خواندن یا خواندن/نوشتن را درخواست می‌کند.

## مثال‌ها

### بررسی نوع

کد زیر به کاربر اجازه می‌دهد یک فایل را از انتخابگر فایل انتخاب کند و سپس بررسی می‌کند که آیا handle بازگشتی یک فایل است یا یک دایرکتوری.

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

### پرس‌وجو/درخواست مجوزها

تابع ناهمگام زیر مقدار `true` را بازمی‌گرداند اگر کاربر مجوز خواندن یا خواندن/نوشتن را به handle فایل داده باشد. در غیر این صورت، مجوز درخواست می‌شود.

```js
// fileHandle is a FileSystemFileHandle
// withWrite is a boolean set to true if write

async function verifyPermission(fileHandle, withWrite) {
  const opts = {};
  if (withWrite) {
    opts.mode = "readwrite";
  }

  // Check if we already have permission, if so, return true.
  if ((await fileHandle.queryPermission(opts)) === "granted") {
    return true;
  }

  // Request permission to the file, if the user grants permission, return true.
  if ((await fileHandle.requestPermission(opts)) === "granted") {
    return true;
  }

  // The user did not grant permission, return false.
  return false;
}
```

### مقایسه ورودی‌ها

تابع زیر یک ورودی را با یک آرایه از ورودی‌ها مقایسه می‌کند و آرایه جدیدی را برمی‌گرداند که در آن هر ورودیِ منطبق حذف شده است.

```js
function removeMatches(fileEntry, entriesArr) {
  const newArr = entriesArr.filter((entry) => !fileEntry.isSameEntry(entry));

  return newArr;
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)