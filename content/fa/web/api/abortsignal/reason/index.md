---
title: "AbortSignal: reason property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AbortSignal/reason"
translated_by: "n8n + AI"
---

ویژگی فقط خواندنی **`reason`** یک مقدار JavaScript را برمی‌گرداند که دلیل abort شدن را نشان می‌دهد.

وقتی سیگنال abort نشده باشد، مقدار این ویژگی `undefined` است.
می‌توان هنگام abort شدن سیگنال، با استفاده از `AbortController.abort()` یا `AbortSignal.abort()`، مقدار مشخصی به آن اختصاص داد.
اگر در این متدها به‌طور صریح مقداری تعیین نشود، به‌طور پیش‌فرض `DOMException` از نوع `"AbortError"` در نظر گرفته می‌شود.

## مقدار

یک مقدار JavaScript که دلیل abort شدن را نشان می‌دهد، یا در صورت abort نشدن، `undefined`.

## مثال‌ها

در قطعه کد زیر، یک شیء `AbortController` جدید می‌سازیم و `AbortSignal` آن را (که از طریق ویژگی `signal` در دسترس است) دریافت می‌کنیم.
سپس با استفاده از ویژگی `aborted` بررسی می‌کنیم که آیا سیگنال abort شده است یا خیر، و وضعیت abort و دلیل آن را در کنسول ثبت می‌کنیم.

```js
const controller = new AbortController();
const signal = controller.signal;

// …

if (signal.aborted) {
  if (signal.reason) {
    console.log(`Request aborted with reason: ${signal.reason}`);
  } else {
    console.log("Request aborted but no reason was given.");
  }
} else {
  console.log("Request not aborted");
}
```

## همچنین ببینید

- [Fetch API](/en-US/docs/Web/API/Fetch_API)