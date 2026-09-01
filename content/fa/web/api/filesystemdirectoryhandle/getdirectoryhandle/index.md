---
title: "FileSystemDirectoryHandle: getDirectoryHandle() method"
short-title: getDirectoryHandle()
slug: Web/API/FileSystemDirectoryHandle/getDirectoryHandle
page-type: web-api-instance-method
browser-compat: api.FileSystemDirectoryHandle.getDirectoryHandle
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}

متد **`getDirectoryHandle()`** در رابط {{domxref("FileSystemDirectoryHandle")}} یک {{domxref('FileSystemDirectoryHandle')}} برای زیرشاخه‌ای با نام مشخص‌شده، در داخل همان دسته‌دایرکتوری که متد روی آن فراخوانی شده است، برمی‌گرداند.

## Syntax

```js-nolint
getDirectoryHandle(name)
getDirectoryHandle(name, options)
```

### Parameters

- `name`
  - : یک رشته که {{domxref('FileSystemHandle.name')}} زیرشاخه‌ای را که می‌خواهید بازیابی کنید، نشان می‌دهد.
- `options` {{optional_inline}}
  - : یک شیء اختیاری حاوی گزینه‌هایی برای زیرشاخه بازیابی‌شده. گزینه‌ها به شرح زیر هستند:
    - `create` {{optional_inline}}
      - : یک مقدار بولی که به‌طور پیش‌فرض `false` است. اگر روی `true` تنظیم شود و دایرکتوری پیدا نشود، دایرکتوری‌ای با نام مشخص‌شده ایجاد و برگردانده می‌شود.

### Return value

یک {{jsxref('Promise')}} که با یک {{domxref('FileSystemDirectoryHandle')}} resolve می‌شود.

### Exceptions

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر {{domxref('PermissionStatus.state')}} برای handle در حالت `readwrite` (زمانی که گزینه `create` برابر `true` باشد) یا در حالت `read` (زمانی که گزینه `create` برابر `false` باشد) برابر `'granted'` نباشد، پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر نام مشخص‌شده یک رشته معتبر نباشد یا شامل کاراکترهایی باشد که با سیستم فایل بومی تداخل داشته باشند، پرتاب می‌شود.
- `TypeMismatchError` {{domxref("DOMException")}}
  - : اگر ورودی برگشتی یک فایل باشد نه یک دایرکتوری، پرتاب می‌شود.
- `NotFoundError` {{domxref("DOMException")}}
  - : اگر ورودی فعلی پیدا نشود یا اگر دایرکتوری هدف وجود نداشته باشد و گزینه `create` برابر `false` باشد، پرتاب می‌شود.

## Examples

مثال زیر یک handle دایرکتوری با نام مشخص‌شده را برمی‌گرداند؛ اگر دایرکتوری وجود نداشته باشد، ایجاد می‌شود.

```js
const dirName = "directoryToGetName";

// assuming we have a directory handle: 'currentDirHandle'
const subDir = await currentDirHandle.getDirectoryHandle(dirName, {
  create: true,
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)