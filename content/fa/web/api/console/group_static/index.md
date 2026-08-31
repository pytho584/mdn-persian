---
title: "console: group() static method"
short-title: group()
slug: Web/API/console/group_static
page-type: web-api-static-method
browser-compat: api.console.group_static
---

{{APIRef("Console API")}} {{AvailableInWorkers}}

متد ایستای **`console.group()`** یک گروه درون‌خطی جدید در [وب کنسول](https://firefox-source-docs.mozilla.org/devtools-user/web_console/index.html) ایجاد می‌کند. در نتیجه، هر پیام کنسول بعدی تا زمانی که {{domxref("console/groupEnd_static", "console.groupEnd()")}} فراخوانی نشود، با یک سطح تورفتگی اضافی نمایش داده می‌شود.

## نحو

```js-nolint
console.group()
console.group(label)
```

### پارامترها

- `label` {{optional_inline}}
  - : برچسب گروه.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

می‌توانید از گروه‌های تودرتو برای سازماندهی بهتر خروجی و ارتباط بصری پیام‌های مرتبط استفاده کنید. برای ایجاد یک بلوک تودرتوی جدید، `console.group()` را فراخوانی کنید. متد `console.groupCollapsed()` مشابه است، با این تفاوت که بلوک جدید جمع‌شده بوده و برای خواندن آن نیاز به کلیک روی دکمه‌ی افشا است.

برای خروج از گروه فعلی، `console.groupEnd()` را فراخوانی کنید. برای مثال، با این کد:

```js
console.log("This is the outer level");
console.group();
console.log("Level 2");
console.group();
console.log("Level 3");
console.warn("More of level 3");
console.groupEnd();
console.log("Back to level 2");
console.groupEnd();
console.log("Back to the outer level");
```

خروجی به این شکل خواهد بود:

![تصویری از پیام‌های تودرتو در خروجی کنسول.](nesting.png)

برای جزئیات بیشتر، بخش [استفاده از گروه‌ها در کنسول](/en-US/docs/Web/API/console#using_groups_in_the_console) در مستندات {{domxref("console")}} را ببینید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("console/groupEnd_static", "console.groupEnd()")}}
- {{domxref("console/groupCollapsed_static", "console.groupCollapsed()")}}
- [مستندات Microsoft Edge برای `console.group()`](https://learn.microsoft.com/en-us/microsoft-edge/devtools/console/api#group)
- [مستندات Node.js برای `console.group()`](https://nodejs.org/docs/latest/api/console.html#consolegrouplabel)
- [مستندات Google Chrome برای `console.group()`](https://developer.chrome.com/docs/devtools/console/api/#group)