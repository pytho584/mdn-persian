---
title: "PerformanceEntry: startTime property"
short-title: startTime
slug: Web/API/PerformanceEntry/startTime
page-type: web-api-instance-property
browser-compat: api.PerformanceEntry.startTime
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`startTime`** اولین {{domxref("DOMHighResTimeStamp","timestamp", "", "no-code")}} ثبت‌شده برای این {{domxref("PerformanceEntry")}} را برمی‌گرداند. معنای این ویژگی به مقدار {{domxref("PerformanceEntry.entryType", "entryType")}} این ورودی بستگی دارد.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}} که نشان‌دهندهٔ اولین زمان‌سنج (timestamp) هنگام ایجاد {{domxref("PerformanceEntry")}} است.

معنای این ویژگی به مقدار {{domxref("PerformanceEntry.entryType","entryType")}} این ورودی عملکرد بستگی دارد:

- `element`
  - یا مقدار {{domxref("PerformanceElementTiming.renderTime", "renderTime")}} این ورودی اگر `0` نباشد، در غیر این صورت مقدار {{domxref("PerformanceElementTiming.loadTime", "loadTime")}} آن.
- `event`
  - زمان ایجاد رویداد، یعنی ویژگی [`timeStamp`](/en-US/docs/Web/API/Event/timeStamp) آن.
- `first-input`
  - زمان ایجاد اولین رویداد ورودی، یعنی [`timeStamp`](/en-US/docs/Web/API/Event/timeStamp) آن رویداد.
- `largest-contentful-paint`
  - مقدار {{domxref("LargestContentfulPaint.renderTime", "renderTime")}} این ورودی اگر `0` نباشد، در غیر این صورت مقدار {{domxref("LargestContentfulPaint.loadTime", "loadTime")}} آن.
- `layout-shift`
  - زمانی که تغییر چیدمان (layout shift) شروع شد.
- `longtask`
  - زمانی که وظیفه (task) شروع شد.
- `mark`
  - زمانی که نشان (mark) با فراخوانی {{domxref("Performance.mark","performance.mark()")}} ایجاد شد.
- `measure`
  - زمانی که اندازه‌گیری (measure) با فراخوانی {{domxref("Performance.measure","performance.measure()")}} ایجاد شد.
- `navigation`
  - همیشه `0`.
- `paint`
  - زمانی که رنگ‌آمیزی (paint) رخ داد.
- `resource`
  - مقدار ویژگی {{domxref("PerformanceResourceTiming.fetchStart", "fetchStart")}} این ورودی.
- `taskattribution`
  - همیشه `0`.
- `visibility-state`
  - زمانی که تغییر وضعیت visibility رخ داد.

## مثال‌ها

### استفاده از ویژگی startTime

مثال زیر کاربرد ویژگی `startTime` را نشان می‌دهد که می‌توانید آن را در هنگام مشاهدهٔ عملکرد (performance observation) ثبت کنید.

توجه: متد {{domxref("performance.mark()")}} به شما امکان می‌دهد تا `startTime` خودتان را تنظیم کنید، و متد {{domxref("performance.measure()")}} امکان تنظیم شروع اندازه‌گیری را فراهم می‌کند.

```js
performance.mark("my-mark");
performance.mark("my-other-mark", { startTime: 12.5 });

loginButton.addEventListener("click", (clickEvent) => {
  performance.measure("login-click", { start: clickEvent.timeStamp });
});

function perfObserver(list, observer) {
  list.getEntries().forEach((entry) => {
    if (entry.entryType === "mark") {
      console.log(`${entry.name}'s startTime: ${entry.startTime}`);
    }
    if (entry.entryType === "measure") {
      console.log(`${entry.name}'s duration: ${entry.duration}`);
    }
  });
}
const observer = new PerformanceObserver(perfObserver);
observer.observe({ entryTypes: ["measure", "mark"] });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}