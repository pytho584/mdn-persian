---
title: "ElementInternals: ariaDescribedByElements property"
short-title: ariaDescribedByElements
slug: Web/API/ElementInternals/ariaDescribedByElements
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaDescribedByElements
---

{{APIRef("DOM")}}

خصوصیت **`ariaDescribedByElements`** از رابط {{domxref("ElementInternals")}} یک آرایه است که شامل عنصر (یا عناصری) می‌شود که توصیف قابل دسترس (accessible description) را برای عنصری که این خصوصیت به آن اعمال شده است فراهم می‌کنند. توصیف قابل دسترس مشابه برچسب قابل دسترس (accessible label) است (به {{domxref("Element/ariaLabelledByElements","ariaLabelledByElements")}} مراجعه کنید)، اما اطلاعات جزئی‌تری ارائه می‌دهد.

مبحث [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) حاوی اطلاعات بیشتری درباره نحوه استفاده از این ویژگی (attribute) و خصوصیت (property) است.

## مقدار (Value)

یک آرایه از زیرکلاس‌های {{domxref("HTMLElement")}}. متن درونی این عناصر می‌تواند با فاصله به هم متصل شود تا توصیف قابل دسترس به دست آید.

هنگام خواندن، آرایه بازگردانده شده ایستا و فقط خواندنی است. هنگام نوشتن، آرایه اختصاص داده شده کپی می‌شود: تغییرات بعدی در آرایه بر مقدار خصوصیت تأثیر نمی‌گذارد.

## توضیحات (Description)

این خصوصیت یک جایگزین انعطاف‌پذیر برای استفاده از ویژگی [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) جهت تنظیم توصیف قابل دسترس است. برخلاف `aria-describedby`، عناصر اختصاص داده شده به این خصوصیت نیازی به داشتن ویژگی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) ندارند.

این خصوصیت ویژگی [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) عنصر را منعکس می‌کند، اما فقط برای مقادیر `id` ارجاع داده شده که با عناصر معتبر درون دامنه (in-scope) مطابقت دارند. اگر خصوصیت تنظیم شود، ویژگی مربوطه پاک می‌شود. برای اطلاعات بیشتر درباره ارجاع‌های منعکس شده عناصر و دامنه به [Reflected element references](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _Reflected attributes_ مراجعه کنید.

## مثال‌ها (Examples)

مثال‌های موجود در مستندات زیر مرتبط هستند:

- {{domxref("Element.ariaDescribedByElements")}} معادل DOM این خصوصیت است. به همان روش استفاده می‌شود، اما درون DOM به جای یک DOM سایه (shadow DOM) و/یا عنصر سفارشی (custom element).

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید (See also)

- ویژگی [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby)
- {{domxref("Element.ariaDescribedByElements")}}
- [Reflected element references](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _Attribute reflection_