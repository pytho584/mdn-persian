---
title: "IntersectionObserver: thresholds property"
---

---
title: "IntersectionObserver: thresholds property"
short-title: thresholds
slug: Web/API/IntersectionObserver/thresholds
page-type: web-api-instance-property
browser-compat: api.IntersectionObserver.thresholds
---

{{APIRef("Intersection Observer API")}}

ویژگی فقط‌خواندنی **`thresholds`** در رابط {{domxref("IntersectionObserver")}} فهرست آستانه‌های تقاطعی را برمی‌گرداند که هنگام نمونه‌سازی observer با {{domxref("IntersectionObserver.IntersectionObserver", "IntersectionObserver()")}} مشخص شده بودند.

اگر هنگام نمونه‌سازی شیء فقط یک نسبت آستانه (threshold ratio) ارائه شده باشد، این ویژگی آرایه‌ای خواهد بود که تنها همان مقدار را در خود دارد.

برای آشنایی با نحوه عملکرد آستانه‌ها، صفحه [Intersection Observer](/en-US/docs/Web/API/Intersection_Observer_API#thresholds) را ببینید.

## مقدار

آرایه‌ای از آستانه‌های تقاطع که در ابتدا با استفاده از ویژگی `threshold` هنگام نمونه‌سازی observer مشخص شده بودند.
اگر فقط یک آستانه (به‌صورت عدد تکی و نه درون آرایه) مشخص شده باشد، این مقدار آرایه تک‌عنصری شامل همان آستانه است.
صرف‌نظر از ترتیبی که آرایه `threshold` اصلی شما داشته است، این آرایه همیشه به ترتیب عددی صعودی مرتب شده است.

اگر هنگام استفاده از `IntersectionObserver()` برای نمونه‌سازی observer، هیچ گزینه `threshold` در نظر گرفته نشده باشد، مقدار `thresholds` برابر با `[0]` است.

> [!NOTE]
> اگرچه شیء `options` که می‌توانید در سازنده {{domxref("IntersectionObserver/IntersectionObserver","IntersectionObserver()")}} مشخص کنید، فیلدی به نام `threshold` دارد، این ویژگی `thresholds` نامیده می‌شود.
> اگر به‌طور تصادفی از `thresholds` به‌عنوان نام فیلد در `options` خود استفاده کنید، آرایه `thresholds` در نهایت `[0.0]` خواهد بود، که احتمالاً انتظار آن را ندارید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}