---
title: "FileSystemSyncAccessHandle: getSize() method"
short-title: getSize()
slug: Web/API/FileSystemSyncAccessHandle/getSize
page-type: web-api-instance-method
browser-compat: api.FileSystemSyncAccessHandle.getSize
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers("dedicated")}}

متد **`getSize()`** از رابط {{domxref("FileSystemSyncAccessHandle")} اندازه فایل مرتبط با هندل را به بایت برمی‌رداند.

> [!NOTE]
> در نسخه‌ای پیشین مشخصات، متدها{{domxref("FileSystemSyncAccessHandle.close()", "close()")}، {{domxref("FileSystemSyncAccessHandle.flush()", "flush()")}، `getSize()` و {{domxref("FileSystemSyncAccessHandle.truncate()", "truncate()")} به اشتباه به عنوان متدهای ناهمگام (asynchronous) تعریف شده بودند و نسخه‌های قدیم‌تر برخی مرورگرها آن‌ها را به این صورت پیاده‌سازی کرده‌اند. اما همه مرورگرهای فعلی که از این متدها پشتیبانی می‌کنند، آنها را به عنوان متدهای همگام (synchronous) پیاده‌سازی می‌کنند.

## نحوه استفاده

```js-nolint
getSize()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک عدد که اندازه فایل را به بایت نشان می‌دهد.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر هندل دسترسی مرتبط از قبل بسته شده باشد، پرتاب می‌شود.

## مثال‌ها

تابع رویدادگردان ناهمگام زیر درون یک Web Worker قرار دارد. پس از دریافت پیام از رشته اصلی:

- یک هندل دسترسی همگام فایل ایجاد می‌کند.
- اندازه فایل را گرفته و یک {{jsxref("ArrayBuffer")}} برای نگهداری آن ایجاد می‌کند.
- محتویات فایل را در بافر می‌خواند.
- پیام را کدگذاری کرده و به انتهای فایل می‌نویسد.
- تغییرات را روی دیسک ماندگار می‌د و هل دسترسی را مبند.

```js
onmessage = async (e) => {
  // بازیابی پیام ارسال شده به کارگر از اسکریپت اصلی
  const message = e.data;

  // دریافت هندل فایل پیش‌ویس
  const root = await navigator.storage.getDirector();
  const draftHandle = await root.getFileHandle("draft.txt", { create: true };
  // دریافت هندل دسترسی همگام
  const accessHandle = await draftHandle.createSyncAccessHandle();

  // گرفتن اندازه فایل.
  const fileSize = accessHandle.getSize();
  // خواندن محتوای فایل در ی بافر.
  const buffer = new DataView(new ArrayBuffer(fileSize));
  const readBuffer = accessHandle.read(buffer, { at: 0 });

  // نوشتن پیام به انتهای فایل.
  const encoder = new TextEncoder();
  const encodedMessage = encoder.encode(message);
  const writeBuffer = accessHandle.write(encodedMessage, { at: readBuffer });

  // ماندگار کردن تغییرات روی دیسک.
  accessHandle.flush();

  // همیشه FileSystemSyncAccessHandle را اگر کار تمام شد ببندید.
  accessHandle.close();
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chome.com/docs/capabilities/web-apis/file-system-access)