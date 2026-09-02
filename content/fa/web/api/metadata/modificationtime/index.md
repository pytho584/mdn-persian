---
title: "Metadata: modificationTime property"
short-title: modificationTime
slug: Web/API/Metadata/modificationTime
page-type: web-api-instance-property
status:
  - experimental
  - non-standard
browser-compat: api.Metadata.modificationTime
---

{{APIRef("File and Directory Entries API")}}{{Non-standard_header}}{{SeeCompatTable}}

خاصیت فقط خواندنی **`modificationTime`** از رابط {{domxref("Metadata")}} یک شیء {{jsxref("Date")}} است که تاریخ و زمان آخرین تغییر ورودی سیستم فایل (یا داده‌های ارجاع‌شده توسط آن ورودی) را مشخص می‌کند. یک ورودی سیستم فایل در صورتی تغییر یافته محسوب می‌شود که فراداده‌ها یا محتویات فایل (یا دایرکتوری، یا هر نوع دیگری از ورودی سیستم فایل که ممکن است روی پلتفرم مورد استفاده وجود داشته باشد) تغییر کرده باشد.

## مقدار

یک نشان زمانی {{jsxref("Date")}} که زمان آخرین تغییر ورودی سیستم فایل را نشان می‌دهد.

## مثال‌ها

این مثال سعی می‌کند یک فایل کاری خاص را در `tmp/work-file.json` دریافت کند. پس از پیدا شدن آن فایل، فراداده‌های آن به دست آمده و سال تغییرات فایل با سال جاری مقایسه می‌شود. اگر آخرین تغییر آن در سالی حداقل پنج سال قبل از سال جاری بوده باشد، فایل حذف شده و یک فایل جدید ایجاد می‌شود.

```js
workingDirectory.getFile(
  "tmp/work-file.json",
  { create: true },
  (fileEntry) => {
    fileEntry.getMetadata((metadata) => {
      if (
        new Date().getFullYear() - metadata.modificationTime.getFullYear() >=
        5
      ) {
        fileEntry.remove(() => {
          workingDirectory.getFile(
            "tmp/work-file.json",
            { create: true },
            (newEntry) => {
              fileEntry = newEntry;
            },
          );
        });
      }
    });
  },
  handleError,
);
```

## مشخصات

این ویژگی از تمام مشخصات حذف شده است و در فرآیند استانداردسازی قرار ندارد.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("Metadata")}}
- {{domxref("FileSystemEntry.getMetadata()")}}
- {{domxref("FileSystemFileEntry")}}