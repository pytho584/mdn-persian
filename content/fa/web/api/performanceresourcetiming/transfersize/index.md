---
title: "PerformanceResourceTiming: transferSize property"
short-title: transferSize
slug: Web/API/PerformanceResourceTiming/transferSize
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.transferSize
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`transferSize`** اندازهٔ منبع واکشی‌شده را بر حسب اکتت (octet) نشان می‌دهد. این اندازه شامل فیلدهای هدرِ پاسخ و همچنین بدنهٔ بارِ پاسخ است (طبق تعریف [RFC7230](https://httpwg.org/specs/rfc7230.html#message.body)).

اگر منبع از کش محلی دریافت شود، یا اگر منبعی با مبدأ متفاوت (cross-origin) باشد، این ویژگی مقدار صفر برمی‌گرداند.

## مقدار

ویژگی `transferSize` می‌تواند یکی از مقادیر زیر را داشته باشد:

- عددی که اندازهٔ منبع واکشی‌شده را بر حسب اکتت نشان می‌دهد. این اندازه شامل فیلدهای هدرِ پاسخ و [بدنهٔ بارِ پاسخ](https://httpwg.org/specs/rfc7230.html#message.body) می‌شود (RFC7230).
- در صورتی که منبع بلافاصله از یک کش بازیابی شده باشد، مقدار `0`.
- در صورتی که منبع نتیجهٔ یک درخواست متقاطع-مبدأ (cross-origin) باشد و هیچ هدر پاسخ HTTP با نام {{HTTPHeader("Timing-Allow-Origin")}} استفاده نشده باشد، مقدار `0`.

## مثال‌ها

### بررسی اینکه آیا محتوا از کش بارگذاری شده است

در محیط‌هایی که از ویژگی {{domxref("PerformanceResourceTiming.responseStatus", "responseStatus")}} پشتیبانی نمی‌کنند، می‌توان از ویژگی `transferSize` برای تشخیص cache hit استفاده کرد. اگر مقدار `transferSize` صفر باشد و اندازهٔ بدنهٔ رمزگشایی‌شدهٔ منبع غیرصفر باشد (به این معنی که منبع هم‌مبدأ است یا هدر {{HTTPHeader("Timing-Allow-Origin")}} را دارد)، آن منبع از کش محلی دریافت شده است.

مثال زیر از {{domxref("PerformanceObserver")}} استفاده می‌کند. این observer هنگام ثبت ورودی‌های عملکرد (performance entries) جدید از نوع `resource` در خط زمانی عملکردِ مرورگر، رویداد مربوط به آن‌ها را اطلاع می‌دهد. برای دسترسی به ورودی‌هایی که پیش از ایجاد observer ثبت شده‌اند، از گزینهٔ `buffered` استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    if (entry.transferSize === 0 && entry.decodedBodySize > 0) {
      console.log(`${entry.name} was loaded from cache`);
    }
  });
});

observer.observe({ type: "resource", buffered: true });
```

مثال زیر از {{domxref("Performance.getEntriesByType()")}} استفاده می‌کند که فقط ورودی‌های عملکردِ `resource` موجود در خط زمانی عملکرد مرورگر را در لحظهٔ فراخوانی این متد نشان می‌دهد:

```js
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  if (entry.transferSize === 0 && entry.decodedBodySize > 0) {
    console.log(`${entry.name} was loaded from cache`);
  }
});
```

### اطلاعات اندازهٔ محتوای متقاطع-مبدأ

اگر مقدار ویژگی `transferSize` برابر `0` باشد و محتوا از کش محلی بارگذاری نشده باشد، احتمالاً منبع یک درخواست متقاطع-مبدأ (cross-origin) است. برای افشای اطلاعات اندازهٔ محتوای متقاطع-مبدأ، لازم است هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} تنظیم شده باشد.

برای مثال، برای اینکه به `https://developer.mozilla.org` اجازه داده شود اندازهٔ محتوا را ببیند، منبع متقاطع-مبدأ باید این هدر را ارسال کند:

```http
Timing-Allow-Origin: https://developer.mozilla.org
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{HTTPHeader("Timing-Allow-Origin")}}