---
title: "FileSystemObserver: observe() method"
short-title: observe()
slug: Web/API/FileSystemObserver/observe
page-type: web-api-instance-method
status:
  - experimental
  - non-standard
browser-compat: api.FileSystemObserver.observe
---

{{securecontext_header}}{{APIRef("File System API")}}{{SeeCompatTable}}{{non-standard_header}}

متد **`observe()`** از رابط {{domxref("FileSystemObserver")}} از ناظر می‌خواهد که نظارت بر تغییرات یک فایل یا دایرکتوری مشخص را آغاز کند.

## نحو (Syntax)

```js-nolint
observe(handle)
observe(handle, options)
```

### پارامترها

- `handle`
  - : شناسه‌ی ورودی (handle) مربوط به درونداد سیستم فایل که فایل یا دایرکتوری مورد نظر برای نظارت را نمایش می‌دهد.
    - برای سیستم فایل قابل مشاهده توسط کاربر (user-observable file system)، این می‌تواند یک {{domxref("FileSystemFileHandle")}} یا {{domxref("FileSystemDirectoryHandle")}} باشد.
    - برای [سیستم فایل خصوصی مبدأ](/en-US/docs/Web/API/File_System_API/Origin_private_file_system) (OPFS)، می‌تواند یک {{domxref("FileSystemFileHandle")}}، {{domxref("FileSystemDirectoryHandle")}}، یا {{domxref("FileSystemSyncAccessHandle")}} باشد.

- `options` {{optional_inline}}
  - : یک شیء که گزینه‌های فراخوانی `observe()` را مشخص می‌کند. می‌تواند شامل ویژگی‌های زیر باشد:
    - `recursive`
      - : یک مقدار بولی که مشخص می‌کند آیا می‌خواهید تغییرات یک دایرکتوری را به صورت بازگشتی (recursive) نظارت کنید. اگر `true` باشد، تغییرات در خود دایرکتوری و تمام زیرشاخه‌ها و فایل‌های درون آن نظارت می‌شود. اگر `false` باشد، تنها تغییرات در خود دایرکتوری و فایل‌های مستقیم درون آن (یعنی فایل‌های داخل زیرشاخه‌ها مستثنی هستند) نظارت می‌شود. مقدار پیش‌فرض `false` است.

        این ویژگی اگر `handle` نمایانگر یک فایل باشد، تأثیری ندارد.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به {{jsxref('undefined')}} حل می‌شود.

### استثناها (Exceptions)

- `NotFoundError` {{domxref("DOMException")}}
  - : اگر فایل یا دایرکتوری که توسط `handle` نمایش داده شده پیدا نشود، پرتاب می‌شود.

## مثال‌ها

### نظارت بر یک فایل یا دایرکتوری

با فرض اینکه یک نمونه از `FileSystemObserver` در دسترس است، می‌توانید با فراخوانی `observe()` نظارت بر تغییرات یک درونداد سیستم فایل را آغاز کنید.

می‌توانید با ارسال یک {{domxref("FileSystemFileHandle")}} یا {{domxref("FileSystemDirectoryHandle")}} به `observe()`، یک فایل یا دایرکتوری در سیستم فایل قابل مشاهده توسط کاربر یا [سیستم فایل خصوصی مبدأ (OPFS)](/en-US/docs/Web/API/File_System_API/Origin_private_file_system) را نظارت کنید. نمونه‌های این اشیاء می‌توانند مثلاً زمانی که کاربر با استفاده از {{domxref("Window.showSaveFilePicker()")}} یا {{domxref("Window.showDirectoryPicker()")}} یک فایل یا دایرکتوری را انتخاب می‌کند، بازگردانده شوند:

```js
// نظارت بر یک فایل
async function observeFile() {
  const fileHandle = await window.showSaveFilePicker();

  await observer.observe(fileHandle);
}

// نظارت بر یک دایرکتوری
async function observeDirectory() {
  const directoryHandle = await window.showDirectoryPicker();

  await observer.observe(directoryHandle);
}
```

همچنین می‌توانید با ارسال یک {{domxref("FileSystemSyncAccessHandle")}} به `observe()`، تغییرات در OPFS را نظارت کنید:

```js
// نظارت بر یک درونداد سیستم فایل OPFS
async function observeOPFSFile() {
  const root = await navigator.storage.getDirectory();
  const draftHandle = await root.getFileHandle("draft.txt", { create: true });
  const syncHandle = await draftHandle.createSyncAccessHandle();

  await observer.observe(syncHandle);
}
```

### نظارت بازگشتی بر یک دایرکتوری

برای نظارت بازگشتی بر یک دایرکتوری، `observe()` را با گزینه‌ی `recursive` برابر با `true` فراخوانی کنید:

```js
// نظارت بازگشتی بر یک دایرکتوری
async function observeDirectory() {
  const directoryHandle = await window.showDirectoryPicker();

  await observer.observe(directoryHandle, { recursive: true });
}
```

## مشخصات (Specifications)

در حال حاضر بخشی از یک مشخصات (specification) نیست. برای PR مربوط به مشخصات، به [https://github.com/whatwg/fs/pull/165](https://github.com/whatwg/fs/pull/165) مراجعه کنید.

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [آزمایش مبدأ (origin trial) API ناظر سیستم فایل](https://developer.chrome.com/blog/file-system-observer#stop-observing-the-file-system) در developer.chrome.com (2024)