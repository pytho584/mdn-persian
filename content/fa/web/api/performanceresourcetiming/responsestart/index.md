```yaml
---
title: "PerformanceResourceTiming: responseStart property"
short-title: responseStart
slug: Web/API/PerformanceResourceTiming/responseStart
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.responseStart
---
```

{{APIRef("Performance API")}}{{AvailableInWorkers}}

خاصیت فقط خواندنی **`responseStart`** یک {{domxref("DOMHighResTimeStamp","timestamp")}} را بلافاصله پس از دریافت اولین بایت پاسخ از سرور، کش یا منبع محلی توسط مرورگر برمی‌گرداند.

## مقدار

خاصیت `responseStart` می‌تواند مقادیر زیر را داشته باشد:

- یک {{domxref("DOMHighResTimeStamp")}} بلافاصله پس از دریافت اولین بایت پاسخ از سرور توسط مرورگر.
- `0` اگر منبع به‌طور آنی از یک کش بازیابی شده باشد.
- `0` اگر منبع یک درخواست بین‌مبدئی (cross-origin) باشد و از هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} استفاده نشده باشد.
- `0` اگر منبع یک درخواست لغو شده باشد.

## مثال‌ها

### اندازه‌گیری زمان درخواست

از خاصیت‌های `responseStart` و {{domxref("PerformanceResourceTiming.requestStart", "requestStart")}} می‌توان برای اندازه‌گیری مدت زمان درخواست استفاده کرد.

```js
const request = entry.responseStart - entry.requestStart;
```

مثال با استفاده از {{domxref("PerformanceObserver")}}، که با ثبت ورودی‌های جدید عملکرد `resource` در جدول زمانی عملکرد مرورگر، اطلاع‌رسانی می‌کند. از گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    const request = entry.responseStart - entry.requestStart;
    if (request > 0) {
      console.log(`${entry.name}: Request time: ${request}ms`);
    }
  });
});

observer.observe({ type: "resource", buffered: true });
```

مثال با استفاده از {{domxref("Performance.getEntriesByType()")}}، که فقط ورودی‌های عملکرد `resource` موجود در جدول زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  const request = entry.responseStart - entry.requestStart;
  if (request > 0) {
    console.log(`${entry.name}: Request time: ${request}ms`);
  }
});
```

### اطلاعات زمان‌بندی بین‌مبدئی

اگر مقدار خاصیت `responseStart` برابر `0` باشد، ممکن است منبع یک درخواست بین‌مبدئی باشد. برای مشاهده اطلاعات زمان‌بندی بین‌مبدئی، باید هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} تنظیم شود.

برای مثال، برای اجازه به `https://developer.mozilla.org` برای مشاهده زمان‌بندی منابع، منبع بین‌مبدئی باید ارسال کند:

```http
Timing-Allow-Origin: https://developer.mozilla.org
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTTPHeader("Timing-Allow-Origin")}}