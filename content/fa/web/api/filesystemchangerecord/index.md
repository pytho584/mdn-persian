---
title: FileSystemChangeRecord
slug: Web/API/FileSystemChangeRecord
page-type: web-api-interface
---

{{APIRef("File System API")}}

دیکشنری **`FileSystemChangeRecord`** از {{domxref("File System API", "File System API", "", "nocode")}} شامل جزئیات یک تغییر واحد است که توسط یک {{domxref("FileSystemObserver")}} مشاهده شده است.

آرگومان `records` که به تابع callback سازندهٔ {{domxref("FileSystemObserver.FileSystemObserver", "FileSystemObserver()")}} ارسال می‌شود، آرایه‌ای از اشیاء `FileSystemChangeRecord` است.

## ویژگی‌های نمونه

- `changedHandle`
  - : ارجاعی به هندل (handle) فایل‌سیستمی که تغییر روی آن مشاهده شده است.
    - برای فایل‌سیستم قابل مشاهده توسط کاربر، این می‌تواند یک {{domxref("FileSystemFileHandle")}} یا {{domxref("FileSystemDirectoryHandle")}} باشد.
    - برای [سیستم فایل خصوصی مبدأ (OPFS)](/en-US/docs/Web/API/File_System_API/Origin_private_file_system)، می‌تواند یک {{domxref("FileSystemFileHandle")}}، {{domxref("FileSystemDirectoryHandle")}} یا {{domxref("FileSystemSyncAccessHandle")}} باشد.

    این ویژگی برای رکوردهایی با نوع `"disappeared"`، `"errored"` یا `"unknown"` برابر با `null` خواهد بود.

- `relativePathComponents`
  - : آرایه‌ای شامل اجزای مسیر که مسیر نسبی فایل را از `root` به `changedHandle` تشکیل می‌دهند، به همراه نام فایل `changedHandle`.

- `relativePathMovedFrom`
  - : آرایه‌ای شامل اجزای مسیر که مسیر نسبی فایل را از `root` به مکان قبلی `changedHandle` می‌سازند، در مورد مشاهدات با نوع `"moved"`. اگر نوع `"moved"` نباشد، این ویژگی برابر با `null` خواهد بود.

- `root`
  - : ارجاعی به هندل ریشهٔ فایل‌سیستم، یعنی همان هندلی که به فراخوانی `observe()` که مشاهده را شروع کرد، منتقل شده است. باز هم، این می‌تواند یک {{domxref("FileSystemFileHandle")}}، {{domxref("FileSystemDirectoryHandle")}} یا {{domxref("FileSystemSyncAccessHandle")}} باشد.

- `type`
  - : رشته‌ای (string) که نوع تغییر مشاهده‌شده را نشان می‌دهد. مقادیر ممکن عبارت‌اند از:
    - `appeared`
      - : فایل یا دایرکتوری ایجاد شده یا به ساختار فایل `root` منتقل شده است.
    - `disappeared`
      - : فایل یا دایرکتوری حذف شده یا از ساختار فایل `root` خارج شده است. برای اینکه بفهمید کدام فایل یا دایرکتوری ناپدید شده، می‌توانید ویژگی `relativePathComponents` را پرس‌وجو کنید.
    - `errored`
      - : یک وضعیت خطا در دایرکتوری مشاهده‌شده رخ داده است. این می‌تواند در موارد زیر رخ دهد:
        - مشاهده دیگر معتبر نیست. این ممکن است زمانی رخ دهد که هندل مشاهده‌شده (یعنی `root` مشاهده) حذف یا منتقل شود. در این حالت، یک مشاهدهٔ `"disappeared"` و سپس یک مشاهدهٔ `"errored"` ثبت خواهد شد. در چنین مواردی، ممکن است بخواهید با استفاده از {{domxref("FileSystemObserver.disconnect()")}} مشاهدهٔ فایل‌سیستم را متوقف کنید.
        - به حداکثر سقف مشاهدات برای هر مبدأ (origin) رسیده است. این سقف به سیستم‌عامل بستگی دارد و از قبل مشخص نیست. اگر این اتفاق بیفتد، سایت ممکن است تصمیم به تلاش مجدد بگیرد، هرچند تضمینی وجود ندارد که سیستم‌عامل منابع کافی را آزاد کرده باشد.
        - مجوز دسترسی به دایرکتوری یا هندل فایل برداشته شده است.
    - `modified`
      - : فایل یا دایرکتوری اصلاح شده است.
    - `moved`
      - : فایل یا دایرکتوری در ساختار فایل ریشه منتقل شده است.
        > [!NOTE]
        > در ویندوز، مشاهدات `"moved"` بین دایرکتوری‌ها پشتیبانی نمی‌شوند. آن‌ها به صورت مشاهدهٔ `"disappeared"` در دایرکتوری مبدأ و مشاهدهٔ `"appeared"` در دایرکتوری مقصد گزارش می‌شوند.
    - `unknown`
      - : نشان می‌دهد که برخی از مشاهدات از دست رفته‌اند. اگر می‌خواهید اطلاعاتی دربارهٔ اینکه در مشاهدات از دست رفته چه چیزی تغییر کرده است به دست آورید، می‌توانید به polling دایرکتوری مشاهده‌شده روی بیاورید.

