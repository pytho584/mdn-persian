---
title: "PerformanceResourceTiming: responseStatus property"
short-title: responseStatus
slug: Web/API/PerformanceResourceTiming/responseStatus
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.responseStatus
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`responseStatus`**، کد وضعیت پاسخ HTTP را نشان می‌دهد که هنگام واکشی منبع برگردانده شده است.

این ویژگی به {{domxref("Response.status")}} در [Fetch API](/en-US/docs/Web/API/Fetch_API) نگاشت می‌شود.

## مقدار

ویژگی `responseStatus` می‌تواند مقادیر زیر را داشته باشد:

- عددی که [کد وضعیت پاسخ HTTP](/en-US/docs/Web/HTTP/Reference/Status) برگردانده‌شده هنگام واکشی منبع را نشان می‌دهد.
- اگر بررسی [CORS](/en-US/docs/Web/HTTP/Guides/CORS) ناموفق باشد، مقدار `0`.
- برای اشیاء {{HTMLElement("iframe")}} با مبدأ متقاطع (cross-origin)، مقدار `0`.

## نمونه‌ها

### بررسی اینکه آیا از کش استفاده شده است

از ویژگی `responseStatus` می‌توان برای بررسی منابع کش‌شده‌ای استفاده کرد که کد وضعیت پاسخ {{HTTPStatus("304")}} `Not Modified` را دارند.

مثال زیر از {{domxref("PerformanceObserver")}} استفاده می‌کند که با ثبت هر ورودی عملکرد جدید از نوع `resource` در جدول زمانی عملکرد مرورگر، اطلاع می‌دهد. از گزینهٔ `buffered` استفاده کنید تا بتوانید به ورودی‌هایی که پیش از ایجاد observer ثبت شده‌اند دسترسی داشته باشید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    if (entry.responseStatus === 304) {
      console.log(`${entry.name} was loaded from cache`);
    }
  });
});

observer.observe({ type: "resource", buffered: true });
```

مثال زیر از {{domxref("Performance.getEntriesByType()")}} استفاده می‌کند که فقط ورودی‌های عملکردی `resource` موجود در جدول زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  if (entry.responseStatus === 304) {
    console.log(`${entry.name} was loaded from cache`);
  }
});
```

همچنین اگر `responseStatus` در دسترس نبود، می‌توانید بررسی کنید که آیا ویژگی {{domxref("PerformanceResourceTiming.transferSize", "transferSize")}} مقدار `0` را بازگردانده است.

### کدهای وضعیت پاسخ با مبدأ متقاطع

اگر مقدار ویژگی `responseStatus` برابر با `0` باشد، احتمالاً منبع یک درخواست با مبدأ متقاطع است. برای اینکه کدهای وضعیت پاسخ با مبدأ متقاطع قابل مشاهده باشند، باید هدر پاسخ HTTP [CORS](/en-US/docs/Web/HTTP/Guides/CORS) یعنی {{HTTPHeader("Access-Control-Allow-Origin")}} تنظیم شود.

برای مثال، برای اینکه به `https://developer.mozilla.org` اجازهٔ مشاهدهٔ کدهای وضعیت پاسخ داده شود، منبع با مبدأ متقاطع باید این هدر را ارسال کند:

```http
Access-Control-Allow-Origin: https://developer.mozilla.org
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [کد وضعیت پاسخ HTTP](/en-US/docs/Web/HTTP/Reference/Status)
- {{domxref("Response.status")}}
- [CORS](/en-US/docs/Web/HTTP/Guides/CORS)