---
title: FileSystemFileEntry
slug: Web/API/FileSystemFileEntry
page-type: web-api-interface
browser-compat: api.FileSystemFileEntry
---

{{APIRef("File and Directory Entries API")}}

رابط کاربری **`FileSystemFileEntry`** در [API ورودیهای پرونده و پوشه](/en-US/docs/Web/API/File_and_Directory_Entries_API) یک پرونده را در یک سیستم فایل نشان میدهد. این رابط، ویژگیهایی برای توصیف صفات پرونده و نیز متد {{domxref("FileSystemFileEntry.file", "file()")}} ارائه میکند که یک شیء {{domxref("File")}} میسازد و میتوان از آن برای خواندن پرونده استفاده کرد.

{{InheritanceDiagram}}

## ویژگیهای نمونه

_ویژگیهای رابط والد خود، یعنی {{domxref("FileSystemEntry")}} را به ارث میبرد، اما هیچ ویژگی منحصربهفردی برای این رابط ندارد._

## روشهای نمونه

- {{domxref("FileSystemFileEntry.createWriter", "createWriter()")}} {{deprecated_inline}} {{non-standard_inline}}
  - : یک شیء {{domxref("FileWriter")}} برمیگرداند که میتوان از آن برای نوشتن داده درون پروندهٔ نماینشده توسط ورودی پوشه استفاده کرد.
- {{domxref("FileSystemFileEntry.file", "file()")}}
  - : یک شیء جدید {{domxref("File")}} میسازد که میتوان از آن برای خواندن پرونده استفاده کرد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [API ورودیهای پرونده و پوشه](/en-US/docs/Web/API/File_and_Directory_Entries_API)