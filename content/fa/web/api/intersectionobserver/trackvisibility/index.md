---
title: "IntersectionObserver: trackVisibility property"
short-title: trackVisibility
slug: Web/API/IntersectionObserver/trackVisibility
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.IntersectionObserver.trackVisibility
---

{{APIRef("Intersection Observer API")}}{{SeeCompatTable}}

خاصیت فقط‌خواندنی **`trackVisibility`** در رابط {{domxref("IntersectionObserver")}} نشان می‌دهد که آیا مشاهده‌گر (observer) علاوه بر تقاطع‌های عنصر، قابلیت مشاهده (visibility) هدف را نیز ردیابی می‌کند یا خیر.

## مقدار

اگر قابلیت مشاهده برای محاسبات تقاطع ردیابی شود، `true` و در غیر این صورت `false`.

این مقدار با استفاده از آرگومان [`option.trackVisibility`](/en-US/docs/Web/API/IntersectionObserver/IntersectionObserver#trackvisibility) در سازندهٔ `IntersectionObserver()` تنظیم می‌شود.

## توضیحات

وقتی ردیابی قابلیت مشاهده فعال نباشد، مشاهده‌گر زمانی که عنصر هدف به viewport عنصر ریشه اسکرول می‌شود، اعلان‌هایی ارائه می‌کند. اما این به شما نمی‌گوید که آیا قابلیت مشاهدهٔ عنصر هدف به خطر افتاده است یا نه — ممکن است بخشی از آن توسط عنصر دیگری پوشانده شده باشد، شفافیت آن کاهش یافته باشد، یا توسط filter، transform یا تغییر دیگری تحریف شده باشد.

وقتی ردیابی قابلیت مشاهده فعال باشد، فقط عناصری که مرورگر آنها را قابل مشاهده می‌داند به‌عنوان متقاطع نشان داده می‌شوند. این الگوریتم محافظه‌کارانه است و ممکن است عناصری را که از نظر فنی قابل مشاهده هستند، مانند عناصری که فقط کاهش شفافیت اندکی دارند، از قلم بیندازد.

توجه داشته باشید که محاسبهٔ قابلیت مشاهده از نظر محاسباتی پرهزینه است. برای جلوگیری از اجرای بیش از حد مکرر این عملیات، از یک {{domxref("IntersectionObserver/delay","delay")}} برای محدود کردن حداقل دورهٔ گزارش‌دهی استفاده می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [زمان‌بندی قابلیت مشاهدهٔ عنصر با Intersection Observer API](/en-US/docs/Web/API/Intersection_Observer_API/Timing_element_visibility)