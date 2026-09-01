```markdown
---
title: FileReaderSync
slug: Web/API/FileReaderSync
page-type: web-api-interface
browser-compat: api.FileReaderSync
---

{{APIRef("File API")}} {{AvailableInWorkers("worker_except_service")}}

رابط **`FileReaderSync`** امکان خواندن همزمان (synchronous) اشیاء {{DOMxRef("File")}} یا {{DOMxRef("Blob")}} را فراهم می‌کند. این رابط [تنها در workerها](/en-US/docs/Web/API/Web_Workers_API/Functions_and_classes_available_to_workers) در دسترس است، زیرا I/O همزمان را ممکن می‌سازد که می‌تواند باعث مسدود شدن شود.

## سازنده

- {{domxref("FileReaderSync.FileReaderSync", "FileReaderSync()")}}
  - : یک شیء جدید `FileReaderSync` برمی‌گرداند.

## ویژگی‌های نمونه

این رابط هیچ ویژگی ندارد.

## روش‌های نمونه

- {{DOMxRef("FileReaderSync.readAsArrayBuffer","FileReaderSync.readAsArrayBuffer()")}}
  - : این روش یک {{DOMxRef("Blob")}} یا {{DOMxRef("File")}} مشخص را به یک {{jsxref("ArrayBuffer")}} تبدیل می‌کند که داده‌های ورودی را به صورت یک رشته دودویی (binary string) نمایش می‌دهد.
- {{DOMxRef("FileReaderSync.readAsBinaryString","FileReaderSync.readAsBinaryString()")}} {{deprecated_inline}}
  - : این روش یک {{DOMxRef("Blob")}} یا {{DOMxRef("File")}} مشخص را به یک رشته (string) تبدیل می‌کند که داده‌های ورودی را به صورت یک رشته دودویی نمایش می‌دهد. این روش منسوخ (deprecated) شده است؛ به جای آن از `readAsArrayBuffer()` استفاده کنید.
- {{DOMxRef("FileReaderSync.readAsText","FileReaderSync.readAsText()")}}
  - : این روش یک {{DOMxRef("Blob")}} یا {{DOMxRef("File")}} مشخص را به یک رشته (string) تبدیل می‌کند که داده‌های ورودی را به صورت یک رشته متنی نمایش می‌دهد. پارامتر اختیاری **`encoding`** مشخص‌کننده رمزگذاری مورد استفاده است (مثلاً iso-8859-1 یا UTF-8). اگر وجود نداشته باشد، روش یک الگوریتم تشخیص برای آن اعمال خواهد کرد.
- {{DOMxRef("FileReaderSync.readAsDataURL","FileReaderSync.readAsDataURL()")}}
  - : این روش یک {{DOMxRef("Blob")}} یا {{DOMxRef("File")}} مشخص را به یک رشته (string) تبدیل می‌کند که داده‌های ورودی را به صورت یک URL داده (data URL) نمایش می‌دهد.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("FileReader")}}
- {{DOMxRef("Blob")}}
- {{DOMxRef("File")}}
```