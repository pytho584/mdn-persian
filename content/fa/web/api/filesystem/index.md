---
title: FileSystem
slug: Web/API/FileSystem
page-type: web-api-interface
browser-compat: api.FileSystem
---

{{APIRef("File and Directory Entries API")}}

اینترفیس **`FileSystem`** در File and Directory Entries API برای نمایش یک سیستم فایل استفاده می‌شود. این اشیا را می‌توان از طریق خاصیت {{domxref("FileSystemEntry.filesystem", "filesystem")}} روی هر ورودی سیستم فایل به دست آورد. برخی مرورگرها APIهای اضافی برای ایجاد و مدیریت سیستم‌های فایل ارائه می‌دهند، مانند متد {{domxref("Window.requestFileSystem", "requestFileSystem()")}} در کروم.

این اینترفیس به شما دسترسی به سیستم فایل کاربران نخواهد داد. در عوض، شما یک «درایو مجازی» در محیط شنی (sandbox) مرورگر خواهید داشت. اگر می‌خواهید به سیستم فایل کاربر دسترسی پیدا کنید، باید از کاربر اجازه بگیرید؛ مثلاً با نصب یک افزونه کروم. API مربوط به کروم را می‌توانید [در مستندات توسعه‌دهندگان کروم](https://developer.chrome.com/docs/apps/reference/fileSystem) بیابید.

## مفاهیم پایه

دو راه برای دسترسی به یک شیء `FileSystem` وجود دارد:

1. می‌توانید مستقیماً با فراخوانی `window.requestFileSystem()`، یک سیستم فایل در محیط شنی (sandboxed) را که مخصوصاً برای برنامه وب شما ایجاد شده است درخواست کنید. اگر این فراخوانی موفق باشد، یک تابع callback اجرا می‌شود که به‌عنوان پارامتر، یک شیء `FileSystem` توصیف‌کننده سیستم فایل دریافت می‌کند.
2. می‌توانید آن را از یک شیء ورودی سیستم فایل، از طریق خاصیت {{domxref("FileSystemEntry.filesystem", "filesystem")}} آن دریافت کنید.

## ویژگی‌های نمونه

- {{domxref("FileSystem.name")}} {{ReadOnlyInline}}
  - : یک رشته (string) که نام سیستم فایل را نشان می‌دهد. این نام در میان تمام فهرست سیستم‌های فایل در دسترس یکتا است.
- {{domxref("FileSystem.root")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("FileSystemDirectoryEntry")}} که پوشه ریشه سیستم فایل را نشان می‌دهد. از طریق این شیء می‌توانید به همه فایل‌ها و پوشه‌های موجود در سیستم فایل دسترسی پیدا کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("FileSystemEntry")}}، {{domxref("FileSystemFileEntry")}} و {{domxref("FileSystemDirectoryEntry")}}