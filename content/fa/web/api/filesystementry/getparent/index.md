---
title: "FileSystemEntry: getParent() method"
short-title: getParent()
slug: Web/API/FileSystemEntry/getParent
page-type: web-api-instance-method
browser-compat: api.FileSystemEntry.getParent
---

{{APIRef("File and Directory Entries API")}}

در رابط {{domxref("FileSystemEntry")}}، متد
**`getParent()`** یک
{{domxref("FileSystemDirectoryEntry")}} به دست می‌آورد.

## نحو (Syntax)

```js-nolint
getParent(successCallback, errorCallback)
getParent(successCallback)
```

### پارامترها

- `successCallback`
  - : تابعی که وقتی ورودی دایرکتوری والد بازیابی شد فراخوانی می‌شود. این تابع یک پارامتر ورودی دریافت می‌کند: یک شیء {{domxref("FileSystemDirectoryEntry")}} که نمایانگر دایرکتوری والد است. والد دایرکتوری ریشه، خودِ دایرکتوری ریشه در نظر گرفته می‌شود، پس حتماً مراقب این مورد باشید.
- `errorCallback` {{optional_inline}}
  - : یک回调 اختیاری که در صورت بروز خطا اجرا می‌شود. این تابع یک پارامتر دارد: یک {{domxref("DOMException")}} که شرح می‌دهد چه چیزی اشتباه رخ داده است.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `DOMException.INVALID_STATE_ERR`
  - : عملیات ناموفق بود زیرا وضعیت سیستم فایل اجازه آن را نمی‌دهد. این می‌تواند برای مثال زمانی رخ دهد که وضعیت کش‌شده سیستم فایل با وضعیت واقعی آن متفاوت باشد.
- `DOMException.NOT_FOUND_ERR`
  - : مسیر مشخص‌شده یافت نشد.
- `DOMException.SECURITY_ERR`
  - : محدودیت‌های امنیتی از به دست آوردن اطلاعات دایرکتوری والد جلوگیری می‌کنند.

## مثال‌ها

این مثال فایل مشخص‌شده توسط متغیر `fileEntry` را به
`"newname.html"` تغییر نام می‌دهد.

```js
fileEntry.getParent(
  (parent) => {
    fileEntry.moveTo(parent, "newname.html", (updatedEntry) => {
      console.log(`File ${fileEntry.name} renamed to newname.html.`);
    });
  },
  (error) => {
    console.error(
      `An error occurred: Unable to rename ${fileEntry.name} to newname.html.`,
    );
  },
);
```

این کار ابتدا با به دست آوردن یک شیء {{domxref("FileSystemDirectoryEntry")}} که نمایانگر دایرکتوری حاوی فایل است انجام می‌شود. سپس از {{domxref("FileSystemEntry.moveTo", "moveTo()")}} برای تغییر نام فایل در آن دایرکتوری استفاده می‌شود.

## استفاده از Promiseها

در حال حاضر، نسخه‌ای مبتنی بر {{jsxref("Promise")}} برای این متد وجود ندارد. با این حال، می‌توانید یک تابع کمکی ساده برای سازگار کردن آن ایجاد کنید، مانند این:

```js
function getParentPromise(entry) {
  return new Promise((resolve, reject) => {
    entry.getParent(resolve, reject);
  });
}
```

رویکرد مشابهی را می‌توان در جای دیگر در API ورودی‌های فایل و دایرکتوری به کار برد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [API ورودی‌های فایل و دایرکتوری](/en-US/docs/Web/API/File_and_Directory_Entries_API)