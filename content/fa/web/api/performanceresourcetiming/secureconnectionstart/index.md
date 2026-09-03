---
title: "PerformanceResourceTiming: secureConnectionStart property"
slug: Web/API/PerformanceResourceTiming/secureConnectionStart
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.secureConnectionStart
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`secureConnectionStart`** یک {{domxref("DOMHighResTimeStamp","timestamp")}} را درست پیش از شروع فرآیند دست‌دهی (handshake) توسط مرورگر برای امن‌سازی اتصال فعلی برمی‌گرداند. اگر از اتصال امن استفاده نشود، این ویژگی صفر برمی‌گرداند.

## مقدار

ویژگی `secureConnectionStart` می‌تواند مقادیر زیر را داشته باشد:

- یک {{domxref("DOMHighResTimeStamp")}} که زمان درست پیش از شروع فرآیند دست‌دهی برای امن‌سازی اتصال فعلی را نشان می‌دهد، به شرطی که منبع از طریق یک اتصال امن واکشی شده باشد.
- `0` اگر از اتصال امن استفاده نشده باشد.
- `0` اگر منبع به‌صورت آنی از حافظهٔ نهان (cache) بازیابی شده باشد.
- `0` اگر منبع یک درخواست متقاطع‌المنشأ (cross-origin) باشد و هیچ هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} استفاده نشده باشد.

## مثال‌ها

### اندازه‌گیری زمان مذاکرهٔ TLS

ویژگی‌های `secureConnectionStart` و {{domxref("PerformanceResourceTiming.requestStart", "requestStart")}} می‌توانند برای اندازه‌گیری مدت زمان لازم برای انجام مذاکرهٔ TLS استفاده شوند.

```js
const tls = entry.requestStart - entry.secureConnectionStart;
```

مثال با استفاده از {{domxref("PerformanceObserver")}} که هنگام ثبت ورودی‌های performance از نوع `resource` در جدول زمانی عملکرد مرورگر، اطلاع‌رسانی می‌کند. برای دسترسی به ورودی‌های قبل از ایجاد observer از گزینهٔ `buffered` استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    const tls = entry.requestStart - entry.secureConnectionStart;
    if (tls > 0) {
      console.log(`${entry.name}: TLS negotiation duration: ${tls}ms`);
    }
  });
});

observer.observe({ type: "resource", buffered: true });
```

مثال با استفاده از {{domxref("Performance.getEntriesByType()")}} که فقط ورودی‌های performance از نوع `resource` موجود در جدول زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  const tls = entry.requestStart - entry.secureConnectionStart;
  if (tls > 0) {
    console.log(`${entry.name}: TLS negotiation duration: ${tls}ms`);
  }
});
```

### اطلاعات زمان‌بندی متقاطع‌المنشأ

اگر مقدار ویژگی `secureConnectionStart` برابر `0` باشد، منبع یا از اتصال امن استفاده نمی‌کند و یا یک درخواست متقاطع‌المنشأ است. برای اجازه دادن به مشاهدهٔ اطلاعات زمان‌بندی متقاطع‌المنشأ، باید هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} تنظیم شود.

برای مثال، برای اجازه دادن به `https://developer.mozilla.org` برای مشاهدهٔ منابع زمان‌بندی، منبع متقاطع‌المنشأ باید ارسال کند:

```http
Timing-Allow-Origin: https://developer.mozilla.org
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTTPHeader("Timing-Allow-Origin")}}