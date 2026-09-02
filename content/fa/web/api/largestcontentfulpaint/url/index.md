---
title: "LargestContentfulPaint: url property"
short-title: url
slug: Web/API/LargestContentfulPaint/url
page-type: web-api-instance-property
browser-compat: api.LargestContentfulPaint.url
---

{{APIRef("Performance API")}}

خاصیت فقط‌خواندنی **`url`** در رابط {{domxref("LargestContentfulPaint")}}، URL درخواست عنصر را در صورتی که عنصر یک تصویر باشد، برمی‌گرداند.

## مقدار

یک رشته (string) شامل URL.

## مثال‌ها

### ثبت url بزرگ‌ترین paint محتوایی

این مثال از {{domxref("PerformanceObserver")}} استفاده می‌کند تا ورودی‌های عملکرد جدید `largest-contentful-paint` را هنگام ثبت در زمان‌بندی عملکرد مرورگر اطلاع‌رسانی کند. گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده شده است.

```js
const observer = new PerformanceObserver((list) => {
  const entries = list.getEntries();
  const lastEntry = entries[entries.length - 1]; // Use the latest LCP candidate
  console.log(lastEntry.url);
});
observer.observe({ type: "largest-contentful-paint", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}