---
title: "IntersectionObserverEntry: intersectionRatio property"
short-title: intersectionRatio
slug: Web/API/IntersectionObserverEntry/intersectionRatio
page-type: web-api-instance-property
browser-compat: api.IntersectionObserverEntry.intersectionRatio
---

{{APIRef("Intersection Observer API")}}

خاصیت فقط‌خواندنی **`intersectionRatio`** در رابط {{domxref("IntersectionObserverEntry")}} به شما می‌گوید چه کسری از عنصر هدف در حال حاضر در محدودهٔ تقاطع ریشه قابل مشاهده است؛ این مقدار بین 0.0 و 1.0 است.

## مقدار

عددی بین 0.0 و 1.0 که نشان می‌دهد چه کسری از عنصر هدف واقعاً در مستطیل تقاطع ریشه قابل مشاهده است.
به‌طور دقیق‌تر، این مقدار نسبت مساحت مستطیل تقاطع ({{domxref("IntersectionObserverEntry.intersectionRect", "intersectionRect")}}) به مساحت مستطیل مرزی عنصر هدف ({{domxref("IntersectionObserverEntry.boundingClientRect", "boundingClientRect")}}) است.

اگر مساحت مستطیل مرزی عنصر هدف صفر باشد، مقدار بازگشتی زمانی 1 است که {{domxref("IntersectionObserverEntry.isIntersecting", "isIntersecting")}} برابر `true` باشد؛ در غیر این صورت مقدار بازگشتی 0 است.

## مثال‌ها

در این مثال ساده، یک callback تقاطع، ویژگی {{cssxref("opacity")}} هر عنصر هدف را به نسبت تقاطع آن عنصر با ریشه تنظیم می‌کند.

```js
function intersectionCallback(entries) {
  entries.forEach((entry) => {
    entry.target.style.opacity = entry.intersectionRatio;
  });
}
```

برای مشاهدهٔ یک مثال کاربردی‌تر، به [مدیریت تغییرات تقاطع](/en-US/docs/Web/API/Intersection_Observer_API/Timing_element_visibility#handling_intersection_changes) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}