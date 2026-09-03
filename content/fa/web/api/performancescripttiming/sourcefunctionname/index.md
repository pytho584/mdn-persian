---
title: "PerformanceScriptTiming: sourceFunctionName property"
short-title: sourceFunctionName
slug: Web/API/PerformanceScriptTiming/sourceFunctionName
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceScriptTiming.sourceFunctionName
---

{{SeeCompatTable}}{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`sourceFunctionName`** در رابط {{domxref("PerformanceScriptTiming")}} رشته‌ای را برمی‌گرداند که نام تابع مؤثر در ایجاد فریم انیمیشن طولانی (LoAF) را نشان می‌دهد.

توجه به این نکته مهم است که نام تابع گزارش‌شده، «نقطه ورود» اسکریپت است؛ یعنی سطح بالای پشته، نه یک زیرتابع کند مشخص.

برای مثال، اگر یک رویدادگردان (event handler) تابعی سطح بالا را فراخوانی کند و آن تابع به‌نوبه خود زیرتابعی کند را صدا بزند، فیلدهای `source*` نام و مکان تابع سطح بالا را گزارش می‌کنند، نه زیرتابع کند را — همیشه تابعی گزارش می‌شود که به API پلتفرم ارسال شده است. دلیل این کار ملاحظات کارایی است؛ زیرا دریافت ردیابی کامل پشته (full stack trace) پرهزینه است.

در قطعه‌کد زیر:

```js
setTimeout(function libFunc() {
  slowFunction();
});
```

مقدار `sourceFunctionName` تابع `libFunc` را گزارش می‌کند، نه `slowFunction` را.

## مقدار

یک رشته. اگر نام تابع پیدا نشود، یک رشتهٔ خالی برمی‌گرداند.

## مثال‌ها

برای مثال‌های مرتبط با API فریم‌های انیمیشن طولانی، به [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing)
- {{domxref("PerformanceLongAnimationFrameTiming")}}