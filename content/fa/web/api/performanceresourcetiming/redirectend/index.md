---
title: "PerformanceResourceTiming: redirectEnd property"
short-title: redirectEnd
slug: Web/API/PerformanceResourceTiming/redirectEnd
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.redirectEnd
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`redirectEnd`** یک {{domxref("DOMHighResTimeStamp","timestamp")}} را بلافاصله پس از دریافت آخرین بایت از پاسخ آخرین تغییرمسیر (redirect) برمی‌گرداند.

هنگام واکشی یک منبع، اگر چندین تغییرمسیر HTTP وجود داشته باشد، و هر یک از تغییرمسیرها مبدأیی متفاوت با سند فعلی داشته باشند، و الگوریتم بررسی مجاز بودن زمان‌بندی (timing allow check) برای هر منبع تغییرمسیر یافته با موفقیت اجرا شود، این ویژگی زمان بلافاصله پس از دریافت آخرین بایت از پاسخ آخرین تغییرمسیر را برمی‌گرداند؛ در غیر این صورت، صفر برگردانده می‌شود.

برای دریافت تعداد تغییرمسیرها، به {{domxref("PerformanceNavigationTiming.redirectCount")}} نیز مراجعه کنید.

## مقدار

ویژگی `redirectEnd` می‌تواند مقادیر زیر را داشته باشد:

- یک {{domxref("DOMHighResTimeStamp","timestamp")}} بلافاصله پس از دریافت آخرین بایت از پاسخ آخرین تغییرمسیر.
- `0` اگر هیچ تغییرمسیری وجود نداشته باشد.
- `0` اگر درخواست، یک درخواست متقاطع‌المنشأ (cross-origin) باشد و از هدر پاسخ {{HTTPHeader("Timing-Allow-Origin")}} استفاده نشده باشد.

## مثال‌ها

### اندازه‌گیری زمان تغییرمسیر

ویژگی‌های `redirectEnd` و {{domxref("PerformanceResourceTiming.redirectStart", "redirectStart")}} می‌توانند برای اندازه‌گیری مدت زمان تغییرمسیر استفاده شوند.

```js
const redirect = entry.redirectEnd - entry.redirectStart;
```

مثال با استفاده از {{domxref("PerformanceObserver")}}، که ورودی‌های جدید عملکرد `resource` را هنگام ثبت در خط زمانی عملکرد مرورگر اطلاع‌رسانی می‌کند. برای دسترسی به ورودی‌های مربوط به قبل از ایجاد observer از گزینه `buffered` استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    const redirect = entry.redirectEnd - entry.redirectStart;
    if (redirect > 0) {
      console.log(`${entry.name}: Redirect time: ${redirect}ms`);
    }
  });
});

observer.observe({ type: "resource", buffered: true });
```

مثال با استفاده از {{domxref("Performance.getEntriesByType()")}}، که فقط ورودی‌های عملکرد `resource` موجود در خط زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  const redirect = entry.redirectEnd - entry.redirectStart;
  if (redirect > 0) {
    console.log(`${entry.name}: Redirect time: ${redirect}ms`);
  }
});
```

### اطلاعات زمان‌بندی متقاطع‌المنشأ

اگر مقدار ویژگی `redirectEnd` برابر با `0` باشد، ممکن است منبع یک درخواست متقاطع‌المنشأ باشد. برای مشاهده اطلاعات زمان‌بندی متقاطع‌المنشأ، باید هدر پاسخ {{HTTPHeader("Timing-Allow-Origin")}} تنظیم شود.

به عنوان مثال، برای اینکه `https://developer.mozilla.org` بتواند زمان‌بندی منابع را مشاهده کند، منبع متقاطع‌المنشأ باید ارسال کند:

```http
Timing-Allow-Origin: https://developer.mozilla.org
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("PerformanceNavigationTiming.redirectCount")}}
- {{HTTPHeader("Timing-Allow-Origin")}}