---
title: "ARIA: aria-readonly attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-readonly"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-readonly attribute"
short-title: aria-readonly
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-readonly
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-readonly
sidebar: accessibilitysidebar
---

ویژگی `aria-readonly` نشان می‌دهد که عنصر قابل ویرایش نیست، اما در غیر این صورت قابل استفاده است.

## توضیحات

زمانی که می‌خواهید نشان دهید یک عنصر تعاملی کار می‌کند اما قابل ویرایش نیست، `aria-readonly="true"` را تنظیم کنید. این به کاربر نشان می‌دهد که یک عنصر تعاملی که معمولاً قابل تمرکز و کپی کردن است، در حالت فقط خواندنی (نه غیرفعال) قرار گرفته است.

وقتی `aria-readonly` روی `true` تنظیم می‌شود، به این معنی است که کاربر می‌تواند مقدار ویجت را بخواند اما تنظیم نکند. عناصر فقط خواندنی همچنان برای کاربر مرتبط هستند، بنابراین نباید از پیمایش کاربر به عنصر یا فرزندان قابل تمرکز آن یا کپی کردن مقدار جلوگیری کنید.

مثال‌ها عبارتند از:

- عناصر فرمی که نباید تغییر کنند.
- سرستون‌ها و سرسطرها در یک صفحه‌گسترده.
- مقدار کل در یک سبد خرید.

اگر مقدار غیرقابل تغییر نباید قابلیت دریافت تمرکز را داشته باشد، به جای آن از [`aria-disabled`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-disabled) استفاده کنید.

> [!NOTE]
> هنگام استفاده از کنترل‌های فرم HTML معنایی، اگر ویژگی `readonly` را تنظیم کنید، نیازی به گنجاندن `aria-readonly="true"` ندارید.

> [!NOTE]
> مقدار `<input type="checkbox">` قابل ویرایش نیست و بنابراین `readonly` مرتبط نیست. با این حال، هنگام ایجاد چک‌باکس‌ها با `role="checkbox"`، ویژگی `aria-readonly` _پشتیبانی می‌شود_.

## مقادیر

- `true`
  - : عنصر فقط خواندنی است.
- `false` (پیش‌فرض)
  - : عنصر فقط خواندنی نیست.

## رابط‌های مرتبط

- {{domxref("Element.ariaReadOnly")}}
  - : ویژگی [`ariaReadOnly`](/en-US/docs/Web/API/Element/ariaReadOnly) که بخشی از رابط {{domxref("Element")}} است، مقدار ویژگی `aria-readonly` را منعکس می‌کند.
- {{domxref("ElementInternals.ariaReadOnly")}}
  - : ویژگی [`ariaReadOnly`](/en-US/docs/Web/API/ElementInternals/ariaReadOnly) که بخشی از رابط {{domxref("ElementInternals")}} است، مقدار ویژگی `aria-readonly` را منعکس می‌کند.

## نقش‌های مرتبط

استفاده شده در نقش‌ها:

- [`checkbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role)
- [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)
- [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role)
- [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)
- [`listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role)
- [`radiogroup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radiogroup_role)
- [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role)
- [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role)
- [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)

به ارث برده شده در نقش‌ها:

- [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
- [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role)
- [`searchbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/searchbox_role)
- [`switch`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role)
- [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [ویژگی `readonly` در HTML](/en-US/docs/Web/HTML/Reference/Attributes/readonly)
- [`aria-disabled`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-disabled)