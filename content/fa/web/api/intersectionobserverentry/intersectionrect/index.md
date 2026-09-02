---
title: "IntersectionObserverEntry: intersectionRect property"
---

---
title: "IntersectionObserverEntry: intersectionRect property"
short-title: intersectionRect
slug: Web/API/IntersectionObserverEntry/intersectionRect
page-type: web-api-instance-property
browser-compat: api.IntersectionObserverEntry.intersectionRect
---

{{APIRef("Intersection Observer API")}}

ویژگی فقط‌خواندنی **`intersectionRect`** در رابط {{domxref("IntersectionObserverEntry")}} یک شیء {{domxref("DOMRectReadOnly")}} است که کوچک‌ترین مستطیلی را توصیف می‌کند که تمام بخشِ در حال حاضر قابل‌مشاهده از عنصر هدف را درون ریشهٔ تقاطع در بر می‌گیرد.

## مقدار

یک {{domxref("DOMRectReadOnly")}} که بخشِ در حال حاضر قابل‌مشاهده از عنصر هدف را درون مستطیل تقاطعِ ریشه توصیف می‌کند.

این مستطیل با محاسبهٔ اشتراک {{domxref("IntersectionObserverEntry", "boundingClientRect")}} با مستطیل‌های برشیِ (clip rectangles) تک‌تک اجدادِ {{domxref("IntersectionObserverEntry.target", "target")}} به‌دست می‌آید، به‌جز خودِ ریشهٔ تقاطع ({{domxref("IntersectionObserver.root", "root")}}).

## مثال‌ها

در این مثال ساده، یک callback تقاطع، مستطیل تقاطع را برای استفادهٔ بعدی توسط کدی که محتوای عناصر هدف را ترسیم می‌کند ذخیره می‌کند، به‌طوری که فقط ناحیهٔ قابل‌مشاهده دوباره ترسیم شود.

```js
function intersectionCallback(entries) {
  entries.forEach((entry) => {
    refreshZones.push({
      element: entry.target,
      rect: entry.intersectionRect,
    });
  });
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}