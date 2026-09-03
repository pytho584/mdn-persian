```
---
title: "PerformanceResourceTiming: connectEnd property"
short-title: connectEnd
slug: Web/API/PerformanceResourceTiming/connectEnd
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.connectEnd
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‑خواندنی **`connectEnd`**، {{domxref("DOMHighResTimeStamp","مهر زمانی")}} را بلافاصله پس از پایان برقراری اتصال مرورگر به سرور برای دریافت منبع (resource) برمی‌گرداند. مقدار این مهر زمانی شامل مدت زمان برقراری اتصال انتقال (transport connection) و همچنین سایر بازه‌های زمانی مانند دست‌دهی TLS و احراز هویت [SOCKS](https://en.wikipedia.org/wiki/SOCKS) می‌شود.

## مقدار

ویژگی `connectEnd` می‌تواند مقادیر زیر را داشته باشد:

- یک {{domxref("DOMHighResTimeStamp")}} که نشان‌دهندهٔ زمان پس از برقراری اتصال است.
- `0` اگر منبع به‌طور آنی از حافظهٔ نهان (cache) بازیابی شود.
- `0` اگر منبع یک درخواست بین‌المللی (cross-origin) باشد و هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} استفاده نشده باشد.

## مثال‌ها

### اندازه‌گیری زمان دست‌دهی TCP

ویژگی‌های `connectEnd` و {{domxref("PerformanceResourceTiming.connectStart", "connectStart")}} برای اندازه‌گیری مدت زمان دست‌دهی TCP قابل استفاده هستند.

```js
const tcp = entry.connectEnd - entry.connectStart;
```

مثال با استفاده از {{domxref("PerformanceObserver")}}، که با ثبت ورودی‌های عملکرد «resource» در جدول زمانی عملکرد مرورگر، آن‌ها را اعلام می‌کند. از گزینهٔ `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    const tcp = entry.connectEnd - entry.connectStart;
    if (tcp > 0) {
      console.log(`${entry.name}: مدت زمان دست‌دهی TCP: ${tcp}ms`);
    }
  });
});

observer.observe({ type: "resource", buffered: true });
```

مثال با استفاده از {{domxref("Performance.getEntriesByType()")}}، که فقط ورودی‌های عملکرد «resource» موجود در جدول زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  const tcp = entry.connectEnd - entry.connectStart;
  if (tcp > 0) {
    console.log(`${entry.name}: مدت زمان دست‌دهی TCP: ${tcp}ms`);
  }
});
```

### اطلاعات زمان‌بندی درخواست‌های بین‌المللی (cross-origin)

اگر مقدار ویژگی `connectEnd` برابر `0` باشد، ممکن است منبع یک درخواست بین‌المللی باشد. برای مشاهدهٔ اطلاعات زمان‌بندی درخواست‌های بین‌المللی، باید هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} تنظیم شود.

برای مثال، برای اجازه دادن به `https://developer.mozilla.org` برای مشاهدهٔ زمان‌بندی منابع، منبع بین‌المللی باید ارسال کند:

```http
Timing-Allow-Origin: https://developer.mozilla.org
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{HTTPHeader("Timing-Allow-Origin")}}
```