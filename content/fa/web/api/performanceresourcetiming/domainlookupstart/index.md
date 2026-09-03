---
title: "PerformanceResourceTiming: domainLookupStart property"
short-title: domainLookupStart
slug: Web/API/PerformanceResourceTiming/domainLookupStart
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.domainLookupStart
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`domainLookupStart`**، {{domxref("DOMHighResTimeStamp","timestamp")}} را درست پیش از آن‌که مرورگر جست‌وجوی نام دامنه را برای منبع آغاز کند بازمی‌گرداند.

## مقدار

ویژگی `domainLookupStart` می‌تواند مقادیر زیر را داشته باشد:

- یک {{domxref("DOMHighResTimeStamp")}} بلافاصله پیش از آن‌که مرورگر جست‌وجوی نام دامنه را برای منبع آغاز کند.
- `0` اگر منبع فوراً از حافظه پنهان (cache) بازیابی شده باشد.
- `0` اگر منبع یک درخواست متقاطع-مبدأ (cross-origin) باشد و هیچ هدر پاسخ HTTP‌ای با نام {{HTTPHeader("Timing-Allow-Origin")}} استفاده نشده باشد.

## مثال‌ها

### اندازه‌گیری زمان جست‌وجوی DNS

از ویژگی‌های `domainLookupStart` و {{domxref("PerformanceResourceTiming.domainLookupEnd", "domainLookupEnd")}} می‌توان برای اندازه‌گیری مدت‌زمان جست‌وجوی DNS استفاده کرد.

```js
const dns = entry.domainLookupEnd - entry.domainLookupStart;
```

مثال زیر با استفاده از {{domxref("PerformanceObserver")}} است که هنگام ثبت ورودی‌های کارایی جدید از نوع `resource` در خط زمانی کارایی مرورگر اطلاع می‌دهد. برای دسترسی به ورودی‌هایی که پیش از ایجاد observer ثبت شده‌اند، از گزینه `buffered` استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    const dns = entry.domainLookupEnd - entry.domainLookupStart;
    if (dns > 0) {
      console.log(`${entry.name}: DNS lookup duration: ${dns}ms`);
    }
  });
});

observer.observe({ type: "resource", buffered: true });
```

مثال زیر از {{domxref("Performance.getEntriesByType()")}} استفاده می‌کند که فقط ورودی‌های کارایی از نوع `resource` موجود در خط زمانی کارایی مرورگر را هنگام فراخوانی این متد نشان می‌دهد:

```js
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  const dns = entry.domainLookupEnd - entry.domainLookupStart;
  if (dns > 0) {
    console.log(`${entry.name}: DNS lookup duration: ${dns}ms`);
  }
});
```

### اطلاعات زمان‌بندی درخواست‌های متقاطع-مبدأ

اگر مقدار ویژگی `domainLookupStart` برابر با `0` باشد، احتمالاً منبع از طریق یک درخواست متقاطع-مبدأ (cross-origin) دریافت شده است. برای امکان مشاهده اطلاعات زمان‌بندی درخواست‌های متقاطع-مبدأ، باید هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} تنظیم شود.

برای مثال، برای اینکه `https://developer.mozilla.org` بتواند اطلاعات زمان‌بندی منابع را مشاهده کند، منبع متقاطع-مبدأ باید پاسخ زیر را ارسال کند:

```http
Timing-Allow-Origin: https://developer.mozilla.org
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTTPHeader("Timing-Allow-Origin")}}