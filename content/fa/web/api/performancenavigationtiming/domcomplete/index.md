---
title: "PerformanceNavigationTiming: domComplete property"
short-title: domComplete
slug: Web/API/PerformanceNavigationTiming/domComplete
page-type: web-api-instance-property
browser-compat: api.PerformanceNavigationTiming.domComplete
---

{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`domComplete`** یک {{domxref("DOMHighResTimeStamp")}} برمی‌گرداند که زمانِ درست قبل از اینکه عامل کاربر (user agent) حالت [`readyState`](/en-US/docs/Web/API/Document/readyState) سند را روی `"complete"` تنظیم کند را نشان می‌دهد.

همچنین به حالت `complete` در {{domxref("Document.readyState")}} توجه کنید که با این ویژگی متناظر است و به حالتی اشاره دارد که در آن سند و همه‌ی منابع فرعی (sub-resources) بارگذاری شده‌اند. این حالت همچنین نشان می‌دهد که رویداد {{domxref("Window/load_event", "load")}} در آستانه‌ی رخ دادن است.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}} که نشان‌دهنده‌ی زمان درست قبل از تنظیم [`readyState`](/en-US/docs/Web/API/Document/readyState) سند به `"complete"` توسط عامل کاربر است.

## مثال‌ها

### ثبت زمان تکمیل DOM

از ویژگی `domComplete` می‌توان برای ثبت (log) زمان تکمیل شدن DOM استفاده کرد.

مثال زیر از {{domxref("PerformanceObserver")}} استفاده می‌کند که هنگام ثبت ورودی‌های عملکردی جدید از نوع `navigation` در خط زمانی عملکرد مرورگر، اطلاع می‌دهد. برای دسترسی به ورودی‌های مربوط به قبل از ایجاد observer، از گزینه‌ی `buffered` استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    console.log(`${entry.name}: domComplete time: ${entry.domComplete}ms`);
  });
});

observer.observe({ type: "navigation", buffered: true });
```

مثال زیر از {{domxref("Performance.getEntriesByType()")}} استفاده می‌کند که فقط ورودی‌های عملکردی `navigation` موجود در خط زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const entries = performance.getEntriesByType("navigation");
entries.forEach((entry) => {
  console.log(`${entry.name}: domComplete time: ${entry.domComplete}ms`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document.readyState")}}