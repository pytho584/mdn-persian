---
title: "console: countReset() static method"
short-title: countReset()
slug: Web/API/console/countReset_static
page-type: web-api-static-method
browser-compat: api.console.countReset_static
---

{{APIRef("Console API")}} {{AvailableInWorkers}}

متد ایستای **`console.countReset()`** شمارنده‌ای را که با {{domxref("console/count_static", "console.count()")}} استفاده می‌شود، بازنشانی می‌کند.

## سینتکس

```js-nolint
console.countReset()
console.countReset(label)
```

### پارامترها

- `label` {{optional_inline}}
  - : یک رشته. اگر ارائه شود، `countReset()` شمارش را برای آن برچسب به ۰ بازنشانی می‌کند. اگر حذف شود، `countReset()` شمارنده پیش‌فرض را به ۰ بازنشانی می‌کند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

برای مثال، با کدی مانند این:

```js
function greet(user) {
  console.count();
  return `hi ${user}`;
}

greet("bob");
greet("alice");
greet("alice");
console.count();
console.countReset();
```

خروجی کنسول چیزی شبیه به این خواهد بود:

```plain
"default: 1"
"default: 2"
"default: 3"
"default: 4"
"default: 0"
```

توجه داشته باشید که فراخوانی `console.counterReset()` مقدار شمارنده پیش‌فرض را به صفر بازنشانی می‌کند.

اگر متغیر `user` را به‌عنوان آرگومان `label` با رشته «bob» به اولین فراخوانی `console.count()` و با رشته «alice» به دومین فراخوانی پاس بدهیم:

```js
function greet(user) {
  console.count(user);
  return `hi ${user}`;
}

greet("bob");
greet("alice");
greet("alice");
console.countReset("bob");
console.count("alice");
```

خروجی به شکل زیر خواهد بود:

```plain
"bob: 1"
"alice: 1"
"alice: 2"
"bob: 0"
"alice: 3"
```

بازنشانی مقدار شمارنده «bob» فقط مقدار همان شمارنده را تغییر می‌دهد. مقدار «alice» بدون تغییر می‌ماند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مستندات Microsoft Edge برای `console.countReset()`](https://learn.microsoft.com/en-us/microsoft-edge/devtools/console/api#countreset)
- [مستندات Node.js برای `console.countReset()`](https://nodejs.org/docs/latest/api/console.html#consolecountresetlabel)
- [مستندات Google Chrome برای `console.countReset()`](https://developer.chrome.com/docs/devtools/console/api/#countreset)