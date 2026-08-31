---
title: "console: profile() static method"
short-title: profile()
slug: Web/API/console/profile_static
page-type: web-api-static-method
status:
  - non-standard
browser-compat: api.console.profile_static
---

{{APIRef("Console API")}}{{Non-standard_header}} {{AvailableInWorkers}}

متد استاتیک **`console.profile()`** شروع به ضبط یک پروفایل عملکرد می‌کند (برای مثال، [ابزار عملکرد فایرفاکس](https://firefox-source-docs.mozilla.org/devtools-user/performance/index.html)).

شما می‌توانید به صورت اختیاری یک آرگومان برای نام‌گذاری پروفایل ارائه دهید و این کار به شما امکان می‌دهد در صورت ضبط چندین پروفایل، فقط آن پروفایل را متوقف کنید. برای مشاهده نحوه تفسیر این آرگومان به {{domxref("console/profileEnd_static", "console.profileEnd()")}} مراجعه کنید.

برای توقف ضبط، {{domxref("console/profileEnd_static", "console.profileEnd()")}} را فراخوانی کنید.

## Syntax

```js-nolint
console.profile(profileName)
```

### پارامترها

- `profileName` {{Optional_Inline}}
  - : نامی که به پروفایل داده می‌شود.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("console/profileEnd_static", "console.profileEnd()")}}