---
title: "ARIA: aria-rowindextext attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindextext"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-rowindextext attribute"
short-title: aria-rowindextext
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-rowindextext
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-rowindextext
sidebar: accessibilitysidebar
---

ویژگی `aria-rowindextext` یک جایگزین متنی قابل خواندن برای انسان از `aria-rowindex` تعریف می‌کند.

هنگامی که یک جدول بسیار طولانی دارید یا عمداً می‌خواهید فقط بخشی از یک جدول را نمایش دهید، ممکن است همه ردیف‌ها در DOM وجود نداشته باشند. در این حالت، از [`aria-rowcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowcount) با یک مقدار صحیح استفاده می‌کنیم تا مشخص کنیم جدول (یا شبکه) اگر همه ردیف‌ها حضور داشتند، تعداد ردیف‌های آن چقدر می‌بود و ویژگی [`aria-rowindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindex) را به هر ردیف و سلول‌های ترکیبی اضافه می‌کنیم تا اطلاعاتی درباره شاخص ردیف در آن جدول بزرگ‌تر فراهم شود. وقتی مقدار `aria-rowindex` معنادار نیست یا شاخص نمایش‌داده‌شده را منعکس نمی‌کند، می‌توانیم `aria-rowindextext` را نیز اضافه کنیم تا یک جایگزین متنی قابل خواندن برای انسان برای مقدار صحیح `aria-rowindex` فراهم کنیم.

`aria-rowindextext` باید فقط **علاوه بر** `aria-rowindex` گنجانده شود، نه به عنوان جایگزین آن. برخی فناوری‌های کمکی از شاخص عددی ردیف برای پیگیری موقعیت کاربر یا ارائه ناوبری جایگزین در جدول استفاده می‌کنند. `aria-rowindextext` زمانی مفید است که آن مقدار صحیح معنادار نباشد یا شاخص نمایش‌داده‌شده را منعکس نکند، مانند بازی شطرنج یا بازی کشتی جنگی.

`aria-rowindextext` به هر {{HTMLElement('tr')}} یا به عناصری با نقش `row` اضافه می‌شود. همچنین می‌توان آن را به سلول‌ها یا عناصر وابسته به هر ردیف اضافه کرد.

## مقادیر

- `<string>`
  - جایگزین متنی قابل خواندن برای انسان از شاخص عددی [`aria-rowindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindex)

## رابط‌های مرتبط

- {{domxref("Element.ariaRowIndexText")}}
  - : ویژگی [`ariaRowIndexText`](/en-US/docs/Web/API/Element/ariaRowIndexText)، بخشی از رابط {{domxref("Element")}}، منعکس‌کننده مقدار ویژگی `aria-rowindextext` است.
- {{domxref("ElementInternals.ariaRowIndexText")}}
  - : ویژگی [`ariaRowIndexText`](/en-US/docs/Web/API/ElementInternals/ariaRowIndexText)، بخشی از رابط {{domxref("ElementInternals")}}، منعکس‌کننده مقدار ویژگی `aria-rowindextext` است.

## نقش‌های مرتبط

مورد استفاده در نقش‌ها:

- [`cell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role)
- [`row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)

به ارث رسیده به نقش‌ها:

- [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
- [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)
- [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`aria-rowindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindex)
- [`aria-rowcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowcount)
- [`aria-rowspan`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowspan)
- [`aria-colindextext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindextext)
- [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex)