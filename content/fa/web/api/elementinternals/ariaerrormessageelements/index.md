---
title: "ElementInternals: ariaErrorMessageElements property"
---

---
title: "ElementInternals: ariaErrorMessageElements property"
short-title: ariaErrorMessageElements
slug: Web/API/ElementInternals/ariaErrorMessageElements
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaErrorMessageElements
---

{{APIRef("DOM")}}

خصوصیت **`ariaErrorMessageElements`** از رابط {{domxref("ElementInternals")}} آرایهای است که شامل عنصر (یا عناصر) فراهمکنندهٔ پیام خطا برای عنصری است که این خصوصیت به آن اعمال میشود.

مبحث [`aria-errormessage`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-errormessage) حاوی اطلاعات بیشتری دربارهٔ نحوهٔ استفاده از ویژگی (attribute) و خصوصیت (property) است.

## مقدار

آرایهای از زیرکلاس‌های {{domxref("HTMLElement")}}.
متن درونی این عناصر را می‌توان با فاصله (space) به هم متصل کرد تا پیام خطا به دست آید.

هنگام خواندن، آرایهٔ بازگردانده‌شده ایستا و فقط‌خواندنی است.
هنگام نوشتن، آرایهٔ تخصیص‌داده‌شده کپی می‌شود: تغییرات بعدی در آرایه بر مقدار این خصوصیت تأثیر نمی‌گذارد.

## توضیحات

این خصوصیت جایگزینی انعطاف‌پذیر برای استفاده از ویژگی [`aria-errormessage`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-errormessage) به‌منظور تنظیم پیام خطای یک عنصر است.
برخلاف `aria-errormessage`، عناصر اختصاص‌داده‌شده به این خصوصیت لزوماً نیازی به داشتن ویژگی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) ندارند.

این خصوصیت ویژگی [`aria-errormessage`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-errormessage) عنصر را در صورت تعریف‌شدن بازتاب می‌دهد، اما فقط برای مقادیر `id` مرجع فهرست‌شده‌ای که با عناصر معتبر درون‌دامنه مطابقت دارند.
اگر این خصوصیت تنظیم شود، ویژگی متناظر پاک می‌شود.
برای اطلاعات بیشتر دربارهٔ مراجع عناصر بازتابی و دامنه، به [مراجع عناصر بازتابی](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _ویژگی‌های بازتابی_ مراجعه کنید.

## مثال‌ها

مثال‌های موجود در اسناد زیر مرتبط هستند:

- {{domxref("Element.ariaErrorMessageElements")}} معادل DOM این خصوصیت است.
  به همان روش استفاده می‌شود، اما در DOM به‌جای shadow DOM و/یا عنصر سفارشی.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی [`aria-errormessage`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-errormessage)
- {{domxref("Element.ariaErrorMessageElements")}}
- [مراجع عناصر بازتابی](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _بازتاب ویژگی_.