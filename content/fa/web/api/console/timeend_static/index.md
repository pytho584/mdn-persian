---
title: "console: timeEnd() static method"
short-title: timeEnd()
slug: Web/API/console/timeEnd_static
page-type: web-api-static-method
browser-compat: api.console.timeEnd_static
---

{{APIRef("Console API")}} {{AvailableInWorkers}}

متد استاتیک **`console.timeEnd()`** تایمری را متوقف می‌کند که قبلاً با فراخوانی {{domxref("console/time_static", "console.time()")}} شروع شده است.

برای جزئیات و مثال‌ها، بخش [تایمرها](/en-US/docs/Web/API/console#timers) را در مستندات ببینید.

## سینتکس

```js-nolint
console.timeEnd()
console.timeEnd(label)
```

### پارامترها

- `label` {{optional_inline}}
  - : رشته‌ای که نام تایمر را برای توقف مشخص می‌کند. پس از توقف، زمان سپری‌شده به‌طور خودکار در کنسول به‌همراه نشانگری که پایان زمان را اعلام می‌کند، نمایش داده می‌شود. اگر این پارامتر حذف شود، برچسب "default" استفاده می‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
console.time("answer time");
alert("Click to continue");
console.timeLog("answer time");
alert("Do a bunch of other stuff…");
console.timeEnd("answer time");
```

خروجی مثال بالا، مدت زمانی را نشان می‌دهد که کاربر برای بستن اولین جعبه هشدار صرف کرده است و سپس زمان تجمعی که کاربر برای بستن هر دو هشدار صرف کرده است:

![خروجی تایمر در کنسول فایرفاکس](timer_output.png)

توجه داشته باشید که نام تایمر هنگام ثبت مقدار تایمر با استفاده از `console.timeLog()` و همچنین هنگام متوقف شدن آن نمایش داده می‌شود. علاوه بر این، فراخوانی `console.timeEnd()` اطلاعات اضافی «timer ended» را ارائه می‌دهد تا مشخص شود که تایمر دیگر زمان را پیگیری نمی‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- برای مثال‌های بیشتر، {{domxref("console/timeLog_static", "console.timeLog()")}} را ببینید.
- {{domxref("console/time_static", "console.time()")}}
- [مستندات `console.timeEnd()` در Microsoft Edge](https://learn.microsoft.com/en-us/microsoft-edge/devtools/console/api#timeend)
- [مستندات `console.timeEnd()` در Node.js](https://nodejs.org/docs/latest/api/console.html#consoletimeendlabel)
- [مستندات `console.timeEnd()` در Google Chrome](https://developer.chrome.com/docs/devtools/console/api/#timeend)