---
title: "PerformanceScriptTiming: invokerType property"
short-title: invokerType
slug: Web/API/PerformanceScriptTiming/invokerType
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceScriptTiming.invokerType
---

{{SeeCompatTable}}{{APIRef("Performance API")}}

ویژگی فقط-خواندنی **`invokerType`** از رابط {{domxref("PerformanceScriptTiming")}} یک مقدار رشته‌ای برمی‌گرداند که نوع قابلیتی را نشان می‌دهد که هنگام فراخوانی، اسکریپت را اجرا کرده است.

## مقدار

یک رشته که نوع invoker نقطه ورود اسکریپت را نشان می‌دهد. مقادیر ممکن عبارتند از:

- `"user-callback"`
  - : یک فراخوان (callback) شناخته‌شده که از درون یک API پلتفرم وب فراخوانی می‌شود، مانند {{domxref("Window.setTimeout", "setTimeout()")}} یا {{domxref("Window.requestAnimationFrame()")}}.
- `"event-listener"`
  - : یک شنونده رویداد (event listener) برای یک رویداد پلتفرم وب، مانند [`click`](/en-US/docs/Web/API/Element/click_event)، [`load`](/en-US/docs/Web/API/Window/load_event)، یا [`keyup`](/en-US/docs/Web/API/Element/keyup_event).
- `"resolve-promise"`
  - : یک تابع کنترل‌کننده (handler) برای حالت resolved یک promise پلتفرم وب، مانند {{domxref("Window/fetch", "fetch()")}}. توجه داشته باشید که در مورد promises، تمام کنترل‌کننده‌های یک promise به عنوان یک نوع ورودی `"script"` واحد گروه‌بندی می‌شوند.
- `"reject-promise"`
  - : یک تابع کنترل‌کننده برای حالت rejected یک promise پلتفرم وب.
- `"classic-script"`
  - : ارزیابی یک اسکریپت استاندارد (به عنوان مثال، از طریق یک عنصر {{htmlelement("script")}} یا یک عبارت [`import()`](/en-US/docs/Web/JavaScript/Reference/Operators/import)).
- `"module-script"`
  - : ارزیابی یک اسکریپت ماژول.

ساختار مقدار {{domxref("PerformanceScriptTiming.invoker")}} به مقدار `invokerType` اسکریپت بستگی دارد. برای جزئیات بیشتر به صفحه `invoker` مراجعه کنید.

## مثال‌ها

برای مثال‌های مرتبط با API فریم‌های انیمیشن طولانی، به [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing)
- {{domxref("PerformanceLongAnimationFrameTiming")}}