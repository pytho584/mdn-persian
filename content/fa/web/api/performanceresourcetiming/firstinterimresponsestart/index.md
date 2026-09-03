---
title: "PerformanceResourceTiming: firstInterimResponseStart property"
short-title: firstInterimResponseStart
slug: Web/API/PerformanceResourceTiming/firstInterimResponseStart
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.firstInterimResponseStart
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

خاصیت فقط‌خواندنی **`firstInterimResponseStart`** یک {{domxref("DOMHighResTimeStamp","زمان‌سنج")}} را بلافاصله پس از دریافت اولین بایت از پاسخ موقت 1xx (برای مثال {{httpstatus(100, "100 Continue")}} یا {{httpstatus(103, "103 Early Hints")}}) از سرور توسط مرورگر برمی‌گرداند.

هیچ خاصیت _end_ای برای `firstInterimResponseStart` وجود ندارد.

## مقدار

خاصیت `firstInterimResponseStart` می‌تواند مقادیر زیر را داشته باشد:

- یک {{domxref("DOMHighResTimeStamp")}} بلافاصله پس از دریافت اولین بایت‌های موقت پاسخ از سرور توسط مرورگر.
- `0` اگر منبع هیچ پاسخ موقتی ارسال نکرده باشد.
- `0` اگر منبع یک درخواست بین‌المنشأ (cross-origin) باشد و هیچ هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} استفاده نشده باشد.

> [!NOTE]
> از آنجا که Early Hints معمولاً فقط در درخواست ناوبری اصلی پشتیبانی می‌شوند که ذاتاً هم‌منشأ است، مقدار `0` معمولاً نشان می‌دهد که Early Hints **استفاده نشده** است.

زمانی که `firstInterimResponseStart` غیرصفر است، این نشان می‌دهد که باید با {{domxref("PerformanceResourceTiming.requestStart", "requestStart")}} برای [مرورگرهای پشتیبانی‌کننده](#browser_compatibility) یکسان باشد.

## مثال‌ها

### اندازه‌گیری زمان درخواست

از خاصیت‌های `firstInterimResponseStart` و `requestStart` می‌توان برای اندازه‌گیری مدت زمانی که مرورگر پس از ارسال درخواست برای دریافت یک پاسخ موقت صرف می‌کند، استفاده کرد.

```js
const request = entry.firstInterimResponseStart - entry.requestStart;
```

مثال زیر از یک {{domxref("PerformanceObserver")}} برای اطلاع‌یابی از ورودی‌های جدید عملکرد `resource` در زمان ثبت آن‌ها در جدول زمانی عملکرد مرورگر استفاده می‌کند. گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer به کار رفته است.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    const request = entry.firstInterimResponseStart - entry.requestStart;
    if (request > 0) {
      console.log(`${entry.name}: Interim response time: ${request}ms`);
    }
  });
});

observer.observe({ type: "resource", buffered: true });
```

مثال زیر از {{domxref("Performance.getEntriesByType()")}} استفاده می‌کند که فقط ورودی‌های عملکرد `resource` موجود در جدول زمانی عملکرد مرورگر در زمان فراخوانی متد را نشان می‌دهد.

```js
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  const request = entry.firstInterimResponseStart - entry.requestStart;
  if (request > 0) {
    console.log(`${entry.name}: Interim response time: ${request}ms`);
  }
});
```

### اطلاعات زمان‌بندی بین‌المنشأ

اگر مقدار خاصیت `firstInterimResponseStart` برابر `0` باشد، ممکن است منبع یک درخواست بین‌المنشأ باشد. برای امکان مشاهده اطلاعات زمان‌بندی بین‌المنشأ، باید هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} تنظیم شود.

برای مثال، برای اجازه دادن به `https://developer.mozilla.org` برای دیدن منابع زمان‌بندی، منبع بین‌المنشأ باید ارسال کند:

```http
Timing-Allow-Origin: https://developer.mozilla.org
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTTPHeader("Timing-Allow-Origin")}}
- {{domxref("PerformanceResourceTiming.finalResponseHeadersStart", "finalResponseHeadersStart")}}