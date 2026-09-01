---
title: "FileSystemObserver: FileSystemObserver() constructor"
short-title: FileSystemObserver()
slug: Web/API/FileSystemObserver/FileSystemObserver
page-type: web-api-constructor
status:
  - experimental
  - non-standard
browser-compat: api.FileSystemObserver.FileSystemObserver
---

{{APIRef("File System API")}}{{SeeCompatTable}}{{non-standard_header}}

سازندهٔ **`FileSystemObserver()`** یک نمونهٔ جدید از شیء {{domxref("FileSystemObserver")}} ایجاد می‌کند.

## Syntax

```js-nolint
new FileSystemObserver(callback)
```

### Parameters

- `callback`
  - : یک تابع بازخورد (callback) تعریف‌شده توسط کاربر که زمانی فراخوانی می‌شود که ناظر (observer) تغییری را در ورودیِ سیستم فایلی که از آن خواسته شده مشاهده کند، شناسایی کند (از طریق {{domxref("FileSystemObserver.observe()")}}). این تابع بازخورد دو پارامتر زیر را دریافت می‌کند:
    - `records`
      - : آرایه‌ای از اشیاء {{domxref("FileSystemChangeRecord")}} که حاوی جزئیات همهٔ تغییرات مشاهده‌شده است.
    - `observer`
      - : ارجاعی به شیء فعلی `FileSystemObserver` که در دسترس قرار می‌گیرد تا مثلاً در صورت نیاز بتوانید پس از دریافت رکوردهای فعلی، مشاهده را با استفاده از متد {{domxref('FileSystemObserver.disconnect()')}} متوقف کنید.

### Return value

یک شیء جدید {{domxref("FileSystemObserver")}}.

## Examples

> [!NOTE]
> برای یک مثال کامل و قابل اجرا، به [File System Observer Demo](https://mdn.github.io/dom-examples/file-system-api/filesystemobserver/) مراجعه کنید ([source code](https://github.com/mdn/dom-examples/tree/main/file-system-api/filesystemobserver)).

### مقداردهی اولیهٔ یک `FileSystemObserver`

قبل از اینکه بتوانید مشاهدهٔ تغییرات فایل یا پوشه را شروع کنید، باید یک `FileSystemObserver` برای مدیریت مشاهدات مقداردهی کنید:

```js
const observer = new FileSystemObserver(callback);
```

بدنهٔ تابع بازخورد را می‌توان به‌گونه‌ای تعریف کرد که مشاهدات تغییرات فایل را به هر شکلی که می‌خواهید برگرداند و پردازش کند:

```js
const callback = (records, observer) => {
  for (const record of records) {
    console.log("Change detected:", record);
    const reportContent = `Change observed to ${record.changedHandle.kind} ${record.changedHandle.name}. Type: ${record.type}.`;
    sendReport(reportContent); // Some kind of user-defined reporting function
  }

  observer.disconnect();
};
```

## Specifications

در حال حاضر بخشی از هیچ مشخصات رسمی نیست. برای PR مربوط به مشخصات، به [https://github.com/whatwg/fs/pull/165](https://github.com/whatwg/fs/pull/165) مراجعه کنید.

## Browser compatibility

{{Compat}}

## See also

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Observer API origin trial](https://developer.chrome.com/blog/file-system-observer#stop-observing-the-file-system) در developer.chrome.com (2024)