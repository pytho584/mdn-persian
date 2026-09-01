---
title: "FileSystemFileEntry: createWriter() method"
short-title: createWriter()
slug: Web/API/FileSystemFileEntry/createWriter
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.FileSystemFileEntry.createWriter
---

{{APIRef("File and Directories Entries API")}}{{deprecated_header}}{{Non-standard_header}}

متد **`createWriter()`** از رابط {{domxref("FileSystemFileEntry")}} یک شیء {{domxref("FileWriter")}} را برمی‌گرداند که می‌توان از آن برای نوشتن داده‌ها در فایل نمایش‌داده‌شده توسط ورودی دایرکتوری استفاده کرد.

## Syntax

```js-nolint
createWriter(successCallback)
createWriter(successCallback, errorCallback)
```

### Parameters

- `successCallback`
  - : یک تابع callback که هنگام ایجاد موفقیت‌آمیز {{domxref("FileWriter")}} فراخوانی می‌شود؛ `FileWriter` به عنوان تنها پارامتر به callback ارسال می‌شود.
- `errorCallback` {{optional_inline}}
  - : در صورت ارائه، این باید یک متد باشد که هنگام بروز خطا در تلاش برای ایجاد {{domxref("FileWriter")}} فراخوانی می‌شود. این callback یک شیء {{domxref("DOMException")}} را به عنوان ورودی دریافت می‌کند که خطا را توصیف می‌کند.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

## Examples

این مثال یک متد به نام `writeToFileEntry()` ایجاد می‌کند که یک رشته متنی را در فایل متناظر با ورودی دایرکتوری داده‌شده می‌نویسد.

```js
function writeToFileEntry(entry, text) {
  entry.createWriter(
    (fileWriter) => {
      let data = Blob([text], { type: "text/plain" });

      fileWriter.write(data);
    },
    (error) => {
      /* برای مدیریت خطا هر کاری لازم است انجام دهید */
    },
  );
}
```

callback موفقیت برای فراخوانی `createWriter()` متنی را که ارسال شده دریافت کرده و یک شیء جدید {{domxref("Blob")}} از نوع `text/plain` ایجاد می‌کند که حاوی متن ارسالی است. سپس این blob به شیء {{domxref("FileWriter")}} خروجی داده می‌شود تا در فایل نوشته شود.

## Specifications

این ویژگی دیگر بخشی از هیچ مشخصاتی نیست. دیگر در مسیر تبدیل شدن به یک استاندارد قرار ندارد.

## Browser compatibility

{{Compat}}

## See also

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)