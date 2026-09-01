---
title: FileSystemDirectoryReader
slug: Web/API/FileSystemDirectoryReader
page-type: web-api-interface
browser-compat: api.FileSystemDirectoryReader
---

{{APIRef("File and Directory Entries API")}}

رابط `FileSystemDirectoryReader` از [API ورودی‌های فایل و دایرکتوری](/en-US/docs/Web/API/File_and_Directory_Entries_API) به شما امکان می‌دهد به اشیاء مبتنی بر {{domxref("FileSystemFileEntry")}} (معمولاً {{domxref("FileSystemFileEntry")}} یا {{domxref("FileSystemDirectoryEntry")}}) که هر ورودی در یک دایرکتوری را نمایش می‌دهند، دسترسی پیدا کنید.

## روش‌های نمونه

- {{domxref("FileSystemDirectoryReader.readEntries", "readEntries()")}}
  - : یک آرایه شامل تعدادی از ورودی‌های دایرکتوری برمی‌گرداند. هر آیتم در این آرایه یک شیء مبتنی بر {{domxref("FileSystemEntry")}} است – معمولاً {{domxref("FileSystemFileEntry")}} یا {{domxref("FileSystemDirectoryEntry")}}.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [API ورودی‌های فایل و دایرکتوری](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("FileSystemDirectoryEntry")}}
- {{domxref("FileSystem")}}