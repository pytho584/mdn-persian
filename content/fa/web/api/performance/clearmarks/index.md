---
title: "Performance: clearMarks() method"
short-title: clearMarks()
slug: Web/API/Performance/clearMarks
page-type: web-api-instance-method
browser-compat: api.Performance.clearMarks
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

متد **`clearMarks()`** همهٔ اشیاء {{domxref("PerformanceMark")}} یا برخی از آن‌ها را از خط زمانی عملکرد مرورگر حذف می‌کند.

## Syntax

```js-nolint
clearMarks()
clearMarks(name)
```

### Parameters

- `name` {{optional_inline}}
  - : رشته‌ای که {{domxref("PerformanceEntry.name", "name")}} مربوط به شیء {{domxref("PerformanceMark")}} را نشان می‌دهد. اگر این آرگومان حذف شود، همهٔ ورودی‌هایی که {{domxref("PerformanceEntry.entryType","entryType")}} آن‌ها `"mark"` است حذف خواهند شد.

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

### حذف نشانگرها

برای پاک‌سازی همهٔ نشانگرهای عملکرد یا فقط برخی ورودی‌های خاص، از متد `clearMarks()` به شکل زیر استفاده کنید:

```js
// Create a bunch of marks
performance.mark("login-started");
performance.mark("login-started");
performance.mark("login-finished");
performance.mark("form-sent");
performance.mark("video-loaded");
performance.mark("video-loaded");

performance.getEntriesByType("mark").length; // 6

// Delete just the "login-started" mark entries
performance.clearMarks("login-started");
performance.getEntriesByType("mark").length; // 4

// Delete all of the mark entries
performance.clearMarks();
performance.getEntriesByType("mark").length; // 0
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("PerformanceMark")}}