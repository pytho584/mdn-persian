---
title: HTMLTableSectionElement
slug: Web/API/HTMLTableSectionElement
page-type: web-api-interface
browser-compat: api.HTMLTableSectionElement
---

{{ APIRef("HTML DOM") }}

رابط **`HTMLTableSectionElement`** ویژگی‌ها و متدهای خاصی (فراتر از رابط {{domxref("HTMLElement")}} که به‌صورت ارث‌بری در اختیار دارد) برای دستکاری چیدمان و نمایش بخش‌های یک جدول HTML، یعنی سرصفحه‌ها، پاورقی‌ها و بدنه (به‌ترتیب {{HTMLElement("thead")}}، {{HTMLElement("tfoot")}} و {{HTMLElement("tbody")}}) فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌های والد خود، {{domxref("HTMLElement")}}، را به ارث می‌برد._

- {{domxref("HTMLTableSectionElement.align")}} {{deprecated_inline}}
  - : یک رشته حاوی مقدار شمارشی که منعکس‌کننده ویژگی [`align`](/en-US/docs/Web/HTML/Reference/Elements/tr#align) است. تراز شدن محتویات عنصر را نسبت به زمینه پیرامون مشخص می‌کند. مقادیر ممکن عبارتند از `"left"`، `"right"` و `"center"`.
- {{domxref("HTMLTableSectionElement.rows")}} {{ReadOnlyInline}}
  - : یک {{domxref("HTMLCollection")}} زنده حاوی ردیف‌های موجود در بخش را برمی‌گرداند. `HTMLCollection` زنده است و با افزودن یا حذف ردیف‌ها به‌طور خودکار به‌روز می‌شود.
- {{domxref("HTMLTableSectionElement.ch")}} {{deprecated_inline}}
  - : یک رشته حاوی یک کاراکتر واحد. این کاراکتر همانی است که تمام سلول‌های یک ستون بر اساس آن تراز می‌شوند. ویژگی [`char`](/en-US/docs/Web/HTML/Reference/Elements/tr#char) را منعکس می‌کند و به‌طور پیش‌فرض برابر با نقطه اعشاری مرتبط با زبان است، مانند `'.'` برای انگلیسی یا `','` برای فرانسوی. این ویژگی اختیاری بود و پشتیبانی خوبی نداشت.
- {{domxref("HTMLTableSectionElement.chOff")}} {{deprecated_inline}}
  - : یک رشته حاوی یک عدد صحیح که نشان می‌دهد چند کاراکتر باید در سمت راست (برای اسکریپت‌های چپ‌به‌راست؛ یا در سمت چپ برای اسکریپت‌های راست‌به‌چپ) کاراکتر تعریف‌شده توسط `HTMLTableRowElement.ch` باقی بماند. این ویژگی اختیاری بود و پشتیبانی خوبی نداشت.
- {{domxref("HTMLTableSectionElement.vAlign")}} {{deprecated_inline}}
  - : یک رشته نشان‌دهنده یک مقدار شمارشی که نحوه تراز عمودی محتوای سلول را مشخص می‌کند. ویژگی [`valign`](/en-US/docs/Web/HTML/Reference/Elements/tr#valign) را منعکس می‌کند و می‌تواند یکی از مقادیر زیر باشد: `"top"`، `"middle"`، `"bottom"` یا `"baseline"`.

## متدهای نمونه

_متدهای والد خود، {{domxref("HTMLElement")}}، را به ارث می‌برد._

- {{domxref("HTMLTableSectionElement.deleteRow()")}}
  - : ردیف متناظر با `index` داده‌شده در پارامتر را از بخش حذف می‌کند. اگر مقدار `index` برابر `-1` باشد، آخرین ردیف حذف می‌شود؛ اگر کوچک‌تر از `-1` یا بزرگ‌تر از تعداد ردیف‌های مجموعه باشد، یک {{DOMxRef("DOMException")}} با مقدار `IndexSizeError` صادر می‌شود.
- {{domxref("HTMLTableSectionElement.insertRow()")}}
  - : یک {{DOMxRef("HTMLTableRowElement")}} نشان‌دهنده یک ردیف جدید از بخش برمی‌گرداند. آن را در مجموعه ردیف‌ها بلافاصله قبل از عنصر {{HTMLElement("tr")}} در موقعیت `index` داده‌شده درج می‌کند. اگر `index` برابر `-1` باشد، ردیف جدید به انتهای مجموعه اضافه می‌شود. اگر `index` کوچک‌تر از `-1` یا بزرگ‌تر از تعداد ردیف‌های مجموعه باشد، یک {{DOMxRef("DOMException")}} با مقدار `IndexSizeError` صادر می‌شود.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- عناصر HTML که این رابط را پیاده‌سازی می‌کنند: {{HTMLElement("tfoot")}}، {{HTMLElement("thead")}} و {{HTMLElement("tbody")}}.