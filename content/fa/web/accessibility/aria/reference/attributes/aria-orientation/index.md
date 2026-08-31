---
title: "ARIA: aria-orientation attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-orientation"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-orientation attribute"
short-title: aria-orientation
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-orientation
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-orientation
sidebar: accessibilitysidebar
---

ویژگی `aria-orientation` نشان می‌دهد که جهت‌گیری عنصر افقی، عمودی، یا ناشناخته/مبهم است.

## توضیحات

ممکن است برای کاربر مهم باشد که جهت‌گیری را بداند تا بتواند در ویجت‌های خاصی پیمایش کند، زیرا جهت‌گیری بر رفتارهای مورد انتظار فلش‌های چپ، راست، بالا و پایین تأثیر می‌گذارد. ویژگی `aria-orientation` برای نشان دادن افقی (`horizontal`)، عمودی (`vertical`) یا تعریف‌نشده (`undefined`) بودن جهت‌گیری یک عنصر به کاربران فناوری کمکی استفاده می‌شود.

چندین ویجت جهت‌گیری پیش‌فرض دارند:

افقی به‌طور پیش‌فرض:

- [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role)
- [`tablist`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tablist_role)
- [`toolbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/toolbar_role)
- [`menubar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menubar_role)

عمودی به‌طور پیش‌فرض:

- [`scrollbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role)
- [`tree`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tree_role)
- [`listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role)
- [`menu`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menu_role)

هر [`separator`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role) باید `aria-orientation` سازگار با جهت‌گیری جداکننده داشته باشد.

هنگامی که گره‌های یک درخت به جای جهت‌گیری عمودی پیش‌فرض، به صورت افقی چیده شده‌اند، یا هنگامی که یک فهرست تب به جای افقی پیش‌فرض، عمودی است، فلش پایین مانند فلش راست عمل می‌کند و فلش بالا مانند فلش چپ عمل می‌کند. در این موارد، کاربران فناوری کمکی باید جهت‌گیری ویجت را بدانند تا بتوانند به درستی پیمایش کنند.

فلش‌های بالا و پایین معمولاً برای اسکرول معمولی مرورگر در دسترس هستند، حتی زمانی که فوکوس داخل یک درخت یا فهرست تب باشد. `aria-orientation` را برای فعال کردن هشدار به کاربران در زمانی که یک ویجت جهت‌گیری پیش‌فرض و مورد انتظار و پیمایش مرتبط را ندارد، اضافه کنید.

همیشه به خاطر داشته باشید که ARIA فقط نحوه ارائه محتوا به کاربران توسط فناوری کمکی را تغییر می‌دهد؛ تغییر رفتار کلیدهای فلش نیاز به جاوااسکریپت دارد.

## مقادیر

- `horizontal`
  - : عنصر به صورت افقی جهت‌گیری شده است.
- `undefined` (پیش‌فرض)
  - : جهت‌گیری عنصر ناشناخته/مبهم است.
- `vertical`
  - : عنصر به صورت عمودی جهت‌گیری شده است.

## رابط‌های مرتبط

- {{domxref("Element.ariaOrientation")}}
  - : ویژگی [`ariaOrientation`](/en-US/docs/Web/API/Element/ariaOrientation)، بخشی از رابط {{domxref("Element")}}، مقدار ویژگی `aria-orientation` را منعکس می‌کند.
- {{domxref("ElementInternals.ariaOrientation")}}
  - : ویژگی [`ariaOrientation`](/en-US/docs/Web/API/ElementInternals/ariaOrientation)، بخشی از رابط {{domxref("ElementInternals")}}، مقدار ویژگی `aria-orientation` را منعکس می‌کند.

## نقش‌های مرتبط

استفاده‌شده در نقش‌ها:

- [`scrollbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role)
- [`select`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/select_role)
- [`separator`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role)
- [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role)
- [`tablist`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tablist_role)
- [`toolbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/toolbar_role)

به ارث رسیده به نقش‌ها:

- [`listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role)
- [`menu`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menu_role)
- [`menubar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menubar_role)
- [`radiogroup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radiogroup_role)
- [`tree`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tree_role)
- [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [درک WCAG: صفحه‌کلید](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Keyboard)