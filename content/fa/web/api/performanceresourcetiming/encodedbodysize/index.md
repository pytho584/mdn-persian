---
title: "PerformanceResourceTiming: encodedBodySize property"
short-title: encodedBodySize
slug: Web/API/PerformanceResourceTiming/encodedBodySize
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.encodedBodySize
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`encodedBodySize`** اندازهٔ (به اوکتت) بدنهٔ دادهٔ باری را نشان می‌دهد که از طریق واکشی (HTTP یا حافظهٔ نهان) دریافت شده است، پیش از حذف هرگونه رمزگذاری محتوای اعمال‌شده (مانند gzip یا Brotli). اگر منبع از حافظهٔ نهان برنامه یا یک منبع محلی بازیابی شود، این ویژگی باید اندازهٔ بدنهٔ دادهٔ بار را پیش از حذف هرگونه رمزگذاری محتوای اعمال‌شده بازگرداند.

## مقدار

ویژگی `encodedBodySize` می‌تواند مقادیر زیر را داشته باشد:

- عددی که اندازهٔ (به اوکتت) بدنهٔ دادهٔ بار دریافت‌شده از واکشی (HTTP یا حافظهٔ نهان) را پیش از حذف هرگونه رمزگذاری محتوای اعمال‌شده نشان می‌دهد.
- `0` اگر منبع یک درخواست متقاطع-مبدأ (cross-origin) باشد و هیچ هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} استفاده نشده باشد.

## مثال‌ها

### بررسی اینکه آیا محتوا فشرده شده است

اگر ویژگی‌های `encodedBodySize` و {{domxref("PerformanceResourceTiming.decodedBodySize", "decodedBodySize")}} مقدار غیر از `null` داشته باشند و با هم تفاوت داشته باشند، محتوا فشرده شده است (مثلاً با gzip یا Brotli).

مثالی با استفاده از {{domxref("PerformanceObserver")}}، که هنگام ثبت ورودی‌های عملکرد جدید از نوع `resource` در خط زمانی عملکرد مرورگر اعلان می‌فرستد. برای دسترسی به ورودی‌هایی که پیش از ساخته‌شدن observer ثبت شده‌اند، از گزینهٔ `buffered` استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    const uncompressed =
      entry.decodedBodySize && entry.decodedBodySize === entry.encodedBodySize;
    if (uncompressed) {
      console.log(`${entry.name} was not compressed!`);
    }
  });
});

observer.observe({ type: "resource", buffered: true });
```

مثالی با استفاده از {{domxref("Performance.getEntriesByType()")}}، که فقط ورودی‌های عملکرد `resource` موجود در خط زمانی عملکرد مرورگر را در لحظهٔ فراخوانی این متد نمایش می‌دهد:

```js
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  const uncompressed =
    entry.decodedBodySize && entry.decodedBodySize === entry.encodedBodySize;
  if (uncompressed) {
    console.log(`${entry.name} was not compressed!`);
  }
});
```

### اطلاعات اندازهٔ محتوای متقاطع-مبدأ

اگر مقدار ویژگی `encodedBodySize` برابر با `0` باشد، منبع احتمالاً یک درخواست متقاطع-مبدأ است. برای افشای اطلاعات اندازهٔ محتوای متقاطع-مبدأ، باید هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} تنظیم شود.

برای مثال، برای آنکه `https://developer.mozilla.org` بتواند اندازه‌های محتوا را ببیند، منبع متقاطع-مبدأ باید هدر زیر را ارسال کند:

```http
Timing-Allow-Origin: https://developer.mozilla.org
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTTPHeader("Timing-Allow-Origin")}}