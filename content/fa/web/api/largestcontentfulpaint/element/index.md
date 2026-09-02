---
title: "LargestContentfulPaint: element property"
short-title: element
slug: Web/API/LargestContentfulPaint/element
page-type: web-api-instance-property
browser-compat: api.LargestContentfulPaint.element
---

{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`element`** در رابط {{domxref("LargestContentfulPaint")}}، یک شیء را برمی‌گرداند که نمایانگر {{domxref("Element")}} مربوط به بزرگ‌ترین نقاشی محتوایی (largest contentful paint) است.

## مقدار

یک {{domxref("Element")}}.

## مثال‌ها

### ثبت عنصر بزرگ‌ترین نقاشی محتوایی

در این مثال از یک {{domxref("PerformanceObserver")}} استفاده می‌شود که ورودی‌های عملکردی جدید `largest-contentful-paint` را هنگام ثبت در خط زمانی عملکرد مرورگر اطلاع‌رسانی می‌کند. گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده شده است.

```js
const observer = new PerformanceObserver((list) => {
  const entries = list.getEntries();
  const lastEntry = entries[entries.length - 1]; // Use the latest LCP candidate
  console.log(lastEntry.element);
});
observer.observe({ type: "largest-contentful-paint", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}