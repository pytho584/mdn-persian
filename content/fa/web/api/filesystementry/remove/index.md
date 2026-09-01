---
title: "FileSystemEntry: remove() method"
short-title: remove()
slug: Web/API/FileSystemEntry/remove
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.FileSystemEntry.remove
---

{{APIRef("File and Directory Entries API")}}{{Deprecated_Header}}{{Non-standard_Header}}

متد **`remove()`** از رابط {{domxref("FileSystemEntry")}} فایل یا دایرکتوری را از سیستم فایل حذف می‌کند. دایرکتوری‌ها قبل از حذف باید خالی باشند.

برای حذف بازگشتی یک دایرکتوری به همراه تمام محتویات و زیرشاخه‌های آن، به جای آن از {{domxref("FileSystemDirectoryEntry.removeRecursively()")}} استفاده کنید.

## Syntax

```js-nolint
remove(successCallback)
remove(successCallback, errorCallback)
```

### Parameters

- `successCallback`
  - : یک تابع که پس از موفقیت‌آمیز بودن حذف فایل فراخوانی می‌شود.
- `errorCallback` {{optional_inline}}
  - : یک callback اختیاری که در صورت شکست تلاش برای حذف فایل فراخوانی می‌شود.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

### Exceptions

- `DOMException.INVALID_MODIFICATION_ERR`
  - : ورودی مشخص شده دایرکتوری ریشه سیستم فایل بوده یا یک دایرکتوری غیر خالی است.
- `DOMException.INVALID_STATE_ERR`
  - : وضعیت ذخیره شده سیستم فایل با وضعیت آن روی دیسک ناسازگار است، بنابراین به دلایل ایمنی فایل قابل حذف نیست.
- `DOMException.NO_MODIFICATION_ALLOWED_ERR`
  - : وضعیت سیستم فایل اجازه حذف فایل یا دایرکتوری را نمی‌دهد.
- `DOMException.NOT_FOUND_ERR`
  - : فایل یا دایرکتوری وجود ندارد.
- `DOMException.SECURITY_ERR`
  - : ورودی به دلیل محدودیت‌های دسترسی یا مجوزها، یا به دلیل تعداد زیاد فراخوانی روی منابع فایل، قابل حذف نیست.

## Examples

این مثال یک فایل کاری موقت را حذف می‌کند.

```js
workingDirectory.getFile(
  "tmp/work-file.json",
  {},
  (fileEntry) => {
    fileEntry.remove(() => {
      /* the file was removed successfully */
    });
  },
  handleError,
);
```

## Browser compatibility

{{Compat}}

## See also

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("FileSystemDirectoryEntry.removeRecursively()")}}