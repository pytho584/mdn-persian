---
title: "FileSystemWritableFileStream: seek() method"
short-title: seek()
slug: Web/API/FileSystemWritableFileStream/seek
page-type: web-api-instance-method
browser-compat: api.FileSystemWritableFileStream.seek
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}

متد **`seek()`** در رابط {{domxref("FileSystemWritableFileStream")}}، موقعیت فعلی نشانگر فایل را به بایتی که هنگام فراخوانی متد مشخص شده است، بهروزرسانی میکند.

## نحو (Syntax)

```js-nolint
seek(position)
```

### پارامترها

- `position`
  - : عددی که موقعیت بایت را از ابتدای فایل مشخص میکند.

### مقدار بازگشتی

یک {{jsxref('Promise')}} که مقدار `undefined` برمیگرداند.

### استثناها (Exceptions)

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر {{domxref('PermissionStatus.state')}} برابر با `granted` نباشد، پرتاب میشود.
- {{jsxref("TypeError")}}
  - : اگر `position` یک عدد نباشد یا تعریف نشده باشد، پرتاب میشود.

## مثالها

تابع ناهمگام زیر، انتخابگر «ذخیره فایل» را باز میکند که پس از انتخاب یک فایل، یک {{domxref('FileSystemFileHandle')}} برمیگرداند. با استفاده از متد {{domxref('FileSystemFileHandle.createWritable()')}}، یک جریان قابل نوشتن (writable stream) از این هندل ایجاد میشود.

سپس، در جریان مینویسیم:

1. یک رشته متنی در جریان نوشته میشود.
2. متد `seek()` برای قرار دادن نشانگر در ابتدای جریان استفاده میشود.
3. یک رشته متنی دوم در ابتدای جریان نوشته میشود که نوشته اول را بازنویسی میکند.

سپس جریان بسته میشود.

```js
async function saveFile() {
  try {
    // create a new handle
    const newHandle = await window.showSaveFilePicker();

    // create a FileSystemWritableFileStream to write to
    const writableStream = await newHandle.createWritable();

    // write our file
    await writableStream.write("My first file content");
    await writableStream.seek(0);
    await writableStream.write("My second file content");

    // close the file and write the contents to disk.
    await writableStream.close();
  } catch (err) {
    console.error(err.name, err.message);
  }
}
```

اگر تابع بالا را اجرا کنید و سپس فایل ایجادشده روی دیسک را باز کنید، باید متن «My second file content» را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)