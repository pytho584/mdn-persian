---
title: "HTMLTableCellElement: align property"
short-title: align
slug: Web/API/HTMLTableCellElement/align
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLTableCellElement.align
---

{{APIRef("HTML DOM")}}{{deprecated_header}}

ویژگی **`align`** از رابط {{domxref("HTMLTableCellElement")}} یک رشته است که نحوه تراز افقی متن را در سلول جدول {{htmlelement("th")}} یا {{htmlelement("td")}} مشخص می‌کند.

> [!NOTE]
> این ویژگی منسوخ شده است و باید از CSS برای تراز افقی متن در یک سلول استفاده شود. به جای آن از ویژگی CSS {{cssxref("text-align")}} استفاده کنید که اولویت دارد.

## مقدار

مقادیر ممکن عبارتند از:

- `left`
  - : متن را به چپ تراز می‌کند. به جای آن از `text-align: left` استفاده کنید.
- `right`
  - : متن را به راست تراز می‌کند. به جای آن از `text-align: right` استفاده کنید.
- `center`
  - : متن را در وسط سلول قرار می‌دهد. به جای آن از `text-align: center` استفاده کنید.

## مثال‌ها

به جای این ویژگی از `text-align` CSS استفاده کنید. یک [example](/en-US/docs/Web/CSS/Reference/Properties/text-align#table_alignment) در صفحه {{cssxref("text-align")}} موجود است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxref("text-align")}}
- [Learn: Styling tables](/en-US/docs/Learn_web_development/Core/Styling_basics/Tables)