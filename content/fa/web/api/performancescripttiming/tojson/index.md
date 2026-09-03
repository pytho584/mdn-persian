---
title: "PerformanceScriptTiming: toJSON() method"
short-title: toJSON()
slug: Web/API/PerformanceScriptTiming/toJSON
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PerformanceScriptTiming.toJSON
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

متد **`toJSON()`** در رابط {{domxref("PerformanceScriptTiming")}} یک {{Glossary("Serialization","سریال‌ساز")}} است؛ این متد یک نمایش JSON از شیء `PerformanceScriptTiming` را برمی‌گرداند.

## نحو (Syntax)

```js-nolint
toJSON()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}} که سریال‌سازی شده‌ی شیء {{domxref("PerformanceScriptTiming")}} است.

## مثال‌ها

### استفاده از متد `toJSON`

در این مثال، فراخوانی `entry.toJSON()` یک نمایش JSON از اولین شیء `PerformanceScriptTiming` موجود در یک فریم انیمیشن طولانی مشاهده‌شده را برمی‌گرداند.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    console.log(entry.scripts[0].toJSON());
  });
});

observer.observe({ type: "long-animation-frame", buffered: true });
```

این کد چیزی شبیه به شیء زیر را در کنسول ثبت می‌کند:

```js
({
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
  windowAttribution: "self",
});
```

برای دریافت یک رشته‌ی JSON، می‌توانید مستقیماً از [`JSON.stringify(entry)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) استفاده کنید؛ این متد به‌طور خودکار `toJSON()` را فراخوانی می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing)
- {{jsxref("JSON")}}