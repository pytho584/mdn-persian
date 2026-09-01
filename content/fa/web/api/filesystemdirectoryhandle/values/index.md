---
title: "FileSystemDirectoryHandle: values() method"
short-title: values()
slug: Web/API/FileSystemDirectoryHandle/values
page-type: web-api-instance-method
browser-compat: api.FileSystemDirectoryHandle.values
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}

متد **`values()`** از رابط {{domxref("FileSystemDirectoryHandle")}} یک پیمایش‌گر ناهمگام جدید برای پیمایش مقادیرِ ورودی‌های درون `FileSystemDirectoryHandle`ای که این متد روی آن فراخوانی شده است، برمی‌گرداند.

## نحو (Syntax)

```js-nolint
values()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک پیمایش‌گر ناهمگام جدید که شامل دسته‌های (handle) هر یک از ورودی‌های درون `FileSystemDirectoryHandle` است.

### استثناها (Exceptions)

- `NotAllowedError` {{domxref("DOMException")}}
  - : در صورتی که {{domxref('PermissionStatus.state')}} برای دسته (handle) در حالت `read` برابر `'granted'` نباشد، پرتاب می‌شود.
- `NotFoundError` {{domxref("DOMException")}}
  - : در صورتی که ورودی جاری یافت نشود، پرتاب می‌شود.

## مثال‌ها

استفاده از حلقهٔ `for await...of` می‌تواند فرایند پیمایش را ساده‌تر کند.

```js
const dirHandle = await window.showDirectoryPicker();

for await (const value of dirHandle.values()) {
  console.log(value);
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)