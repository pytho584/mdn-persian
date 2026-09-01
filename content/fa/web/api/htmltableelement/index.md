---
title: "HTMLTableElement"
slug: Web/API/HTMLTableElement
page-type: web-api-interface
browser-compat: api.HTMLTableElement
---

{{APIRef("HTML DOM")}}

رابط **`HTMLTableElement`** ویژگی‌ها و روش‌های ویژه‌ای (فراتر از رابط شیء {{DOMxRef("HTMLElement")}} که به طور ارث‌بری در دسترس است) برای دستکاری طرح و نمایش جدول‌ها در یک سند HTML ارائه می‌دهد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌های والد خود، {{DOMxRef("HTMLElement")}} را به ارث می‌برد._

- {{DOMxRef("HTMLTableElement.caption")}}
  - : یک {{DOMxRef("HTMLTableCaptionElement")}} که اولین {{HTMLElement("caption")}} فرزند این عنصر را نشان می‌دهد، یا اگر وجود نداشته باشد، `null` را برمی‌گرداند. هنگام تنظیم، اگر شیء یک `<caption>` را نشان ندهد، یک {{DOMxRef("DOMException")}} با نام `HierarchyRequestError` پرتاب می‌شود. اگر یک شیء صحیح داده شود، به عنوان اولین فرزند این عنصر در درخت درج می‌شود و اولین `<caption>` که فرزند این عنصر است (در صورت وجود) از درخت حذف می‌شود.
- {{DOMxRef("HTMLTableElement.tHead")}}
  - : یک {{DOMxRef("HTMLTableSectionElement")}} که اولین {{HTMLElement("thead")}} فرزند این عنصر را نشان می‌دهد، یا اگر وجود نداشته باشد، `null` را برمی‌گرداند. هنگام تنظیم، اگر شیء یک `<thead>` را نشان ندهد، یک {{DOMxRef("DOMException")}} با نام `HierarchyRequestError` پرتاب می‌شود. اگر یک شیء صحیح داده شود، بلافاصله قبل از اولین عنصری که نه {{HTMLElement("caption")}} است و نه {{HTMLElement("colgroup")}} در درخت درج می‌شود، یا اگر چنین عنصری وجود نداشته باشد، به عنوان آخرین فرزند درج می‌شود، و اولین `<thead>` که فرزند این عنصر است (در صورت وجود) از درخت حذف می‌شود.
- {{DOMxRef("HTMLTableElement.tFoot")}}
  - : یک {{DOMxRef("HTMLTableSectionElement")}} که اولین {{HTMLElement("tfoot")}} فرزند این عنصر را نشان می‌دهد، یا اگر وجود نداشته باشد، `null` را برمی‌گرداند. هنگام تنظیم، اگر شیء یک `<tfoot>` را نشان ندهد، یک {{DOMxRef("DOMException")}} با نام `HierarchyRequestError` پرتاب می‌شود. اگر یک شیء صحیح داده شود، بلافاصله قبل از اولین عنصری که نه {{HTMLElement("caption")}} است، نه {{HTMLElement("colgroup")}} و نه {{HTMLElement("thead")}} در درخت درج می‌شود، یا اگر چنین عنصری وجود نداشته باشد، به عنوان آخرین فرزند درج می‌شود، و اولین `<tfoot>` که فرزند این عنصر است (در صورت وجود) از درخت حذف می‌شود.
- {{DOMxRef("HTMLTableElement.rows")}} {{ReadOnlyInline}}
  - : یک {{DOMxRef("HTMLCollection")}} زنده برمی‌گرداند که شامل تمام ردیف‌های این عنصر است، یعنی تمام {{HTMLElement("tr")}}هایی که فرزند این عنصر هستند یا فرزند یکی از فرزندان {{HTMLElement("thead")}}، {{HTMLElement("tbody")}} و {{HTMLElement("tfoot")}} آن هستند. اعضای ردیف یک `<thead>` ابتدا، به ترتیب درخت، و اعضای یک `<tbody>` در آخر، همچنین به ترتیب درخت ظاهر می‌شوند. `HTMLCollection` زنده است و هنگام تغییر `HTMLTableElement` به طور خودکار به‌روز می‌شود.
- {{DOMxRef("HTMLTableElement.tBodies")}} {{ReadOnlyInline}}
  - : یک {{DOMxRef("HTMLCollection")}} زنده برمی‌گرداند که شامل تمام {{HTMLElement("tbody")}}های این عنصر است. `HTMLCollection` زنده است و هنگام تغییر `HTMLTableElement` به طور خودکار به‌روز می‌شود.

