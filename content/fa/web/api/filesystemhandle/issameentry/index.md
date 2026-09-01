---
title: "FileSystemHandle: isSameEntry() method"
short-title: isSameEntry()
slug: Web/API/FileSystemHandle/isSameEntry
page-type: web-api-instance-method
browser-compat: api.FileSystemHandle.isSameEntry
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}

متد **`isSameEntry()`** از رابط {{domxref("FileSystemHandle")}} دو {{domxref("FileSystemHandle", "handles")}} را مقایسه می‌کند تا ببیند آیا ورودی‌های مرتبط (چه فایل و چه دایرکتوری) با هم مطابقت دارند یا نه.

## نحو (Syntax)

```js-nolint
isSameEntry(fileSystemHandle)
```

### پارامترها

- {{domxref("FileSystemHandle")}}
  - : یک `FileSystemHandle` که باید با handle ای که متد روی آن فراخوانی شده است مطابقت داده شود.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک {{jsxref('Boolean')}} تحقق می‌یابد.

## مثال‌ها

تابع زیر یک ورودی واحد را با یک آرایه از ورودی‌ها مقایسه می‌کند و یک {{jsxref("Promise")}} برمی‌گرداند که با یک آرایه جدید که شامل ورودی‌های غیرمطابقت‌دار است، تحقق می‌یابد (ورودی‌های مطابقت‌دار حذف شده‌اند).

```js
async function removeMatches(fileEntry, entriesArr) {
  const newArr = [];
  for (const entry of entriesArr) {
    if (!(await fileEntry.isSameEntry(entry))) {
      newArr.push(entry);
    }
  }
  return newArr;
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)