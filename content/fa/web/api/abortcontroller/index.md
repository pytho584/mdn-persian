---
title: "AbortController"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AbortController"
translated_by: "n8n + AI"
---

# AbortController

رابط **`AbortController`** یک شیء کنترلی است که به شما اجازه می‌دهد یک یا چند درخواست وب را در صورت نیاز لغو کنید.

می‌توانید با استفاده از سازندهٔ `AbortController()` یک نمونهٔ جدید از `AbortController` ایجاد کنید. ارتباط با عملیات ناهمگام از طریق یک شیء `AbortSignal` انجام می‌شود.

## Constructor

- `AbortController()`
  - : یک نمونهٔ جدید از `AbortController` ایجاد می‌کند.

## Instance properties

- `signal`
  - : یک شیء `AbortSignal` را برمی‌گرداند که می‌تواند برای ارتباط با یک عملیات ناهمگام یا لغو آن به کار رود.

## Instance methods

- `abort()`
  - : عملیات ناهمگام را پیش از تکمیل شدن لغو می‌کند. این متد می‌تواند درخواست‌های fetch، مصرف بدنهٔ پاسخ‌ها و استریم‌ها را لغو کند.

## Examples

برای مثال‌های استفاده، به صفحهٔ [`AbortSignal`](/en-US/docs/Web/API/AbortSignal#examples) مراجعه کنید. می‌توانید یک [مثال کامل کاری روی GitHub](https://github.com/mdn/dom-examples/tree/main/abort-api) پیدا کنید؛ همچنین می‌توانید [اجرای زندهٔ آن را ببینید](https://mdn.github.io/dom-examples/abort-api/).

## جستارهای وابسته

- [Fetch API](/en-US/docs/Web/API/Fetch_API)
- [Abortable Fetch](https://developer.chrome.com/blog/abortable-fetch/) نوشتهٔ Jake Archibald