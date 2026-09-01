---
title: "ElementInternals: ariaFlowToElements property"
short-title: ariaFlowToElements
slug: Web/API/ElementInternals/ariaFlowToElements
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaFlowToElements
---

{{APIRef("DOM")}}

ویژگی **`ariaFlowToElements`** در رابط {{domxref("ElementInternals")}} آرایه‌ای شامل عنصر (یا عناصری) است که ترتیب خواندن جایگزینی برای محتوا فراهم می‌کنند و ترتیب خواندن پیش‌فرض عمومی را به صلاح‌دید کاربر لغو می‌کنند. اگر تنها یک عنصر ارائه شود، این عنصر، عنصر بعدی در ترتیب خواندن است. اگر چندین عنصر ارائه شوند، هر عنصر نشان‌دهنده یک مسیر احتمالی است که باید برای انتخاب به کاربر ارائه شود.

مبحث [`aria-flowto`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-flowto) اطلاعات بیشتری درباره نحوه استفاده از این ویژگی و صفت ارائه می‌دهد.

## مقدار

آرایه‌ای از زیرکلاس‌های {{domxref("HTMLElement")}}.

هنگام خواندن، آرایه بازگردانده‌شده ایستا و فقط‌خواندنی است. هنگام نوشتن، آرایه اختصاص‌داده‌شده کپی می‌شود: تغییرات بعدی در آرایه بر مقدار ویژگی تأثیری نمی‌گذارد.

## توضیحات

این ویژگی جایگزینی انعطاف‌پذیر برای استفاده از صفت [`aria-flowto`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-flowto) برای تنظیم ترتیب خواندن جایگزین است. برخلاف `aria-flowto`، عناصری که به این ویژگی اختصاص داده می‌شوند لزومی ندارد دارای ویژگی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) باشند.

این ویژگی صفت [`aria-flowto`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-flowto) عنصر را وقتی تعریف شده باشد بازتاب می‌دهد، اما فقط برای مقادیر مرجع `id` فهرست‌شده که با عناصر معتبر در دامنه مطابقت دارند. اگر این ویژگی تنظیم شود، صفت مربوطه پاک می‌شود. برای اطلاعات بیشتر درباره ارجاع‌های بازتاب‌شده به عناصر و دامنه، به [ارجاع‌های بازتاب‌شده به عناصر](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _Reflected attributes_ مراجعه کنید.

## مثال‌ها

مثال‌های موجود در اسناد زیر مرتبط هستند:

- {{domxref("Element.ariaFlowToElements")}} معادل DOM این ویژگی است. به همان شکل استفاده می‌شود، اما در DOM به جای shadow DOM و/یا عنصر سفارشی.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- صفت [`aria-flowto`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-flowto)
- {{domxref("Element.ariaFlowToElements")}}
- [ارجاع‌های بازتاب‌شده به عناصر](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _Attribute reflection_.