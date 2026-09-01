---
title: "ElementInternals: ariaOwnsElements property"
---

---
title: "ElementInternals: ariaOwnsElements property"
short-title: ariaOwnsElements
slug: Web/API/ElementInternals/ariaOwnsElements
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaOwnsElements
---

{{APIRef("DOM")}}

ویژگی **`ariaOwnsElements`** در رابط {{domxref("ElementInternals")}} آرایه‌ای شامل عنصر (یا عناصر) است که رابطهٔ بصری، عملکردی یا زمینه‌ای بین یک عنصر والد که این ویژگی روی آن اعمال می‌شود و عناصر فرزند آن را تعریف می‌کنند. این ویژگی زمانی استفاده می‌شود که سلسله‌مراتب DOM سایه‌ای (shadow DOM) نتواند این رابطه را نشان دهد و در غیر این صورت در دسترس فناوری کمکی قرار نخواهد گرفت.

موضوع [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns) اطلاعات بیشتری درباره نحوه استفاده از این صفت و ویژگی ارائه می‌دهد.

## مقدار

آرایه‌ای از زیرکلاس‌های {{domxref("HTMLElement")}}.

هنگام خواندن، آرایه بازگشتی ثابت و فقط‌خواندنی است.
هنگام نوشتن، آرایه اختصاص‌داده‌شده کپی می‌شود: تغییرات بعدی در آرایه مقدار ویژگی را تحت تأثیر قرار نمی‌دهد.

## توضیحات

این ویژگی یک جایگزین انعطاف‌پذیر برای استفاده از صفت [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns) جهت نشان دادن مالکیت یک عنصر است.
برخلاف `aria-owns`، عناصر اختصاص‌داده‌شده به این ویژگی نیازی به داشتن صفت [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) ندارند.

ویژگی، صفت [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns) عنصر را وقتی تعریف شده باشد منعکس می‌کند، اما فقط برای مقادیر مرجع `id` فهرست‌شده که با عناصر معتبر درون‌قلمرو مطابقت دارند.
اگر ویژگی تنظیم شود، صفت مربوطه پاک می‌شود.
برای اطلاعات بیشتر درباره بازتاب مراجع عناصر (reflected element references) و قلمرو، به [بازتاب مراجع عناصر](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _صفت‌های بازتاب‌شده_ مراجعه کنید.

## مثال‌ها

مثال‌های موجود در اسناد زیر مرتبط هستند:

- {{domxref("Element.ariaOwnsElements")}} معادل DOM این ویژگی است.
  به همین صورت استفاده می‌شود، اما در DOM به جای DOM سایه‌ای و/یا عنصر سفارشی.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- صفت [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns)
- {{domxref("Element.ariaOwnsElements")}}
- [بازتاب مراجع عناصر](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _بازتاب صفت‌ها_.