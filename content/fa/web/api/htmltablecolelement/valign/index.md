---
title: "HTMLTableColElement: vAlign property"
short-title: vAlign
slug: Web/API/HTMLTableColElement/vAlign
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLTableColElement.vAlign
---

{{APIRef("HTML DOM")}}{{deprecated_header}}

ویژگی **`vAlign`** از رابط {{domxref("HTMLTableColElement")}} یک رشته است که نحوه‌ی تراز عمودی متن را در یک عنصر ستون {{htmlelement("col")}} جدول مشخص می‌کند.

> [!NOTE]
> این ویژگی منسوخ شده است و باید از CSS برای تراز عمودی متن در یک ستون استفاده کرد. به جای آن از ویژگی CSS {{cssxref("vertical-align")}} که اولویت دارد استفاده کنید تا متن را در هر سلول ستون به صورت عمودی تراز کنید. از آنجایی که عناصر {{htmlelement("td")}} فرزندان {{htmlelement("col")}} نیستند، نمی‌توانید این ویژگی را مستقیماً روی یک عنصر {{HTMLElement("col")}} تنظیم کنید؛ باید سلول‌های ستون را با استفاده از `td:nth-child(n)` یا مشابه آن انتخاب کنید (`n` شماره ستون است).

## مقدار

مقادیر ممکن عبارت‌اند از: `"top"`، `"middle"`، `"bottom"`، یا `"baseline"`.

- `top`
  - : متن را در بالای ستون تراز کنید. به جای آن از `vertical-align: top` استفاده کنید.
- `center`
  - : متن را به صورت عمودی در وسط ستون قرار دهید. مترادف `middle`. به جای آن از `vertical-align: middle` استفاده کنید.
- `middle`
  - : متن را به صورت عمودی در وسط ستون قرار دهید. به جای آن از `vertical-align: middle` استفاده کنید.
- `bottom`
  - : متن را در پایین ستون تراز کنید. به جای آن از `vertical-align: bottom` استفاده کنید.
- `baseline`
  - : مشابه `top`، اما خط پایه‌ی متن را تا حد امکان به بالا نزدیک کنید تا هیچ بخشی از نویسه خارج از سلول نباشد.

## مثال‌ها

از `vertical-align` CSS استفاده کنید. از آنجایی که عناصر {{htmlelement("td")}} یک ستون فرزندان {{htmlelement("col")}} نیستند، نمی‌توانید آن را مستقیماً روی یک {{HTMLElement("col")}} تنظیم کنید؛ باید سلول‌ها را با استفاده از `td:nth-child(n)` یا مشابه آن انتخاب کنید (`n` شماره ستون است).

یک [مثال](/en-US/docs/Web/CSS/Reference/Selectors/:nth-child#styling_a_table_column) در صفحه‌ی {{cssxref(":nth-child()")}} موجود است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxref("vertical-align")}}
- {{cssxref(":nth-child()")}}
- [یادگیری: استایل‌دهی به جداول](/en-US/docs/Learn_web_development/Core/Styling_basics/Tables)