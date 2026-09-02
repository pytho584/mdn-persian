---
title: "IdleDeadline: timeRemaining() method"
short-title: timeRemaining()
slug: Web/API/IdleDeadline/timeRemaining
page-type: web-api-instance-method
browser-compat: api.IdleDeadline.timeRemaining
---

{{APIRef("Background Tasks")}}

متد **`timeRemaining()`** از رابط {{domxref("IdleDeadline")}} تعداد تخمینی میلی‌ثانیه‌هایی را برمی‌گرداند که عامل کاربر (user agent) همچنان بیکار (idle) خواهد ماند. این فراخوان (callback) می‌تواند در هر زمان این متد را فراخوانی کند تا مشخص شود چقدر زمان برای ادامه کار قبل از بازگشت دارد. برای مثال، اگر فراخوان یک کار را به پایان برساند و کار دیگری برای شروع داشته باشد، می‌تواند `timeRemaining()` را فراخوانی کند تا ببیند آیا زمان کافی برای تکمیل کار بعدی وجود دارد یا خیر. اگر زمان کافی نباشد، فراخوان می‌تواند بلافاصله بازگردد یا به دنبال کار دیگری برای انجام با زمان باقی‌مانده بگردد.

زمانی که `timeRemaining()` به `0` می‌رسد، توصیه می‌شود فراخوان کنترل را به حلقه رویداد (event loop) عامل کاربر بازگرداند.

> [!NOTE]
> مقدار بازگردانده‌شده توسط `timeRemaining()` یک تخمین از مدت زمانی است که عامل کاربر باور دارد قبل از اجرای وظیفه حساس به تأخیر بعدی (latency-critical task) در دسترس است. این تخمین ثابت نیست و اگر کار با اولویت بالاتری وارد شود، می‌تواند به‌طور ناگهانی به ۰ کاهش یابد. برای مثال، تخمین مرورگر ممکن است در وسط یک فراخوان بیکار (idle callback) در صورت کلیک کاربر تغییر کند. توسعه‌دهندگان نباید فرض کنند که این مقدار همیشه مانند یک تایمر شمارش معکوس به‌صورت خطی کاهش می‌یابد.

## نحو

```js-nolint
timeRemaining()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک مقدار {{domxref("DOMHighResTimeStamp")}} (که یک عدد اعشاری است) که تعداد میلی‌ثانیه‌هایی را نشان می‌دهد که عامل کاربر تخمین می‌زند در دوره بیکاری فعلی باقی مانده است. این مقدار در حالت ایده‌آل دقتی در حدود ۵ میکروثانیه دارد.

اگر ویژگی {{domxref("IdleDeadline.didTimeout", "didTimeout")}} آبجکت {{domxref("IdleDeadline")}} برابر با `true` باشد، این متد صفر برمی‌گرداند.

## مثال‌ها

[نمونه کامل](/en-US/docs/Web/API/Background_Tasks_API#example) را در مقاله [Cooperative Scheduling of Background Tasks API](/en-US/docs/Web/API/Background_Tasks_API) ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Collaborative Scheduling of Background Tasks](/en-US/docs/Web/API/Background_Tasks_API)
- {{domxref("IdleDeadline")}}
- {{domxref("Window.requestIdleCallback()")}}
- {{domxref("Window.cancelIdleCallback()")}}