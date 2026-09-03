---
title: "PerformanceElementTiming: element property"
short-title: element
slug: Web/API/PerformanceElementTiming/element
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceElementTiming.element
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

ویژگی فقط‑خواندنی **`element`** از رابط {{domxref("PerformanceElementTiming")}} یک {{domxref("Element")}} برمی‌گرداند که اشاره‌گری به عنصر تحت نظارت است.

## مقدار

یک {{domxref("Element")}}، یا اگر عنصر یک عنصر [DOM سایه‌ای](/en-US/docs/Web/API/Web_components/Using_shadow_DOM) باشد، [`null`](/en-US/docs/Web/JavaScript/Reference/Operators/null) برمی‌گرداند.

## مثال‌ها

### ثبت عنصر تحت نظارت

در این مثال، یک عنصر {{HTMLElement("img")}} با افزودن ویژگی [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming) تحت نظارت قرار گرفته است. یک {{domxref("PerformanceObserver")}} ثبت می‌شود تا همه ورودی‌های عملکرد از نوع `"element"` را دریافت کند و از پرچم `buffered` برای دسترسی به داده‌های قبل از ایجاد observer استفاده می‌شود. عنصر DOM که تحت نظارت است در کنسول ثبت می‌شود.

```html
<img src="image.jpg" alt="a nice image" elementtiming="big-image" />
```

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    if (entry.identifier === "big-image") {
      console.log(entry.element);
    }
  });
});
observer.observe({ type: "element", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}