---
title: "PerformanceResourceTiming: requestStart property"
short-title: requestStart
slug: Web/API/PerformanceResourceTiming/requestStart
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.requestStart
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`requestStart`** یک {{domxref("DOMHighResTimeStamp","timestamp")}} (برچسب زمانی) را بلافاصله قبل از شروع درخواست مرورگر از سرور، حافظه نهان یا منبع محلی بازمی‌گرداند. اگر اتصال انتقال خراب شود و مرورگر درخواست را دوباره ارسال کند، مقدار بازگشتی شروع درخواست مجدد خواهد بود.

هیچ ویژگی _end_ برای `requestStart` وجود ندارد. برای اندازه‌گیری زمان درخواست، مقدار {{domxref("PerformanceResourceTiming.responseStart", "responseStart")}} - `requestStart` را محاسبه کنید (به مثال زیر مراجعه کنید).

## مقدار

ویژگی `requestStart` می‌تواند مقادیر زیر را داشته باشد:

- یک {{domxref("DOMHighResTimeStamp")}} که نشان‌دهنده زمان بلافاصله قبل از شروع درخواست مرورگر از سرور است.
- `0` اگر منبع فوراً از حافظه نهان بازیابی شود.
- `0` اگر درخواست منبع یک درخواست cross-origin باشد و هیچ هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} استفاده نشود.
- `0` اگر درخواست منبع لغو شده باشد.

زمانی که {{domxref("PerformanceResourceTiming.firstInterimResponseStart", "firstInterimResponseStart")}} غیرصفر است، نشان می‌دهد که باید برای [مرورگرهای پشتیبانی‌کننده](#browser_compatibility) همان مقدار `requestStart` باشد.

وقتی هیچ پاسخ میانی وجود ندارد، `requestStart` با `finalResponseHeadersStart` برابر است و `firstInterimResponseStart` صفر است.

## مثال‌ها

### اندازه‌گیری زمان درخواست

از ویژگی‌های `requestStart` و {{domxref("PerformanceResourceTiming.responseStart", "responseStart")}} می‌توان برای اندازه‌گیری مدت زمان درخواست استفاده کرد.

```js
const request = entry.responseStart - entry.requestStart;
```

مثال با استفاده از {{domxref("PerformanceObserver")}} که هنگام ثبت ورودی‌های عملکرد `resource` در جدول زمانی عملکرد مرورگر، اطلاع می‌دهد. از گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد ناظر استفاده کنید.

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

مثال با استفاده از {{domxref("Performance.getEntriesByType()")}} که فقط ورودی‌های عملکرد `resource` موجود در جدول زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  const request = entry.responseStart - entry.requestStart;
  if (request > 0) {
    console.log(`${entry.name}: Request time: ${request}ms`);
  }
});
```

### اطلاعات زمان‌بندی درخواست‌های cross-origin

اگر مقدار ویژگی `requestStart` صفر باشد، ممکن است منبع یک درخواست cross-origin باشد. برای اجازه مشاهده اطلاعات زمان‌بندی cross-origin، باید هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} تنظیم شود.

برای مثال، برای اجازه دادن به `https://developer.mozilla.org` برای دیدن منابع زمان‌بندی، منبع cross-origin باید ارسال کند:

```http
Timing-Allow-Origin: https://developer.mozilla.org
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTTPHeader("Timing-Allow-Origin")}}