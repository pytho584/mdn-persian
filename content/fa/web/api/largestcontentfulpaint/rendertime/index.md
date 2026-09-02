---
title: "LargestContentfulPaint: renderTime property"
---

---
title: "LargestContentfulPaint: renderTime property"
short-title: renderTime
slug: Web/API/LargestContentfulPaint/renderTime
page-type: web-api-instance-property
browser-compat: api.LargestContentfulPaint.renderTime
---

{{APIRef("Performance API")}}

خاصیت فقط-خواندنی **`renderTime`** از رابط {{domxref("LargestContentfulPaint")}} نشان‌دهنده زمانی است که عنصر روی صفحه نمایش داده شد.

## مقدار

خاصیت `renderTime` می‌تواند مقادیر زیر را داشته باشد:

- یک {{domxref("DOMHighResTimeStamp","timestamp")}} (برچسب زمانی) که زمان نمایش عنصر روی صفحه را بر حسب میلی‌ثانیه نشان می‌دهد.
- `0` یا یک {{domxref("DOMHighResTimeStamp","timestamp")}} نادقیق (coarsened) اگر منبع یک درخواست متقاطع (cross-origin) باشد و از هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} استفاده نشده باشد.

### زمان نمایش تصویر متقاطع (cross-origin)

به دلایل امنیتی، مقدار خاصیت `renderTime` در صورتی که منبع یک درخواست متقاطع باشد، در ابتدا `0` بود.

مرورگرها [اکنون ممکن است در این موارد یک زمان نمایش اندکی نادقیق را ارائه دهند](https://github.com/w3c/paint-timing/issues/104). برای [پشتیبانی مرورگر](#browser_compatibility) بررسی کنید.

برای نمایش اطلاعات دقیق‌تر زمان نمایش متقاطع، باید هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} تنظیم شود.

برای مثال، برای اجازه دادن به `https://developer.mozilla.org` برای دیدن یک `renderTime` دقیق، منبع متقاطع باید ارسال کند:

```http
Timing-Allow-Origin: https://developer.mozilla.org
```

### استفاده از `startTime` به جای `renderTime`

صرف‌نظر از دقت `renderTime`، توسعه‌دهندگان باید از {{domxref("PerformanceEntry.startTime", "startTime")}} به جای `renderTime` به عنوان زمان LCP استفاده کنند. این مقدار `renderTime` ورودی را برمی‌گرداند اگر `0` نباشد، و در غیر این صورت مقدار {{domxref("LargestContentfulPaint.loadTime", "loadTime")}} این ورودی را برمی‌گرداند، بنابراین نیاز به بررسی مقدار 0 برای مرورگرهای غیرپشتیبان را برطرف می‌کند.

## مثال‌ها

### ثبت زمان renderTime بزرگترین محتوای نقاشی شده

این مثال از یک {{domxref("PerformanceObserver")}} استفاده می‌کند که ورودی‌های عملکرد `largest-contentful-paint` جدید را هنگام ثبت در جدول زمانی عملکرد مرورگر اطلاع می‌دهد. گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده می‌شود.

```js
const observer = new PerformanceObserver((list) => {
  const entries = list.getEntries();
  const lastEntry = entries[entries.length - 1]; // Use the latest LCP candidate
  console.log(lastEntry.renderTime);
});
observer.observe({ type: "largest-contentful-paint", buffered: true });
```

## مشخصات

{{Specifications}}

## پشتیبانی مرورگر

{{Compat}}