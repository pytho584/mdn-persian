---
title: "HTMLTableSectionElement: vAlign property"
---

---
title: "HTMLTableSectionElement: vAlign property"
short-title: vAlign
slug: Web/API/HTMLTableSectionElement/vAlign
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLTableSectionElement.vAlign
---

{{APIRef("HTML DOM")}}{{deprecated_header}}

ویژگی **`vAlign`** از رابط {{domxref("HTMLTableSectionElement")}} یک رشته است که نشان می‌دهد متن در یک بخش جدول شامل {{htmlelement("thead")}}، {{htmlelement("tbody")}} یا {{htmlelement("tfoot")}} چگونه به‌صورت عمودی تراز شود. سطرها و سلول‌های منفرد می‌توانند آن را بازنویسی کنند.

> [!NOTE]
> این ویژگی منسوخ شده است. به‌جای آن از ویژگی CSS {{cssxref("vertical-align")}} برای تراز عمودی متن در سلول‌های بخش استفاده کنید.

## مقدار

مقادیر ممکن عبارت‌اند از: `"top"`، `"middle"`، `"bottom"` یا `"baseline"`

- `top`
  - : تراز کردن متن در بالای سلول. به‌جای آن از `vertical-align: top` استفاده کنید.
- `center`
  - : متن را به‌صورت عمودی در سلول وسط‌چین می‌کند. مترادف `middle` است. به‌جای آن از `vertical-align: middle` استفاده کنید.
- `middle`
  - : متن را به‌صورت عمودی در سلول وسط‌چین می‌کند. به‌جای آن از `vertical-align: middle` استفاده کنید.
- `bottom`
  - : تراز کردن متن در پایین سلول. به‌جای آن از `vertical-align: bottom` استفاده کنید.
- `baseline`
  - : مشابه `top` است، اما خط پایهٔ متن را تا حد امکان به بالای سلول نزدیک می‌کند، به‌گونه‌ای که هیچ بخشی از نویسه‌ها خارج از سلول نباشد.

## مثال‌ها

به‌جای آن از {{cssxref("vertical-align")}} استفاده کنید که اولویت دارد؛ همان‌طور که در مثال [تراز عمودی سلول‌های جدول](/en-US/docs/Web/CSS/Reference/Properties/vertical-align#vertical_alignment_in_a_table_cell) نشان داده شده است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxref("vertical-align")}}
- [یادگیری: استایل‌دهی به جدول‌ها](/en-US/docs/Learn_web_development/Core/Styling_basics/Tables)