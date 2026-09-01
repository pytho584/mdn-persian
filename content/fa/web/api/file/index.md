---
title: File
slug: Web/API/File
page-type: web-api-interface
browser-compat: api.File
---

{{APIRef("File API")}}{{AvailableInWorkers}}

رابطهٔ **`File`** اطلاعاتی دربارهٔ پرونده‌ها فراهم می‌کند و به جاوااسکریپت در یک صفحهٔ وب اجازه می‌دهد تا به محتوای آن‌ها دسترسی یابد.

اشیاء `File` معمولاً از یک شیء {{DOMxRef("FileList")}} به دست می‌آیند که در نتیجهٔ انتخاب پرونده‌ها توسط کاربر از طریق عنصر {{HTMLElement("input")}} بازگردانده می‌شود، یا از شیء {{DOMxRef("DataTransfer")}} مربوط به عملیات کشیدن و رها کردن.

یک شیء `File` نوعی خاص از {{DOMxRef("Blob")}} است و می‌تواند در هر زمینه‌ای که یک Blob قابل استفاده است به کار رود. به‌ویژه، APIهای زیر هر دو نوع اشیاء `Blob` و `File` را می‌پذیرند:

- {{DOMxRef("FileReader")}}
- {{DOMxRef("URL.createObjectURL_static", "URL.createObjectURL()")}}
- {{DOMxRef("Window.createImageBitmap()")}} و {{DOMxRef("WorkerGlobalScope.createImageBitmap()")}}
- گزینهٔ [`body`](/en-US/docs/Web/API/RequestInit#body) در {{domxref("Window/fetch", "fetch()")}}
- {{DOMxRef("XMLHttpRequest.send()")}}

برای اطلاعات بیشتر و مثال‌ها، [استفاده از پرونده‌ها در برنامه‌های وب](/en-US/docs/Web/API/File_API/Using_files_from_web_applications) را ببینید.

{{InheritanceDiagram}}

## سازنده

- {{DOMxRef("File.File", "File()")}}
  - : یک `File` تازه‌ساخته را برمی‌گرداند.

## ویژگی‌های نمونه

_رابطهٔ `File` همچنین ویژگی‌هایی را از رابطهٔ {{DOMxRef("Blob")}} به ارث می‌برد._

- {{DOMxRef("File.lastModified")}} {{ReadOnlyInline}}
  - : زمان آخرین تغییر پرونده را بر حسب میلی‌ثانیه از مبدأ یونیکس (نیمه‌شب ۱ ژانویهٔ ۱۹۷۰) برمی‌گرداند.
- {{DOMxRef("File.lastModifiedDate")}} {{Deprecated_Inline}} {{ReadOnlyInline}} {{Non-standard_Inline}}
  - : آخرین تاریخ تغییر {{JSxRef("Date")}} پرونده‌ای که شیء `File` به آن ارجاع می‌دهد را برمی‌گرداند.
- {{DOMxRef("File.name")}} {{ReadOnlyInline}}
  - : نام پرونده‌ای که شیء `File` به آن ارجاع می‌دهد را برمی‌گرداند.
- {{DOMxRef("File.webkitRelativePath")}} {{ReadOnlyInline}}
  - : مسیری که URL مربوط به `File` نسبت به آن سنجیده می‌شود را برمی‌گرداند.

## روش‌های نمونه

_رابطهٔ `File` همچنین روش‌هایی را از رابطهٔ {{DOMxRef("Blob")}} به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از پرونده‌ها در برنامه‌های وب](/en-US/docs/Web/API/File_API/Using_files_from_web_applications)
- {{DOMxRef("FileReader")}}