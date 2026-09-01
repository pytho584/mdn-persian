---
title: "HTMLObjectElement"
---

---
title: HTMLObjectElement
slug: Web/API/HTMLObjectElement
page-type: web-api-interface
browser-compat: api.HTMLObjectElement
---

{{ APIRef("HTML DOM") }}

رابط **`HTMLObjectElement`** ویژگی‌ها و روش‌های خاصی را (فراتر از ویژگی‌هایی که به‌صورت ارث‌بری از رابط {{domxref("HTMLElement")}} در اختیار دارد) برای دستکاری چیدمان و نمایش عنصر {{HTMLElement("object")}} فراهم می‌کند که نمایانگر منابع خارجی است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌های والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

- {{domxref("HTMLObjectElement.align")}} {{deprecated_inline}}
  - : یک رشته که مشخصه‌ای شمارشی را نشان می‌دهد و ترازبندی محتویات عنصر را نسبت به بافت اطراف مشخص می‌کند. مقادیر ممکن عبارت‌اند از `"left"`، `"right"`، `"justify"` و `"center"`.
- {{domxref("HTMLObjectElement.archive")}} {{deprecated_inline}}
  - : یک رشته که ویژگی HTML [`archive`](/en-US/docs/Web/HTML/Reference/Elements/object#archive) را بازتاب می‌دهد و حاوی فهرستی از بایگانی‌ها برای منابع این شیء است.
- {{domxref("HTMLObjectElement.border")}} {{deprecated_inline}}
  - : یک رشته که ویژگی HTML [`border`](/en-US/docs/Web/HTML/Reference/Elements/object#border) را بازتاب می‌دهد و عرض حاشیه دور شیء را مشخص می‌کند.
- {{domxref("HTMLObjectElement.code")}} {{deprecated_inline}}
  - : یک رشته که نام فایل کلاس یک اپلت را نشان می‌دهد و شامل زیرکلاس اپلت یا مسیر رسیدن به کلاس، از جمله خود فایل کلاس است.
- {{domxref("HTMLObjectElement.codeBase")}} {{deprecated_inline}}
  - : یک رشته که ویژگی HTML [`codebase`](/en-US/docs/Web/HTML/Reference/Elements/object#codebase) را بازتاب می‌دهد و مسیر پایه را برای حل کردن URIهای نسبی مشخص می‌کند.
- {{domxref("HTMLObjectElement.codeType")}} {{deprecated_inline}}
  - : یک رشته که ویژگی HTML [`codetype`](/en-US/docs/Web/HTML/Reference/Elements/object#codetype) را بازتاب می‌دهد و نوع محتوای داده را مشخص می‌کند.
- {{domxref("HTMLObjectElement.contentDocument")}} {{ReadOnlyInline}}
  - : یک {{domxref("Document")}} برمی‌گرداند که نمایانگر سند فعالِ بافت مرور تو در توی عنصر object است؛ در صورت نبودِ آن، `null` برمی‌گرداند.
- {{domxref("HTMLObjectElement.contentWindow")}} {{ReadOnlyInline}}
  - : یک {{glossary("WindowProxy")}} برمی‌گرداند که نمایانگر پنجرهٔ proxy بافت مرور تو در توی عنصر object است؛ در صورت نبودِ آن، `null` برمی‌گرداند.
- {{domxref("HTMLObjectElement.data")}}
  - : یک رشته برمی‌گرداند که ویژگی HTML [`data`](/en-US/docs/Web/HTML/Reference/Elements/object#data) را بازتاب می‌دهد و آدرس داده‌های یک منبع را مشخص می‌کند.
- {{domxref("HTMLObjectElement.declare")}} {{deprecated_inline}}
  - : یک مقدار بولین که ویژگی HTML [`declare`](/en-US/docs/Web/HTML/Reference/Elements/object#declare) را بازتاب می‌دهد و نشان می‌دهد که این یک اعلان است، نه نمونه‌سازی، از شیء.
- {{domxref("HTMLObjectElement.form")}} {{ReadOnlyInline}}
  - : یک {{domxref("HTMLFormElement")}} برمی‌گرداند که نمایانگر فرم مالک عنصر object است؛ در صورت نبودِ آن، `null` برمی‌گرداند.
- {{domxref("HTMLObjectElement.height")}}
  - : یک رشته برمی‌گرداند که ویژگی HTML [`height`](/en-US/docs/Web/HTML/Reference/Elements/object#height) را بازتاب می‌دهد و ارتفاع نمایش‌داده‌شده منبع را بر حسب پیکسل CSS مشخص می‌کند.
- {{domxref("HTMLObjectElement.hspace")}} {{deprecated_inline}}
  - : یک `long` که فاصله افقی دور کنترل را بر حسب پیکسل نشان می‌دهد.
- {{domxref("HTMLObjectElement.name")}}
  - : یک رشته برمی‌گرداند که ویژگی HTML [`name`](/en-US/docs/Web/HTML/Reference/Elements/object#name) را بازتاب می‌دهد و نام بافت مرور را مشخص می‌کند.
- {{domxref("HTMLObjectElement.standby")}} {{deprecated_inline}}
  - : یک رشته که ویژگی HTML [`standby`](/en-US/docs/Web/HTML/Reference/Elements/object#standby) را بازتاب می‌دهد و پیامی را مشخص می‌کند که هنگام بارگذاری شیء نمایش داده می‌شود.
- {{domxref("HTMLObjectElement.type")}}
  - : یک رشته که ویژگی HTML [`type`](/en-US/docs/Web/HTML/Reference/Elements/object#type) را بازتاب می‌دهد و نوع MIME منبع را مشخص می‌کند.
- {{domxref("HTMLObjectElement.useMap")}} {{deprecated_inline}}
  - : یک رشته که ویژگی HTML [`usemap`](/en-US/docs/Web/HTML/Reference/Elements/object#usemap) را بازتاب می‌دهد و عنصر {{HTMLElement("map")}} مورد استفاده را مشخص می‌کند.
- {{domxref("HTMLObjectElement.validationMessage")}} {{ReadOnlyInline}}
  - : یک رشته برمی‌گرداند که پیامی محلی‌شده را نشان می‌دهد و محدودیت‌های اعتبارسنجی را توصیف می‌کند که کنترل آن‌ها را برآورده نمی‌کند (در صورت وجود). اگر کنترل کاندیدای اعتبارسنجی محدودیت‌ها نباشد (`willValidate` برابر `false` است) یا محدودیت‌های خود را برآورده کند، این رشته خالی است.
- {{domxref("HTMLObjectElement.validity")}} {{ReadOnlyInline}}
  - : یک {{domxref("ValidityState")}} برمی‌گرداند که حالت‌های اعتبارسنجی این عنصر را نشان می‌دهد.
- {{domxref("HTMLObjectElement.vspace")}} {{deprecated_inline}}
  - : یک `long` که فاصله افقی دور کنترل را بر حسب پیکسل نشان می‌دهد.
- {{domxref("HTMLObjectElement.width")}}
  - : یک رشته که ویژگی HTML [`width`](/en-US/docs/Web/HTML/Reference/Elements/object#width) را بازتاب می‌دهد و عرض نمایش‌داده‌شده منبع را بر حسب پیکسل CSS مشخص می‌کند.
- {{domxref("HTMLObjectElement.willValidate")}} {{ReadOnlyInline}}
  - : یک مقدار بولین برمی‌گرداند که نشان می‌دهد آیا این عنصر کاندیدای اعتبارسنجی محدودیت‌ها است یا خیر. برای اشیاء `HTMLObjectElement` همیشه `false` است.

## روش‌های نمونه

_روش‌های والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

- {{domxref("HTMLObjectElement.checkValidity()")}}
  - : همیشه `true` برمی‌گرداند، زیرا عناصر {{HTMLElement("object")}} هرگز کاندیدای اعتبارسنجی محدودیت‌ها نیستند.
- {{domxref("HTMLObjectElement.getSVGDocument()")}}
  - : SVG تعبیه‌شده را به‌صورت یک {{domxref("Document")}} برمی‌گرداند.
- {{domxref("HTMLObjectElement.reportValidity()")}}
  - : همیشه `true` برمی‌گرداند، زیرا عناصر {{HTMLElement("object")}} هرگز کاندیدای اعتبارسنجی محدودیت‌ها نیستند.
- {{domxref("HTMLObjectElement.setCustomValidity()")}}
  - : یک پیام اعتبارسنجی سفارشی برای عنصر تنظیم می‌کند. اگر این پیام رشته خالی نباشد، عنصر دچار خطای اعتبارسنجی سفارشی است و اعتبارسنجی نمی‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- عنصر HTML پیاده‌ساز این رابط: {{HTMLElement("object")}}