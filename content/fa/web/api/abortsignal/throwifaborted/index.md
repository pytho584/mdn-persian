---
title: "AbortSignal: throwIfAborted() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AbortSignal/throwIfAborted"
translated_by: "n8n + AI"
---

متد **`throwIfAborted()`** در صورتی که سیگنال (signal) لغو (abort) شده باشد، دلیل (`reason`) لغو آن را پرتاب می‌کند؛ در غیر این صورت هیچ کاری انجام نمی‌دهد.

هر API‌ای که نیاز به پشتیبانی از لغو (aborting) داشته باشد، می‌تواند یک شیء `AbortSignal` دریافت کند و از `throwIfAborted()` برای بررسی و پرتاب در هنگام علامت‌دهی رویداد [`abort`](/en-US/docs/Web/API/AbortSignal/abort_event) استفاده کند.

همچنین می‌توان از این متد برای لغو عملیات در نقاط خاصی از کد استفاده کرد، به‌جای اینکه سیگنال را به توابعی که آن را می‌پذیرند، ارسال کرد.

## نحوه استفاده

```js-nolint
throwIfAborted()
```

### پارامترها

ندارد.

### مقدار برگشتی

ندارد (`undefined`).

## مثال‌ها

مثال‌های زیر برگرفته از مشخصات (specification) هستند.

### لغو یک عملیات polling

این مثال نشان می‌دهد که چگونه می‌توان از `throwIfAborted()` برای لغو یک عملیات polling استفاده کرد.

یک تابع ناهمگام `waitForCondition()` را در نظر بگیرید که با یک تابع ناهمگام دیگر `func`، یک مقدار هدف `targetValue` و یک `AbortSignal` فراخوانی می‌شود. این متد نتیجه `func` را در یک حلقه با `targetValue` مقایسه می‌کند و در صورت تطابق، بازمی‌گردد.

```js
async function waitForCondition(func, targetValue, { signal } = {}) {
  while (true) {
    signal?.throwIfAborted();

    const result = await func();
    if (result === targetValue) {
      return;
    }
  }
}
```

در هر تکرار حلقه، از `throwIfAborted()` استفاده می‌کنیم تا اگر عملیات لغو شده باشد، دلیل (`reason`) سیگنال را پرتاب کنیم (در غیر این‌صورت کاری انجام نمی‌دهد). اگر سیگنال لغو شود، این کار باعث رد شدن (reject) پرامیس `waitForCondition()` می‌شود.

## همچنین ببینید

- [Fetch API](/en-US/docs/Web/API/Fetch_API)