---
title: "AbortSignal: abort() static method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AbortSignal/abort_static"
translated_by: "n8n + AI"
---

## AbortSignal: متد استاتیک abort()

متد استاتیک **`AbortSignal.abort()`** یک `AbortSignal` برمی‌گرداند که از قبل در حالت abort قرار دارد (و رویداد `abort` را فعال نمی‌کند).

این معادل کوتاه‌شدهٔ کد زیر است:

```js
const controller = new AbortController();
controller.abort();
return controller.signal;
```

برای مثال، می‌توان این سیگنال را به متد fetch ارسال کرد تا منطق abort آن اجرا شود (یعنی ممکن است کد طوری سازمان‌دهی شده باشد که حتی اگر عملیات fetch مورد نظر شروع نشده باشد، منطق abort اجرا شود).

> [!NOTE]
> هدف این متد مشابه `Promise.reject` است.

## نحوه استفاده

```js-nolint
AbortSignal.abort()
AbortSignal.abort(reason)
```

### پارامترها

- `reason`
  - : دلیل abort شدن عملیات؛ می‌تواند هر مقدار جاوااسکریپتی باشد. اگر مشخص نشود، دلیل برابر با یک `DOMException` با نام `"AbortError"` در نظر گرفته می‌شود.

### مقدار بازگشتی

یک نمونه از `AbortSignal` که ویژگی `aborted` آن `true` و ویژگی `reason` آن برابر با مقدار دلیل تعیین‌شده یا مقدار پیش‌فرض است.