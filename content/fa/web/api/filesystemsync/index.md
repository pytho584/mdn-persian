---
title: FileSystemSync
slug: Web/API/FileSystemSync
page-type: web-api-interface
status:
  - deprecated
  - non-standard
browser-compat: api.FileSystemSync
---

{{APIRef("File and Directory Entries API")}}{{Non-standard_Header}}{{Deprecated_Header}}

در [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)، شیء `FileSystemSync` یک سامانهٔ فایل را نشان می‌دهد و دو ویژگی دارد.

> [!WARNING]
> این رابط منسوخ شده و دیگر در مسیر استاندارد نیست.
> _دیگر از آن استفاده نکنید._ به‌جای آن از [File System API](/en-US/docs/Web/API/File_System_API) استفاده کنید.

## مفاهیم پایه

شیء `FileSystemSync` دروازهٔ ورود به کل این API است و زیاد از آن استفاده خواهید کرد. پس به محض دریافت ارجاع، آن را در یک متغیر سراسری یا ویژگی کلاس ذخیره کنید.

## ویژگی‌های نمونه

- `name` {{ReadOnlyInline}} {{Non-standard_Inline}} {{Deprecated_Inline}}
  - : رشته‌ای که نام سامانهٔ فایل را نشان می‌دهد. این نام باید در فهرست سامانه‌های فایلِ در دسترس یکتا باشد.
- `root` {{ReadOnlyInline}} {{Non-standard_Inline}} {{Deprecated_Inline}}
  - : یک `DirectoryEntry` که دایرکتوری ریشهٔ سامانهٔ فایل است.

## مشخصات

این قابلیت دیگر بخشی از هیچ مشخصاتی نیست و در مسیر تبدیل‌شدن به استاندارد نیز نیست.

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)