```
---
title: "History: back() method"
---

---
title: "History: back() method"
short-title: back()
slug: Web/API/History/back
page-type: web-api-instance-method
browser-compat: api.History.back
---

{{APIRef("History API")}}

متد **`back()`** از واسط {{domxref("History")}} باعث میشود مرورگر یک صفحه به عقب در تاریخچه نشست برود.

همان اثری را دارد که فراخوانی {{domxref("History.go", "history.go(-1)")}}. اگر صفحهٔ قبلی وجود نداشته باشد، این فراخوانی هیچ کاری انجام نمیدهد.

این متد {{glossary("asynchronous")}} است. برای تعیین اینکه ناوبری چه زمانی تکمیل شده است، یک شنونده برای رویداد {{domxref("Window/popstate_event", "popstate")}} اضافه کنید.

## Syntax

```js-nolint
back()
```

### Parameters

هیچ.

### Return value

هیچ ({{jsxref("undefined")}}).

### Exceptions

- `SecurityError` {{domxref("DOMException")}}
  - : اگر سند مرتبط کاملاً فعال نباشد، پرتاب میشود. مرورگرها همچنین ناوبریها را محدود میکنند و در صورت فراخوانی بیش از حد مکرر، ممکن است این خطا را پرتاب کنند، هشدار تولید کنند، یا از فراخوانی صرفنظر کنند.

## Examples

مثال کوتاه زیر باعث میشود دکمهای در صفحه، یک ورودی در تاریخچه نشست به عقب برود.

### HTML

```html
<button id="go-back">Go back!</button>
```

### JavaScript

```js
document.getElementById("go-back").addEventListener("click", () => {
  history.back();
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("History")}}
- [Working with the History API](/en-US/docs/Web/API/History_API/Working_with_the_History_API)
```