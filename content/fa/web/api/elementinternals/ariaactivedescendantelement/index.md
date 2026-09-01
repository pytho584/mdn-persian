---
title: "Element: ariaActiveDescendantElement property"
short-title: ariaActiveDescendantElement
slug: Web/API/ElementInternals/ariaActiveDescendantElement
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaActiveDescendantElement
---

{{APIRef("DOM")}}

خاصیت **`ariaActiveDescendantElement`** از رابط {{domxref("ElementInternals")}} نمایانگر عنصر فعال کنونی زمانی است که تمرکز روی یک ویجت [`composite`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/composite_role)، [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)، [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)، [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role) یا [`application`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role) باشد.

مبحث [`aria-activedescendant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-activedescendant) اطلاعات بیشتری درباره نحوه استفاده از این ویژگی و خاصیت در اختیار شما قرار می‌دهد.

## مقدار

یک زیرکلاس از {{domxref("HTMLElement")}} که نمایانگر فرزند فعال است، یا در صورت نبود فرزند فعال، مقدار `null`.

## توضیحات

این خاصیت یک جایگزین انعطاف‌پذیر برای استفاده از ویژگی [`aria-activedescendant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-activedescendant) است.
برخلاف `aria-activedescendant`، عنصری که به این خاصیت نسبت داده می‌شود لزومی ندارد دارای ویژگی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) باشد.

این خاصیت ویژگی [`aria-activedescendant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-activedescendant) عنصر را زمانی که تعریف شده باشد بازتاب می‌دهد، اما فقط برای مقادیر `id` مرجع که با عناصر معتبر درون‌حوزه مطابقت دارند.
اگر این خاصیت تنظیم شود، ویژگی متناظر پاک می‌شود.
برای اطلاعات بیشتر درباره مراجع عناصر بازتاب‌شده و حوزه، به [مراجع عناصر بازتاب‌شده](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _ویژگی‌های بازتاب‌شده_ مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- ویژگی [`aria-activedescendant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-activedescendant)
- {{domxref("Element.ariaActiveDescendantElement")}}
- [مراجع عناصر بازتاب‌شده](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _بازتاب ویژگی‌ها_.