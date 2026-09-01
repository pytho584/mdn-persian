---
title: "HTMLTableCaptionElement: align property"
short-title: align
slug: Web/API/HTMLTableCaptionElement/align
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLTableCaptionElement.align
---

{{APIRef("HTML DOM")}}{{deprecated_header}}

ویژگی **`align`** در رابط {{domxref("HTMLTableCaptionElement")}} یک رشته است که نحوه تراز افقی متن را در عنصر جدول {{htmlelement("caption")}} مشخص می‌کند.

> [!NOTE]
> این ویژگی منسوخ شده است و برای تراز افقی متن در یک سلول باید از CSS استفاده شود. به جای آن از ویژگی CSS {{cssxref("text-align")}} استفاده کنید که اولویت دارد و متن را به صورت افقی در سلول عنوان جدول تراز می‌کند.

## مقدار

مقادیر ممکن عبارتند از:

- `left`
  - : تراز کردن متن به چپ. به جای آن از `text-align: left` استفاده کنید.
- `right`
  - : تراز کردن متن به راست. به جای آن از `text-align: right` استفاده کنید.
- `center`
  - : وسط‌چین کردن متن در سلول. به جای آن از `text-align: center` استفاده کنید.

## مثال‌ها

به جای آن از CSS `text-align` استفاده کنید. یک [مثال](/en-US/docs/Web/CSS/Reference/Properties/text-align#table_alignment) در صفحه {{cssxref("text-align")}} موجود است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxref("text-align")}}
- {{cssxref("caption-side")}}
- [یادگیری: استایل‌دهی به جدول‌ها](/en-US/docs/Learn_web_development/Core/Styling_basics/Tables)