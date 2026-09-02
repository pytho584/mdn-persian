```
---
title: "IntersectionObserver: root property"
short-title: root
slug: Web/API/IntersectionObserver/root
page-type: web-api-instance-property
browser-compat: api.IntersectionObserver.root
---

{{APIRef("Intersection Observer API")}}

ویژگی فقط‌خواندنی **`root`** در رابط {{domxref("IntersectionObserver")}}، عنصر ({{domxref("Element")}}) یا سند ({{domxref("Document")}})‌ای را مشخص می‌کند که مرزهای آن به عنوان {{Glossary("bounding box")}} (جعبه مرزی) {{Glossary("viewport")}} (نمایش‌گاه) برای عنصر هدف (هدف مشاهده‌گر) در نظر گرفته می‌شود.

اگر `root` برابر با `null` باشد، از مرزهای نمایش‌گاه واقعی سند استفاده می‌شود.

## مقدار

یک شیء {{domxref("Element")}} یا {{domxref("Document")}} که جعبه مرزی آن به عنوان مرزهای نمایش‌گاه برای تعیین میزان دید عنصر هدف استفاده می‌شود. تقاطع این مستطیل مرزی، با اعمال هر حاشیه (margin) مشخص‌شده در گزینه‌های ارسال‌شده به سازنده {{domxref("IntersectionObserver.IntersectionObserver", "IntersectionObserver()")}}، مرزهای عنصر هدف، منهای مرزهای هر عنصر یا شیء دیگری که با عنصر هدف هم‌پوشانی دارد، به عنوان ناحیه قابل مشاهده عنصر هدف در نظر گرفته می‌شود.

اگر `root` برابر با `null` باشد، سند مالک (owning document) به عنوان ریشه استفاده می‌شود و مرزهای نمایش‌گاه آن (یعنی ناحیه قابل مشاهده سند) به عنوان مرزهای ریشه به کار می‌روند.

## مثال‌ها

این مثال، {{cssxref("border")}} (حاشیه) عنصر ریشه مشاهده‌گر تقاطع را به صورت یک خط سبز متوسط به ضخامت ۲ پیکسل تنظیم می‌کند.

```js
observer.root.style.border = "2px solid #44aa44";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [زمان‌بندی دید عناصر با استفاده از API Intersection Observer](/en-US/docs/Web/API/Intersection_Observer_API/Timing_element_visibility)
```