---
title: "PerformanceNavigationTiming: redirectCount property"
short-title: redirectCount
slug: Web/API/PerformanceNavigationTiming/redirectCount
page-type: web-api-instance-property
browser-compat: api.PerformanceNavigationTiming.redirectCount
---

{{APIRef("Performance API")}}

خاصیت فقط‌خواندنی **`redirectCount`** یک عدد را برمی‌گرداند که تعداد ریدایرکت‌ها را از آخرین ناوبری غیر-ریدایرکت در بافت مرور فعلی نشان می‌دهد.

هرچه تعداد ریدایرکت‌ها در یک صفحه بیشتر باشد، زمان بارگذاری صفحه طولانی‌تر است. برای بهبود کارایی صفحه وب خود، از ریدایرکت‌های متعدد خودداری کنید.

از ویژگی‌های {{domxref("PerformanceResourceTiming.redirectStart", "redirectStart")}} و {{domxref("PerformanceResourceTiming.redirectEnd", "redirectEnd")}} می‌توان برای اندازه‌گیری زمان ریدایرکت استفاده کرد. توجه داشته باشید که این مقادیر برای ریدایرکت‌های متقابل-دامنه (cross-origin) مقدار `0` برمی‌گردانند.

توجه داشته باشید که ریدایرکت‌های سمت کلاینت، مانند `<meta http-equiv="refresh" content="0; url=https://example.com/">`، در اینجا در نظر گرفته نمی‌شوند.

## مقدار

ویژگی `redirectCount` می‌تواند مقادیر زیر را داشته باشد:

- یک عدد که تعداد ریدایرکت‌ها را از آخرین ناوبری غیر-ریدایرکت در بافت مرور فعلی نشان می‌دهد.
- اگر ریدایرکت متقابل-دامنه باشد، مقدار `0`.

## مثال‌ها

### ثبت ورودی‌ها با ریدایرکت‌ها

ویژگی `redirectCount` می‌تواند برای بررسی وجود یک یا چند ریدایرکت استفاده شود. ما نام ورودی و زمان ریدایرکت را در صورت موجود بودن، ثبت می‌کنیم.

مثال با استفاده از {{domxref("PerformanceObserver")}}، که با ثبت شدن ورودی‌های جدید عملکرد `navigation` در جدول زمانی عملکرد مرورگر، اطلاع می‌دهد. از گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    const name = entry.name;
    const redirectCount = entry.redirectCount;
    const redirectTime = entry.redirectEnd - entry.redirectStart;
    if (redirectCount > 0) {
      console.log(`${name}: Redirect count: ${redirectCount}`);
      if (redirectTime > 0) {
        console.log(`${name}: Redirect time: ${redirectTime}ms`);
      }
    }
  });
});

observer.observe({ type: "navigation", buffered: true });
```

مثال با استفاده از {{domxref("Performance.getEntriesByType()")}}، که فقط ورودی‌های عملکرد `navigation` موجود در جدول زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const entries = performance.getEntriesByType("navigation");
entries.forEach((entry) => {
  const name = entry.name;
  const redirectCount = entry.redirectCount;
  const redirectTime = entry.redirectEnd - entry.redirectStart;
  if (redirectCount > 0) {
    console.log(`${name}: Redirect count: ${redirectCount}`);
    if (redirectTime > 0) {
      console.log(`${name}: Redirect time: ${redirectTime}ms`);
    }
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("PerformanceResourceTiming.redirectStart")}}
- {{domxref("PerformanceResourceTiming.redirectEnd")}}