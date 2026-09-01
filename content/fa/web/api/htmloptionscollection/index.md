---
title: "HTMLOptionsCollection"
---

---
title: HTMLOptionsCollection
slug: Web/API/HTMLOptionsCollection
page-type: web-api-interface
browser-compat: api.HTMLOptionsCollection
---

{{ APIRef("HTML DOM") }}

**`HTMLOptionsCollection`** یک رابط (interface) است که مجموعه‌ای از عناصر HTML [`<option>`](/en-US/docs/Web/HTML/Reference/Elements/option) را (به ترتیب سند) نشان می‌دهد و روش‌ها و ویژگی‌هایی برای انتخاب از فهرست و همچنین تغییر اختیاری موارد آن ارائه می‌دهد. این شیء فقط توسط ویژگی `options` در [select](/en-US/docs/Web/API/HTMLSelectElement) بازگردانده می‌شود.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("HTMLOptionsCollection.length")}}
  - : تعداد گزینه‌های موجود در مجموعه را برمی‌گرداند یا تنظیم می‌کند.
- {{domxref("HTMLOptionsCollection.selectedIndex")}}
  - : شماره اندیس اولین عنصر {{HTMLElement("option")}} انتخاب‌شده. مقدار `1-` نشان می‌دهد که هیچ عنصری انتخاب نشده است.

## روش‌های نمونه

_این رابط، روش‌های والد خود، [`HTMLCollection`](/en-US/docs/Web/API/HTMLCollection) را به ارث می‌برد._

- {{domxref("HTMLOptionsCollection.add()")}}
  - : یک عنصر {{domxref("HTMLOptionElement")}} یا {{domxref("HTMLOptGroupElement")}} را به مجموعه عناصر `option` اضافه می‌کند یا آن را قبل از یک گزینه مشخص می‌افزاید.
- {{domxref("HTMLOptionsCollection.remove()")}}
  - : عنصر واقع در اندیس مشخص‌شده را از مجموعه گزینه‌ها حذف می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("HTMLOptionElement")}}
- {{DOMxRef("HTMLCollection")}}
- {{DOMxRef("HTMLOptGroupElement")}}
- {{DOMxRef("HTMLSelectElement")}}
- [راهنمای مجموعه‌های نمایه‌دار](/en-US/docs/Web/JavaScript/Guide/Indexed_collections)