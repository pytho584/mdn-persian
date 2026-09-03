---
title: "PerformanceLongAnimationFrameTiming: toJSON() method"
short-title: toJSON()
slug: Web/API/PerformanceLongAnimationFrameTiming/toJSON
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PerformanceLongAnimationFrameTiming.toJSON
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

متد **`toJSON()`** در رابط {{domxref("PerformanceLongAnimationFrameTiming")}} یک {{Glossary("Serialization","سریال‌ساز")}} است؛ این متد یک نمایش JSON از شیء `PerformanceLongAnimationFrameTiming` برمی‌گرداند.

## نحو (Syntax)

```js-nolint
toJSON()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}} که سریال‌سازی شیء {{domxref("PerformanceLongAnimationFrameTiming")}} است.

## مثال‌ها

### استفاده از متد `toJSON`

در این مثال، فراخوانی `entry.toJSON()` یک نمایش JSON از شیء `PerformanceLongAnimationFrameTiming` برمی‌گرداند.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    console.log(entry.toJSON());
  });
});

observer.observe({ type: "long-animation-frame", buffered: true });
```

این کار شیئی شبیه به زیر را در کنسول ثبت می‌کند:

```js
({
  blockingDuration: 0,
  duration: 60,
  entryType: "long-animation-frame",
  firstUIEventTimestamp: 11801.099999999627,
  name: "long-animation-frame",
  renderStart: 11858.800000000745,
  scripts: [
    {
      duration: 45,
      entryType: "script",
      executionStart: 11803.199999999255,
      forcedStyleAndLayoutDuration: 0,
      invoker: "DOMWindow.onclick",
      invokerType: "event-listener",
      name: "script",
      pauseDuration: 0,
      sourceURL: "https://web.dev/js/index-ffde4443.js",
      sourceFunctionName: "myClickHandler",
      sourceCharPosition: 17796,
      startTime: 11803.199999999255,
      window: {
        // …شیء Window…
      },
      windowAttribution: "self",
    },
  ],
  startTime: 11802.400000000373,
  styleAndLayoutStart: 11858.800000000745,
});
```

برای دریافت رشته JSON، می‌توانید مستقیماً از [`JSON.stringify(entry)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) استفاده کنید؛ این تابع به‌طور خودکار `toJSON()` را فراخوانی می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing)
- {{jsxref("JSON")}}