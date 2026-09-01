---
title: "FileSystemWritableFileStream"
---

---
title: FileSystemWritableFileStream
slug: Web/API/FileSystemWritableFileStream
page-type: web-api-interface
browser-compat: api.FileSystemWritableFileStream
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}

رابط **`FileSystemWritableFileStream`** در {{domxref("File System API", "File System API", "", "nocode")}} یک شیء {{domxref('WritableStream')}} با متدهای کمکی اضافی است که روی یک فایل مشخص روی دیسک کار می‌کند. این رابط از طریق متد {{domxref('FileSystemFileHandle.createWritable()')}} قابل دسترسی است.

{{InheritanceDiagram}}

## خصوصیات نمونه

_خصوصیات والد خود، {{DOMxRef("WritableStream")}} را به ارث می‌برد._

## متدهای نمونه

_متدهای والد خود، {{DOMxRef("WritableStream")}} را به ارث می‌برد._

- {{domxref('FileSystemWritableFileStream.write()')}}
  - : محتوا را در فایلی که این متد روی آن فراخوانی شده است، در آفست فعلی نشانگر فایل می‌نویسد.
- {{domxref('FileSystemWritableFileStream.seek()')}}
  - : آفست فعلی نشانگر فایل را به موقعیت (به بایت) مشخص‌شده به‌روزرسانی می‌کند.
- {{domxref('FileSystemWritableFileStream.truncate()')}}
  - : فایل مرتبط با جریان را به اندازهٔ مشخص‌شده (به بایت) تغییر اندازه می‌دهد.

## مثال‌ها

تابع ناهمگام زیر، انتخابگر «ذخیره فایل» (Save File) را باز می‌کند که پس از انتخاب یک فایل، یک {{domxref('FileSystemFileHandle')}} برمی‌گرداند. سپس با استفاده از متد {{domxref('FileSystemFileHandle.createWritable()')}}، یک جریان نوشتنی از روی این هندل ساخته می‌شود.

سپس یک رشته متنی در جریان نوشته می‌شود و جریان متعاقباً بسته می‌شود.

```js
async function saveFile() {
  // create a new handle
  const newHandle = await window.showSaveFilePicker();

  // create a FileSystemWritableFileStream to write to
  const writableStream = await newHandle.createWritable();

  // write our file
  await writableStream.write("This is my file content");

  // close the file and write the contents to disk.
  await writableStream.close();
}
```

مثال‌های زیر گزینه‌های مختلفی را نشان می‌دهند که می‌توان به متد `write()` ارسال کرد.

```js
// just pass in the data (no options)
writableStream.write(data);

// writes the data to the stream from the determined position
writableStream.write({ type: "write", position, data });

// updates the current file cursor offset to the position specified
writableStream.write({ type: "seek", position });

// resizes the file to be size bytes long
writableStream.write({ type: "truncate", size });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)