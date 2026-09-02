---
title: "LargestContentfulPaint: size property"
short-title: size
slug: Web/API/LargestContentfulPaint/size
page-type: web-api-instance-property
browser-compat: api.LargestContentfulPaint.size
---

{{APIRef("Performance API")}}

ویژگی فقط‑خواندنی **`size`** از رابط {{domxref("LargestContentfulPaint")}} اندازهٔ ذاتی عنصری را برمی‌گرداند که بزرگ‌ترین نقاشی محتوایی (Largest Contentful Paint) است.

اندازهٔ عنصر برابر است با `width` ضربدر `height` {{domxref("DOMRectReadOnly","مستطیل")}}ی که این عنصر روی صفحه ایجاد می‌کند.

## مقدار

یک عدد صحیح که نشان‌دهندهٔ عرض ضربدر ارتفاع عنصر است.

## مثال‌ها

### ثبت اندازهٔ بزرگ‌ترین عنصر نقاشی محتوایی

این مثال از {{domxref("PerformanceObserver")}} استفاده می‌کند تا ورودی‌های جدید عملکرد `largest-contentful-paint` را هنگام ثبت در جدول زمانی عملکرد مرورگر اطلاع‌رسانی کند. گزینهٔ `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده شده است.

```js
const observer = new PerformanceObserver((list) => {
  const entries = list.getEntries();
  const lastEntry = entries[entries.length - 1]; // از آخرین نامزد LCP استفاده کنید
  console.log(lastEntry.size);
});
observer.observe({ type: "largest-contentful-paint", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}