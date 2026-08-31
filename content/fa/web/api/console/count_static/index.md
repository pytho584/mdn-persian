---
title: "console: count() static method"
short-title: count()
slug: Web/API/console/count_static
page-type: web-api-static-method
browser-compat: api.console.count_static
---

{{APIRef("Console API")}} {{AvailableInWorkers}}

متد استاتیک **`console.count()`** تعداد دفعات فراخوانیِ این فراخوانی خاصِ `count()` را در لاگ ثبت می‌کند.

## نحو (Syntax)

```js-nolint
console.count()
console.count(label)
```

### پارامترها

- `label` {{Optional_Inline}}
  - : یک رشته. اگر ارائه شود، `count()` تعداد دفعاتی که با این برچسب فراخوانی شده است را خروجی می‌دهد. اگر حذف شود، `count()` طوری رفتار می‌کند که گویی با برچسب «پیش‌فرض» (default) فراخوانی شده است.

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
greet();
console.count();
```

خروجی کنسول چیزی شبیه به این خواهد بود:

```plain
"default: 1"
"default: 2"
"default: 3"
"default: 4"
```

برچسب به صورت `default` نمایش داده می‌شود، زیرا برچسب صریحی ارائه نشده بود.

اگر متغیر `user` را به عنوان آرگومان `label` در اولین فراخوانی `console.count()` و رشته «alice» را در دومین فراخوانی پاس دهیم:

```js
function greet(user) {
  console.count(user);
  return `hi ${user}`;
}

greet("bob");
greet("alice");
greet("alice");
console.count("alice");
```

خروجی زیر را خواهیم دید:

```plain
"bob: 1"
"alice: 1"
"alice: 2"
"alice: 3"
```

اکنون شمارش‌های جداگانه‌ای را فقط بر اساس مقدار `label` نگه می‌داریم.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مستندات مایکروسافت اج برای `console.count()`](https://learn.microsoft.com/en-us/microsoft-edge/devtools/console/api#count)
- [مستندات Node.js برای `console.count()`](https://nodejs.org/docs/latest/api/console.html#consolecountlabel)
- [مستندات گوگل کروم برای `console.count()`](https://developer.chrome.com/docs/devtools/console/api/#count)