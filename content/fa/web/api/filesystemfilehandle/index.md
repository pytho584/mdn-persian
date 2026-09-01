---
title: "FileSystemFileHandle"
---

---
title: FileSystemFileHandle
slug: Web/API/FileSystemFileHandle
page-type: web-api-interface
browser-compat: api.FileSystemFileHandle
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}

رابط **`FileSystemFileHandle`** از {{domxref("File System API", "File System API", "", "nocode")}} نمایانگر دسته‌ای به یک ورودی سیستم فایل است. این رابط از طریق متد {{domxref('window.showOpenFilePicker()')}} در دسترس قرار می‌گیرد.

توجه داشته باشید که عملیات خواندن و نوشتن به مجوزهای دسترسی به فایل وابسته‌اند؛ اگر هیچ تب دیگری از همان خاستگاه (origin) باز نمانده باشد، این مجوزها پس از بازخوانی صفحه پایدار نمی‌مانند. می‌توان از متد {{domxref("FileSystemHandle.queryPermission()", "queryPermission")}} در رابط {{domxref("FileSystemHandle")}} برای بررسی وضعیت مجوز پیش از دسترسی به یک فایل استفاده کرد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌هایی را از والد خود، {{DOMxRef("FileSystemHandle")}}، به ارث می‌برد._

## متدهای نمونه

_متدهایی را از والد خود، {{DOMxRef("FileSystemHandle")}}، به ارث می‌برد._

- {{domxref('FileSystemFileHandle.getFile', 'getFile()')}}
  - : یک {{jsxref('Promise')}} برمی‌گرداند که به یک شیء {{domxref('File')}} resolve می‌شود و وضعیت روی دیسکِ ورودیِ متناظر با این دسته را نشان می‌دهد.
- {{domxref('FileSystemFileHandle.createSyncAccessHandle', 'createSyncAccessHandle()')}}
  - : یک {{jsxref('Promise')}} برمی‌گرداند که به یک شیء {{domxref('FileSystemSyncAccessHandle')}} resolve می‌شود و می‌توان از آن برای خواندن و نوشتن همگام (synchronously) در یک فایل استفاده کرد. ماهیت همگام بودن این متد مزیت‌های عملکردی به همراه دارد، اما فقط در [Web Workers](/en-US/docs/Web/API/Web_Workers_API) اختصاصی قابل استفاده است.
- {{domxref('FileSystemFileHandle.createWritable', 'createWritable()')}}
  - : یک {{jsxref('Promise')}} برمی‌گرداند که به یک شیء {{domxref('FileSystemWritableFileStream')}} تازه‌ساخته‌شده resolve می‌شود و می‌توان از آن برای نوشتن در یک فایل استفاده کرد.

## مثال‌ها

### خواندن یک فایل

تابع ناهمگام زیر یک انتخابگر فایل ارائه می‌دهد و به محض انتخاب یک فایل، از متد `getFile()` برای بازیابی محتوا استفاده می‌کند.

```js
async function getTheFile() {
  const pickerOpts = {
    types: [
      {
        description: "Images",
        accept: {
          "image/*": [".png", ".gif", ".jpeg", ".jpg"],
        },
      },
    ],
    excludeAcceptAllOption: true,
    multiple: false,
  };

  // open file picker
  const [fileHandle] = await window.showOpenFilePicker(pickerOpts);
  // get file contents
  const fileData = await fileHandle.getFile();
  return fileData;
}
```

### نوشتن یک فایل

تابع ناهمگام زیر محتوای داده‌شده را به دسته فایل و در نتیجه به دیسک می‌نویسد.

```js
async function writeFile(fileHandle, contents) {
  // Create a FileSystemWritableFileStream to write to.
  const writable = await fileHandle.createWritable();

  // Write the contents of the file to the stream.
  await writable.write(contents);

  // Close the file and write the contents to disk.
  await writable.close();
}
```

### خواندن و نوشتن همگام یک فایل

تابع مدیریت رویداد ناهمگام زیر درون یک Web Worker قرار دارد. هنگام دریافت پیام از نخ اصلی، کارهای زیر را انجام می‌دهد:

- یک دسته دسترسی همگام به فایل ایجاد می‌کند.
- اندازه فایل را می‌گیرد و یک {{jsxref("ArrayBuffer")}} برای نگهداشتن محتوای فایل ایجاد می‌کند.
- محتوای فایل را در بافر می‌خواند.
- پیام را کدگذاری می‌کند و آن را به انتهای فایل می‌نویسد.
- تغییرات را روی دیسک ماندگار می‌کند و دسته دسترسی را می‌بندد.

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
> در نسخه‌های قبلی مشخصات (spec)، متدهای {{domxref("FileSystemSyncAccessHandle.close()", "close()")}}، {{domxref("FileSystemSyncAccessHandle.flush()", "flush()")}}، {{domxref("FileSystemSyncAccessHandle.getSize()", "getSize()")}} و {{domxref("FileSystemSyncAccessHandle.truncate()", "truncate()")}} به اشتباه به‌عنوان متدهای ناهمگام مشخص شده بودند و نسخه‌های قدیمی‌تر برخی مرورگرها آن‌ها را به این صورت پیاده‌سازی می‌کنند. با این حال، همه مرورگرهای فعلی که از این متدها پشتیبانی می‌کنند، آن‌ها را به‌صورت متدهای همگام پیاده‌سازی می‌کنند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [File System Access API: ساده‌سازی دسترسی به فایل‌های محلی](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)