### ویژگی‌های منسوخ

> [!WARNING]
> ویژگی‌های زیر منسوخ شده‌اند. باید از استفاده از آن‌ها خودداری کنید.

- {{DOMxRef("HTMLTableElement.align")}} {{deprecated_inline}}
  - : یک رشته حاوی یک مقدار شمارشی که منعکس‌کننده ویژگی [`align`](/en-US/docs/Web/HTML/Reference/Elements/table#align) است. تراز محتوای عنصر را نسبت به بافت اطراف نشان می‌دهد. مقادیر ممکن عبارتند از `"left"`, `"right"` و `"center"`.
- {{DOMxRef("HTMLTableElement.bgColor")}} {{deprecated_inline}}
  - : یک رشته حاوی رنگ پس‌زمینه سلول‌ها. ویژگی منسوخ [`bgColor`](/en-US/docs/Web/HTML/Reference/Elements/table#bgcolor) را منعکس می‌کند.
- {{DOMxRef("HTMLTableElement.border")}} {{deprecated_inline}}
  - : یک رشته حاوی عرض border جدول بر حسب پیکسل. ویژگی منسوخ [`border`](/en-US/docs/Web/HTML/Reference/Elements/table#border) را منعکس می‌کند.
- {{DOMxRef("HTMLTableElement.cellPadding")}} {{deprecated_inline}}
  - : یک رشته حاوی عرض فضای افقی و عمودی بین محتوای سلول و borderهای سلول بر حسب پیکسل. ویژگی منسوخ [`cellpadding`](/en-US/docs/Web/HTML/Reference/Elements/table#cellpadding) را منعکس می‌کند.
- {{DOMxRef("HTMLTableElement.cellSpacing")}} {{deprecated_inline}}
  - : یک رشته حاوی عرض جداسازی افقی و عمودی بین سلول‌ها بر حسب پیکسل. ویژگی منسوخ [`cellspacing`](/en-US/docs/Web/HTML/Reference/Elements/table#cellspacing) را منعکس می‌کند.
- {{DOMxRef("HTMLTableElement.frame")}} {{deprecated_inline}}
  - : یک رشته حاوی نوع borderهای خارجی جدول. ویژگی منسوخ [`frame`](/en-US/docs/Web/HTML/Reference/Elements/table#frame) را منعکس می‌کند و می‌تواند یکی از مقادیر زیر را داشته باشد: `"void"`, `"above"`, `"below"`, `"hsides"`, `"vsides"`, `"lhs"`, `"rhs"`, `"box"` یا `"border"`.
- {{DOMxRef("HTMLTableElement.rules")}} {{deprecated_inline}}
  - : یک رشته حاوی نوع borderهای داخلی جدول. ویژگی منسوخ [`rules`](/en-US/docs/Web/HTML/Reference/Elements/table#rules) را منعکس می‌کند و می‌تواند یکی از مقادیر زیر را داشته باشد: `"none"`, `"groups"`, `"rows"`, `"cols"` یا `"all"`.
- {{DOMxRef("HTMLTableElement.summary")}} {{deprecated_inline}}
  - : یک رشته حاوی توضیحی در مورد هدف یا ساختار جدول. ویژگی منسوخ [`summary`](/en-US/docs/Web/HTML/Reference/Elements/table#summary) را منعکس می‌کند.
- {{DOMxRef("HTMLTableElement.width")}} {{deprecated_inline}}
  - : یک رشته حاوی طول بر حسب پیکسل یا درصد از عرض مورد نظر کل جدول. ویژگی منسوخ [`width`](/en-US/docs/Web/HTML/Reference/Elements/table#width) را منعکس می‌کند.

## روش‌های نمونه

_روش‌های والد خود، {{DOMxRef("HTMLElement")}} را به ارث می‌برد._

- {{DOMxRef("HTMLTableElement.createTHead()")}}
  - : یک {{DOMxRef("HTMLTableSectionElement")}} برمی‌گرداند که اولین {{HTMLElement("thead")}} فرزند این عنصر را نشان می‌دهد. اگر هیچ‌کدام یافت نشود، یک مورد جدید ایجاد می‌شود و بلافاصله قبل از اولین عنصری که نه {{HTMLElement("caption")}} است و نه {{HTMLElement("colgroup")}} در درخت درج می‌شود، یا اگر چنین عنصری وجود نداشته باشد، به عنوان آخرین فرزند درج می‌شود.
- {{DOMxRef("HTMLTableElement.deleteTHead()")}}
  - : اولین {{HTMLElement("thead")}} که فرزند این عنصر است را حذف می‌کند.
- {{DOMxRef("HTMLTableElement.createTFoot()")}}
  - : یک {{DOMxRef("HTMLTableSectionElement")}} برمی‌گرداند که اولین {{HTMLElement("tfoot")}} فرزند این عنصر را نشان می‌دهد. اگر هیچ‌کدام یافت نشود، یک مورد جدید ایجاد می‌شود و به عنوان آخرین فرزند در درخت درج می‌شود.
- {{DOMxRef("HTMLTableElement.deleteTFoot()")}}
  - : اولین {{HTMLElement("tfoot")}} که فرزند این عنصر است را حذف می‌کند.
- {{DOMxRef("HTMLTableElement.createTBody()")}}
  - : یک {{DOMxRef("HTMLTableSectionElement")}} برمی‌گرداند که یک {{HTMLElement("tbody")}} جدید را نشان می‌دهد که فرزند این عنصر است. این عنصر بعد از آخرین عنصری که یک {{HTMLElement("tbody")}} است در درخت درج می‌شود، یا اگر چنین عنصری وجود نداشته باشد، به عنوان آخرین فرزند درج می‌شود.
- {{DOMxRef("HTMLTableElement.createCaption()")}}
  - : یک {{DOMxRef("HTMLElement")}} برمی‌گرداند که اولین {{HTMLElement("caption")}} فرزند این عنصر را نشان می‌دهد. اگر هیچ‌کدام یافت نشود، یک مورد جدید ایجاد می‌شود و به عنوان اولین فرزند عنصر {{HTMLElement("table")}} در درخت درج می‌شود.
- {{DOMxRef("HTMLTableElement.deleteCaption()")}}
  - : اولین {{HTMLElement("caption")}} که فرزند این عنصر است را حذف می‌کند.
- {{DOMxRef("HTMLTableElement.insertRow()")}}
  - : یک {{DOMxRef("HTMLTableRowElement")}} برمی‌گرداند که یک ردیف جدید از جدول را نشان می‌دهد. آن را در مجموعه ردیف‌ها بلافاصله قبل از عنصر {{HTMLElement("tr")}} در موقعیت `index` داده شده درج می‌کند. در صورت لزوم یک {{HTMLElement("tbody")}} ایجاد می‌شود. اگر `index` برابر `-1` باشد، ردیف جدید به انتهای مجموعه اضافه می‌شود. اگر `index` کوچکتر از `-1` یا بزرگتر از تعداد ردیف‌های مجموعه باشد، یک {{DOMxRef("DOMException")}} با مقدار `IndexSizeError` پرتاب می‌شود.
- {{DOMxRef("HTMLTableElement.deleteRow()")}}
  - : ردیف مربوط به `index` داده شده در پارامتر را حذف می‌کند. اگر مقدار `index` برابر `-1` باشد، آخرین ردیف حذف می‌شود؛ اگر کوچکتر از `-1` یا بزرگتر از تعداد ردیف‌های مجموعه باشد، یک {{DOMxRef("DOMException")}} با مقدار `IndexSizeError` پرتاب می‌شود.

## مثال‌ها

### استفاده از رابط DOM جدول

رابط `HTMLTableElement` برخی روش‌های راحت برای ایجاد و دستکاری جدول‌ها فراهم می‌کند. دو روش پرکاربرد {{domxref("HTMLTableElement.insertRow")}} و {{domxref("HTMLTableRowElement.insertCell")}} هستند.

برای افزودن یک ردیف و چند سلول به یک جدول موجود:

```html
<table id="table0">
  <tbody>
    <tr>
      <td>ردیف 0 سلول 0</td>
      <td>ردیف 0 سلول 1</td>
    </tr>
  </tbody>
</table>
```

```js
const table = document.getElementById("table0");
const row = table.insertRow(-1);

for (let i = 0; i < 2; i++) {
  const cell = row.insertCell(-1);
  const text = `ردیف ${row.rowIndex} سلول ${i}`;
  cell.appendChild(document.createTextNode(text));
}
```

{{EmbedLiveSample("using_the_dom_table_interface", "", "300")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML که این رابط را پیاده‌سازی می‌کند: {{HTMLElement("table")}}.