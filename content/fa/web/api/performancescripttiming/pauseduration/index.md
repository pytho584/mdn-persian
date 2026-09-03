---
title: "PerformanceScriptTiming: pauseDuration property"
short-title: pauseDuration
slug: Web/API/PerformanceScriptTiming/pauseDuration
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceScriptTiming.pauseDuration
---

{{SeeCompatTable}}{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`pauseDuration`** در رابط {{domxref("PerformanceScriptTiming")}} یک {{domxref("DOMHighResTimeStamp")}} برمی‌گرداند که کل زمان صرف‌شده توسط اسکریپت بر روی عملیات همزمان «مکث‌کننده» (مانند فراخوانی‌های {{domxref("Window.alert()")}} یا {{domxref("XMLHttpRequest")}}های همزمان) را بر حسب میلی‌ثانیه نشان می‌دهد.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}}.

## مثال‌ها

برای مثال‌های مرتبط با API فریم‌های انیمیشن طولانی، به [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing)
- {{domxref("PerformanceLongAnimationFrameTiming")}}