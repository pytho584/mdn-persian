---
title: IntersectionObserverEntry
slug: Web/API/IntersectionObserverEntry
page-type: web-api-interface
browser-compat: api.IntersectionObserverEntry
---

{{APIRef("Intersection Observer API")}}

رابط **`IntersectionObserverEntry`** در [Intersection Observer API](/en-US/docs/Web/API/Intersection_Observer_API)، تقاطع بین عنصر هدف و ظرف ریشه (root container) آن را در یک لحظهٔ مشخص از تغییر توصیف می‌کند.

نمونه‌هایی از `IntersectionObserverEntry` در پارامتر `entries` به تابع بازگشت (callback) یک {{domxref("IntersectionObserver")}} تحویل داده می‌شوند؛ در غیر این صورت، این اشیاء فقط با فراخوانی {{domxref("IntersectionObserver.takeRecords()")}} قابل دریافت هستند.

## سازنده

- {{domxref("IntersectionObserverEntry.IntersectionObserverEntry", "IntersectionObserverEntry()")}} {{experimental_inline}}
  - : یک شیء `IntersectionObserverEntry` جدید می‌سازد.

## ویژگی‌های نمونه

- {{domxref("IntersectionObserverEntry.boundingClientRect")}} {{ReadOnlyInline}}
  - : مستطیل محدودهٔ عنصر هدف را به صورت یک {{domxref("DOMRectReadOnly")}} برمی‌گرداند. محدوده‌ها طبق آنچه در مستندات {{domxref("Element.getBoundingClientRect()")}} توضیح داده شده محاسبه می‌شوند.
- {{domxref("IntersectionObserverEntry.intersectionRatio")}} {{ReadOnlyInline}}
  - : نسبت `intersectionRect` به `boundingClientRect` را برمی‌گرداند.
- {{domxref("IntersectionObserverEntry.intersectionRect")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMRectReadOnly")}} برمی‌گرداند که نمایانگر ناحیهٔ قابل مشاهدهٔ هدف است.
- {{domxref("IntersectionObserverEntry.isIntersecting")}} {{ReadOnlyInline}}
  - : یک مقدار بولی است که اگر عنصر هدف با ریشهٔ مشاهده‌گر تقاطع (intersection observer) تقاطع داشته باشد، `true` است. اگر این مقدار `true` باشد، `IntersectionObserverEntry` گذار به حالت تقاطع را توصیف می‌کند؛ اگر `false` باشد، یعنی گذار از حالت تقاطع به عدم تقاطع است.
- {{domxref("IntersectionObserverEntry.rootBounds")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMRectReadOnly")}} برای ریشهٔ مشاهده‌گر تقاطع برمی‌گرداند.
- {{domxref("IntersectionObserverEntry.target")}} {{ReadOnlyInline}}
  - : عنصر {{domxref("Element")}} که تقاطع آن با ریشه تغییر کرده است.
- {{domxref("IntersectionObserverEntry.time")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که زمان ثبت تقاطع را نشان می‌دهد، نسبت به [time origin](/en-US/docs/Web/API/Performance/timeOrigin) مربوط به `IntersectionObserver`.

## متدهای نمونه

این رابط هیچ متدی ندارد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}