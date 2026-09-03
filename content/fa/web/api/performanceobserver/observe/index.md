---
title: "PerformanceObserver: observe() method"
short-title: observe()
slug: Web/API/PerformanceObserver/observe
page-type: web-api-instance-method
browser-compat: api.PerformanceObserver.observe
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

متد **`observe()`** از رابط **{{domxref("PerformanceObserver")}}** برای مشخص کردن مجموعه‌ای از انواع ورودی‌های عملکرد (performance entry types) که باید مشاهده شوند، استفاده می‌شود.

برای فهرست انواع ورودی‌ها به {{domxref("PerformanceEntry.entryType")}} مراجعه کنید و برای فهرست انواع ورودی‌هایی که عامل کاربر (user agent) پشتیبانی می‌کند، به {{domxref("PerformanceObserver.supportedEntryTypes_static", "PerformanceObserver.supportedEntryTypes")}} مراجعه کنید.

هنگامی که یک ورودی عملکرد منطبق ثبت می‌شود، تابع callback ناظر عملکرد (performance observer) — که هنگام ایجاد {{domxref("PerformanceObserver")}} تنظیم شده است — فراخوانی می‌شود.

## Syntax

```js-nolint
observe(options)
```

### Parameters

- `options`
  - : یک شیء با اعضای احتمالی زیر:
    - `buffered`
      - : یک پرچم بولی (boolean) که نشان می‌دهد آیا ورودی‌های بافر شده باید در صف بافر ناظر قرار گیرند یا خیر. فقط باید با گزینه `type` استفاده شود.
    - `durationThreshold`
      - : یک {{domxref("DOMHighResTimeStamp")}} که آستانه (threshold) را برای ورودی‌های {{domxref("PerformanceEventTiming")}} تعریف می‌کند. پیش‌فرض 104 میلی‌ثانیه است و به نزدیک‌ترین مضرب 8 میلی‌ثانیه گرد می‌شود. کمترین آستانه ممکن 16 میلی‌ثانیه است. نمی‌تواند همراه با گزینه `entryTypes` استفاده شود.
    - `entryTypes`
      - : آرایه‌ای از رشته‌ها که هر کدام یک نوع ورودی عملکرد را برای مشاهده مشخص می‌کند. نمی‌تواند همراه با گزینه‌های `type`، `buffered` یا `durationThreshold` استفاده شود.

        برای فهرست نام‌های معتبر انواع ورودی عملکرد به {{domxref("PerformanceEntry.entryType")}} مراجعه کنید. انواع ناشناخته نادیده گرفته می‌شوند، اگرچه ممکن است مرورگر یک پیام هشدار در کنسول برای کمک به توسعه‌دهندگان در اشکال‌زدایی کدشان نمایش دهد. اگر هیچ نوع معتبری یافت نشود، `observe()` هیچ اثری ندارد.

    - `type`
      - : یک رشته منفرد که دقیقاً یک نوع ورودی عملکرد را برای مشاهده مشخص می‌کند. نمی‌تواند همراه با گزینه `entryTypes` استفاده شود.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

## Examples

### مشاهده چندین نوع ورودی عملکرد

این مثال یک `PerformanceObserver` ایجاد می‌کند و نوع‌های ورودی `"mark"` و `"measure"` را همانطور که توسط گزینه `entryTypes` در متد `observe()` مشخص شده، مشاهده می‌کند.

```js
const observer = new PerformanceObserver((list, obj) => {
  list.getEntries().forEach((entry) => {
    // Process "mark" and "measure" events
  });
});
observer.observe({ entryTypes: ["mark", "measure"] });
```

### مشاهده یک نوع ورودی عملکرد منفرد

مثال زیر رویدادهای بافر شده را بازیابی می‌کند و برای رویدادهای جدیدتر مربوط به زمان‌بندی منابع (resource timing) ({{domxref("PerformanceResourceTiming")}}) با استفاده از گزینه‌های پیکربندی `buffered` و `type` مشترک می‌شود. هرگاه نیاز به پیکربندی ناظر برای استفاده از گزینه `buffered` یا `durationThreshold` دارید، به جای `entryType` از `type` استفاده کنید. در غیر این صورت جمع‌آوری چندین نوع ورودی عملکرد کار نخواهد کرد.

```js
const observer = new PerformanceObserver((list, obj) => {
  list.getEntries().forEach((entry) => {
    // Process "resource" events
  });
});
observer.observe({ type: "resource", buffered: true });
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}