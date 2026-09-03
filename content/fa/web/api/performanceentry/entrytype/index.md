---
title: "PerformanceEntry: entryType property"
short-title: entryType
slug: Web/API/PerformanceEntry/entryType
page-type: web-api-instance-property
browser-compat: api.PerformanceEntry.entryType
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

خاصیت فقط‌خواندنی **`entryType`** یک رشته برمی‌گرداند که نوع معیار عملکردی را که این ورودی نشان می‌دهد مشخص می‌کند.

همه `entryType`های پشتیبانی‌شده با استفاده از خاصیت ایستا {{domxref("PerformanceObserver.supportedEntryTypes_static", "PerformanceObserver.supportedEntryTypes")}} در دسترس هستند.

## مقدار

یک رشته. مقدار بازگشتی به زیرنوع شیء `PerformanceEntry` بستگی دارد. برخی زیرنوع‌ها بیش از یک `entryType` دارند.

- `element`
  - : زمان بارگذاری عناصر را گزارش می‌دهد.

    نمونه ورودی یک شیء {{domxref("PerformanceElementTiming")}} خواهد بود.

- `event`
  - : تأخیر رویدادها را گزارش می‌دهد.

    نمونه ورودی یک شیء {{domxref("PerformanceEventTiming")}} خواهد بود.

- `first-input`
  - : {{Glossary("First Input Delay")}} (FID) را گزارش می‌دهد.

    نمونه ورودی یک شیء {{domxref("PerformanceEventTiming")}} خواهد بود.

- `interaction-contentful-paint`
  - : بزرگ‌ترین نقاشی (paint) را که یک عنصر پس از یک تعامل روی صفحه ایجاد کرده است گزارش می‌دهد.

    نمونه ورودی یک شیء {{domxref("InteractionContentfulPaint")}} خواهد بود.

- `largest-contentful-paint`
  - : بزرگ‌ترین نقاشی را که یک عنصر روی صفحه ایجاد کرده است گزارش می‌دهد.

    نمونه ورودی یک شیء {{domxref("LargestContentfulPaint")}} خواهد بود.

- `layout-shift`
  - : پایداری چیدمان صفحات وب را بر اساس جابه‌جایی عناصر در صفحه گزارش می‌دهد.

    نمونه ورودی یک شیء {{domxref("LayoutShift")}} خواهد بود.

- `long-animation-frame`
  - : نمونه‌هایی از [فریم‌های انیمیشن طولانی (LoAFها)](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing#what_is_a_long_animation_frame) را گزارش می‌دهد.

    نمونه ورودی یک شیء {{domxref("PerformanceLongAnimationFrameTiming")}} خواهد بود.

- `longtask`
  - : نمونه‌هایی از وظایف طولانی را گزارش می‌دهد.

    نمونه ورودی یک شیء {{domxref("PerformanceLongTaskTiming")}} خواهد بود.

- `mark`
  - : نشانگرهای عملکرد سفارشی شما را گزارش می‌دهد.

    نمونه ورودی یک شیء {{domxref("PerformanceMark")}} خواهد بود.

- `measure`
  - : اندازه‌گیری‌های عملکرد سفارشی شما را گزارش می‌دهد.

    نمونه ورودی یک شیء {{domxref("PerformanceMeasure")}} خواهد بود.

- `navigation`
  - : زمان‌بندی ناوبری سند را گزارش می‌دهد.

    نمونه ورودی یک شیء {{domxref("PerformanceNavigationTiming")}} خواهد بود.

- `paint`
  - : لحظه‌های کلیدی رندر سند (اولین نقاشی، اولین نقاشی با محتوا) را هنگام بارگذاری صفحه گزارش می‌دهد.

    نمونه ورودی یک شیء {{domxref("PerformancePaintTiming")}} خواهد بود.

- `resource`
  - : اطلاعات زمان‌بندی منابع در یک سند را گزارش می‌دهد.

    نمونه ورودی یک شیء {{domxref("PerformanceResourceTiming")}} خواهد بود.

- `soft-navigation`
  - : نقاشی‌هایی را گزارش می‌دهد که پس از تعامل کاربر و به‌روزرسانی URL که یک {{Glossary("soft navigation")}} را فعال کرده است، روی صفحه ایجاد می‌شوند.

    نمونه ورودی یک شیء {{domxref("PerformanceSoftNavigation")}} خواهد بود.

- `taskattribution`
  - : نوع کاری را گزارش می‌دهد که به‌طور قابل توجهی در وظیفه طولانی نقش داشته است.

    نمونه ورودی یک شیء {{domxref("TaskAttributionTiming")}} خواهد بود.

- `visibility-state`
  - : زمان تغییر وضعیت دید صفحه را گزارش می‌دهد، یعنی زمانی که یک تب از پس‌زمینه به پیش‌زمینه می‌آید یا برعکس.

    نمونه ورودی یک شیء {{domxref("VisibilityStateEntry")}} خواهد بود.

## مثال‌ها

### فیلتر کردن ورودی‌های عملکرد بر اساس نوع

خاصیت `entryType` می‌تواند هنگام فیلتر کردن ورودی‌های عملکرد خاص مفید باشد. برای مثال، ممکن است بخواهید همه منابع اسکریپت را بررسی کنید، بنابراین باید به دنبال `entryType` برابر با `"resource"` و {{domxref("PerformanceResourceTiming.initiatorType", "initiatorType")}} برابر با `"script"` بگردید.

```js
const scriptResources = performance
  .getEntries()
  .filter(
    (entry) =>
      entry.entryType === "resource" && entry.initiatorType === "script",
  );
console.log(scriptResources);
```

### دریافت ورودی‌های عملکرد بر اساس نوع

هم {{domxref("Performance")}} و هم {{domxref("PerformanceObserver")}} روش‌هایی را ارائه می‌دهند که به شما امکان می‌دهند ورودی‌های عملکرد را مستقیماً بر اساس نوع دریافت کنید. لزوماً برای این کار به خاصیت `entryType` نیاز ندارید؛ در عوض می‌توانید از {{domxref("Performance.getEntriesByType()")}} یا {{domxref("PerformanceObserverEntryList.getEntriesByType()")}} استفاده کنید.

همچنین، هنگام مشاهده با {{domxref("PerformanceObserver")}}، روش {{domxref("PerformanceObserver.observe", "observe()")}} یک آرایه از `entryTypes` را در شیء گزینه‌های خود دریافت می‌کند که می‌توانید تعیین کنید کدام نوع ورودی‌ها را مشاهده کنید.

```js
// همه ورودی‌های resource را در این نقطه ثبت کنید
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  console.log(`${entry.name}'s duration: ${entry.duration}`);
});

// نسخه PerformanceObserver
// همه ورودی‌های resource را زمانی که در دسترس هستند ثبت کنید
function perfObserver(list, observer) {
  list.getEntriesByType("resource").forEach((entry) => {
    console.log(`${entry.name}'s duration: ${entry.duration}`);
  });
}
const observer = new PerformanceObserver(perfObserver);
observer.observe({ entryTypes: ["resource", "navigation"] });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("PerformanceObserver.supportedEntryTypes_static", "PerformanceObserver.supportedEntryTypes")}}
- {{domxref("Performance.getEntriesByType()")}}
- {{domxref("PerformanceObserverEntryList.getEntriesByType()")}}