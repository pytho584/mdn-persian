---
title: "HTMLTableRowElement"
---

---
title: HTMLTableRowElement
slug: Web/API/HTMLTableRowElement
page-type: web-api-interface
browser-compat: api.HTMLTableRowElement
---

{{ APIRef("HTML DOM") }}

رابط **`HTMLTableRowElement`** ویژگی‌ها و متدهای خاصی را برای دستکاری چیدمان و نمایش ردیف‌ها در یک جدول HTML فراهم می‌کند (علاوه بر رابط {{domxref("HTMLElement")}} که به‌صورت ارث‌بری در اختیار دارد).

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌های والد خود، یعنی {{domxref("HTMLElement")}}، را به ارث می‌برد._

- {{domxref("HTMLTableRowElement.cells")}} {{ReadOnlyInline}}
  - : یک {{domxref("HTMLCollection")}} زنده شامل سلول‌های ردیف را بازمی‌گرداند. `HTMLCollection` زنده است و هنگام افزودن یا حذف سلول‌ها به‌طور خودکار به‌روزرسانی می‌شود.
- {{domxref("HTMLTableRowElement.rowIndex")}} {{ReadOnlyInline}}
  - : عددی را بازمی‌گرداند که موقعیت منطقی ردیف را در کل جدول نشان می‌دهد. اگر ردیف بخشی از جدول نباشد، `-1` بازگردانده می‌شود.
- {{domxref("HTMLTableRowElement.sectionRowIndex")}} {{ReadOnlyInline}}
  - : عددی را بازمی‌گرداند که موقعیت منطقی ردیف را در بخش جدولی که به آن تعلق دارد نشان می‌دهد. اگر ردیف بخشی از هیچ بخشی نباشد، `-1` بازگردانده می‌شود.

## متدهای نمونه

_متدهای والد خود، یعنی {{domxref("HTMLElement")}}، را به ارث می‌برد._

- {{domxref("HTMLTableRowElement.deleteCell()")}}
  - : سلول متناظر با `index` را حذف می‌کند. اگر `index` برابر `-1` باشد، آخرین سلول ردیف حذف می‌شود. اگر `index` کمتر از `-1` یا بیشتر از تعداد سلول‌های مجموعه باشد، یک {{DOMxRef("DOMException")}} با مقدار `IndexSizeError` پرتاب می‌شود.
- {{domxref("HTMLTableRowElement.insertCell()")}}
  - : یک {{domxref("HTMLTableCellElement")}} بازمی‌گرداند که سلول جدیدی از ردیف را نشان می‌دهد. سلول درست قبل از موقعیت `index` در مجموعه سلول‌های ردیف درج می‌شود. اگر `index` برابر `-1` باشد، سلول جدید به انتهای مجموعه اضافه می‌شود. اگر `index` کمتر از `-1` یا بیشتر از تعداد سلول‌های مجموعه باشد، یک {{DOMxRef("DOMException")}} با مقدار `IndexSizeError` پرتاب می‌شود.

## ویژگی‌های منسوخ‌شده

> [!WARNING]
> این ویژگی‌ها منسوخ شده‌اند و دیگر نباید استفاده شوند. مستند کردن آن‌ها عمدتاً برای کمک به درک پایگاه‌های کد قدیمی است.

- {{domxref("HTMLTableRowElement.align")}} {{deprecated_inline}}
  - : رشته‌ای حاوی یک مقدار شمارشی که ویژگی [`align`](/en-US/docs/Web/HTML/Reference/Elements/tr#align) را بازتاب می‌دهد. تراز بودن محتویات عنصر را نسبت به بافت اطراف نشان می‌دهد. مقادیر ممکن عبارت‌اند از `"left"`, `"right"` و `"center"`.
- {{domxref("HTMLTableRowElement.bgColor")}} {{deprecated_inline}}
  - : رشته‌ای حاوی رنگ پس‌زمینه سلول‌ها. ویژگی منسوخ [`bgColor`](/en-US/docs/Web/HTML/Reference/Elements/tr#bgcolor) را بازتاب می‌دهد.
- {{domxref("HTMLTableRowElement.ch")}} {{deprecated_inline}}
  - : رشته‌ای حاوی یک کاراکتر واحد. این کاراکتر، کاراکتری است که همه سلول‌های یک ستون بر اساس آن تراز می‌شوند. ویژگی [`char`](/en-US/docs/Web/HTML/Reference/Elements/tr#char) را بازتاب می‌دهد و به‌طور پیش‌فرض روی ممیز اعشاری مرتبط با زبان تنظیم می‌شود، مثلاً `'.'` برای انگلیسی یا `','` برای فرانسوی. این ویژگی اختیاری بود و پشتیبانی خوبی از آن نمی‌شد.
- {{domxref("HTMLTableRowElement.chOff")}} {{deprecated_inline}}
  - : رشته‌ای حاوی یک عدد صحیح که مشخص می‌کند چند کاراکتر باید در سمت راست (برای نوشتن‌های چپ‌به‌راست؛ یا در سمت چپ برای نوشتن‌های راست‌به‌چپ) کاراکتر تعریف‌شده با `HTMLTableRowElement.ch` باقی بماند. این ویژگی اختیاری بود و پشتیبانی خوبی از آن نمی‌شد.
- {{domxref("HTMLTableRowElement.vAlign")}} {{deprecated_inline}}
  - : رشته‌ای که یک مقدار شمارشی را نشان می‌دهد و نحوه تراز عمودی محتوای سلول را تعیین می‌کند. ویژگی [`valign`](/en-US/docs/Web/HTML/Reference/Elements/tr#valign) را بازتاب می‌دهد و می‌تواند یکی از مقادیر زیر باشد: `"top"`, `"middle"`, `"bottom"` یا `"baseline"`.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML که این رابط را پیاده‌سازی می‌کند: {{HTMLElement("tr")}}.