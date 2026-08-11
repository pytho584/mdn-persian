---
title: "AbortSignal: timeout() static method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AbortSignal/timeout_static"
translated_by: "n8n + AI"
---

متد استاتیک **`AbortSignal.timeout()`** یک شیء {{domxref("AbortSignal")}} برمی‌گرداند که پس از مدت زمان مشخصی به‌طور خودکار abort می‌شود.

هنگام timeout، این سیگنال با یک `TimeoutError` از نوع {{domxref("DOMException")}} abort می‌شود.

مبنای timeout زمان فعال است، نه زمان سپری‌شده؛ بنابراین اگر کد در یک worker معلق اجرا شود یا سند در حافظهٔ پنهان back-forward ([bfcache](https://web.dev/articles/bfcache)) قرار داشته باشد، عملاً متوقف می‌ماند.

برای ترکیب چند سیگنال می‌توانید از {{domxref("AbortSignal/any_static", "AbortSignal.any()")}} استفاده کنید، مثلاً برای abort مستقیم یک دانلود با کمک یک سیگنال timeout یا با فراخوانی {{domxref("AbortController.abort()")}}.

## Syntax

```js-nolint
AbortSignal.timeout(time)
```

### Parameters

- `time`
  - : زمان «active» به میلی‌ثانیه پیش از آنکه `AbortSignal` برگشتی abort شود. این مقدار باید در بازهٔ ۰ تا {{jsxref("Number.MAX_SAFE_INTEGER")}} باشد.

### Return value

یک {{domxref("AbortSignal")}}.

به‌هنگام timeout سیگنال abort شده و ویژگی {{domxref("AbortSignal.reason")}} آن برابر با یک `TimeoutError` از نوع {{domxref("DOMException")}} قرار می‌گیرد؛ در صورتی که عملیات توسط کاربر متوقف شده باشد، این ویژگی برابر با `AbortError` از نوع {{domxref("DOMException")}} خواهد بود.

## Examples

مثال زیر یک عملیات fetch را نشان می‌دهد که اگر پس از ۵ ثانیه ناموفق بماند با timeout متوقف می‌شود. توجه کنید که این شکست ممکن است دلایل دیگری هم داشته باشد؛ مثلاً متد پشتیبانی نشود، دکمهٔ "stop" مرورگر فشرده شود یا مشکلی دیگر پیش بیاید.

```js
const url = "https://path_to_large_file.mp4";

try {
  const res = await fetch(url, { signal: AbortSignal.timeout(5000) });
  const result = await res.blob();
  // …
} catch (err) {
  if (err.name === "TimeoutError") {
    // This exception is from the abort signal
    console.error("Timeout: It took more than 5 seconds to get the result!");
  } else if (err.name === "AbortError") {
    // This exception is from the fetch itself
    console.error(
      "Fetch aborted by user action (browser stop button, closing tab, etc.",
    );
  } else if (err.name === "TypeError") {
    console.error("AbortSignal.timeout() method is not supported");
  } else {
    // A network error, or some other problem.
    console.error(`Error: type: ${err.name}, message: ${err.message}`);
  }
}
```

## Specifications

## Browser compatibility