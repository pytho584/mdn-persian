---
title: "PerformanceResourceTiming: redirectStart property"
short-title: redirectStart
slug: Web/API/PerformanceResourceTiming/redirectStart
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.redirectStart
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`redirectStart`** یک {{domxref("DOMHighResTimeStamp","timestamp")}} برمی‌گرداند که زمان شروع واکشی (fetch) آغازکنندهٔ تغییرمسیر را نشان می‌دهد.

اگر هنگام واکشی منبع، تغییرمسیرهای HTTP رخ دهد و هر تغییرمسیری که با مبدأ سند فعلی هم‌مبدأ نیست، الگوریتم بررسی مجاز بودن زمان (timing allow check) را با موفقیت بگذراند، این ویژگی زمان شروع واکشیِ آغازکنندهٔ تغییرمسیر را برمی‌گرداند؛ در غیر این صورت، صفر برمی‌گردد.

برای دریافت تعداد تغییرمسیرها، همچنین به {{domxref("PerformanceNavigationTiming.redirectCount")}} مراجعه کنید.

## مقدار

ویژگی `redirectStart` می‌تواند مقادیر زیر را داشته باشد:

- یک {{domxref("DOMHighResTimeStamp","timestamp")}} که زمان شروع واکشی‌ای را نشان می‌دهد که تغییرمسیر را آغاز می‌کند.
- `0` اگر تغییرمسیری وجود نداشته باشد.
- `0` اگر منبع یک درخواست بین‌مبدأ (cross-origin) باشد و هیچ هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} استفاده نشده باشد.

## مثال‌ها

### اندازه‌گیری زمان تغییرمسیر

از ویژگی‌های `redirectStart` و {{domxref("PerformanceResourceTiming.redirectEnd", "redirectEnd")}} می‌توان برای اندازه‌گیری مدت‌زمان تغییرمسیر استفاده کرد.

```js
const redirect = entry.redirectEnd - entry.redirectStart;
```

مثال زیر با استفاده از {{domxref("PerformanceObserver")}} کار می‌کند؛ این observer با ثبت ورودی‌های جدید عملکرد از نوع `resource` در بازه زمانی عملکرد مرورگر، اطلاع می‌دهد. از گزینهٔ `buffered` برای دسترسی به ورودی‌هایی استفاده کنید که پیش از ایجاد observer ثبت شده‌اند.

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

مثال زیر از {{domxref("Performance.getEntriesByType()")}} استفاده می‌کند که فقط ورودی‌های عملکرد `resource` حاضر در بازه زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  const redirect = entry.redirectEnd - entry.redirectStart;
  if (redirect > 0) {
    console.log(`${entry.name}: Redirect time: ${redirect}ms`);
  }
});
```

### اطلاعات زمان‌بندی بین‌مبدأ

اگر مقدار ویژگی `redirectStart` برابر با `0` باشد، منبع احتمالاً یک درخواست بین‌مبدأ است. برای اینکه مشاهدهٔ اطلاعات زمان‌بندی بین‌مبدأ ممکن شود، باید هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} تنظیم شود.

برای مثال، برای اینکه به `https://developer.mozilla.org` اجازه داده شود منابع زمان‌بندی را ببیند، منبع بین‌مبدأ باید هدر زیر را ارسال کند:

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