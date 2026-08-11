---
title: "AbortSignal: aborted property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AbortSignal/aborted"
translated_by: "n8n + AI"
---

# AbortSignal: ویژگی aborted

ویژگی فقط‌خواندنی **`aborted`** یک مقدار بازمی‌گرداند که نشان می‌دهد آیا عملیات ناهمگام (asynchronous) که با این سیگنال در ارتباط هستند، لغو شده‌اند (`true`) یا خیر (`false`).

## مقدار

`true` (لغو شده) یا `false`

## مثال‌ها

در قطعه کد زیر، یک شیء جدید `AbortController` می‌سازیم و `AbortSignal` آن را (که از طریق ویژگی `signal` در دسترس است) دریافت می‌کنیم. سپس با استفاده از ویژگی `aborted` بررسی می‌کنیم که آیا این سیگنال لغو شده است یا خیر و پیام مناسبی را در کنسول چاپ می‌کنیم.

```js
const controller = new AbortController();
const signal = controller.signal;

// …

if (signal.aborted) {
  console.log("Request has been aborted");
} else {
  console.log("Request not aborted");
}
```

## جستارهای وابسته

- [Fetch API](/en-US/docs/Web/API/Fetch_API)