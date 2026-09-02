---
title: Metadata
slug: Web/API/Metadata
page-type: web-api-interface
status:
  - experimental
  - non-standard
browser-compat: api.Metadata
---

{{APIRef("File and Directory Entries API")}}{{Non-standard_Header}}{{SeeCompatTable}}

رابطِ **`Metadata`** حاوی اطلاعاتی دربارهٔ یک ورودیِ سیستم فایل است. این فراداده شامل اندازهٔ فایل و تاریخ و زمان آخرین تغییر آن می‌شود.

> [!NOTE]
> این رابط در حوزهٔ سراسری در دسترس نیست؛ در عوض، برای دریافت یک شیء `Metadata` که یک {{domxref("FileSystemEntry")}} را توصیف می‌کند، از متد {{domxref("FileSystemEntry.getMetadata()")}} استفاده می‌کنید.

## ویژگی‌های نمونه

- {{domxref("Metadata.modificationTime", "modificationTime")}} {{ReadOnlyInline}} {{Experimental_Inline}} {{Non-standard_Inline}}
  - : یک شیء {{jsxref("Date")}} که تاریخ و زمان تغییر یافتن ورودی را نشان می‌دهد.
- {{domxref("Metadata.size", "size")}} {{ReadOnlyInline}} {{Experimental_Inline}} {{Non-standard_Inline}}
  - : یک عدد صحیح بدون علامت ۶۴-بیتی که اندازهٔ ورودی را بر حسب بایت نشان می‌دهد.

## مشخصات

این ویژگی از همهٔ مشخصات حذف شده است و در فرایند استانداردسازی قرار ندارد.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("FileSystemEntry")}}
- {{domxref("FileSystemFileEntry")}} و {{domxref("FileSystemDirectoryEntry")}}