---
title: "ElementInternals: ariaDetailsElements property"
---

---
title: "ElementInternals: ariaDetailsElements property"
short-title: ariaDetailsElements
slug: Web/API/ElementInternals/ariaDetailsElements
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaDetailsElements
---

{{APIRef("DOM")}}

ویژگی **`ariaDetailsElements`** از رابط {{domxref("ElementInternals")}} یک آرایه شامل عنصر (یا عناصری) است که جزئیات دسترس‌پذیر (accessible details) را برای عنصر موردنظر فراهم می‌کنند. جزئیات دسترس‌پذیر مشابه توضیح دسترس‌پذیر (به {{domxref("ElementInternals/ariaDescribedByElements","ariaDescribedByElements")}} مراجعه کنید) است، اما اطلاعات مفصل‌تری ارائه می‌دهد.

مبحث [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) شامل اطلاعات بیشتری در مورد نحوه استفاده از این صفت (attribute) و این ویژگی (property) است.

## مقدار

یک آرایه از زیرکلاس‌های {{domxref("HTMLElement")}}.
متن داخلی این عناصر را می‌توان با فاصله به هم متصل کرد تا جزئیات دسترس‌پذیر به دست آید.

هنگام خواندن، آرایه بازگردانده‌شده ایستا و فقط‌خواندنی است.
هنگام نوشتن، آرایه اختصاصداده‌شده کپی می‌شود: تغییرات بعدی در آرایه بر مقدار ویژگی تأثیر نمی‌گذارد.

## توضیحات

این ویژگی یک جایگزین انعطاف‌پذیر برای استفاده از صفت [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) به‌منظور تنظیم اطلاعات جزئیات دسترس‌پذیر است.
برخلاف `aria-details`، عناصری که به این ویژگی نسبت داده می‌شوند لزوماً نیازی به داشتن صفت [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) ندارند.

این ویژگی، صفت [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) عنصر را هنگام تعریف‌شدن بازتاب می‌دهد، اما فقط برای مقادیر `id` فهرست‌شده‌ای که با عناصر معتبر در محدوده (in-scope) تطابق دارند.
اگر این ویژگی تنظیم شود، صفت متناظر پاک می‌شود.
برای اطلاعات بیشتر در مورد ارجاع عناصر بازتاب‌شده و محدوده، به [ارجاع عناصر بازتاب‌شده](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _Reflected attributes_ مراجعه کنید.

## مثال‌ها

مثال‌های موجود در اسناد زیر مرتبط هستند:

- {{domxref("Element.ariaDetailsElements")}} معادل DOM این ویژگی است.
  به همان روش استفاده می‌شود، اما درون DOM به جای یک DOM سایه (shadow DOM) و/یا عنصر سفارشی (custom element).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- صفت [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details)
- {{domxref("Element.ariaDetailsElements")}}
- [ارجاع عناصر بازتاب‌شده](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _Attribute reflection_.