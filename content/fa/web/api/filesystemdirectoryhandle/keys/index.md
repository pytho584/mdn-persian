---
title: "FileSystemDirectoryHandle: keys() method"
short-title: keys()
slug: Web/API/FileSystemDirectoryHandle/keys
page-type: web-api-instance-method
browser-compat: api.FileSystemDirectoryHandle.keys
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}

متد **`keys()`** در رابط {{domxref("FileSystemDirectoryHandle")}} یک تکرارکننده‌ی ناهمگام جدید برمی‌گرداند که برای پیمایش کلیدهای ورودی‌های درون `FileSystemDirectoryHandle` که این متد روی آن فراخوانی می‌شود، استفاده می‌شود.

## نحو (Syntax)

```js-nolint
keys()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک تکرارکننده‌ی ناهمگام جدید که شامل کلیدهای هر ورودی درون `FileSystemDirectoryHandle` است.

### استثناها (Exceptions)

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر وضعیت {{domxref('PermissionStatus.state')}} برای هندل در حالت `read` برابر با `'granted'` نباشد، پرتاب می‌شود.
- `NotFoundError` {{domxref("DOMException")}}
  - : اگر ورودی فعلی یافت نشود، پرتاب می‌شود.

## مثال‌ها

استفاده از حلقه‌ی `for await...of` می‌تواند فرآیند پیمایش را ساده‌تر کند.

```js
const dirHandle = await window.showDirectoryPicker();

for await (const key of dirHandle.keys()) {
  console.log(key);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)