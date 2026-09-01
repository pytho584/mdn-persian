---
title: HTMLOutputElement
slug: Web/API/HTMLOutputElement
page-type: web-api-interface
browser-compat: api.HTMLOutputElement
---

{{APIRef("HTML DOM")}}

رابط **`HTMLOutputElement`** ویژگی‌ها و روش‌هایی (فراتر از موارد به‌ارث‌برده از {{domxref("HTMLElement")}}) برای دستکاری چیدمان و نمایش عناصر {{HTMLElement("output")}} فراهم می‌کند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("HTMLOutputElement.HTMLOutputElement", "HTMLOutputElement()")}} {{experimental_inline}}
  - : یک شی `HTMLOutputElement` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌هایی را از والد خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

- {{domxref("HTMLOutputElement.defaultValue")}}
  - : یک رشته که مقدار پیش‌فرض عنصر را نشان می‌دهد، در ابتدا رشتهٔ خالی.
- {{domxref("HTMLOutputElement.form")}} {{ReadOnlyInline}}
  - : یک {{domxref("HTMLFormElement")}} که فرم مرتبط با کنترل را نشان می‌دهد و منعکس‌کنندهٔ ویژگی HTML [`form`](/en-US/docs/Web/HTML/Reference/Elements/output#form) در صورت تعریف شدن است.
- {{domxref("HTMLOutputElement.htmlFor")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMTokenList")}} که منعکس‌کنندهٔ ویژگی HTML [`for`](/en-US/docs/Web/HTML/Reference/Elements/output#for) است و شامل لیستی از شناسه‌های عناصر دیگر در همان سند است که در مقدار محاسبه‌شدهٔ `value` مشارکت دارند (یا به‌نوعی بر آن تأثیر می‌گذارند).
- {{domxref("HTMLOutputElement.labels")}} {{ReadOnlyInline}}
  - : یک {{domxref("NodeList")}} از عناصر {{HTMLElement("label")}} مرتبط با عنصر.
- {{domxref("HTMLOutputElement.name")}}
  - : یک رشته که منعکس‌کنندهٔ ویژگی HTML [`name`](/en-US/docs/Web/HTML/Reference/Elements/output#name) است و حاوی نام کنترلی است که با داده‌های فرم ارسال می‌شود.
- {{domxref("HTMLOutputElement.type")}} {{ReadOnlyInline}}
  - : رشتهٔ `"output"`.
- {{domxref("HTMLOutputElement.validationMessage")}} {{ReadOnlyInline}}
  - : یک رشته که یک پیام بومی‌سازی‌شده را نشان می‌دهد و محدودیت‌های اعتبارسنجی را که کنترل برآورده نمی‌کند (در صورت وجود) توصیف می‌کند. اگر کنترل کاندیدای اعتبارسنجی محدودیت نباشد (`willValidate` برابر `false` باشد) یا محدودیت‌های خود را برآورده کند، این رشته خالی است.
- {{domxref("HTMLOutputElement.validity")}} {{ReadOnlyInline}}
  - : یک {{domxref("ValidityState")}} که وضعیت‌های اعتبار این عنصر را نشان می‌دهد.
- {{domxref("HTMLOutputElement.value")}}
  - : یک رشته که مقدار محتویات عنصر را نشان می‌دهد. مانند ویژگی {{domxref("Node.textContent")}} رفتار می‌کند.
- {{domxref("HTMLOutputElement.willValidate")}} {{ReadOnlyInline}}
  - : یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا عنصر کاندیدای اعتبارسنجی محدودیت است یا خیر. برای اشیاء `HTMLOutputElement` همیشه `false` است.

## روش‌های نمونه

_این رابط همچنین روش‌هایی را از والد خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

- {{domxref("HTMLOutputElement.checkValidity()")}}
  - : اعتبار عنصر را بررسی می‌کند و یک مقدار بولی حاوی نتیجهٔ بررسی برمی‌گرداند.
- {{domxref("HTMLOutputElement.reportValidity()")}}
  - : این روش مشکلات مربوط به محدودیت‌های عنصر (در صورت وجود) را به کاربر گزارش می‌دهد. اگر مشکلی وجود داشته باشد، یک رویداد {{domxref("HTMLInputElement/invalid_event", "invalid")}} در عنصر ایجاد می‌کند و `false` برمی‌گرداند؛ اگر مشکلی نباشد، `true` برمی‌گرداند.

    هنگامی که مشکل گزارش می‌شود، عامل کاربر ممکن است عنصر را متمرکز کرده و موقعیت پیمایش سند را تغییر دهد یا اقدام دیگری انجام دهد که توجه کاربر را به عنصر جلب کند. اگر عنصر از چندین مشکل به‌طور همزمان رنج ببرد، عامل کاربر ممکن است بیش از یک نقض محدودیت را گزارش دهد. اگر عنصر رندر نشود، عامل کاربر ممکن است خطا را برای اسکریپت در حال اجرا گزارش دهد به‌جای اینکه کاربر را مطلع کند.

- {{domxref("HTMLOutputElement.setCustomValidity()")}}
  - : یک پیام اعتبار سفارشی برای عنصر تنظیم می‌کند. اگر این پیام رشتهٔ خالی نباشد، عنصر از یک خطای اعتبار سفارشی رنج می‌برد و اعتبارسنجی نمی‌شود.

## حالت‌ها

این عنصر در یکی از دو حالت عمل می‌کند: _حالت پیش‌فرض_ و _حالت مقدار_.

### حالت پیش‌فرض

در ابتدا، عنصر در حالت پیش‌فرض است، بنابراین محتویات عنصر هم مقدار عنصر و هم مقدار پیش‌فرض آن را نشان می‌دهد.

اگر عنصر در حالت پیش‌فرض باشد و نوادگان عنصر به هر نحوی تغییر کنند، ویژگی `defaultValue` به مقدار ویژگی {{domxref("Node.textContent","textContent")}} تنظیم می‌شود.

بازنشانی فرم، عنصر را به حالت پیش‌فرض برمی‌گرداند و ویژگی {{domxref("Node.textContent","textContent")}} را به مقدار ویژگی `defaultValue` تنظیم می‌کند.

### حالت مقدار

عنصر زمانی وارد حالت مقدار می‌شود که محتویات ویژگی `value` تنظیم شوند. در غیر این صورت ویژگی `value` مانند ویژگی {{domxref("Node.textContent","textContent")}} رفتار می‌کند. هنگامی که عنصر در حالت مقدار است، مقدار پیش‌فرض فقط از طریق ویژگی `defaultValue` قابل دسترسی است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML که این رابط را پیاده‌سازی می‌کند: {{HTMLElement("output")}}.