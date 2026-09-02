---
title: "IntersectionObserverEntry: target property"
short-title: target
slug: Web/API/IntersectionObserverEntry/target
page-type: web-api-instance-property
browser-compat: api.IntersectionObserverEntry.target
---

{{APIRef("Intersection Observer API")}}

ویژگی **`target`** (فقط‌خواندنی) از رابط {{domxref("IntersectionObserverEntry")}} مشخص می‌کند کدام {{domxref("Element")}} هدف‌گیری شده، میزان تقاطع خود با ریشه تقاطع (intersection root) را تغییر داده است.

## مقدار

ویژگی `target` در `IntersectionObserverEntry` تعیین می‌کند کدام {{domxref("Element")}} که قبلاً با فراخوانی {{domxref("IntersectionObserver.observe()")}} هدف‌گیری شده بود، تغییری در تقاطع با ریشه را تجربه کرده است.

## مثال‌ها

در این مثال ساده، {{cssxref("opacity")}} هر عنصر هدف‌گیری شده، برابر با {{domxref("IntersectionObserverEntry.intersectionRatio", "intersectionRatio")}} آن قرار داده می‌شود.

```js
function intersectionCallback(entries) {
  entries.forEach((entry) => {
    entry.target.style.opacity = entry.intersectionRatio;
  });
}
```

برای مشاهده یک مثال ملموس‌تر، به [مدیریت تغییرات تقاطع](/en-US/docs/Web/API/Intersection_Observer_API/Timing_element_visibility#handling_intersection_changes) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
