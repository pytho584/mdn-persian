---
title: "PerformanceResourceTiming: decodedBodySize property"
---

---
title: "PerformanceResourceTiming: decodedBodySize property"
short-title: decodedBodySize
slug: Web/API/PerformanceResourceTiming/decodedBodySize
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.decodedBodySize
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`decodedBodySize`** اندازه (بر حسب اکتت) بدنه پیام را برمی‌گرداند که از طریق fetch (HTTP یا حافظه پنهان) دریافت شده و پس از آن هرگونه کدگذاری محتوای اعمال‌شده (مانند gzip یا Brotli) از آن حذف شده است. اگر منبع از حافظه پنهان برنامه یا منابع محلی بازیابی شود، اندازه بار (payload) را پس از حذف هرگونه کدگذاری محتوای اعمال‌شده برمی‌گرداند.

## مقدار

ویژگی `decodedBodySize` می‌تواند مقادیر زیر را داشته باشد:

- عددی که اندازه (بر حسب اکتت) بدنه پیام دریافت‌شده از fetch (HTTP یا حافظه پنهان) را پس از حذف هرگونه کدگذاری محتوای اعمال‌شده نشان می‌دهد.
- `0` اگر منبع یک درخواست متقاطع-منشأ باشد و هیچ هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} استفاده نشده باشد.

## مثال‌ها

### بررسی اینکه آیا محتوا فشرده شده است

اگر ویژگی‌های `decodedBodySize` و {{domxref("PerformanceResourceTiming.encodedBodySize", "encodedBodySize")}} غیر null باشند و با هم تفاوت داشته باشند، محتوا فشرده شده است (مثلاً gzip یا Brotli).

مثال زیر از {{domxref("PerformanceObserver")}} استفاده می‌کند؛ این observer با ثبت ورودی‌های عملکردی `resource` جدید در خط زمانی عملکرد مرورگر، اطلاع می‌دهد. با استفاده از گزینه `buffered` می‌توانید به ورودی‌هایی که پیش از ایجاد observer ثبت شده‌اند نیز دسترسی داشته باشید.

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

مثال زیر از {{domxref("Performance.getEntriesByType()")}} استفاده می‌کند که فقط ورودی‌های عملکردی `resource` حاضر در خط زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

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

### اطلاعات اندازه محتوای متقاطع-منشأ

اگر مقدار ویژگی `decodedBodySize` برابر با `0` باشد، منبع ممکن است یک درخواست متقاطع-منشأ باشد. برای در دسترس قرار دادن اطلاعات اندازه محتوای متقاطع-منشأ، باید هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} تنظیم شود.

برای مثال، برای اینکه `https://developer.mozilla.org` بتواند اندازه محتوا را ببیند، منبع متقاطع-منشأ باید ارسال کند:

```http
Timing-Allow-Origin: https://developer.mozilla.org
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTTPHeader("Timing-Allow-Origin")}}