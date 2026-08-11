---
title: "AbortSignal: any() static method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AbortSignal/any_static"
translated_by: "n8n + AI"
---

متد static **`AbortSignal.any()`** یک iterable از abort signalها دریافت کرده و یک {{domxref("AbortSignal")}} برمی‌گرداند. abort signal برگردانده شده به محض abort شدن هر یک از abort signalهای ورودی، خودش هم abort می‌شود. دلیل abort ({{domxref("AbortSignal.reason", "abort reason")}}) برابر با دلیل اولین سیگنالی که abort شده تنظیم می‌شود. اگر هر یک از abort signalهای داده شده از قبل abort شده باشند، {{domxref("AbortSignal")}} برگشتی هم از قبل abort شده خواهد بود.

## Syntax

```js-nolint
AbortSignal.any(iterable)
```

### Parameters

- `iterable`
  - : یک [iterable](/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#the_iterable_protocol) (مثلاً یک {{jsxref("Array")}}) از abort signalها.

### Return value

یک {{domxref("AbortSignal")}} که:

- **از قبل abort شده**، اگر هر یک از abort signalهای ورودی از قبل abort شده باشد. دلیل abort سیگنال برگشتی از قبل برابر با {{domxref("AbortSignal.reason", "reason")}} اولین abort signalای که abort شده بود تنظیم می‌شود.
- **به صورت غیرهمزمان abort می‌شود**، زمانی که هر یک از abort signalهای درون `iterable` abort شوند. {{domxref("AbortSignal.reason", "reason")}} برابر با دلیل اولین سیگنالی که abort می‌شود تنظیم خواهد شد.

## Examples

### استفاده از `AbortSignal.any()`

این مثال ترکیب یک signal از یک {{domxref("AbortController")}} و یک timeout signal از {{domxref("AbortSignal/timeout_static", "AbortSignal.timeout")}} را نشان می‌دهد.

```js
const cancelDownloadButton = document.getElementById("cancelDownloadButton");

const userCancelController = new AbortController();

cancelDownloadButton.addEventListener("click", () => {
  userCancelController.abort();
});

// Timeout after 5 minutes
const timeoutSignal = AbortSignal.timeout(1_000 * 60 * 5);

// This signal will abort when either the user clicks the cancel button or 5 minutes is up
// whichever is sooner
const combinedSignal = AbortSignal.any([
  userCancelController.signal,
  timeoutSignal,
]);

try {
  const res = await fetch(someUrlToDownload, {
    // Stop the fetch when any of the signals aborts
    signal: combinedSignal,
  });
  const body = await res.blob();
  // Do something with downloaded content:
  // …
} catch (e) {
  if (e.name === "AbortError") {
    // Cancelled by the user
  } else if (e.name === "TimeoutError") {
    // Show user that download timed out
  } else {
    // Other error, e.g. network error
  }
}
```