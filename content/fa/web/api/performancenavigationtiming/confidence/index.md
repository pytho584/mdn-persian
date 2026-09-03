---
title: "PerformanceNavigationTiming: confidence property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/PerformanceNavigationTiming/confidence"
---

---
title: "PerformanceNavigationTiming: confidence property"
short-title: confidence
slug: Web/API/PerformanceNavigationTiming/confidence
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceNavigationTiming.confidence
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

خاصیت فقط‌خواندنی **`confidence`** در رابط {{domxref("PerformanceNavigationTiming")}} یک شیء {{domxref("PerformanceTimingConfidence")}} برمی‌گرداند که اطلاعاتی را نشان می‌دهد که آیا یک رکورد عملکرد نمایانگر عملکرد معمولی برنامه است یا احتمالاً تحت تأثیر عوامل خارجی قرار دارد.

برای مثال، اگر یک وب‌سایت پس از «راه‌اندازی سرد» مرورگر یا بازیابی نشست بارگذاری شود، ممکن است صفحات آن در نتیجه کندتر بارگذاری شوند. در چنین مواردی، یک مقدار `low` برای {{domxref("PerformanceTimingConfidence.value", "value")}} مرتبط با رکورد عملکرد بازگردانده می‌شود. از سوی دیگر، اگر مرورگر تعیین کند که یک رکورد عملکرد بازگردانده‌شده نمایانگر عملکرد معمولی برنامه است، مقدار اطمینان `high` بازگردانده می‌شود.

این معیار اطمینان برای توسعه‌دهندگان زمانی مفید است که می‌خواهند تشخیص دهند آیا یک مشکل عملکرد یک نگرانی واقعی است یا یک مورد پرت که توسط عوامل خارجی ایجاد شده است.

## مقدار

یک شیء {{domxref("PerformanceTimingConfidence")}}.

## مثال‌ها

### استفاده پایه

این مثال از یک {{domxref("PerformanceObserver")}} برای بازیابی داده‌های اطمینان از ورودی‌های مشاهده‌شده {{domxref("PerformanceNavigationTiming")}} استفاده می‌کند. خاصیت {{domxref("PerformanceTimingConfidence.value", "value")}} یک مقدار شمارشی از `low` یا `high` است که یک معیار اطمینان کلی را نشان می‌دهد، در حالی که خاصیت {{domxref("PerformanceTimingConfidence.randomizedTriggerRate", "randomizedTriggerRate")}} عددی در بازه `0` تا `1` (شامل) است که یک مقدار درصدی را نشان می‌دهد که نشان می‌دهد هر چند وقت یک بار هنگام افشای `value` نویز اعمال می‌شود.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    console.log(
      `${entry.name} confidence: ${entry.confidence.value}`,
      `Trigger rate: ${entry.confidence.randomizedTriggerRate}`,
    );
  });
});

observer.observe({ type: "navigation", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("PerformanceTimingConfidence")}}