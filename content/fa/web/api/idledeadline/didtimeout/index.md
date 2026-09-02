---
title: "IdleDeadline: didTimeout property"
short-title: didTimeout
slug: Web/API/IdleDeadline/didTimeout
page-type: web-api-instance-property
browser-compat: api.IdleDeadline.didTimeout
---

{{APIRef("Background Tasks")}}

ویژگی فقط‌خواندنی **`didTimeout`** در رابط **{{domxref("IdleDeadline")}}** یک مقدار بولی است که مشخص می‌کند آیا فراخوان بیکاری به این دلیل فراخوانی شده است که بازه زمانی تعیین‌شده هنگام فراخوانی {{domxref("Window.requestIdleCallback()")}} منقضی شده است یا نه.

اگر `didTimeout` برابر با `true` باشد، متد {{domxref("IdleDeadline.timeRemaining", "timeRemaining()")}} شیء `IdleDeadline` تقریباً ۰ را بازمی‌گرداند.

فراخوان‌های بیکاری از مفهوم مهلت زمانی پشتیبانی می‌کنند تا اطمینان حاصل شود که هر وظیفه‌ای که قرار است انجام دهند واقعاً انجام می‌شود، حتی اگر عامل کاربر هرگز زمان بیکاری کافی نداشته باشد. فراخوان شما معمولاً مقدار `didTimeout` را بررسی می‌کند اگر لازم باشد حتی وقتی مرورگر بیش از حد مشغول است و نمی‌تواند زمان در اختیارتان بگذارد، عملی را انجام دهد؛ در این حالت باید با انجام وظیفه موردنیاز یا در حالت ایده‌آل، حداقل کاری که بتواند کارها را در جریان نگه دارد، واکنش نشان دهید و سپس فراخوان جدیدی زمان‌بندی کنید تا دوباره برای انجام باقی‌مانده کار تلاش کنید.

## مقدار

یک مقدار بولی است که اگر فراخوان به دلیل سپری شدن مهلت زمانی آن در حال اجرا باشد، مقدار `true` دارد و اگر فراخوان به این دلیل اجرا می‌شود که عامل کاربر بیکار است و زمان را در اختیار فراخوان می‌گذارد، مقدار `false` دارد.

## مثال‌ها

[مثال کامل](/en-US/docs/Web/API/Background_Tasks_API#example) ما را در مقاله [Cooperative Scheduling of Background Tasks API](/en-US/docs/Web/API/Background_Tasks_API) ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Collaborative Scheduling of Background Tasks](/en-US/docs/Web/API/Background_Tasks_API)
- {{domxref("IdleDeadline")}}
- {{domxref("Window.requestIdleCallback()")}}
- {{domxref("Window.cancelIdleCallback()")}}