---
title: "PerformanceResourceTiming: nextHopProtocol property"
short-title: nextHopProtocol
slug: Web/API/PerformanceResourceTiming/nextHopProtocol
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.nextHopProtocol
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`nextHopProtocol`** رشته‌ای است که پروتکل شبکه‌ای مورد استفاده برای دریافت منبع را نشان می‌دهد، همان‌طور که توسط [شناسه پروتکل ALPN (RFC7301)](https://www.iana.org/assignments/tls-extensiontype-values/tls-extensiontype-values.xhtml#alpn-protocol-ids) مشخص شده است.

وقتی از پروکسی استفاده می‌شود، اگر اتصال تونلی برقرار شده باشد، این ویژگی شناسه پروتکل ALPN پروتکل تونل‌شده را برمی‌گرداند. در غیر این صورت، این ویژگی شناسه پروتکل ALPN اولین پرش به سمت پروکسی را برمی‌گرداند.

## مقدار

ویژگی `nextHopProtocol` می‌تواند مقادیر زیر را داشته باشد:

- رشته‌ای که پروتکل شبکه‌ای مورد استفاده برای دریافت منبع را نشان می‌دهد، همان‌طور که توسط [شناسه پروتکل ALPN (RFC7301)](https://www.iana.org/assignments/tls-extensiontype-values/tls-extensiontype-values.xhtml#alpn-protocol-ids) مشخص شده است. مقادیر معمول عبارت‌اند از:
  - `"http/0.9"`
  - `"http/1.0"`
  - `"http/1.1"`
  - `"h2"`
  - `"h2c"`
  - `"h3"`
- اگر منبع یک درخواست متقاطع (cross-origin) باشد و هیچ هدر پاسخ HTTP {‎{HTTPHeader("Timing-Allow-Origin")}} استفاده نشده باشد، یک رشته خالی.

## مثال‌ها

### ثبت منابعی که نه HTTP/2 استفاده می‌کنند و نه HTTP/3

ویژگی `nextHopProtocol` می‌تواند برای مشاهده مناطقی استفاده شود که از پروتکل HTTP/2 یا HTTP/3 استفاده نمی‌کنند.

مثال زیر از {{domxref("PerformanceObserver")}} استفاده می‌کند که با ثبت ورودی‌های عملکرد جدید `resource` در زمان‌بند عملکرد مرورگر، اطلاع می‌دهد. از گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    const protocol = entry.nextHopProtocol;
    if (protocol && !(protocol === "h2" || protocol === "h3")) {
      console.log(`${entry.name} uses ${protocol}.`);
    }
  });
});

observer.observe({ type: "resource", buffered: true });
```

مثال زیر از {{domxref("Performance.getEntriesByType()")}} استفاده می‌کند که فقط ورودی‌های عملکرد `resource` موجود در زمان‌بند عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  const protocol = entry.nextHopProtocol;
  if (protocol && !(protocol === "h2" || protocol === "h3")) {
    console.log(`${entry.name} uses ${protocol}.`);
  }
});
```

### اطلاعات پروتکل شبکه منابع متقاطع

اگر مقدار ویژگی `nextHopProtocol` یک رشته خالی باشد، ممکن است منبع یک درخواست متقاطع باشد. برای افشای اطلاعات پروتکل شبکه متقاطع، باید هدر پاسخ HTTP {‎{HTTPHeader("Timing-Allow-Origin")}} تنظیم شود.

برای مثال، برای اجازه دادن به `https://developer.mozilla.org` برای دیدن اطلاعات پروتکل شبکه، منبع متقاطع باید ارسال کند:

```http
Timing-Allow-Origin: https://developer.mozilla.org
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTTPHeader("Timing-Allow-Origin")}}
- {{Glossary("HTTP 2", "HTTP/2")}}
- {{Glossary("HTTP 3", "HTTP/3")}}