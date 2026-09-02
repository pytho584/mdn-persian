---
title: "IdleDeadline"
slug: Web/API/IdleDeadline
page-type: web-api-interface
browser-compat: api.IdleDeadline
---

{{APIRef("Background Tasks")}}

رابط `IdleDeadline` به عنوان نوع دادهٔ پارامتر ورودی به callback‌های idle که با فراخوانی {{domxref("Window.requestIdleCallback()")}} ایجاد می‌شوند، استفاده می‌شود. این رابط یک متد به نام {{domxref("IdleDeadline.timeRemaining", "timeRemaining()")}} ارائه می‌دهد که به شما امکان می‌دهد تخمین بزنید عامل کاربر (user agent) تا چه مدت دیگر بیکار خواهد ماند، و همچنین یک ویژگی به نام {{domxref("IdleDeadline.didTimeout", "didTimeout")}} که به شما امکان می‌دهد تعیین کنید آیا callback شما به دلیل منقضی شدن مدت زمان وقفه (timeout) اجرا می‌شود یا خیر.

برای آشنایی بیشتر با نحوهٔ کار callback‌های درخواست، به [زمان‌بندی مشارکتی وظایف پس‌زمینه](/en-US/docs/Web/API/Background_Tasks_API) مراجعه کنید.

## ویژگی‌های نمونه (Instance properties)

- {{domxref("IdleDeadline.didTimeout")}} {{ReadOnlyInline}}
  - : یک مقدار Boolean که اگر callback به دلیل منقضی شدن مدت زمان وقفه‌ای که هنگام نصب callback idle مشخص شده بود اجرا شود، مقدار آن `true` است.

## روش‌های نمونه (Instance methods)

- {{domxref("IdleDeadline.timeRemaining()")}}
  - : یک {{domxref("DOMHighResTimeStamp")}} برمی‌گرداند که یک مقدار اعشاری است و تخمینی از تعداد میلی‌ثانیه‌های باقی‌مانده در دورهٔ بیکاری (idle period) فعلی ارائه می‌دهد. اگر دورهٔ بیکاری به پایان رسیده باشد، مقدار 0 است. callback شما می‌تواند این متد را مکرراً فراخوانی کند تا ببیند آیا زمان کافی برای انجام کار بیشتر قبل از بازگشت وجود دارد یا خیر.

## مثال

مثال کامل ما را در مقالهٔ [زمان‌بندی مشارکتی وظایف پس‌زمینه](/en-US/docs/Web/API/Background_Tasks_API#example) مشاهده کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [زمان‌بندی مشارکتی وظایف پس‌زمینه](/en-US/docs/Web/API/Background_Tasks_API)
- {{domxref("Window.requestIdleCallback()")}}
- {{domxref("Window.cancelIdleCallback()")}}