بسته به سیستم‌عامل، همهٔ مشاهدات با همان سطح از جزئیات گزارش نمی‌شوند؛ برای مثال، زمانی که محتویات یک دایرکتوری به‌صورت بازگشتی تغییر می‌کنند. در بهترین حالت، وب‌سایت یک رکورد تغییر دقیق دریافت می‌کند که شامل نوع تغییر و یک هندل برای مسیر آسیب‌دیده است. در بدترین حالت، وب‌سایت یک رکورد تغییر عمومی‌تر (یعنی از نوع `"unknown"`) دریافت می‌کند که همچنان برای فهمیدن اینکه کدام هندل تغییر کرده، نیاز به پیمایش (enumerate) دایرکتوری دارد.

این هنوز هم نسبت به polling یک بهبود است، زیرا پیمایش دایرکتوری می‌تواند به‌صورت درخواستی (on-demand) از تابع callback آغاز شود، به‌جای اینکه لازم باشد به‌صورت دوره‌ای برای تغییرات polling انجام شود.

## مثال‌ها

### مقداردهی اولیهٔ `FileSystemObserver`

قبل از اینکه بتوانید مشاهدهٔ تغییرات فایل یا دایرکتوری را شروع کنید، باید یک `FileSystemObserver` را برای مدیریت مشاهدات مقداردهی اولیه کنید. این کار با استفاده از سازندهٔ {{domxref("FileSystemObserver.FileSystemObserver", "FileSystemObserver()")}} انجام می‌شود که یک تابع callback به عنوان آرگومان می‌گیرد:

```js
const observer = new FileSystemObserver(callback);
```

متن [تابع callback](/en-US/docs/Web/API/FileSystemObserver/FileSystemObserver#callback) را می‌توان طوری مشخص کرد که مشاهدات تغییرات فایل را به هر شکلی که می‌خواهید برگرداند و پردازش کند. هر شیء داخل آرایهٔ `records` یک شیء `FileSystemChangeRecord` است:

```js
const callback = (records, observer) => {
  for (const record of records) {
    console.log("Change detected:", record);
    const reportContent = `Change observed to ${record.changedHandle.kind} ${record.changedHandle.name}. Type: ${record.type}.`;
    sendReport(reportContent); // Some kind of user-defined reporting function
  }

  observer.disconnect();
};
```

## مشخصات

در حال حاضر بخشی از هیچ مشخصات (specification) نیست. برای PR مرتبط با مشخصات، به [https://github.com/whatwg/fs/pull/165](https://github.com/whatwg/fs/pull/165) مراجعه کنید.

## همچنین ببینید

- سازندهٔ {{domxref("FileSystemObserver.FileSystemObserver", "FileSystemObserver()")}}
- [File System API](/en-US/docs/Web/API/File_System_API)
- [آزمایش origin برای File System Observer API](https://developer.chrome.com/blog/file-system-observer#stop-observing-the-file-system) در developer.chrome.com (۲۰۲۴)