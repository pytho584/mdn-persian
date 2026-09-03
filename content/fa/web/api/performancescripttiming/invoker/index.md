---
title: "PerformanceScriptTiming: invoker property"
short-title: invoker
slug: Web/API/PerformanceScriptTiming/invoker
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceScriptTiming.invoker
---

{{SeeCompatTable}}{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`invoker`** در رابط {{domxref("PerformanceScriptTiming")}} یک مقدار رشته‌ای برمی‌گرداند که مشخص‌کنندهٔ قابلیتی است که با فراخوانیِ آن، اسکریپت اجرا شده است.

## مقدار

یک رشته که ساختار آن به مقدار {{domxref("PerformanceScriptTiming.invokerType")}} اسکریپت بستگی دارد:

| `invokerType`                             | ساختار رشتهٔ `invoker`                                                                                                                                                                                                                                            | مثال(ها)                                                                                             |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| `"user-callback"`                         | کلاس شیئی که تابعِ شامل‌کننده روی آن تعریف شده، به‌دنبال یک نقطه و سپس نام تابع.                                                                                                                                                                                     | `"Window.requestAnimationFrame"`, `"Window.setTimeout"`                                             |
| `"event-listener"`                        | مقدار {{domxref("Element.tagName", "tagName")}} عنصر، به‌دنبال یک علامت هش و `id` آن (`#id`) یا اگر `id` وجود نداشته باشد، `src=` و مقدار `src` درون کروشه (`[src=url]`)، سپس یک نقطه و ویژگی کنترل‌کننده رویداد. | `"IMG#hero.onload"`, `"IMG[src=https://example.com/img.jpg].onload"`, `"BUTTON#updateCart.onclick"` |
| `"resolve-promise"` یا `"reject-promise"` | شیء و متدی که promise را فراخوانی کرده، به‌دنبال یک نقطه، و سپس `"then"` برای `"resolve-promise"` و `"catch"` برای `"reject-promise"`.                                                                                                         | `"Response.json.then"`, `"Response.json.catch"`                                                     |
| `"classic-script"` یا `"module-script"`   | نشانی منبع (URL) اسکریپت فراخوانی‌کننده.                                                                                                                                                                                                                        | `"https://example.com/scripts/myscript.js"`                                                         |

## مثال‌ها

برای مثال‌های مرتبط با API فریم‌های انیمیشن طولانی، به [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing)
- {{domxref("PerformanceLongAnimationFrameTiming")}}