---
title: "HTMLTableRowElement: align property"
---

{{APIRef("HTML DOM")}}{{deprecated_header}}

## HTMLTableRowElement: align property

خاصیت **`align`** در رابط {{domxref("HTMLTableRowElement")}} یک رشته (string) است که نحوهٔ تراز افقی متن در ردیف جدول `<tr>` را مشخص می‌کند. سلول‌های جداگانه می‌توانند آن را بازنویسی (override) کنند.

> [!NOTE]
> این خاصیت منسوخ شده است (deprecated) و برای تراز افقی متن در یک سلول باید از CSS استفاده شود. به جای آن، از خاصیت CSS `text-align` که اولویت دارد، برای تراز افقی متن در یک ردیف استفاده کنید.

## Value

مقادیر ممکن عبارتند از:

- `left`
  - متن را به سمت چپ تراز می‌کند. به جای آن از `text-align: left` استفاده کنید.
- `right`
  - متن را به سمت راست تراز می‌کند. به جای آن از `text-align: right` استفاده کنید.
- `center`
  - متن را در سلول وسط می‌چیند. به جای آن از `text-align: center` استفاده کنید.
- `justify`
  - متن را در عرض سلول پخش می‌کند. به جای آن از `text-align: justify` استفاده کنید.
- `char`
  - هرگز به طور کامل پشتیبانی نشد، متن را به یک کاراکتر مشخص تراز می‌کند. در صورت پشتیبانی، از `text-align: <string>` استفاده کنید که در آن رشته یک کاراکتر است.

## Examples

به جای آن از CSS `text-align` استفاده کنید. یک [مثال](/en-US/docs/Web/CSS/Reference/Properties/text-align#table_alignment) در صفحهٔ `text-align` موجود است.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{cssxref("text-align")}}
- [یادگیری: استایل‌دهی به جداول](/en-US/docs/Learn_web_development/Core/Styling_basics/Tables)