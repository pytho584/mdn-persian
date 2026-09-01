```
---
title: "FileSystemDirectoryHandle: getFileHandle() method"
---

---
title: "FileSystemDirectoryHandle: getFileHandle() method"
short-title: getFileHandle()
slug: Web/API/FileSystemDirectoryHandle/getFileHandle
page-type: web-api-instance-method
browser-compat: api.FileSystemDirectoryHandle.getFileHandle
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}

متد **`getFileHandle()`** از رابط {{domxref("FileSystemDirectoryHandle")}} یک {{domxref('FileSystemFileHandle')}} برای فایلی با نام مشخص‌شده، درون شاخه‌ای که متد روی آن فراخوانی می‌شود، برمی‌گرداند.

## سینتکس

```js-nolint
getFileHandle(name)
getFileHandle(name, options)
```

### پارامترها

- `name`
  - : یک رشته (string) که نمایانگر {{domxref('FileSystemHandle.name')}} فایلی است که می‌خواهید بازیابی کنید.
- `options` {{optional_inline}}
  - : یک شیء (object) با ویژگی‌های زیر:
    - `create` {{optional_inline}}
      - : یک {{jsxref('Boolean')}}. پیش‌فرض `false`. وقتی روی `true` تنظیم شود، اگر فایل پیدا نشود، فایلی با نام مشخص‌شده ایجاد و بازگردانده می‌شود.

### مقدار بازگشتی

یک {{jsxref('Promise')}} که با یک {{domxref('FileSystemFileHandle')}} resolve می‌شود.

### استثناها

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر {{domxref('PermissionStatus.state')}} برای هندل (handle) در حالت `readwrite` (وقتی گزینه `create` روی `true` است) یا در حالت `read` (وقتی گزینه `create` روی `false` است) برابر با `'granted'` نباشد، پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر نام مشخص‌شده یک رشته معتبر نباشد یا شامل کاراکترهایی باشد که با سیستم فایل بومی تداخل ایجاد کنند، پرتاب می‌شود.
- `TypeMismatchError` {{domxref("DOMException")}}
  - : اگر ورودی نام‌برده یک شاخه باشد نه یک فایل، پرتاب می‌شود.
- `NotFoundError` {{domxref("DOMException")}}
  - : اگر ورودی جاری پیدا نشود یا اگر فایل وجود نداشته باشد و گزینه `create` روی `false` تنظیم شده باشد، پرتاب می‌شود.

## مثال‌ها

مثال زیر یک هندل فایل را با نام مشخص‌شده برمی‌گرداند؛ اگر فایل وجود نداشته باشد، ایجاد می‌شود.

```js
const fileName = "fileToGetName";

// assuming we have a directory handle: 'currentDirHandle'
const fileHandle = await currentDirHandle.getFileHandle(fileName, {
  create: true,
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)
```