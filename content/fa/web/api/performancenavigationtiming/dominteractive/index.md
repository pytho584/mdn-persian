---
title: "PerformanceNavigationTiming: domInteractive property"
short-title: domInteractive
slug: Web/API/PerformanceNavigationTiming/domInteractive
page-type: web-api-instance-property
browser-compat: api.PerformanceNavigationTiming.domInteractive
---

{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`domInteractive`** یک {{domxref("DOMHighResTimeStamp")}} برمی‌گرداند که نشان‌دهندهٔ زمان دقیقاً قبل از آن است که عامل کاربر (user agent) [`readyState`](/en-US/docs/Web/API/Document/readyState) سند را روی `"interactive"` تنظیم کند.

> [!NOTE]
> این ویژگی **با** {{Glossary("Time to interactive")}} (TTI) یکی نیست. این ویژگی به زمانی اشاره دارد که ساخت DOM به پایان رسیده و تعامل با آن از طریق جاوااسکریپت ممکن است. همچنین به وضعیت `interactive` در {{domxref("Document.readyState")}} مراجعه کنید که با این ویژگی متناظر است.

اندازه‌گیری زمان پردازش DOM ممکن است اهمیت چندانی نداشته باشد، مگر اینکه سایت شما منبع HTML بسیار بزرگی برای ساخت مدل شیء سند (Document Object Model) داشته باشد.

اگر جاوااسکریپت مسدودکنندهٔ تجزیه (parser-blocking) وجود نداشته باشد، رویداد [`DOMContentLoaded`](/en-US/docs/Web/API/Document/DOMContentLoaded_event) (برای زمان‌سنجی به [`domContentLoadedEventStart`](/en-US/docs/Web/API/PerformanceNavigationTiming/domContentLoadedEventStart) مراجعه کنید) بلافاصله پس از `domInteractive` رخ می‌دهد.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}} که نشان‌دهندهٔ زمان دقیقاً قبل از تنظیم [`readyState`](/en-US/docs/Web/API/Document/readyState) سند روی `"interactive"` توسط عامل کاربر است.

## مثال‌ها

### ثبت زمان تعامل با DOM

از ویژگی `domInteractive` می‌توان برای ثبت زمانی که ساخت DOM به پایان رسیده و تعامل با آن ممکن است استفاده کرد.

مثال با استفاده از {{domxref("PerformanceObserver")}}، که ورودی‌های عملکرد `navigation` جدید را هنگام ثبت شدن در خط زمانی عملکرد مرورگر اطلاع‌رسانی می‌کند. از گزینهٔ `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    console.log(
      `${entry.name}: domInteractive time: ${entry.domInteractive}ms`,
    );
  });
});

observer.observe({ type: "navigation", buffered: true });
```

مثال با استفاده از {{domxref("Performance.getEntriesByType()")}}، که فقط ورودی‌های عملکرد `navigation` موجود در خط زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const entries = performance.getEntriesByType("navigation");
entries.forEach((entry) => {
  console.log(`${entry.name}: domInteractive time: ${entry.domInteractive}ms`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document.readyState")}}