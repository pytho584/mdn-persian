---
title: "FileSystemDirectoryEntry: createReader() method"
---

---
title: "FileSystemDirectoryEntry: createReader() method"
short-title: createReader()
slug: Web/API/FileSystemDirectoryEntry/createReader
page-type: web-api-instance-method
browser-compat: api.FileSystemDirectoryEntry.createReader
---

{{APIRef("File and Directory Entries API")}}

متد **`createReader()`** در رابط {{domxref("FileSystemDirectoryEntry")}} یک شیء {{domxref("FileSystemDirectoryReader")}} بازمی‌گرداند که می‌توان از آن برای خواندن ورودی‌های دایرکتوری استفاده کرد.

## Syntax

```js-nolint
createReader()
```

### Parameters

پارامتری ندارد.

### Return value

یک شیء {{domxref("FileSystemDirectoryReader")}} که می‌توان از آن برای خواندن ورودی‌های دایرکتوری استفاده کرد.

## Examples

این مثال یک تابع ناهمگام به نام `readDirectory()` ایجاد می‌کند که همهٔ ورودی‌های موجود در {{domxref("FileSystemDirectoryEntry")}} داده‌شده را دریافت کرده و آن‌ها را در یک آرایه بازمی‌گرداند.

```js
async function readDirectory(directory) {
  const dirReader = directory.createReader();
  const entries = [];

  while (true) {
    const results = await new Promise((resolve, reject) => {
      dirReader.readEntries(resolve, reject);
    });

    if (!results.length) {
      break;
    }

    for (const entry of results) {
      entries.push(entry);
    }
  }

  return entries;
}
```

این کار با فراخوانی تکراری {{domxref("FileSystemDirectoryReader.readEntries", "readEntries()")}} انجام می‌شود تا همهٔ ورودی‌های دایرکتوری دریافت شوند و هر دسته از نتایج به آرایه اضافه شود. وقتی یک آرایهٔ خالی بازگردانده شود، یعنی همهٔ ورودی‌ها خوانده شده‌اند و حلقه پایان می‌یابد.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("FileSystemDirectoryReader")}}
- {{domxref("FileSystemDirectoryEntry")}}
- {{domxref("FileSystemFileEntry")}}
- {{domxref("FileSystemEntry")}}