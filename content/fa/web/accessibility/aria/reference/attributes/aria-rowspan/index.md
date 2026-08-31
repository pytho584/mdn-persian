---
title: "ARIA: aria-rowspan attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowspan"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-rowspan attribute"
short-title: aria-rowspan
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-rowspan
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-rowspan
sidebar: accessibilitysidebar
---

ویژگی `aria-rowspan` تعداد ردیف‌هایی را تعریف می‌کند که یک سلول یا سلول شبکه‌ای در یک جدول، شبکه یا شبکه درختی می‌پوشاند.

## توضیحات

مشابه ویژگی `rowspan` در عناصر {{HTMLElement('td')}} و {{HTMLElement('th')}}، اما برای سلول‌ها و سلول‌های شبکه‌ای که در جدول بومی قرار ندارند، ویژگی `aria-rowspan` تعداد ردیف‌هایی را که یک `cell` یا `gridcell` در یک `table`، `grid` یا `treegrid` می‌پوشاند، تعریف می‌کند.

این ویژگی برای سلول‌ها و سلول‌های شبکه‌ای در نظر گرفته شده است که **جزء** یک {{HTMLElement('table')}} در HTML نیستند. وقتی یک سلول در یک `<table>` معنایی قرار می‌گیرد، اگر یک `<td>` یا `<th>` بیش از یک ردیف را پوشش دهد، باید از ویژگی `rowspan` استفاده کرد. اگر هر دو وجود داشته باشند، `rowspan` بر `aria-rowspan` اولویت دارد. اما مانند همه ویژگی‌های ARIA، `aria-rowspan` تنها بر درخت دسترس‌پذیری تأثیر می‌گذارد و چیدمان شما را تغییر نمی‌دهد.

> [!NOTE]
> ARIA درخت دسترس‌پذیری و نحوه ارائه محتوا توسط فناوری کمکی به کاربران شما را تغییر می‌دهد. ARIA هیچ چیز را در مورد عملکرد، رفتار یا ظاهر یک عنصر تغییر نمی‌دهد. هنگام استفاده از عناصر غیرمعنایی، باید از CSS برای مدیریت چیدمان و ظاهر استفاده کنید.

مقدار `aria-rowspan` یک عدد صحیح بزرگ‌تر یا مساوی ۰ و کمتر از مقداری است که باعث می‌شود سلول یا سلول شبکه‌ای با سلول یا سلول شبکه‌ای بعدی در همان ستون هم‌پوشانی پیدا کند. تنظیم مقدار روی `0` نشان می‌دهد که سلول یا سلول شبکه‌ای باید همه ردیف‌های باقی‌مانده در گروه ردیف را پوشش دهد. مقدار پیش‌فرض `1` است.

## مقدارها

- `<integer>`
  - : یک عدد صحیح بزرگ‌تر یا مساوی `0` و کمتر از مقداری که باعث می‌شود یک سلول با سلول بعدی در همان ستون هم‌پوشانی پیدا کند.

## رابط‌های مرتبط

- {{domxref("Element.ariaRowSpan")}}
  - : ویژگی [`ariaRowSpan`](/en-US/docs/Web/API/Element/ariaRowSpan)، بخشی از رابط {{domxref("Element")}}، مقدار ویژگی `aria-rowspan` را منعکس می‌کند.
- {{domxref("ElementInternals.ariaRowSpan")}}
  - : ویژگی [`ariaRowSpan`](/en-US/docs/Web/API/ElementInternals/ariaRowSpan)، بخشی از رابط {{domxref("ElementInternals")}}، مقدار ویژگی `aria-rowspan` را منعکس می‌کند.

## نقش‌های مرتبط

نقش‌های استفاده‌شده:

- [`cell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role)

به ارث برده‌شده در نقش‌ها:

- [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
- [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- The [`rowspan`](/en-US/docs/Web/HTML/Reference/Elements/td#rowspan) attribute on {{HTMLElement('td')}}
- [`aria-rowindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindex)
- [`aria-colspan`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colspan)