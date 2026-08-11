---
title: "AbortController: abort() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AbortController/abort"
translated_by: "n8n + AI"
---

## متد `abort()` از `AbortController`

متد **`abort()`** در رابط `AbortController`، یک عملیات ناهمگام را پیش از تکمیل شدن متوقف می‌کند.  
با این متد می‌توانید [درخواست‌های fetch](/en-US/docs/Web/API/Window/fetch)، مصرف بدنهٔ پاسخ‌ها، یا استریم‌ها را لغو کنید.

## نحو

```js-nolint
abort()
abort(reason)
```

### پارامترها

- `reason` {{optional_inline}}
  - : دلیل لغو عملیات که می‌تواند هر مقدار جاوااسکریپتی باشد.  
    اگر مشخص نشود، دلیل به `"AbortError"` (یک `DOMException`) تنظیم می‌شود.

### مقدار بازگشتی

هیچ (`undefined`).

## مثال‌ها

برای نمونه‌های استفاده، [صفحهٔ `AbortSignal`](/en-US/docs/Web/API/AbortSignal#examples) را ببینید.  
همچنین می‌توانید یک [مثال کامل روی GitHub](https://github.com/mdn/dom-examples/tree/main/abort-api) و [نسخهٔ زندهٔ آن](https://mdn.github.io/dom-examples/abort-api/) را مشاهده کنید.

## همچنین ببینید

- [Fetch API](/en-US/docs/Web/API/Fetch_API)