---
title: "FileSystemDirectoryEntry: removeRecursively() method"
short-title: removeRecursively()
slug: Web/API/FileSystemDirectoryEntry/removeRecursively
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.FileSystemDirectoryEntry.removeRecursively
---

{{APIRef("File and Directory Entries API")}}{{Deprecated_Header}}{{Non-standard_Header}}

متد **`removeRecursively()`** از رابط {{domxref("FileSystemDirectoryEntry")}} دایرکتوری (پوشه) و تمام محتوای آن را به صورت بازگشتی حذف می‌کند، با پیمایش سلسله‌مراتبی کل زیردرخت فایل‌ها و دایرکتوری‌های زیرمجموعه.

برای حذف یک فایل یا یک دایرکتوری خالی، می‌توانید از {{domxref("FileSystemEntry.remove()")}} نیز استفاده کنید.

## Syntax

```js-nolint
removeRecursively(successCallback)
removeRecursively(successCallback, errorCallback)
```

### Parameters

- `successCallback`
  - : یک تابع که پس از اتمام فرآیند حذف دایرکتوری فراخوانی می‌شود. این تابع هیچ پارامتری ندارد.
- `errorCallback` {{optional_inline}}
  - : یک تابع که در صورت بروز خطا در حین تلاش برای حذف زیردرخت دایرکتوری فراخوانی می‌شود. یک {{domxref("DOMException")}} که خطای رخ داده را توصیف می‌کند به عنوان ورودی دریافت می‌کند.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

### Exceptions

اگر خطایی رخ دهد و `errorCallback` مشخص شده باشد، آن تابع با یک پارامتر فراخوانی می‌شود: یک شیء {{domxref("DOMException")}} که خطا را توصیف می‌کند. {{domxref("DOMException.code")}} مشخص می‌کند که چه نوع خطایی رخ داده است، به شرح زیر:

- `DOMException.INVALID_MODIFICATION_ERR`
  - : تلاش برای حذف دایرکتوری ریشه انجام شده است؛ این کار مجاز نیست.
- `DOMException.NO_MODIFICATION_ALLOWED_ERR`
  - : وضعیت سیستم فایل اجازه تغییر را نمی‌دهد.
- `DOMException.NOT_FOUND_ERR`
  - : دایرکتوری که توسط {{domxref("FileSystemDirectoryEntry")}} نمایش داده می‌شود دیگر وجود ندارد.
- `DOMException.NOT_READABLE_ERR`
  - : دایرکتوری قابل دسترسی نیست؛ احتمالاً توسط برنامه دیگری در حال استفاده است یا در سطح سیستم عامل قفل شده است.
- `DOMException.SECURITY_ERR`
  - : به دلایل امنیتی نمی‌توان دایرکتوری را حذف کرد. دلایل احتمالی عبارتند از:
    - دایرکتوری و/یا محتویات آن ممکن است از طریق یک برنامه وب ایمن نباشند.
    - تماس‌های زیادی با سیستم فایل در حال انجام است.
    - سایر نگرانی‌های امنیتی که توسط عامل کاربر یا سیستم عامل مطرح شده است.

> [!NOTE]
> اگر تلاش کنید دایرکتوری را حذف کنید که شامل یک یا چند فایل غیرقابل حذف است، یا در حین حذف تعدادی از فایل‌ها خطایی رخ دهد، ممکن است برخی فایل‌ها حذف نشوند. باید یک `errorCallback` ارائه دهید تا این وضعیت را زیر نظر گرفته و مدیریت کنید، شاید با تلاش مجدد.

## Examples

```js
directory.removeRecursively(
  () => {
    /* The directory was removed successfully */
  },
  () => {
    /* an error occurred while removing the directory */
  },
);
```

## Browser compatibility

{{Compat}}

## See also

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("FileSystemDirectoryEntry")}}
- {{domxref("FileSystemEntry.remove()")}}