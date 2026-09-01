---
title: "Origin private file system"
slug: Web/API/File_System_API/Origin_private_file_system
page-type: guide
browser-compat: api.StorageManager.getDirectory
---

{{securecontext_header}}{{DefaultAPISidebar("File System API")}}{{AvailableInWorkers}}

**سیستم فایل خصوصی مبدأ** (OPFS) یک نقطه پایانی ذخیره‌سازی است که به عنوان بخشی از [File System API](/en-US/docs/Web/API/File_System_API) ارائه می‌شود و نسبت به مبدأ صفحه خصوصی است و مانند سیستم فایل معمولی برای کاربر قابل مشاهده نیست. این سیستم دسترسی به نوع خاصی از فایل را فراهم می‌کند که برای کارایی بهینه‌سازی شده و امکان نوشتن در محل (in-place) در محتوای آن را می‌دهد.

## کار با فایل‌ها با استفاده از File System Access API

[File System Access API](https://wicg.github.io/file-system-access/) که [File System API](/en-US/docs/Web/API/File_System_API) را گسترش می‌دهد، با استفاده از روش‌های انتخاب فایل (picker)، دسترسی به فایل‌ها را فراهم می‌کند. برای مثال:

1. متد {{domxref("Window.showOpenFilePicker()")}} به کاربر امکان می‌دهد فایلی را برای دسترسی انتخاب کند که در نتیجه یک شیء {{domxref("FileSystemFileHandle")}} بازگردانده می‌شود.
2. متد {{domxref("FileSystemFileHandle.getFile()")}} برای دسترسی به محتویات فایل فراخوانی می‌شود و محتوا با استفاده از {{domxref("FileSystemFileHandle.createWritable()")}} / {{domxref("FileSystemWritableFileStream.write()")}} تغییر می‌کند.
3. از {{domxref("FileSystemHandle.requestPermission()", "FileSystemHandle.requestPermission({mode: 'readwrite'})")}} برای درخواست مجوز کاربر جهت ذخیره تغییرات استفاده می‌شود.
4. اگر کاربر درخواست مجوز را بپذیرد، تغییرات در فایل اصلی ذخیره می‌شوند.

این روش کار می‌کند، اما محدودیت‌هایی دارد. این تغییرات روی سیستم فایل قابل مشاهده توسط کاربر اعمال می‌شوند، بنابراین بررسی‌های امنیتی زیادی (به عنوان مثال، [مرور امن](https://developers.google.com/safe-browsing) در کروم) برای محافظت در برابر نوشتن محتوای مخرب در آن سیستم فایل وجود دارد. این نوشتن‌ها در محل انجام نمی‌شوند و در عوض از یک فایل موقت استفاده می‌کنند. فایل اصلی تغییر نمی‌کند مگر اینکه همه بررسی‌های امنیتی را پشت سر بگذارد.

در نتیجه، این عملیات نسبتاً کند هستند. زمانی که به‌روزرسانی‌های متنی کوچک انجام می‌دهید، این کندی چندان محسوس نیست، اما هنگام انجام تغییرات فایل بزرگ‌تر و در مقیاس وسیع مانند تغییرات پایگاه داده [SQLite](https://sqlite.org/wasm)، کارایی آسیب می‌بیند.

## OPFS چگونه چنین مشکلاتی را حل می‌کند؟

OPFS دسترسی سطح پایین و بایت‌به‌بایت به فایل‌ها ارائه می‌دهد که نسبت به مبدأ صفحه خصوصی است و برای کاربر قابل مشاهده نیست. در نتیجه، به همان مجموعه بررسی‌های امنیتی و اعطای مجوزها نیازی ندارد و بنابراین از فراخوانی‌های File System Access API سریع‌تر است. همچنین مجموعه‌ای از فراخوانی‌های همزمان (synchronous) در دسترس دارد (سایر فراخوانی‌های File System API ناهمزمان هستند) که فقط می‌توانند در web workerها اجرا شوند تا نخ اصلی مسدود نشود.

به طور خلاصه، تفاوت OPFS با سیستم فایل قابل مشاهده توسط کاربر به این صورت است:

- OPFS مشمول [محدودیت‌های سهمیه ذخیره‌سازی مرورگر](/en-US/docs/Web/API/Storage_API/Storage_quotas_and_eviction_criteria) است، دقیقاً مانند هر مکانیزم ذخیره‌سازی تقسیم‌بندی‌شده بر اساس مبدأ (مثلاً {{domxref("IndexedDB API", "IndexedDB API", "", "nocode")}}). می‌توانید میزان فضای ذخیره‌سازی استفاده‌شده توسط OPFS را از طریق {{domxref("StorageManager.estimate()", "navigator.storage.estimate()")}} مشاهده کنید.
- پاک کردن داده‌های ذخیره‌سازی سایت، OPFS را حذف می‌کند.
- برای دسترسی به فایل‌ها در OPFS، درخواست مجوز و بررسی‌های امنیتی لازم نیست.
- مرورگرها محتویات OPFS را در جایی روی دیسک نگه می‌دارند، اما نباید انتظار داشته باشید که فایل‌های ایجاد شده را یک‌به‌یک مطابقت دهید. OPFS برای نمایش به کاربر طراحی نشده است.

## چگونه به OPFS دسترسی پیدا می‌کنید؟

برای دسترسی به OPFS، ابتدا متد {{domxref("StorageManager.getDirectory()", "navigator.storage.getDirectory()")}} را فراخوانی می‌کنید. این متد یک ارجاع به یک شیء {{domxref("FileSystemDirectoryHandle")}} برمی‌گرداند که ریشه OPFS را نشان می‌دهد.

## دستکاری OPFS از نخ اصلی

هنگام دسترسی به OPFS از نخ اصلی، از APIهای ناهمزمان مبتنی بر {{jsxref("Promise")}} استفاده می‌کنید. می‌توانید با فراخوانی {{domxref("FileSystemDirectoryHandle.getFileHandle()")}} و {{domxref("FileSystemDirectoryHandle.getDirectoryHandle()")}} به ترتیب روی شیء {{domxref("FileSystemDirectoryHandle")}} که نمایانگر ریشه OPFS است (و دایرکتوری‌های فرزند، در صورت ایجاد)، به دسته‌های فایل ({{domxref("FileSystemFileHandle")}}) و دایرکتوری ({{domxref("FileSystemDirectoryHandle")}}) دسترسی پیدا کنید.

> [!NOTE]
> ارسال `{ create: true }` به روش‌های بالا باعث می‌شود فایل یا پوشه در صورت وجود نداشتن ایجاد شود.

```js
// یک سلسله‌مراتب از فایل‌ها و پوشه‌ها ایجاد کنید
const fileHandle = await opfsRoot.getFileHandle("my first file", {
  create: true,
});
const directoryHandle = await opfsRoot.getDirectoryHandle("my first folder", {
  create: true,
});
const nestedFileHandle = await directoryHandle.getFileHandle(
  "my first nested file",
  { create: true },
);
const nestedDirectoryHandle = await directoryHandle.getDirectoryHandle(
  "my first nested folder",
  { create: true },
);

// دسترسی به فایل‌ها و پوشه‌های موجود از طریق نام آن‌ها
const existingFileHandle = await opfsRoot.getFileHandle("my first file");
const existingDirectoryHandle =
  await opfsRoot.getDirectoryHandle("my first folder");
```

### خواندن یک فایل

1. یک فراخوانی {{domxref("FileSystemDirectoryHandle.getFileHandle()")}} انجام دهید تا یک شیء {{domxref("FileSystemFileHandle")}} بازگردانده شود.
2. متد {{domxref("FileSystemFileHandle.getFile()")}} را فراخوانی کنید تا یک شیء {{domxref("File")}} بازگردانده شود. این یک نوع تخصصی از {{domxref("Blob")}} است و بنابراین می‌توان آن را مانند هر `Blob` دیگری دستکاری کرد. برای مثال، می‌توانید مستقیماً از طریق {{domxref("Blob.text()")}} به محتوای متنی دسترسی پیدا کنید.

### نوشتن یک فایل

1. یک فراخوانی {{domxref("FileSystemDirectoryHandle.getFileHandle()")}} انجام دهید تا یک شیء {{domxref("FileSystemFileHandle")}} بازگردانده شود.
2. متد {{domxref("FileSystemFileHandle.createWritable()")}} را فراخوانی کنید تا یک شیء {{domxref("FileSystemWritableFileStream")}} بازگردانده شود که نوع تخصصی {{domxref("WritableStream")}} است.
3. محتوا را با استفاده از یک فراخوانی {{domxref("FileSystemWritableFileStream.write()")}} در آن بنویسید.
4. جریان را با استفاده از {{domxref("WritableStream.close()")}} ببندید.

### حذف یک فایل یا پوشه

می‌توانید {{domxref("FileSystemDirectoryHandle.removeEntry()")}} را روی دایرکتوری والد فراخوانی کنید و نام موردی را که می‌خواهید حذف کنید به آن بدهید:

```js
directoryHandle.removeEntry("my first nested file");
```

همچنین می‌توانید {{domxref("FileSystemHandle.remove()")}} را روی {{domxref("FileSystemFileHandle")}} یا {{domxref("FileSystemDirectoryHandle")}} که نمایانگر مورد موردنظر برای حذف است فراخوانی کنید. برای حذف یک پوشه شامل همه زیرپوشه‌ها، گزینه `{ recursive: true }` را ارسال کنید.

```js
await fileHandle.remove();
await directoryHandle.remove({ recursive: true });
```

روش زیر یک راه سریع برای پاک کردن کل OPFS ارائه می‌دهد:

```js
await (await navigator.storage.getDirectory()).remove({ recursive: true });
```

### فهرست کردن محتویات یک پوشه

{{domdomain("FileSystemDirectoryHandle")}} یک [تکرارگر ناهمزمان](/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#the_async_iterator_and_async_iterable_protocols) است. بنابراین می‌توانید با یک حلقه [`for await...of`](/en-US/docs/Web/JavaScript/Reference/Statements/for-await...of) و روش‌های استانداردی مانند [`entries()`](/en-US/docs/Web/API/FileSystemDirectoryHandle/entries)، [`values()`](/en-US/docs/Web/API/FileSystemDirectoryHandle/entries) و [`keys()`](/en-US/docs/Web/API/FileSystemDirectoryHandle/entries) روی آن تکرار کنید.

برای مثال:

```js
for await (let [name, handle] of directoryHandle) {
}
for await (let [name, handle] of directoryHandle.entries()) {
}
for await (let handle of directoryHandle.values()) {
}
for await (let name of directoryHandle.keys()) {
}
```

## دستکاری OPFS از یک web worker

web workerها نخ اصلی را مسدود نمی‌کنند، بنابراین می‌توانید از APIهای دسترسی همزمان به فایل در این زمینه استفاده کنید. APIهای همزمان سریع‌تر هستند، زیرا نیازی به کار با قول‌ها (promise) ندارند.

می‌توانید با فراخوانی {{domdomain("FileSystemFileHandle.createSyncAccessHandle()")}} روی یک {{domdomain("FileSystemFileHandle")}} معمولی به صورت همزمان به یک فایل دسترسی پیدا کنید:

> [!NOTE]
> با وجود اینکه «Sync» در نام آن وجود دارد، خود متد `createSyncAccessHandle()` ناهمزمان است.

```js
const opfsRoot = await navigator.storage.getDirectory();
const fileHandle = await opfsRoot.getFileHandle("my-high-speed-file.txt", {
  create: true,
});
const syncAccessHandle = await fileHandle.createSyncAccessHandle();
```

روش‌های _همزمان_ متعددی روی {{domdomain("FileSystemSyncAccessHandle")}} برگشتی موجود است:

- {{domdomain("FileSystemSyncAccessHandle.getSize", "getSize()")}}: اندازه فایل را بر حسب بایت برمی‌گرداند.
- {{domdomain("FileSystemSyncAccessHandle.write", "write()")}}: محتوای یک بافر را در فایل می‌نویسد، در صورت تمایل در یک آفست مشخص، و تعداد بایت‌های نوشته‌شده را برمی‌گرداند. بررسی تعداد بایت‌های نوشته‌شده به فراخواننده امکان می‌دهد خطاها و نوشتن‌های جزئی را تشخیص داده و مدیریت کند.
- {{domdomain("FileSystemSyncAccessHandle.read", "read()")}}: محتویات فایل را در یک بافر می‌خواند، در صورت تمایل در یک آفست مشخص.
- {{domdomain("FileSystemSyncAccessHandle.truncate", "truncate()")}}: اندازه فایل را به اندازه داده‌شده تغییر می‌دهد.
- {{domdomain("FileSystemSyncAccessHandle.flush", "flush()")}}: اطمینان حاصل می‌کند که محتویات فایل شامل تمام تغییرات انجام‌شده از طریق `write()` است.
- {{domdomain("FileSystemSyncAccessHandle.close", "close()")}}: دسته دسترسی را می‌بندد.

در اینجا مثالی آورده شده است که از همه روش‌های ذکر شده در بالا استفاده می‌کند:

```js
const opfsRoot = await navigator.storage.getDirectory();
const fileHandle = await opfsRoot.getFileHandle("fast", { create: true });
const accessHandle = await fileHandle.createSyncAccessHandle();

const textEncoder = new TextEncoder();
const textDecoder = new TextDecoder();

// Initialize this variable for the size of the file.
let size;
// The current size of the file, initially `0`.
size = accessHandle.getSize();
// Encode content to write to the file.
const content = textEncoder.encode("Some text");
// Write the content at the beginning of the file.
accessHandle.write(content, { at: size });
// Flush the changes.
accessHandle.flush();
// The current size of the file, now `9` (the length of "Some text").
size = accessHandle.getSize();

// Encode more content to write to the file.
const moreContent = textEncoder.encode("More content");
// Write the content at the end of the file.
accessHandle.write(moreContent, { at: size });
// Flush the changes.
accessHandle.flush();
// The current size of the file, now `21` (the length of
// "Some textMore content").
size = accessHandle.getSize();

// Prepare a data view of the length of the file.
const dataView = new DataView(new ArrayBuffer(size));

// Read the entire file into the data view.
accessHandle.read(dataView, { at: 0 });
// Logs `"Some textMore content"`.
console.log(textDecoder.decode(dataView));

// Read starting at offset 9 into the data view.
accessHandle.read(dataView, { at: 9 });
// Logs `"More content"`.
console.log(textDecoder.decode(dataView));

// Truncate the file after 4 bytes.
accessHandle.truncate(4);
```

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [سیستم فایل خصوصی مبدأ](https://web.dev/articles/origin-private-file-system) در web.dev