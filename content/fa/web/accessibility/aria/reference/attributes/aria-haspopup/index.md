---
title: "ARIA: aria-haspopup attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-haspopup"
translated_by: "n8n + AI"
---
---
title: "ARIA: aria-haspopup attribute"
short-title: aria-haspopup
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-haspopup
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-haspopup
sidebar: accessibilitysidebar
---

ویژگی `aria-haspopup` در دسترس بودن و نوع عنصر پاپ‌آپ تعاملی را نشان می‌دهد که می‌تواند توسط عنصری که این ویژگی روی آن تنظیم شده است، فعال شود.

## توضیحات

در ARIA، منوها، لیست‌باکس‌ها، درختان، گریدها و دیالوگ‌های تعاملی که هنگام فعال شدن روی محتوای دیگر ظاهر می‌شوند، «پاپ‌آپ» در نظر گرفته می‌شوند. این پاپ‌آپ‌ها توسط یک یا چند عنصر تعاملی در صفحه فعال می‌شوند. در دسترس بودن و نوع پاپ‌آپی که عنصر تعاملی فعال می‌کند باید با حالت `aria-haspopup` مشخص شود.

وجود `aria-haspopup` با یکی از شش مقدار شمارشی - `menu`، `listbox`، `tree`، `grid`، `dialog` یا `true` - نشان می‌دهد که عنصر می‌تواند یک پاپ‌آپ را فعال کند و چه نوع پاپ‌آپی نمایش داده خواهد شد. در مقابل، عنصری که پاپ‌آپ می‌شود باید نقشی متناسب داشته باشد. مقدار `true` معادل `menu` است. هر مقدار دیگر، از جمله یک رشته خالی یا [نقش](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles) دیگر، به‌گونه‌ای رفتار می‌شود که گویی `false` تنظیم شده است.

یک [`tooltip`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tooltip_role) در این زمینه پاپ‌آپ در نظر گرفته نمی‌شود، زیرا تعاملی نیست.

> [!NOTE]
> مطمئن شوید که نقش عنصری که به‌عنوان ظرف محتوای پاپ‌آپ عمل می‌کند، [`menu`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menu_role)، [`listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role)، [`tree`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tree_role)، [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role) یا [`dialog`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/dialog_role) باشد و مقدار `aria-haspopup` با نقش ظرف پاپ‌آپ مطابقت داشته باشد.

حالت `aria-haspopup` به کاربران فناوری کمکی اطلاع می‌دهد که یک پاپ‌آپ وجود دارد و نوع آن چیست، اما تعاملی ارائه نمی‌دهد. برای اینکه پاپ‌آپ از طریق صفحه‌کلید قابل دسترسی باشد، مطمئن شوید عنصری که `aria-haspopup` دارد قابل تمرکز (focusable) است و می‌تواند پاپ‌آپ را فعال کند، یک مکانیسم صفحه‌کلید برای باز کردن پاپ‌آپ وجود دارد، و عنصر پاپ‌آپ تمرکز همه فرزندان خود را مدیریت می‌کند.

> [!NOTE]
> ARIA قابلیت دسترسی را فعال نمی‌کند. ARIA فقط رفتار مورد نظر عملکرد شما را منتقل می‌کند.

هنگام ایجاد یک [`menubar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menubar_role)، یک [`menuitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role) والد باید `aria-haspopup="menu"` (یا `true`) داشته باشد. هر دکمه‌ای که یک منو را باز می‌کند باید نقش [`button`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role) داشته باشد یا ترجیحاً یک {{HTMLElement('button')}} باشد و همچنین `aria-haspopup="menu"` (یا `true`) روی آن تنظیم شود. عناصر [`Tab`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role) با منوهای پاپ‌آپ نیز باید `aria-haspopup="menu"` داشته باشند. توجه داشته باشید که `menubar`ها نباید برای ایجاد ناوبری وب‌سایت استفاده شوند.

> [!NOTE]
> عناصر با نقش [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role) به‌طور ضمنی مقدار `aria-haspopup` برابر با `listbox` دارند.

## مقادیر

- `false` (پیش‌فرض)
  - عنصر پاپ‌آپ ندارد.
- `true`
  - پاپ‌آپ یک منو است.
- `menu`
  - پاپ‌آپ یک منو است.
- `listbox`
  - پاپ‌آپ یک لیست‌باکس است.
- `tree`
  - پاپ‌آپ یک درخت است.
- `grid`
  - پاپ‌آپ یک گرید است.
- `dialog`
  - پاپ‌آپ یک دیالوگ است.

## رابط‌های مرتبط

- {{domxref("Element.ariaHasPopup")}}
  - ویژگی [`ariaHasPopup`](/en-US/docs/Web/API/Element/ariaHasPopup) که بخشی از رابط {{domxref("Element")}} است، مقدار ویژگی `aria-haspopup` را منعکس می‌کند که نشان‌دهنده در دسترس بودن و نوع عنصر پاپ‌آپ تعاملی (مانند منو یا دیالوگ) است که می‌تواند توسط یک عنصر فعال شود.
- {{domxref("ElementInternals.ariaHasPopup")}}
  - ویژگی [`ariaHasPopup`](/en-US/docs/Web/API/ElementInternals/ariaHasPopup) از رابط {{domxref("ElementInternals")}} مقدار ویژگی `aria-haspopup` را منعکس می‌کند.

## نقش‌های مرتبط

استفاده در نقش‌ها:

- [`application`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role)
- [`button`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role)
- [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)
- [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)
- [`link`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/link_role)
- [`menuitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role)
- [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role)
- [`tab`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role)
- [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)
- [`treeitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treeitem_role)

به‌ارث‌برده شده در نقش‌ها:

- [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
- [`menuitemcheckbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role)
- [`menuitemradio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role)
- [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role)
- [`searchbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/searchbox_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls)
- [`menu`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menu_role)
- [`listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role)
- [`tree`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tree_role)
- [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role)
- [`dialog`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/dialog_role)
- [مثال نوار ابزار](https://www.w3.org/WAI/ARIA/apg/patterns/toolbar/examples/toolbar/) - شیوه‌های WAI ARIA کنسرسیوم وب جهانی