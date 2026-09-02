---
title: "LargestContentfulPaint: id property"
short-title: id
slug: Web/API/LargestContentfulPaint/id
page-type: web-api-instance-property
browser-compat: api.LargestContentfulPaint.id
---

{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`id`** از رابط {{domxref("LargestContentfulPaint")}}، شناسه (ID) عنصری را برمی‌گرداند که بزرگ‌ترین رنگ‌آمیزی محتوایی (largest contentful paint) است.

## مقدار

یک رشته حاوی شناسه عنصر، یا رشته خالی اگر چنین شناسه‌ای وجود نداشته باشد.

## مثال‌ها

### ثبت شناسه عنصر بزرگ‌ترین رنگ‌آمیزی محتوایی

این مثال از یک {{domxref("PerformanceObserver")}} استفاده می‌کند که ورودی‌های عملکرد `largest-contentful-paint` جدید را هنگام ثبت در جدول زمانی عملکرد مرورگر اطلاع‌رسانی می‌کند. گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده می‌شود.

```js
const observer = new PerformanceObserver((list) => {
  const entries = list.getEntries();
  const lastEntry = entries[entries.length - 1]; // Use the latest LCP candidate
  console.log(lastEntry.id);
});
observer.observe({ type: "largest-contentful-paint", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}