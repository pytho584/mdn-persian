---
title: "Blob: slice() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Blob/slice"
translated_by: "n8n + AI"
---

---
title: "Blob: slice() method"
short-title: slice()
slug: Web/API/Blob/slice
page-type: web-api-instance-method
browser-compat: api.Blob.slice
---

{{APIRef("File API")}}{{AvailableInWorkers}}

متد **`slice()`** از رابط {{domxref("Blob")}} یک شیء جدید `Blob` ایجاد و بازمی‌گرداند که حاوی داده‌هایی از زیرمجموعه‌ای از blob است که روی آن فراخوانی شده است.

## نحو

```js-nolint
slice()
slice(start)
slice(start, end)
slice(start, end, contentType)
```

### پارامترها

- `start` {{optional_inline}}
  - : یک شاخص در {{domxref("Blob")}} که اولین بایتی را که باید در {{domxref("Blob")}} جدید گنجانده شود مشخص می‌کند. اگر مقدار منفی تعیین کنید، به عنوان فاصله‌ای از انتهای {{domxref("Blob")}} به سمت ابتدا در نظر گرفته می‌شود. برای مثال، 10- دهمین بایت از انتهای {{domxref("Blob")}} خواهد بود. مقدار پیش‌فرض 0 است. اگر مقداری برای `start` بزرگ‌تر از اندازه {{domxref("Blob")}} منبع مشخص کنید، {{domxref("Blob")}} بازگشتی اندازه 0 دارد و هیچ داده‌ای ندارد.
- `end` {{optional_inline}}
  - : یک شاخص در {{domxref("Blob")}} که اولین بایتی را مشخص می‌کند که در {{domxref("Blob")}} جدید _شامل_ _نخواهد_ شد (یعنی بایت دقیقاً در این شاخص شامل نمی‌شود). اگر مقدار منفی تعیین کنید، به عنوان فاصله‌ای از انتهای {{domxref("Blob")}} به سمت ابتدا در نظر گرفته می‌شود. برای مثال، 10- دهمین بایت از انتهای {{domxref("Blob")}} خواهد بود. مقدار پیش‌فرض `size` است.
- `contentType` {{optional_inline}}
  - : نوع محتوایی که به {{domxref("Blob")}} جدید اختصاص داده می‌شود؛ این مقدار، مقدار ویژگی `type` آن خواهد بود. مقدار پیش‌فرض یک رشته خالی است.

### مقدار بازگشتی

یک شیء جدید {{domxref("Blob")}} حاوی زیرمجموعه مشخص‌شده‌ای از داده‌های موجود در blob که این متد روی آن فراخوانی شده است. blob اصلی تغییری نمی‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Blob")}}
- [استفاده از فایل‌ها در برنامه‌های وب](/en-US/docs/Web/API/File_API/Using_files_from_web_applications)