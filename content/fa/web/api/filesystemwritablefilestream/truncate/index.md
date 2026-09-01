---
title: "FileSystemWritableFileStream: truncate() method"
short-title: truncate()
slug: Web/API/FileSystemWritableFileStream/truncate
page-type: web-api-instance-method
browser-compat: api.FileSystemWritableFileStream.truncate
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}

متد **`truncate()`** از رابط {{domxref("FileSystemWritableFileStream")}}، اندازهٔ فایل مرتبط با جریان را به اندازهٔ مشخص‌شده (بر حسب بایت) تغییر می‌دهد.

اگر اندازهٔ مشخص‌شده بزرگ‌تر از اندازهٔ فعلی فایل باشد، فایل با بایت‌های `0x00` پر می‌شود.

مکان‌نمای (cursor) فایل نیز هنگام فراخوانی `truncate()` به‌روزرسانی می‌شود.
اگر آفست کوچک‌تر از اندازه باشد، بدون تغییر می‌ماند.
اگر آفست بزرگ‌تر از اندازه باشد، آفست روی همان اندازه تنظیم می‌شود.
این کار تضمین می‌کند که نوشتن‌های بعدی با خطا مواجه نشوند.

تا زمانی که جریان بسته نشده است، هیچ تغییری در فایل واقعی روی دیسک اعمال نمی‌شود.
تغییرات معمولاً به‌جای آن در یک فایل موقت نوشته می‌شوند.

## نحو

```js-nolint
truncate(size)
```

### پارامترها

- `size`
  - : عددی که مشخص می‌کند اندازهٔ جریان به چند بایت تغییر یابد.

### مقدار بازگشتی

یک {{jsxref('Promise')}} که مقدار `undefined` را برمی‌گرداند.

### استثناها

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر {{domxref('PermissionStatus.state')}} برابر با `granted` نباشد، پرتاب می‌شود.
- {{domxref("QuotaExceededError")}}
  - : اگر اندازهٔ جدید فایل بزرگ‌تر از اندازهٔ اصلی فایل باشد و از [سهمیهٔ ذخیره‌سازی](/en-US/docs/Web/API/Storage_API/Storage_quotas_and_eviction_criteria) مرورگر فراتر رود، پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر `size` یک عدد نباشد یا تعریف نشده باشد، پرتاب می‌شود.

## مثال‌ها

تابع ناهمگام زیر، انتخابگر «ذخیرهٔ فایل» (Save File) را باز می‌کند که پس از انتخاب یک فایل، یک {{domxref('FileSystemFileHandle')}} برمی‌گرداند. سپس با استفاده از متد {{domxref('FileSystemFileHandle.createWritable()')}} یک جریان قابل‌نوشتن ایجاد می‌شود.

در ادامه، در این جریان می‌نویسیم:

1. یک رشتهٔ متنی در جریان نوشته می‌شود.
2. از متد `truncate()` برای تغییر اندازهٔ فایل به ۸ بایت استفاده می‌شود.
3. یک رشتهٔ متنی دوم در ابتدای جریان نوشته می‌شود و نوشتهٔ اول را بازنویسی می‌کند.

سپس جریان بسته می‌شود.

```js
async function saveFile() {
  try {
    // create a new handle
    const newHandle = await window.showSaveFilePicker();

    // create a FileSystemWritableFileStream to write to
    const writableStream = await newHandle.createWritable();

    // write our file
    await writableStream.write("This is my first file content");
    await writableStream.truncate(8);
    await writableStream.write("my second file content");

    // close the file and write the contents to disk.
    await writableStream.close();
  } catch (err) {
    console.error(err.name, err.message);
  }
}
```

اگر تابع بالا را اجرا کنید و سپس فایل حاصل را که روی دیسک ایجاد شده است باز کنید، باید متن «This is my second file content» را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)