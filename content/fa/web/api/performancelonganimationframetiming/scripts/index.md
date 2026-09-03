---
title: "PerformanceLongAnimationFrameTiming: scripts property"
short-title: scripts
slug: Web/API/PerformanceLongAnimationFrameTiming/scripts
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceLongAnimationFrameTiming.scripts
---

{{SeeCompatTable}}{{APIRef("Performance API")}}

ویژگی فقط‑خواندنی **`scripts`** از رابط {{domxref("PerformanceLongAnimationFrameTiming")}} یک آرایه از اشیاء {{domxref("PerformanceScriptTiming")}} برمی‌گرداند.

نسبت‌دهی اسکریپت فقط برای اسکریپت‌هایی که در ریسه اصلی (main thread) یک صفحه اجرا می‌شوند، از جمله `<iframe>`های هم‌مبدأ، ارائه می‌شود. با این حال، `<iframe>`های متقاطع‑مبدأ، [web workers](/en-US/docs/Web/API/Web_Workers_API)، [service workers](/en-US/docs/Web/API/Service_Worker_API)، و کد [افزونه‌ها](/en-US/docs/Mozilla/Add-ons/WebExtensions) در فریم‌های انیمیشن طولانی نسبت‌دهی اسکریپت نخواهند داشت، حتی اگر بر مدت زمان یک فریم تأثیر بگذارند.

## مقدار

یک آرایه از اشیاء {{domxref("PerformanceScriptTiming")}}.

## مثال‌ها

برای مثال‌های مرتبط با API فریم‌های انیمیشن طولانی، به [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing)
- {{domxref("PerformanceScriptTiming")}}