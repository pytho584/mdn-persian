---
title: "FileSystemSyncAccessHandle: read() method"
short-title: read()
slug: Web/API/FileSystemSyncAccessHandle/read
page-type: web-api-instance-method
browser-compat: api.FileSystemSyncAccessHandle.read
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers("dedicated")}}

متد **`read()``** از رابط {{domxref("FileSystemSyncAccessHandle")}} محتوای فایل مرتبط با دسته را در یک بافر مشخص شده، به‌صورت اختیاری در یک آفست معین، می‌خواند.

## نحو (Syntax)

```js-nolint
read(buffer, options)
```

### پارامترها

- `buffer`
  - : یک {{jsxref("ArrayBuffer")}} یا `ArrayBufferView` (مانند {{jsxref("DataView")}}) که نشان‌دهنده بافری است که محتوای فایل باید در آن خوانده شود. توجه داشته باشید که نمی‌توانید مستقیماً محتویات یک `ArrayBuffer` را دستکاری کنید. در عوض، یکی از اشیاء آرایه تایپ‌شده مانند {{jsxref("Int8Array")}} یا یک شیء {{jsxref("DataView")}} ایجاد می‌کنید که بافر را در قالبی خاص نمایش می‌دهد و از آن برای خواندن و نوشتن محتویات بافر استفاده می‌کنید.
- `options` {{optional_inline}}
  - : یک شیء گزینه‌ها که شامل ویژگی‌های زیر است:
    - `at`
      - : یک عدد که نشان‌دهنده آفست (بر حسب بایت) است که فایل باید از آن位置 خوانده شود.

### مقدار بازگشتی

یک عدد که تعداد بایت‌های خوانده‌شده از فایل را نشان می‌دهد.

### استثناها (Exceptions)

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر دسته دسترسی مرتبط قبلاً بسته شده باشد، پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر سیستم فایل زیرین از خواندن فایل از آفست مشخص‌شده پشتیبانی نکند، پرتاب می‌شود.

## مثال‌ها

تابع کنترل‌کننده رویداد ناهمگام زیر درون یک Web Worker قرار دارد. پس از دریافت پیام از رشته اصلی، موارد زیر را انجام می‌دهد:

- یک دسته دسترسی همگام به فایل ایجاد می‌کند.
- اندازه فایل را دریافت می‌کند و یک {{jsxref("ArrayBuffer")}} برای نگهداری آن ایجاد می‌کند.
- محتویات فایل را درون بافر می‌خواند.
- پیام را رمزگذاری می‌کند و آن را به انتهای فایل می‌نویسد.
- تغییرات را روی دیسک ذخیره می‌کند و دسته دسترسی را می‌بندد.

```js
onmessage = async (e) => {
  // دریافت پیام ارسال‌شده به worker از اسکریپت اصلی
  const message = e.data;

  // دریافت دسته فایل پیش‌نویس
  const root = await navigator.storage.getDirectory();
  const draftHandle = await root.getFileHandle("draft.txt", { create: true });
  // دریافت دسته دسترسی همگام
  const accessHandle = await draftHandle.createSyncAccessHandle();

  // دریافت اندازه فایل
  const fileSize = accessHandle.getSize();
  // خواندن محتوای فایل در یک بافر
  const buffer = new DataView(new ArrayBuffer(fileSize));
  const readBuffer = accessHandle.read(buffer, { at: 0 });

  // نوشتن پیام در انتهای فایل
  const encoder = new TextEncoder();
  const encodedMessage = encoder.encode(message);
  const writeBuffer = accessHandle.write(encodedMessage, { at: readBuffer });

  // ذخیره تغییرات روی دیسک
  accessHandle.flush();

  // همیشه FileSystemSyncAccessHandle را در صورت اتمام کار ببندید
  accessHandle.close();
};
```

> [!NOTE]
> در نسخه‌های قدیمی‌تر مشخصات، متدهای {{domxref("FileSystemSyncAccessHandle.close()", "close()")}}، {{domxref("FileSystemSyncAccessHandle.flush()", "flush()")}}، {{domxref("FileSystemSyncAccessHandle.getSize()", "getSize()")}} و {{domxref("FileSystemSyncAccessHandle.truncate()", "truncate()")}} به اشتباه به‌عنوان متدهای ناهمگام مشخص شده بودند و نسخه‌های قدیمی‌تر برخی مرورگرها آن‌ها را به این صورت پیاده‌سازی می‌کنند. با این حال، تمام مرورگرهای فعلی که از این متدها پشتیبانی می‌کنند، آن‌ها را به‌عنوان متدهای همگام پیاده‌سازی می‌کنند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)