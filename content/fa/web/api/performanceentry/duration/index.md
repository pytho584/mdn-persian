---
title: "PerformanceEntry: duration property"
short-title: duration
slug: Web/API/PerformanceEntry/duration
page-type: web-api-instance-property
browser-compat: api.PerformanceEntry.duration
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط خواندنی **`duration`** یک {{domxref("DOMHighResTimeStamp","timestamp", "", "no-code")}} (زمان‌سنج) را برمی‌گرداند که مدت زمان {{domxref("PerformanceEntry","performance entry", "", "no-code")}} (ورودی عملکرد) است. معنای این ویژگی به مقدار {{domxref("PerformanceEntry.entryType", "entryType")}} این ورودی بستگی دارد.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}} که نشان‌دهنده مدت زمان {{domxref("PerformanceEntry","performance entry", "", "no-code")}} است. اگر مفهوم مدت زمان برای یک معیار عملکرد خاص قابل اعمال نباشد، مقدار `0` برگردانده می‌شود.

معنای این ویژگی به مقدار {{domxref("PerformanceEntry.entryType","entryType")}} این ورودی عملکرد بستگی دارد:

- `event`
  - : زمان از `startTime` رویداد تا رنگ‌آمیزی (paint) بعدی (به نزدیک‌ترین 8 میلی‌ثانیه گرد شده).
- `first-input`
  - : زمان از `startTime` اولین رویداد ورودی تا رنگ‌آمیزی بعدی (به نزدیک‌ترین 8 میلی‌ثانیه گرد شده).
- `longtask`
  - : زمان سپری شده بین شروع و پایان کار، با دقت 1 میلی‌ثانیه.
- `measure`
  - : مدت زمان اندازه‌گیری.
- `navigation`
  - : تفاوت بین ویژگی‌های {{domxref("PerformanceNavigationTiming.loadEventEnd", "loadEventEnd")}} و {{domxref("PerformanceEntry.startTime", "startTime")}} ورودی.
- `resource`
  - : مقدار {{domxref("PerformanceResourceTiming/responseEnd", "responseEnd")}} ورودی منهای مقدار {{domxref("PerformanceEntry.startTime","startTime")}} آن.

برای انواع ورودی زیر، `duration` قابل اعمال نیست و در این حالت مقدار همیشه `0` است:

- `element`
- `largest-contentful-paint`
- `layout-shift`
- `mark`
- `paint`
- `taskattribution`
- `visibility-state`

## مثال‌ها

### استفاده از ویژگی duration

مثال زیر تمام ورودی‌های عملکرد مشاهده‌شده با `duration` بزرگتر از `0` را ثبت می‌کند.

```js
function perfObserver(list, observer) {
  list.getEntries().forEach((entry) => {
    if (entry.duration > 0) {
      console.log(`${entry.name}'s duration: ${entry.duration}`);
    }
  });
}
const observer = new PerformanceObserver(perfObserver);
observer.observe({ entryTypes: ["measure", "mark", "resource"] });
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}