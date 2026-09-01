---
title: "HTMLInputElement: files property"
short-title: files
slug: Web/API/HTMLInputElement/files
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.files
---

{{APIRef("File and Directory Entries API")}}

ویژگی **`HTMLInputElement.files`** به شما امکان دسترسی به {{domxref("FileList")}} انتخاب‌شده با عنصر [`<input type="file">`](/en-US/docs/Web/HTML/Reference/Elements/input/file) را می‌دهد.

## مقدار

یک شیء {{domxref("FileList")}} که فایل‌های انتخاب‌شده را فهرست می‌کند (در صورت وجود)، یا `null` اگر **`HTMLInputElement`** از نوع `type="file"` نباشد.

## مثال‌ها

مثال زیر نشان می‌دهد که چگونه می‌توانید به ویژگی **`HTMLInputElement.files`** دسترسی پیدا کنید و نام، تاریخ تغییر، اندازه و نوع هر فایل انتخاب‌شده توسط کاربر را در کنسول ثبت کنید.

### HTML

```html
<input id="files" type="file" multiple />
```

### JavaScript

توجه داشته باشید که **`HTMLInputElement.files`** حتی اگر فایلی انتخاب نشده باشد، همچنان یک نمونه از {{domxref("FileList")}} برمی‌گرداند. بنابراین پیمایش آن با {{JSxref("Statements/for...of", "for...of")}} بدون نیاز به بررسی وجود فایل‌ها ایمن است.

```js
const fileInput = document.getElementById("files");

console.log(fileInput.files instanceof FileList); // true even if empty

for (const file of fileInput.files) {
  console.log(file.name); // prints file name
  let fileDate = new Date(file.lastModified);
  console.log(fileDate.toLocaleDateString()); // prints legible date
  console.log(
    file.size < 1000 ? file.size : `${Math.round(file.size / 1000)}KB`,
  );
  console.log(file.type); // prints MIME type
}
```

## مشخصات

{{ Specifications }}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DataTransfer.files")}}