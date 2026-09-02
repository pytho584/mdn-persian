---
title: "HTMLTableSectionElement: align property"
short-title: align
slug: Web/API/HTMLTableSectionElement/align
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLTableSectionElement.align
---

{{APIRef("HTML DOM")}}{{deprecated_header}}

ویژگی **`align`** از رابط {{domxref("HTMLTableSectionElement")}} یک رشته است که نحوهٔ تراز افقی متن را در یک بخش جدول شامل {{htmlelement("thead")}}، {{htmlelement("tbody")}} یا {{htmlelement("tfoot")}} مشخص می‌کند. سطرها و سلول‌های جداگانه می‌توانند این مقدار را بازنویسی (override) کنند.

> [!NOTE]
> این ویژگی منسوخ شده است و باید از CSS برای تراز افقی متن در یک سلول استفاده کرد. به جای آن از ویژگی CSS {{cssxref("text-align")}} که اولویت دارد برای تراز افقی متن در سلول‌های بخش استفاده کنید.

## مقدار

مقادیر ممکن عبارتند از:

- `left`
  - : تراز چپ متن. به جای آن از `text-align: left` استفاده کنید.
- `right`
  - : تراز راست متن. به جای آن از `text-align: right` استفاده کنید.
- `center`
  - : وسط‌چین کردن متن در سلول. به جای آن از `text-align: center` استفاده کنید.

## مثال‌ها

به جای آن از CSS `text-align` استفاده کنید. یک [مثال](/en-US/docs/Web/CSS/Reference/Properties/text-align#table_alignment) در صفحهٔ {{cssxref("text-align")}} موجود است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{cssxref("text-align")}}
- [آموزش: استایل‌دهی به جداول](/en-US/docs/Learn_web_development/Core/Styling_basics/Tables)