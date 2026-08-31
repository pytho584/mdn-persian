---
title: "console: timeLog() static method"
short-title: timeLog()
slug: Web/API/console/timeLog_static
page-type: web-api-static-method
browser-compat: api.console.timeLog_static
---

{{APIRef("Console API")}}{{AvailableInWorkers}}

متد ایستای **`console.timeLog()`** مقدار فعلی زمان‌سنجی را که قبلاً با فراخوانی {{domxref("console/time_static", "console.time()")}} شروع شده است، در کنسول ثبت می‌کند.

## نحو (Syntax)

```js-nolint
console.timeLog()
console.timeLog(label)
console.timeLog(label, val1)
console.timeLog(label, val1, /* …, */ valN)
```

### پارامترها

- `label` {{optional_inline}}
  - : نام زمان‌سنجی که باید در کنسول ثبت شود. اگر حذف شود، برچسب «default» استفاده می‌شود.
- `valN` {{optional_inline}}
  - : مقادیر اضافی که پس از خروجی زمان‌سنج در کنسول ثبت می‌شوند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## توضیحات

متد `console.timeLog()` مقدار فعلی یک زمان‌سنج را ثبت می‌کند.

می‌توان نام یک زمان‌سنج را به این متد ارسال کرد. این کار سعی می‌کند مقدار زمان‌سنجی را که با آن نام در فراخوانی قبلی {{domxref("console/time_static", "console.time()")}} ایجاد شده است، ثبت کند:

```js
console.time("reticulating splines");
reticulateSplines();
console.timeLog("reticulating splines");
// reticulating splines: 650ms
```

اگر نام زمان‌سنج حذف شود، زمان‌سنج با نام «default» در نظر گرفته می‌شود:

```js
console.time();
reticulateSplines();
console.timeLog();
// default: 780ms
```

```js
console.time("default");
reticulateSplines();
console.timeLog();
// default: 780ms
```

اگر زمان‌سنج متناظری وجود نداشته باشد، `console.timeLog()` هشداری مانند زیر را ثبت می‌کند:

```plain
Timer "timer name" doesn't exist.
```

می‌توانید مقادیر اضافی را نیز پس از خروجی زمان‌سنج در کنسول ثبت کنید:

```js
console.time();
reticulateSplines();
console.timeLog("default", "Hello", "world");
// default: 780ms Hello world
```

برای جزئیات و مثال‌های بیشتر، بخش [Timers](/en-US/docs/Web/API/console#timers) را در مستندات ببینید.

## مثال‌ها

```js
console.time("answer time");
alert("Click to continue");
console.timeLog("answer time");
alert("Do a bunch of other stuff…");
console.timeEnd("answer time");
```

خروجی مثال بالا، زمان صرف‌شده توسط کاربر برای بستن اولین جعبه هشدار و سپس زمان تجمعی صرف‌شده برای بستن هر دو هشدار را نشان می‌دهد:

```plain
answer time: 2542ms debugger eval code:3:9
answer time: 4161ms - timer ended
```

توجه کنید که نام زمان‌سنج هم هنگام ثبت مقدار آن با `console.timeLog()` و هم هنگام توقف آن نمایش داده می‌شود. علاوه بر این، فراخوانی `console.timeEnd()` اطلاعات اضافی «timer ended» را دارد تا مشخص شود که زمان‌سنج دیگر زمان را اندازه‌گیری نمی‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("console/time_static", "console.time()")}}
- برای مثال‌های بیشتر، {{domxref("console/timeEnd_static", "console.timeEnd()")}} را ببینید.
- [مستندات Node.js برای `console.timeLog()`](https://nodejs.org/docs/latest/api/console.html#consoletimeloglabel-data)