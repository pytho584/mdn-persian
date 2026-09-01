---
title: "HTMLTableColElement: align property"
short-title: align
slug: Web/API/HTMLTableColElement/align
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLTableColElement.align
---

{{APIRef("HTML DOM")}}{{deprecated_header}}

ویژگی **`align`** از رابط {{domxref("HTMLTableColElement")}} یک رشته است که نحوهٔ تراز افقی متن در یک عنصر ستون {{htmlelement("col")}} جدول را مشخص می‌کند.

> [!NOTE]
> این ویژگی منسوخ شده است و برای تراز افقی متن در یک ستون باید از CSS استفاده شود. به جای آن از ویژگی CSS {{cssxref("text-align")}} که اولویت دارد استفاده کنید.
>
> از آنجایی که عناصر {{htmlelement("td")}} فرزندان {{htmlelement("col")}} نیستند، نمی‌توانید آن را مستقیماً روی یک عنصر {{HTMLElement("col")}} تنظیم کنید. باید سلول‌های ستون را با استفاده از یک انتخابگر مانند `td:nth-last-child(n)` یا مشابه آن انتخاب کنید (`n` شماره ستون از انتها است).

## Value

مقادیر ممکن عبارتند از:

- `left`
  - : متن را به سمت چپ تراز می‌کند. به جای آن از `text-align: left` که مستقیماً روی {{HTMLElement("td")}} یا {{HTMLElement("th")}} اعمال می‌شود استفاده کنید.
- `right`
  - : متن را به سمت راست تراز می‌کند. به جای آن از `text-align: right` که مستقیماً روی `<td>` یا `<th>` اعمال می‌شود استفاده کنید.
- `center`
  - : متن را در سلول وسط‌چین می‌کند. به جای آن از `text-align: center` استفاده کنید.

## Examples

از ویژگی CSS `text-align` روی عناصر {{htmlelement("td")}} و {{htmlelement("th")}} استفاده کنید. از آنجایی که عناصر {{htmlelement("td")}} یک ستون فرزندان {{htmlelement("col")}} نیستند، تنظیم ویژگی `align` در HTML یا ویژگی `text-align` در CSS روی یک عنصر {{HTMLElement("col")}} تأثیری نخواهد داشت. در عوض، سلول‌های یک ستون را با استفاده از یک انتخابگر مانند [`:is(td, tr):nth-child(n)`](/en-US/docs/Web/CSS/Reference/Selectors/:nth-child) که در آن `n` شماره ستون است، یا مشابه آن انتخاب کنید.

یک [مثال](/en-US/docs/Web/CSS/Reference/Selectors/:nth-child#styling_a_table_column) در صفحهٔ {{cssxref(":nth-child()")}} موجود است.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{cssxref("text-align")}}
- {{cssxref(":nth-child()")}}
- {{cssxref(":nth-last-child()")}}
- [Learn: Styling tables](/en-US/docs/Learn_web_development/Core/Styling_basics/Tables)