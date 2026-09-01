---
title: "FileSystemSyncAccessHandle: flush() method"
short-title: flush()
slug: Web/API/FileSystemSyncAccessHandle/flush
page-type: web-api-instance-method
browser-compat: api.FileSystemSyncAccessHandle.flush
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers("dedicated")}}

متد **`flush()`** از رابط {{domxref("FileSystemSyncAccessHandle")}} هرگونه تغییری که از طریق متد {{domxref('FileSystemSyncAccessHandle.write', 'write()')}} روی فایل مرتبط با دسته‌ایجاد شده است را به دیسک ذخیره می‌کند.

به خاطر داشته باشید که فقط در صورتی نیاز به فراخوانی این متد دارید که بخواهید تغییرات در یک زمان مشخص روی دیسک اعمال شوند؛ در غیر این صورت می‌توانید اجازه دهید سیستم‌عامل زیرین در زمان مناسب خود این کار را انجام دهد، که در بیشتر موارد کافی است.

> [!NOTE]
> در نسخه‌های قدیمی‌تر مشخصات، {{domxref("FileSystemSyncAccessHandle.close()", "close()")}}، `flush()`، {{domxref("FileSystemSyncAccessHandle.getSize()", "getSize()")}} و {{domxref("FileSystemSyncAccessHandle.truncate()", "truncate()")}} به اشتباه به عنوان متدهای ناهمگام (async) تعریف شده بودند و نسخه‌های قدیمی‌تر برخی مرورگرها آن‌ها را به همین صورت پیاده‌سازی کرده‌اند. با این حال، تمام مرورگرهای فعلی که از این متدها پشتیبانی می‌کنند، آن‌ها را به صورت همگام (sync) پیاده‌سازی کرده‌اند.

## Syntax

```js-nolint
flush()
```

### Parameters

هیچکدام.

### Return value

هیچکدام ({{jsxref('undefined')}}).

### Exceptions

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر دسته‌دسترسی مرتبط از قبل بسته شده باشد، این خطا صادر می‌شود.

## Examples

تابع رویدادگردان ناهمگام زیر درون یک Web Worker قرار دارد. پس از دریافت پیام از نخ اصلی، کارهای زیر را انجام می‌دهد:

- یک دسته‌دسترسی همگام به فایل ایجاد می‌کند.
- اندازه فایل را می‌گیرد و یک {{jsxref("ArrayBuffer")}} متناسب با آن ایجاد می‌کند.
- محتوای فایل را در بافر می‌خواند.
- پیام را کدگذاری کرده و به انتهای فایل می‌نویسد.
- تغییرات را روی دیسک ذخیره کرده و دسته‌دسترسی را می‌بندد.

```js
onmessage = async (e) => {
  // Retrieve message sent to work from main script
  const message = e.data;

  // Get handle to draft file
  const root = await navigator.storage.getDirectory();
  const draftHandle = await root.getFileHandle("draft.txt", { create: true });
  // Get sync access handle
  const accessHandle = await draftHandle.createSyncAccessHandle();

  // Get size of the file.
  const fileSize = accessHandle.getSize();
  // Read file content to a buffer.
  const buffer = new DataView(new ArrayBuffer(fileSize));
  const readBuffer = accessHandle.read(buffer, { at: 0 });

  // Write the message to the end of the file.
  const encoder = new TextEncoder();
  const encodedMessage = encoder.encode(message);
  const writeBuffer = accessHandle.write(encodedMessage, { at: readBuffer });

  // Persist changes to disk.
  accessHandle.flush();

  // Always close FileSystemSyncAccessHandle if done.
  accessHandle.close();
};
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)