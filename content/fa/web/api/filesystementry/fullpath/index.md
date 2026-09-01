---
title: "FileSystemEntry: fullPath property"
short-title: fullPath
slug: Web/API/FileSystemEntry/fullPath
page-type: web-api-instance-property
browser-compat: api.FileSystemEntry.fullPath
---

{{APIRef("File and Directory Entries API")}}

ویژگی فقط خواندنی **`fullPath`** در رابط {{domxref("FileSystemEntry")}} یک رشته برمی‌گرداند که مسیر کامل و مطلق از ریشهٔ سیستم فایل تا فایل نمایش‌داده‌شده توسط این ورودی را مشخص می‌کند.

این ویژگی را می‌توان به‌عنوان مسیری که نسبت به دایرکتوری ریشه نسبی است و با یک "/" در ابتدای آن به‌صورت مطلق درآمده نیز در نظر گرفت.

## مقدار

رشته‌ای که مسیر کامل ورودی را نشان می‌دهد.

## مثال‌ها

این مثال تابعی را نشان می‌دهد که با یک سیستم فایل فراخوانی می‌شود؛ سپس یک {{domxref("FileSystemFileEntry")}} برای فایلی به نام `data.json` دریافت می‌کند و مسیر کامل آن را برمی‌گرداند.

```js
function gotFileSystem(fs) {
  let path = "";

  fs.root.getFile(
    "data.json",
    { create: true, exclusive: true },
    (entry) => {
      path = fullPath;
    },
    handleError(error),
  );

  return path;
}
```

بدیهی است که این مثال تا حدی ساختگی است، زیرا می‌دانیم مسیر کامل فایل `"/data.json"` است (چون خودمان آن را جستجو کرده‌ایم)، اما این مفهوم برای سناریوهایی که مسیر را نمی‌دانید همچنان معتبر است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("FileSystemEntry")}}