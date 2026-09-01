---
title: "File and Directory Entries API"
slug: Web/API/File_and_Directory_Entries_API
page-type: web-api-overview
browser-compat: api.FileSystem
---

{{DefaultAPISidebar("File and Directory Entries API")}}

File and Directory Entries API روشی را برای پردازش پوشه‌ها و فهرست‌های فایلی فراهم می‌کند که کاربر از طریق یک ورودی فرم یا عملیات کشیدن‑و‑رها کردن ارائه می‌دهد. این API نسخه‌ی پیشرفته‌تری از [File API](/en-US/docs/Web/API/File) است که به شما امکان می‌دهد با یک فایل واحد کار کنید. در ابتدا قرار بود از یک سیستم فایل مجازی کامل پشتیبانی کند، اما اکنون فقط از عملیات خواندن روی داده‌های ارائه‌شده توسط کاربر پشتیبانی می‌کند.

برای مقایسه‌ی این API با [File System API](/en-US/docs/Web/API/File_System_API) و [File API](/en-US/docs/Web/API/File_API)، به [رابطه با سایر APIهای مرتبط با فایل](/en-US/docs/Web/API/File_API#relationship_to_other_file-related_apis) مراجعه کنید.

## دسترسی به یک سیستم فایل

دو راه برای دسترسی به سیستم‌های فایل تعریف‌شده در پیش‌نویس فعلی مشخصات وجود دارد:

- هنگام مدیریت رویداد {{domxref("HTMLElement/drop_event", "drop")}} برای کشیدن‑و‑رها کردن، می‌توانید {{domxref("DataTransferItem.webkitGetAsEntry()")}} را فراخوانی کنید تا {{domxref("FileSystemEntry")}} مربوط به آیتم رهاشده را دریافت کنید. اگر نتیجه `null` نباشد، آن آیتم یک فایل یا پوشه‌ی رهاشده است و می‌توانید از فراخوانی‌های سیستم فایل برای کار با آن استفاده کنید.
- ویژگی {{domxref("HTMLInputElement.webkitEntries")}} به شما امکان می‌دهد به اشیاء {{domxref("FileSystemFileEntry")}} مربوط به فایل‌های انتخاب‌شده‌ی فعلی دسترسی پیدا کنید، اما فقط در صورتی که آن فایل‌ها با کشیدن‑و‑رها کردن روی انتخاب‌گر فایل رها شده باشند ([باگ 1326031 فایرفاکس](https://bugzil.la/1326031)). اگر {{domxref("HTMLInputElement.webkitdirectory")}} برابر با `true` باشد، عنصر {{HTMLElement("input")}} به جای آن یک انتخاب‌گر پوشه است و برای هر پوشه‌ی انتخاب‌شده، اشیاء {{domxref("FileSystemDirectoryEntry")}} دریافت می‌کنید.

## تاریخچه

API سیستم فایل اصلی برای این ایجاد شد که مرورگرها بتوانند از دسترسی به یک سیستم فایل مجازی sandbox شده روی حافظه‌ی کاربر پشتیبانی کنند. کار بر روی استانداردسازی این مشخصات در سال ۲۰۱۲ متوقف شد، اما در آن زمان، گوگل کروم پیاده‌سازی مخصوص خودش از این API را داشت. با گذشت زمان، تعدادی از وب‌سایت‌ها و برنامه‌های وب محبوب شروع به استفاده از آن کردند، اغلب بدون ارائه‌ی هیچ راهکاری برای بازگشت به APIهای استاندارد یا حتی بررسی اینکه API قبل از استفاده در دسترس است. موزیلا در عوض تصمیم گرفت APIهای دیگری را پیاده‌سازی کند که می‌توانند بسیاری از همان مشکلات را حل کنند، مانند [IndexedDB](/en-US/docs/Web/API/IndexedDB_API)؛ برای اطلاعات بیشتر به پست وبلاگ [چرا Firefox فاقد FileSystem API است؟](https://hacks.mozilla.org/2012/07/why-no-filesystem-api-in-firefox/) مراجعه کنید.

در نتیجه، تعدادی از وب‌سایت‌های محبوب در مرورگرهایی غیر از کروم به درستی کار نمی‌کردند. برای حل این مشکل، ویژگی‌هایی از API گوگل که درباره‌ی آنها اجماع حاصل شده بود به عنوان File and Directory Entries API استاندارد شد و سپس در سایر مرورگرها پیاده‌سازی گردید.

## رابط‌ها

File and Directory Entries API شامل رابط‌های زیر است:

- {{domxref("FileSystem")}}
  - : یک سیستم فایل را نمایش می‌دهد.
- {{domxref("FileSystemEntry")}}
  - : رابط پایه‌ای که یک ورودی واحد در یک سیستم فایل را نمایش می‌دهد. این رابط توسط رابط‌های دیگری که فایل‌ها یا پوشه‌ها را نشان می‌دهند پیاده‌سازی می‌شود.
- {{domxref("FileSystemFileEntry")}}
  - : یک فایل واحد را در یک سیستم فایل نمایش می‌دهد.
- {{domxref("FileSystemDirectoryEntry")}}
  - : یک پوشه‌ی واحد را در یک سیستم فایل نمایش می‌دهد.
- {{domxref("FileSystemDirectoryReader")}}
  - : با فراخوانی {{domxref("FileSystemDirectoryEntry.createReader()")}} ایجاد می‌شود. این رابط قابلیت خواندن محتویات یک پوشه را فراهم می‌کند.

### افزونه‌های مربوط به سایر رابط‌ها

- {{domxref("DataTransferItem.webkitGetAsEntry()")}}
  - : یک شیء مبتنی بر {{domxref("FileSystemEntry")}} برمی‌گرداند که ورودی فایل انتخاب‌شده را در سیستم فایل خودش نمایش می‌دهد. این شیء معمولاً یک {{domxref("FileSystemFileEntry")}} یا {{domxref("FileSystemDirectoryEntry")}} خواهد بود.
- {{domxref("File.webkitRelativePath")}}
  - : مسیری را برمی‌گرداند که URL فایل نسبت به آن قرار دارد.
- {{domxref("HTMLInputElement.webkitdirectory")}}
  - : یک مقدار بولی که ویژگی [`webkitdirectory`](/en-US/docs/Web/HTML/Reference/Elements/input#webkitdirectory) را نشان می‌دهد. اگر `true` باشد، رابط انتخاب‌گر سیستم فایل فقط پوشه‌ها را می‌پذیرد، نه فایل‌ها را.
- {{domxref("HTMLInputElement.webkitEntries")}}
  - : فایل‌ها یا پوشه‌های انتخاب‌شده‌ی فعلی را توصیف می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File API](/en-US/docs/Web/API/File_API)
- [File System API](/en-US/docs/Web/API/File_System_API)