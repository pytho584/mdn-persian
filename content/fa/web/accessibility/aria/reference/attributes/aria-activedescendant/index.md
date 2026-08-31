---
title: "ARIA: aria-activedescendant attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-activedescendant"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-activedescendant attribute"
short-title: aria-activedescendant
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-activedescendant
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-activedescendant
sidebar: accessibilitysidebar
---

ویژگی `aria-activedescendant` عنصر فعال کنونی را مشخص می‌کند، زمانی که فوکوس روی یک ویجت [`composite`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/composite_role)، [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)، [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)، [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role)، یا [`application`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role) قرار دارد.

## توضیحات

ویژگی `aria-activedescendant` روشی برای مدیریت فوکوس برای فناوری‌های کمکی روی عناصر تعاملی فراهم می‌کند، زمانی که این عناصر شامل چندین فرزند قابل فوکوس مانند منوها، شبکه‌ها و نوار ابزار هستند. به‌جای اینکه صفحه‌خوان فوکوس را بین عناصر تحت مالکیت جابه‌جا کند، می‌توان از `aria-activedescendant` روی عناصر ظرف استفاده کرد تا به عنصر فعال کنونی اشاره کند و کاربران فناوری کمکی را هنگام فوکوس از عنصر فعال کنونی آگاه سازد.

با `aria-activedescendant`، مرورگر فوکوس DOM را روی عنصر ظرف یا روی یک عنصر ورودی که عنصر ظرف را کنترل می‌کند، نگه می‌دارد. با این حال، عامل کاربر (user agent) رویدادها و حالت‌های فوکوس دسکتاپ را طوری به فناوری کمکی منتقل می‌کند که گویی عنصر ارجاع‌شده توسط `aria-activedescendant` فوکوس دارد.

این ویژگی فقط روی عناصری مرتبط است که دارای نقش ویجت [`composite`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/composite_role)، [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)، [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)، [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role) یا [`application`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role) هستند و `id` آن‌ها به‌عنوان مقدار ویژگی ارجاع داده شده است.

این ویژگی مدیریت ارائه اطلاعات به فناوری‌های کمکی درباره اینکه کدام عنصر فوکوس دارد را بر عهده دارد، اما در واقع فوکوس ایجاد نمی‌کند. تغییر فوکوس و مدیریت مقدار ویژگی با جاوااسکریپت انجام می‌شود. علاوه بر مدیریت آن مقدار ویژگی، مطمئن شوید که فرزند فعال کنونی هنگام فوکوس قابل مشاهده و در دیدرس باشد (یا به درون دید اسکرول شود).

هنگام تنظیم مقدار `aria-activedescendant` روی عنصری که فوکوس DOM دارد، مطمئن شوید که مقدار به یک عنصر تحت مالکیت اشاره می‌کند — یا به یک فرزند از عنصر دارای فوکوس DOM، یا به یک فرزند منطقی که توسط ویژگی [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns) مشخص شده است.

هنگامی که عنصر دارای فوکوس DOM یک combobox، textbox یا searchbox است، [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls) را لحاظ کنید تا به عنصری که از `aria-activedescendant` پشتیبانی می‌کند ارجاع دهد.

مقدار `aria-activedescendant` به یک عنصر تحت مالکیت از عنصر کنترل‌شده اشاره می‌کند. برای مثال، در یک combobox، فوکوس ممکن است روی combobox باقی بماند، در حالی که مقدار `aria-activedescendant` روی عنصر combobox به یک فرزند از listbox بازشو اشاره می‌کند که توسط combobox کنترل می‌شود.

> [!NOTE]
> این ویژگی فقط روی تعداد کمی از نقش‌ها پشتیبانی می‌شود. برای مثال، `dialog`ها از `aria-activedescendant` پشتیبانی نمی‌کنند. وقتی یک combobox یک dialog را باز می‌کند، فوکوس DOM از combobox به داخل dialog حرکت می‌کند، زیرا این عنصر با این ویژگی قابل ارجاع نیست.

> [!NOTE]
> وقتی فرزندی از یک `listbox`، `grid` یا `tree` بازشو فوکوس می‌شود، فوکوس DOM روی combobox باقی می‌ماند و `aria-activedescendant` در combobox روی مقداری تنظیم شده است که به عنصر فوکوس‌شده درون بازشو اشاره می‌کند.

## مقادیر

- ارجاع شناسه (ID reference)
  - : به‌عنوان مقدار خود، `id` عنصر دارای فوکوس کنونی را می‌گیرد.

## رابط‌های مرتبط

- {{domxref("Element.ariaActiveDescendantElement")}}
  - : ویژگی `ariaActiveDescendantElement` بخشی از رابط هر عنصر است.
    مقدار آن نمونه‌ای از یک زیرکلاس از {{domxref("Element")}} است که ارجاع `id` را در ویژگی `aria-activedescendant` بازتاب می‌دهد ([با برخی ملاحظات](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references)).
- {{domxref("ElementInternals.ariaActiveDescendantElement")}}
  - : ویژگی `ariaActiveDescendantElement` بخشی از رابط هر عنصر سفارشی است.
    مقدار آن نمونه‌ای از یک زیرکلاس از {{domxref("Element")}} است که ارجاع `id` را در ویژگی `aria-activedescendant` بازتاب می‌دهد ([با برخی ملاحظات](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references)).

## نقش‌های مرتبط

فقط به‌عنوان ویژگی روی عناصر دارای نقش‌های زیر مرتبط است:

- [`application`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role)
- [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)
- [`composite`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/composite_role)
- [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role)
- [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)

## مشخصات

{{Specifications}}