```markdown
---
title: "FileSystemSyncAccessHandle: truncate() method"
short-title: truncate()
slug: Web/API/FileSystemSyncAccessHandle/truncate
page-type: web-api-instance-method
browser-compat: api.FileSystemSyncAccessHandle.truncate
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers("dedicated")}}

متد **`truncate()`** از رابط {{domxref("FileSystemSyncAccessHandle")}} اندازه فایل مرتبط با دسته را به تعداد مشخصی بایت تغییر می‌دهد.

> [!NOTE]
> در نسخه‌های اولیه مشخصات، متدهای {{domxref("FileSystemSyncAccessHandle.close()", "close()")}}، {{domxref("FileSystemSyncAccessHandle.flush()", "flush()")}}، {{domxref("FileSystemSyncAccessHandle.getSize()", "getSize()")}} و `truncate()` به اشتباه به‌عنوان متدهای ناهمزمان (async) مشخص شده بودند و نسخه‌های قدیمی‌تر برخی مرورگرها آن‌ها را به همین صورت پیاده‌سازی کرده‌اند. با این حال، تمام مرورگرهای فعلی که از این متدها پشتیبانی می‌کنند، آن‌ها را به‌عنوان متدهای همزمان (sync) پیاده‌سازی می‌کنند.

## نحو

```js-nolint
truncate(newSize)
```

### پارامترها

- `newSize`
  - : تعداد بایت‌هایی که فایل باید به آن اندازه تغییر کند.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref('undefined')}}).

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : در صورتی که دسته دسترسی مرتبط از قبل بسته شده باشد، یا اگر تغییر داده‌های باینری فایل به‌دلایل دیگر ناموفق باشد، پرتاب می‌شود.
- {{domxref("QuotaExceededError")}}
  - : اگر `newSize` بزرگتر از اندازه اصلی فایل باشد و از [سهمیه ذخیره‌سازی](/en-US/docs/Web/API/Storage_API/Storage_quotas_and_eviction_criteria) مرورگر فراتر رود، پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر سیستم فایل زیرین از تنظیم اندازه فایل به اندازه جدید پشتیبانی نکند، پرتاب می‌شود.

## مثال‌ها

```js
async function truncateFile() {
  // Get handle to draft file
  const root = await navigator.storage.getDirectory();
  const draftHandle = await root.getFileHandle("draft.txt", { create: true });
  // Get sync access handle
  const accessHandle = await draftHandle.createSyncAccessHandle();

  // Truncate the file to 0 bytes
  accessHandle.truncate(0);

  // Persist changes to disk.
  accessHandle.flush();

  // Always close FileSystemSyncAccessHandle if done.
  accessHandle.close();
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)
```