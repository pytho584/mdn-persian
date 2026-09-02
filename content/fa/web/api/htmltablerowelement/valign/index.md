---
title: "HTMLTableRowElement: vAlign property"
---

---
title: "HTMLTableRowElement: vAlign property"
short-title: vAlign
slug: Web/API/HTMLTableRowElement/vAlign
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLTableRowElement.vAlign
---

{{APIRef("HTML DOM")}}{{deprecated_header}}

ویژگی **`vAlign`** از رابط {{domxref("HTMLTableRowElement")}} یک رشته (string) است که نحوهٔ تراز عمودی متن را در یک ردیف جدول {{htmlelement("tr")}} مشخص می‌کند. سلول‌های تکی می‌توانند آن را بازنویسی کنند.

> [!NOTE]
> این ویژگی منسوخ (deprecated) شده است. به‌جای آن از ویژگی CSS {{cssxref("vertical-align")}} برای تراز عمودی متن در یک ردیف استفاده کنید.

## مقدار

مقادیر ممکن عبارت‌اند از: `"top"`, `"middle"`, `"bottom"`, یا `"baseline"`

- `top`
  - : متن را در بالای سلول تراز می‌کند. به‌جای آن از `vertical-align: top` استفاده کنید.

- `center`
  - : متن را به‌صورت عمودی در وسط سلول قرار می‌دهد. مترادف `middle` است. به‌جای آن از `vertical-align: middle` استفاده کنید.

- `middle`
  - : متن را به‌صورت عمودی در وسط سلول قرار می‌دهد. به‌جای آن از `vertical-align: middle` استفاده کنید.

- `bottom`
  - : متن را در پایین سلول تراز می‌کند. به‌جای آن از `vertical-align: bottom` استفاده کنید.

- `baseline`
  - : مشابه `top` است، اما خط پایهٔ متن را تا حد امکان نزدیک به بالا تراز می‌کند به‌گونه‌ای که هیچ بخشی از نویسه خارج از سلول نباشد.

## مثال‌ها

به‌جای آن از CSS {{cssxref("vertical-align")}} استفاده کنید که اولویت دارد؛ همان‌طور که در مثال [تراز عمودی سلول‌های جدول](/en-US/docs/Web/CSS/Reference/Properties/vertical-align#vertical_alignment_in_a_table_cell) نشان داده شده است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxref("vertical-align")}}
- [یادگیری: استایل‌دهی به جدول‌ها](/en-US/docs/Learn_web_development/Core/Styling_basics/Tables)