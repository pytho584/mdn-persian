---
title: "File: File() constructor"
short-title: File()
slug: Web/API/File/File
page-type: web-api-constructor
browser-compat: api.File.File
---

{{APIRef("File API")}}{{AvailableInWorkers}}

سازنده **`File()`** یک شیء جدید از نوع {{domxref("File")}} ایجاد می‌کند.

## نحو (Syntax)

```js-nolint
new File(fileBits, fileName)
new File(fileBits, fileName, options)
```

### پارامترها

- `fileBits`
  - : یک شیء تکرارپذیر (iterable) مانند {{jsxref("Array")}}، شامل {{jsxref("ArrayBuffer")}}ها، {{jsxref("TypedArray")}}ها، {{jsxref("DataView")}}ها، {{domxref("Blob")}}ها، رشته‌ها، یا ترکیبی از هر یک از این عناصر که درون {{domxref("File")}} قرار می‌گیرند. توجه داشته باشید که رشته‌ها در اینجا به صورت {{glossary("UTF-8")}} کدگذاری می‌شوند، برخلاف رشته‌های معمول جاوااسکریپت که {{glossary("UTF-16")}} هستند.
- `fileName`
  - : یک رشته که نام فایل یا مسیر فایل را نشان می‌دهد.
- `options` {{optional_inline}}
  - : یک شیء گزینه‌ها که شامل ویژگی‌های اختیاری برای فایل است. گزینه‌های موجود به شرح زیر هستند:
    - `type` {{optional_inline}}
      - : یک رشته که نوع MIME محتوایی را که در فایل قرار می‌گیرد مشخص می‌کند. مقدار پیش‌فرض `""` است.
    - `endings` {{optional_inline}}
      - : نحوه تفسیر کاراکترهای خط جدید (`\n`) درون محتوا، در صورتی که داده‌ها متن باشند. مقدار پیش‌فرض `transparent` است که کاراکترهای خط جدید را بدون تغییر در blob کپی می‌کند. برای تبدیل خطوط جدید به قرارداد محلی سیستم میزبان، مقدار `native` را مشخص کنید.
    - `lastModified` {{optional_inline}}
      - : یک عدد که تعداد میلی‌ثانیه‌های بین مبدأ زمان یونیکس و آخرین زمان تغییر فایل را نشان می‌دهد. مقدار پیش‌فرض {{jsxref("Date.now()")}} است.

## مثال‌ها

```js
const file = new File(["foo"], "foo.txt", {
  type: "text/plain",
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("FileReader")}}
- {{domxref("Blob")}}