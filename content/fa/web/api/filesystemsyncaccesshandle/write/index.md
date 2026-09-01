---
title: "FileSystemSyncAccessHandle: write() method"
short-title: write()
slug: Web/API/FileSystemSyncAccessHandle/write
page-type: web-api-instance-method
browser-compat: api.FileSystemSyncAccessHandle.write
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers("dedicated")}}

متد **`write()`** از رابط {{domxref("FileSystemSyncAccessHandle")}} محتوای یک بافر مشخص را در فایل مرتبط با دستگیره می‌نویسد، به‌صورت اختیاری در یک آفست مشخص.

فایل‌های درون [سیستم فایل خصوصی مبدأ](/en-US/docs/Web/API/File_System_API/Origin_private_file_system) برای کاربران نهایی قابل مشاهده نیستند؛ بنابراین مانند متدهایی که روی فایل‌های موجود در سیستم فایل قابل مشاهده برای کاربر اجرا می‌شوند، تحت همان بررسی‌های امنیتی قرار نمی‌گیرند. در نتیجه، نوشتن‌هایی که با استفاده از `FileSystemSyncAccessHandle.write()` انجام می‌شوند، عملکرد بسیار بالاتری دارند. این موضوع آن‌ها را برای به‌روزرسانی‌های وسیع و در مقیاس بزرگ فایل، مانند اصلاح پایگاه داده [SQLite](https://sqlite.org/wasm)، مناسب می‌سازد.

## دستور زبان

```js-nolint
write(buffer, options)
```

### پارامترها

- `buffer`
  - : یک {{jsxref("ArrayBuffer")}} یا `ArrayBufferView` (مانند یک {{jsxref("DataView")}}) که بافر مورد نظر برای نوشتن در فایل را نشان می‌دهد.
- `options` {{optional_inline}}
  - : یک شیء گزینه‌ها شامل ویژگی‌های زیر:
    - `at`
      - : عددی که آفست را بر حسب بایت از ابتدای فایل مشخص می‌کند و بافر باید در آن نقطه نوشته شود.

> [!NOTE]
> شما نمی‌توانید به طور مستقیم محتویات یک `ArrayBuffer` را دستکاری کنید. در عوض، یک شیء آرایه تایپ‌شده مانند {{jsxref("Int8Array")}} یا {{jsxref("DataView")}} می‌سازید که بافر را در قالبی خاص نشان می‌دهد و از آن برای خواندن و نوشتن محتویات بافر استفاده می‌کنید.

### مقدار بازگشتی

عددی که تعداد بایت‌های نوشته‌شده در فایل را نشان می‌دهد.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر دستگیره دسترسی مرتبط از قبل بسته شده باشد، یا اصلاح داده‌های دودویی فایل به طور کامل ناموفق باشد، پرتاب می‌شود.
- {{domxref("QuotaExceededError")}}
  - : اگر ظرفیت داده افزایش‌یافته از [سهمیه ذخیره‌سازی](/en-US/docs/Web/API/Storage_API/Storage_quotas_and_eviction_criteria) مرورگر فراتر رود، پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر سیستم فایل زیرین از نوشتن فایل از آفست مشخص‌شده پشتیبانی نکند، پرتاب می‌شود.

## مثال‌ها

تابع کنترل‌کننده رویداد ناهمگام زیر درون یک Web Worker قرار دارد. پس از دریافت پیام از نخ اصلی، کارهای زیر را انجام می‌دهد:

- یک دستگیره دسترسی همگام به فایل ایجاد می‌کند.
- اندازه فایل را به دست می‌آورد و یک {{jsxref("ArrayBuffer")}} برای نگهداری آن می‌سازد.
- محتویات فایل را در بافر می‌خواند.
- پیام را کدگذاری می‌کند و آن را به انتهای فایل می‌نویسد.
- تغییرات را روی دیسک ماندگار می‌کند و دستگیره دسترسی را می‌بندد.

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

> [!NOTE]
> در نسخه‌های پیشین مشخصات، متدهای {{domxref("FileSystemSyncAccessHandle.close()", "close()")}}، {{domxref("FileSystemSyncAccessHandle.flush()", "flush()")}}، {{domxref("FileSystemSyncAccessHandle.getSize()", "getSize()")}} و {{domxref("FileSystemSyncAccessHandle.truncate()", "truncate()")}} به اشتباه به عنوان متدهای ناهمگام تعریف شده بودند و نسخه‌های قدیمی‌تر برخی مرورگرها آن‌ها را به این صورت پیاده‌سازی می‌کنند. با این حال، همه مرورگرهای فعلی که از این متدها پشتیبانی می‌کنند، آن‌ها را به عنوان متدهای همگام پیاده‌سازی می‌کنند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: ساده‌سازی دسترسی به فایل‌های محلی](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)