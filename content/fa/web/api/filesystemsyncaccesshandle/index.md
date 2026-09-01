---
title: FileSystemSyncAccessHandle
slug: Web/API/FileSystemSyncAccessHandle
page-type: web-api-interface
browser-compat: api.FileSystemSyncAccessHandle
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers("dedicated")}}

رابط **`FileSystemSyncAccessHandle`** از {{domxref("File System API", "File System API", "", "nocode")}} یک هندل همزمان برای یک ورودی سیستم فایل را نشان می‌دهد.

این کلاس فقط درون [Web Worker](/en-US/docs/Web/API/Web_Workers_API)های اختصاصی قابل دسترسی است (تا متدهای آن اجرای ریسه اصلی را مسدود نکنند) برای فایل‌هایی در [سیستم فایل خصوصی مبدأ](/en-US/docs/Web/API/File_System_API/Origin_private_file_system) که برای کاربران نهایی قابل مشاهده نیست.

در نتیجه، متدهای آن مشمول همان بررسی‌های امنیتی که متدهای اجرا شده روی فایل‌های درون سیستم فایل قابل مشاهده برای کاربر هستند، نمی‌شوند و بنابراین عملکرد بسیار بالاتری دارند. این آنها را برای به‌روزرسانی‌های فایل بزرگ و قابل توجه مانند تغییرات پایگاه داده [SQLite](https://sqlite.org/wasm) مناسب می‌کند.

به این رابط از طریق متد {{domxref('FileSystemFileHandle.createSyncAccessHandle()')}} دسترسی پیدا می‌شود.

> [!NOTE]
> در نسخه‌های قبلی مشخصات، متدهای {{domxref("FileSystemSyncAccessHandle.close()", "close()")}}، {{domxref("FileSystemSyncAccessHandle.flush()", "flush()")}}، {{domxref("FileSystemSyncAccessHandle.getSize()", "getSize()")}} و {{domxref("FileSystemSyncAccessHandle.truncate()", "truncate()")}} به اشتباه به عنوان متدهای ناهمزمان مشخص شده بودند و نسخه‌های قدیمی برخی مرورگرها آنها را به این صورت پیاده‌سازی می‌کنند. با این حال، تمام مرورگرهای فعلی که از این متدها پشتیبانی می‌کنند، آنها را به عنوان متدهای همزمان پیاده‌سازی می‌کنند.

## ویژگی‌های نمونه

هیچکدام.

## روش‌های نمونه

- {{domxref('FileSystemSyncAccessHandle.close', 'close()')}}
  - یک هندل فایل همزمان باز را می‌بندد، هرگونه عملیات بیشتر روی آن را غیرفعال می‌کند و قفل انحصاری که قبلاً روی فایل مرتبط با هندل فایل قرار داده شده بود را آزاد می‌کند.
- {{domxref('FileSystemSyncAccessHandle.flush', 'flush()')}}
  - هر تغییری که از طریق متد {{domxref('FileSystemSyncAccessHandle.write', 'write()')}} روی فایل مرتبط با هندل ایجاد شده است را روی دیسک ذخیره می‌کند.
- {{domxref('FileSystemSyncAccessHandle.getSize', 'getSize()')}}
  - اندازه فایل مرتبط با هندل را بر حسب بایت برمی‌گرداند.
- {{domxref('FileSystemSyncAccessHandle.read', 'read()')}}
  - محتوای فایل مرتبط با هندل را در یک بافر مشخص شده می‌خواند، به صورت اختیاری در یک آفست مشخص.
- {{domxref('FileSystemSyncAccessHandle.truncate', 'truncate()')}}
  - اندازه فایل مرتبط با هندل را به تعداد بایت مشخص شده تغییر می‌دهد.
- {{domxref('FileSystemSyncAccessHandle.write', 'write()')}}
  - محتوای یک بافر مشخص شده را در فایل مرتبط با هندل می‌نویسد، به صورت اختیاری در یک آفست مشخص.

## مثال‌ها

تابع مدیریت رویداد ناهمزمان زیر درون یک Web Worker قرار دارد. هنگام دریافت پیام از ریسه اصلی:

- یک هندل دسترسی همزمان فایل ایجاد می‌کند.
- اندازه فایل را می‌گیرد و یک {{jsxref("ArrayBuffer")}} برای نگهداری آن ایجاد می‌کند.
- محتوای فایل را در بافر می‌خواند.
- پیام را رمزگذاری کرده و آن را به انتهای فایل می‌نویسد.
- تغییرات را روی دیسک ذخیره کرده و هندل دسترسی را می‌بندد.

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

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)