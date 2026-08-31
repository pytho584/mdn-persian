---
title: "console: profileEnd() static method"
short-title: profileEnd()
slug: Web/API/console/profileEnd_static
page-type: web-api-static-method
status:
  - non-standard
browser-compat: api.console.profileEnd_static
---

{{APIRef("Console API")}}{{Non-standard_header}} {{AvailableInWorkers}}

متد استاتیک **`console.profileEnd()`** ضبط یک پروفایل را که قبلاً با {{domxref("console/profile_static", "console.profile()")}} شروع شده است، متوقف می‌کند.

می‌توانید به‌صورت اختیاری یک آرگومان برای نام‌گذاری پروفایل ارائه دهید. این کار به شما امکان می‌دهد اگر چندین پروفایل در حال ضبط دارید، فقط آن پروفایل خاص را متوقف کنید.

- اگر به `console.profileEnd()` یک نام پروفایل داده شود و با نام پروفایل در حال ضبط مطابقت داشته باشد، آن پروفایل متوقف می‌شود.
- اگر به `console.profileEnd()` یک نام پروفایل داده شود و با نام پروفایل در حال ضبط مطابقت نداشته باشد، هیچ تغییری اعمال نخواهد شد.
- اگر به `console.profileEnd()` نام پروفایلی داده نشود، آخرین پروفایل شروع‌شده توقف می‌شود.

## سینتکس

```js-nolint
console.profileEnd(profileName)
```

### پارامترها

- `profileName` {{Optional_Inline}}
  - : نامی که به پروفایل داده می‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("console/profile_static", "console.profile()")}}