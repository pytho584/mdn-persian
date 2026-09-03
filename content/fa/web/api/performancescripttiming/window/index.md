---
title: "PerformanceScriptTiming: window property"
---

---
title: "PerformanceScriptTiming: window property"
short-title: window
slug: Web/API/PerformanceScriptTiming/window
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceScriptTiming.window
---

{{SeeCompatTable}}{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`window`** از رابط {{domxref("PerformanceScriptTiming")}} یک ارجاع به یک شیء {{domxref("Window")}} برمی‌گرداند که نمایانگر `window` ظرف (یعنی سند سطح بالا یا یک {{htmlelement("iframe")}}) است که اسکریپت ایجادکننده فریم انیمیشن طولانی (LoAF) در آن اجرا شده است.

## مقدار

یک شیء {{domxref("Window")}}، یا `null` اگر پنجره دیگر فعال نباشد (ارجاع شیء یک [`WeakRef`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/WeakRef) است).

## مثال‌ها

برای مثال‌های مرتبط با API فریم‌های انیمیشن طولانی، به [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing)
- {{domxref("PerformanceLongAnimationFrameTiming")}}