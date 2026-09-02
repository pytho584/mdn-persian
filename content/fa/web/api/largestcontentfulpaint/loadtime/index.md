---
title: "LargestContentfulPaint: loadTime property"
---

---
title: "LargestContentfulPaint: loadTime property"
short-title: loadTime
slug: Web/API/LargestContentfulPaint/loadTime
page-type: web-api-instance-property
browser-compat: api.LargestContentfulPaint.loadTime
---

{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`loadTime`** در رابط {{domxref("LargestContentfulPaint")}}، زمان بارگذاری عنصر را برمی‌گرداند.

## مقدار

یک {{domxref("DOMHighResTimeStamp","timestamp")}} (برچسب زمانی) که زمان بارگذاری عنصر را بر حسب میلی‌ثانیه نشان می‌دهد.

## مثال‌ها

### ثبت loadTime بزرگ‌ترین رنگ‌آمیزی محتوا

این مثال از یک {{domxref("PerformanceObserver")}} استفاده می‌کند که هنگام ثبت ورودی‌های جدید `largest-contentful-paint` در جدول زمانی عملکرد مرورگر، اعلان دریافت می‌کند. گزینه `buffered` برای دسترسی به ورودی‌هایی که پیش از ایجاد observer ثبت شده‌اند استفاده می‌شود.

```js
const observer = new PerformanceObserver((list) => {
  const entries = list.getEntries();
  const lastEntry = entries[entries.length - 1]; // Use the latest LCP candidate
  console.log(lastEntry.loadTime);
});
observer.observe({ type: "largest-contentful-paint", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}