---
title: "Clipboard"
slug: Web/API/Clipboard
page-type: web-api-interface
browser-compat: api.Clipboard
---

{{APIRef("Clipboard API")}}{{SecureContext_Header}}

رابطهٔ **`Clipboard`** در [Clipboard API](/en-US/docs/Web/API/Clipboard_API) دسترسی خواندن و نوشتن به محتویات کلیپبورد سیستمی را فراهم میکند. این امکان را به برنامههای وب میدهد تا ویژگیهای بریدن، کپی کردن و چسباندن را پیادهسازی کنند.

{{InheritanceDiagram}}

کلیپبورد سیستمی از طریق ویژگی سراسری {{domxref("Navigator.clipboard")}} در دسترس قرار میگیرد.

همهٔ متدهای Clipboard API بهصورت غیرهمزمان عمل میکنند؛ آنها یک {{jsxref("Promise")}} برمیگردانند که پس از تکمیل دسترسی به کلیپبورد resolve میشود. اگر دسترسی به کلیپبورد رد شود، این promise رد میشود.

همهٔ متدها به یک [زمینهٔ امن](/en-US/docs/Web/Security/Defenses/Secure_Contexts) نیاز دارند. الزامات اضافی برای استفاده از این API در بخش [ملاحظات امنیتی](/en-US/docs/Web/API/Clipboard_API#security_considerations) در نمای کلی این API بحث شده است.

## روشهای نمونه

_`Clipboard` بر اساس رابط {{domxref("EventTarget")}} ساخته شده و شامل روشهای آن است._

- {{domxref("Clipboard.read()","read()")}}
  - : دادههای دلخواه (مانند تصاویر) را از کلیپبورد درخواست میکند و یک {{jsxref("Promise")}} برمیگرداند که با آرایهای از اشیاء {{domxref("ClipboardItem")}} حاوی محتویات کلیپبورد resolve میشود.
- {{domxref("Clipboard.readText()","readText()")}}
  - : متن را از کلیپبورد سیستمی درخواست میکند و یک {{jsxref("Promise")}} برمیگرداند که پس از آماده شدن، با یک رشته حاوی متن کلیپبورد fulfilled میشود.
- {{domxref("Clipboard.write()","write()")}}
  - : دادههای دلخواه را در کلیپبورد سیستمی مینویسد و یک {{jsxref("Promise")}} برمیگرداند که پس از تکمیل عملیات resolve میشود.
- {{domxref("Clipboard.writeText()","writeText()")}}
  - : متن را در کلیپبورد سیستمی مینویسد و یک {{jsxref("Promise")}} برمیگرداند که وقتی متن بهطور کامل در کلیپبورد کپی شد resolve میشود.

## رویدادها

- {{domxref("Clipboard.clipboardchange_event","clipboardchange")}} {{experimental_inline}}
  - : زمانی رخ میدهد که محتویات کلیپبورد سیستمی به هر شکلی تغییر کند، مثلاً از طریق یک دستور کپی سیستمی یا از طریق یک متد API مانند {{domxref("Clipboard.writeText()")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document.execCommand()")}}