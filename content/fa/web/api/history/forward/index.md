---
title: "History: forward() method"
short-title: forward()
slug: Web/API/History/forward
page-type: web-api-instance-method
browser-compat: api.History.forward
---

{{APIRef("History API")}}

متد **`forward()`** در رابط {{domxref("History")}} باعث می‌شود مرورگر یک صفحه به جلو در تاریخچه جلسه حرکت کند. این متد همان اثر فراخوانی {{domxref("History.go", "history.go(1)")}} را دارد.

این متد {{glossary("asynchronous", "ناهمگام")}} است. برای تعیین زمان تکمیل پیمایش، یک شنونده برای رویداد {{domxref("Window/popstate_event", "popstate")}} اضافه کنید.

## Syntax

```js-nolint
forward()
```

### Parameters

هیچ.

### Return value

هیچ ({{jsxref("undefined")}}).

### Exceptions

- `SecurityError` {{domxref("DOMException")}}
  - : اگر سند مرتبط کاملاً فعال نباشد، این خطا پرتاب می‌شود. مرورگرها همچنین پیمایش‌ها را محدود می‌کنند و ممکن است در صورت فراخوانی بیش از حد مکرر، این خطا را پرتاب کنند، هشدار تولید کنند، یا فراخوانی را نادیده بگیرند.

## Examples

مثال‌های زیر دکمه‌ای ایجاد می‌کنند که یک قدم به جلو در تاریخچه جلسه حرکت می‌کند.

### HTML

```html
<button id="go-forward">Go Forward!</button>
```

### JavaScript

```js
document.getElementById("go-forward").addEventListener("click", (e) => {
  history.forward();
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("History")}}
- {{domxref("Window/popstate_event", "popstate")}}
- [کار با History API](/en-US/docs/Web/API/History_API/Working_with_the_History_API)