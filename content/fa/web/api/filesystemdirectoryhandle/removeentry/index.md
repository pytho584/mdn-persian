---
title: "FileSystemDirectoryHandle: removeEntry() method"
short-title: removeEntry()
slug: Web/API/FileSystemDirectoryHandle/removeEntry
page-type: web-api-instance-method
browser-compat: api.FileSystemDirectoryHandle.removeEntry
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}

متد **`removeEntry()`** در رابط {{domxref("FileSystemDirectoryHandle")}} تلاش می‌کند یک ورودی را حذف کند، در صورتی که هندل دایرکتوری شامل یک فایل یا پوشه با نام مشخص‌شده باشد.

## Syntax

```js-nolint
removeEntry(name)
removeEntry(name, options)
```

### Parameters

- `name`
  - : یک رشته که {{domxref('FileSystemHandle.name')}} ورودی مورد نظر برای حذف را نشان می‌دهد.
- `options` {{optional_inline}}
  - : یک شیء اختیاری حاوی گزینه‌ها که به صورت زیر است:
    - `recursive` {{optional_inline}}
      - : یک مقدار بولین که به طور پیش‌فرض `false` است. وقتی روی `true` تنظیم شود، ورودی‌ها به صورت بازگشتی حذف می‌شوند.

### Return value

یک {{jsxref('Promise')}} که با `undefined` حل می‌شود.

### Exceptions

- {{jsxref("TypeError")}}
  - : اگر نام یک رشته معتبر نباشد یا حاوی کاراکترهای مجاز در سیستم فایل نباشد، پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر {{domxref('PermissionStatus.state')}} برای هندل در حالت `'granted'` با مجوز `readwrite` نباشد، پرتاب می‌شود.
- `InvalidModificationError` {{domxref("DOMException")}}
  - : اگر `recursive` روی `false` تنظیم شده باشد و ورودی مورد نظر برای حذف دارای زیرشاخه باشد، پرتاب می‌شود.
- `NotFoundError` {{domxref("DOMException")}}
  - : اگر ورودی فعلی یافت نشود یا ورودی با نام مشخص‌شده یافت یا مطابقت داده نشود، پرتاب می‌شود.

## Examples

مثال زیر یک ورودی را در داخل هندل دایرکتوری حذف می‌کند.

```js
const entryName = "entryToRemove";

// assuming we have a directory handle: 'currentDirHandle'
currentDirHandle.removeEntry(entryName).then(() => {
  // code to run if removing was successful
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)