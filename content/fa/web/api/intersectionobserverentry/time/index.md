---
title: "IntersectionObserverEntry: time property"
---

---
title: "IntersectionObserverEntry: time property"
short-title: time
slug: Web/API/IntersectionObserverEntry/time
page-type: web-api-instance-property
browser-compat: api.IntersectionObserverEntry.time
---

{{APIRef("Intersection Observer API")}}

ویژگی فقطخواندنی **`time`** از رابط {{domxref("IntersectionObserverEntry")}} یک {{domxref("DOMHighResTimeStamp")}} است که زمان وقوع تغییر تقاطع را نسبت به زمان ایجاد سند نشان می‌دهد.

## Value

یک {{domxref("DOMHighResTimeStamp")}} که زمان وقوع تغییر تقاطع توصیف‌شده توسط `IntersectionObserverEntry` را برای عنصر {{domxref("IntersectionObserverEntry.target", "target")}} نشان می‌دهد. این زمان بر حسب میلی‌ثانیه از زمان ایجاد سندِ حاوی عنصر محاسبه می‌شود.

## Examples

برای یک مثال کامل که از ویژگی `time` برای پیگیری مدت زمان قابل مشاهده بودن عناصر برای کاربر استفاده می‌کند، به [Timing element visibility with the Intersection Observer API](/en-US/docs/Web/API/Intersection_Observer_API/Timing_element_visibility) مراجعه کنید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}