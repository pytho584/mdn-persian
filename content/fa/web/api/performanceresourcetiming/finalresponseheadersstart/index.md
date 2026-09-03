---
title: "PerformanceResourceTiming: finalResponseHeadersStart property"
short-title: finalResponseHeadersStart
slug: Web/API/PerformanceResourceTiming/finalResponseHeadersStart
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.finalResponseHeadersStart
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`finalResponseHeadersStart`** یک {{domxref("DOMHighResTimeStamp","timestamp")}} را بلافاصله پس از آن‌که مرورگر نخستین بایت پاسخ نهایی سند (مثلاً {{httpstatus(200, "200 OK")}}) را از سرور دریافت می‌کند، برمی‌گرداند.

این ویژگی با **{{domxref("PerformanceResourceTiming.requestStart", "requestStart")}}** تفاوت دارد (که ممکن است به‌صورت **{{domxref("PerformanceResourceTiming.firstInterimResponseStart", "firstInterimResponseStart")}}** نیز نمایش داده شود)، زیرا این زمان از نخستین بایت‌های هر پاسخی، از جمله پاسخ‌های میانی (مثلاً 103 Early Hints) شروع می‌شود و ممکن است پاسخ نهایی خیلی دیرتر برسد.

وقتی هیچ پاسخ میانی وجود نداشته باشد، `requestStart` با `finalResponseHeadersStart` یکسان است و `firstInterimResponseStart` برابر 0 است.

هیچ ویژگی `_end_` برای `finalResponseHeadersStart` وجود ندارد.

## مقدار

ویژگی `finalResponseHeadersStart` می‌تواند مقادیر زیر را داشته باشد:

- یک {{domxref("DOMHighResTimeStamp")}} بلافاصله پس از دریافت نخستین بایت‌های پاسخ نهایی از سرور توسط مرورگر.
- `0`، اگر منبع (resource) با یک درخواست متقاطع-منشأ (cross-origin) دریافت شده باشد و هیچ هدر پاسخ HTTP با نام {{HTTPHeader("Timing-Allow-Origin")}} استفاده نشده باشد.

## مثال‌ها

### اندازه‌گیری زمان درخواست

از ویژگی‌های `finalResponseHeadersStart` و {{domxref("PerformanceResourceTiming.requestStart", "requestStart")}} می‌توان برای اندازه‌گیری مدت زمانی استفاده کرد که مرورگر پس از ارسال درخواست، صرف می‌کند تا دریافت پاسخ نهایی را آغاز کند.

```js
const request = entry.finalResponseHeadersStart - entry.requestStart;
```

مثال زیر از یک {{domxref("PerformanceObserver")}} استفاده می‌کند تا وقتی ورودی‌های کارایی `resource` جدید در خط زمانی کارایی مرورگر ثبت می‌شوند، آن‌ها را اعلان کند. گزینهٔ `buffered` برای دسترسی به ورودی‌هایی استفاده می‌شود که پیش از ایجاد observer ثبت شده‌اند.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    const request = entry.finalResponseHeadersStart - entry.requestStart;
    if (request > 0) {
      console.log(`${entry.name}: final response time: ${request}ms`);
    }
  });
});

observer.observe({ type: "resource", buffered: true });
```

مثال زیر از {{domxref("Performance.getEntriesByType()")}} استفاده می‌کند؛ این متد فقط ورودی‌های کارایی `resource` را نشان می‌دهد که در هنگام فراخوانیِ متد، در خط زمانی کارایی مرورگر وجود دارند.

```js
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  const request = entry.finalResponseHeadersStart - entry.requestStart;
  if (request > 0) {
    console.log(`${entry.name}: final response time: ${request}ms`);
  }
});
```

مثال زیر نحوهٔ اندازه‌گیری زمان بین آغاز هدرهای نخستین پاسخ و آغاز هدرهای پاسخ نهایی را نشان می‌دهد.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    const diff = entry.finalResponseHeadersStart - entry.responseStart;
    if ((entry.finalResponseHeadersStart > 0) & (diff > 0)) {
      console.log(
        `${entry.name}: time between first and final response start: ${diff}ms`,
      );
    }
  });
});

observer.observe({ type: "resource", buffered: true });
```

### اطلاعات زمان‌بندی متقاطع-منشأ

اگر مقدار ویژگی `finalResponseHeadersStart` برابر `0` باشد، احتمالاً منبع از طریق یک درخواست متقاطع-منشأ (cross-origin) دریافت شده است. برای اینکه امکان مشاهدهٔ اطلاعات زمان‌بندی متقاطع-منشأ فراهم شود، باید هدر پاسخ HTTP با نام {{HTTPHeader("Timing-Allow-Origin")}} تنظیم شود.

برای مثال، برای اینکه به `https://developer.mozilla.org` اجازه داده شود اطلاعات زمان‌بندی منابع را ببیند، منبع متقاطع-منشأ باید هدر زیر را ارسال کند:

```http
Timing-Allow-Origin: https://developer.mozilla.org
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTTPHeader("Timing-Allow-Origin")}}
- {{domxref("PerformanceResourceTiming.firstInterimResponseStart", "firstInterimResponseStart")}}