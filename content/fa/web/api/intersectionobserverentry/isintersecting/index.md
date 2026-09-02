---
title: "IntersectionObserverEntry: isIntersecting property"
short-title: isIntersecting
slug: Web/API/IntersectionObserverEntry/isIntersecting
page-type: web-api-instance-property
browser-compat: api.IntersectionObserverEntry.isIntersecting
---

{{APIRef("Intersection Observer API")}}

ویژگی فقط‌خواندنی **`isIntersecting`** در رابط {{domxref("IntersectionObserverEntry")}} یک مقدار بولی است که اگر عنصرِ هدف با ریشهٔ (root) مشاهده‌گر تقاطع (intersection observer) تقاطع داشته باشد، `true` خواهد بود.

اگر این مقدار `true` باشد، آنگاه `IntersectionObserverEntry` گذار به حالت تقاطع را توصیف می‌کند؛ اگر `false` باشد، یعنی گذار از وضعیت تقاطع به وضعیت عدم تقاطع انجام شده است.

## مقدار

یک مقدار بولی که نشان می‌دهد آیا عنصر {{domxref("IntersectionObserverEntry.target", "target")}} به حالت تقاطع وارد شده است (`true`) یا از حالت تقاطع خارج شده است (`false`).

## مثال‌ها

در این مثال ساده، یک callback تقاطع برای به‌روزرسانی شمارنده‌ای به کار رفته است که تعداد عناصرِ هدفِ در حال تقاطع با {{domxref("IntersectionObserver.root", "intersection root", "", 1)}} را نشان می‌دهد.

```js
function intersectionCallback(entries) {
  entries.forEach((entry) => {
    if (entry.isIntersecting) {
      intersectingCount += 1;
    } else {
      intersectingCount -= 1;
    }
  });
}
```

برای مشاهدهٔ یک مثال ملموس‌تر، به [مدیریت تغییرات تقاطع](/en-US/docs/Web/API/Intersection_Observer_API/Timing_element_visibility#handling_intersection_changes) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}