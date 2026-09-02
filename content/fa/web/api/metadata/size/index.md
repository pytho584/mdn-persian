```
---
title: "Metadata: size property"
short-title: size
slug: Web/API/Metadata/size
page-type: web-api-instance-property
status:
  - experimental
  - non-standard
browser-compat: api.Metadata.size
---

{{APIRef("File and Directory Entries API")}}{{Non-standard_header}}{{SeeCompatTable}}

خاصیت فقط‌خواندنی **`size`** در رابط {{domxref("Metadata")}} اندازهٔ فایل یا شیء سیستم فایل ارجاع‌شده را به بایت مشخص می‌کند.

## مقدار

عددی که اندازهٔ فایل را به بایت نشان می‌دهد.

## مثال‌ها

این مثال اندازهٔ یک فایل گزارش را بررسی می‌کند و اگر بزرگ‌تر از یک مگابایت باشد آن را حذف می‌کند.

```js
workingDirectory.getFile(
  "log/important.log",
  {},
  (fileEntry) => {
    fileEntry.getMetadata((metadata) => {
      if (metadata.size > 1048576) {
        fileEntry.remove(() => {
          /* log file removed; do something clever here */
        });
      }
    });
  },
  handleError,
);
```

## مشخصات

این ویژگی از همهٔ مشخصات حذف شده است و در روند استانداردسازی قرار ندارد.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("Metadata")}}
- {{domxref("FileSystemEntry.getMetadata()")}}
- {{domxref("FileSystemFileEntry")}}
```