---
title: "console: trace() static method"
short-title: trace()
slug: Web/API/console/trace_static
page-type: web-api-static-method
browser-compat: api.console.trace_static
---

{{APIRef("Console API")}} {{AvailableInWorkers}}

متد ایستای **`console.trace()`** یک ردیابی پشته (stack trace) را در کنسول خروجی می‌دهد.

> [!NOTE]
> در برخی مرورگرها، `console.trace()` ممکن است علاوه بر پشته، توالی فراخوانی‌ها و رویدادهای ناهمگام (async events) که به `console.trace()` فعلی منتهی شده‌اند را نیز نمایش دهد — حتی اگر آن‌ها روی پشته‌ی فراخوانی نباشند — تا به شناسایی منشأ حلقه‌ی ارزیابی رویداد فعلی کمک کند.

برای جزئیات و مثال‌ها، بخش [ردیابی پشته](/en-US/docs/Web/API/console#stack_traces) را در مستندات {{domxref("console")}} ببینید.

## نحو (Syntax)

```js-nolint
console.trace()
console.trace(object1, /* …, */ objectN)
```

### پارامترها

- `objects` {{optional_inline}}
  - : صفر یا چند شیء که همراه با ردیابی در کنسول خروجی داده می‌شوند. این اشیاء دقیقاً به همان روشی که اگر به متد {{domxref("console/log_static", "console.log()")}} منتقل می‌شدند، جمع‌آوری و قالب‌بندی می‌شوند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
function foo() {
  function bar() {
    console.trace();
  }
  bar();
}

foo();
```

در کنسول، ردیابی زیر نمایش داده می‌شود:

```plain
bar
foo
<anonymous>
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [مستندات Microsoft Edge برای `console.trace()`](https://learn.microsoft.com/en-us/microsoft-edge/devtools/console/api#trace)
- [مستندات Node.js برای `console.trace()`](https://nodejs.org/docs/latest/api/console.html#consoletracemessage-args)
- [مستندات Google Chrome برای `console.trace()`](https://developer.chrome.com/docs/devtools/console/api/#trace)