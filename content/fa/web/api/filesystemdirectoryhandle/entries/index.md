---
title: "FileSystemDirectoryHandle: entries() method"
short-title: entries()
slug: Web/API/FileSystemDirectoryHandle/entries
page-type: web-api-instance-method
browser-compat: api.FileSystemDirectoryHandle.entries
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}

متد **`entries()`** در رابط {{domxref("FileSystemDirectoryHandle")}} یک تکرارکننده‌ی ناهمگام جدید برای پیمایش جفت‌های کلید-مقدار ورودی‌های درون `FileSystemDirectoryHandle` که این متد روی آن فراخوانی شده است، برمی‌گرداند. این جفت‌های کلید-مقدار به شکل آرایه‌ای مانند `[key, value]` هستند.

## نحو (Syntax)

```js-nolint
entries()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک تکرارکننده‌ی ناهمگام جدید که شامل جفت‌های کلید-مقدار هر ورودی درون `FileSystemDirectoryHandle` است.

### استثناها

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر {{domxref('PermissionStatus.state')}} برای هندل در حالت `'granted'` نباشد، پرتاب می‌شود.
- `NotFoundError` {{domxref("DOMException")}}
  - : اگر ورودی فعلی یافت نشود، پرتاب می‌شود.

## مثال‌ها

استفاده از حلقه‌ی `for await...of` می‌تواند فرآیند پیمایش را ساده‌تر کند.

```js
const dirHandle = await window.showDirectoryPicker();

for await (const [key, value] of dirHandle.entries()) {
  console.log({ key, value });
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)