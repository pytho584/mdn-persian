---
title: "HighlightRegistry: get() method"
short-title: get()
slug: Web/API/HighlightRegistry/get
page-type: web-api-instance-method
browser-compat: api.HighlightRegistry.get
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-map.prototype.get
---

{{APIRef("CSS Custom Highlight API")}}

متد **`get()`** از رابط {{domxref("HighlightRegistry")}}، شیء {{domxref("Highlight")}} با نام مشخص را از ثبت‌نام (registry) بازمی‌گرداند.

`HighlightRegistry` یک شیء شبیه به {{jsxref("Map")}} است، بنابراین این متد مشابه استفاده از {{jsxref("Map.get()")}} است.

## نحو

```js-nolint
get(name)
```

### پارامترها

- `name`
  - : نام شیء `Highlight` که باید از ثبت‌نام بازگردانده شود. نام باید یک {{jsxref("String")}} باشد.

### مقدار بازگشتی

شیء `Highlight` مرتبط با نام مشخص‌شده، یا {{jsxref("undefined")}} اگر نام در `HighlightRegistry` یافت نشود.

## مثال‌ها

نمونه کد زیر نحوه ایجاد یک `Highlight` جدید، افزودن آن به ثبت‌نام و بازیابی آن با نامش با استفاده از متد `get()` را نشان می‌دهد:

```js
const fooHighlight = new Highlight();
CSS.highlights.set("foo", fooHighlight);

console.log(CSS.highlights.get("foo")); // Returns the fooHighlight object.
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- [CSS Custom Highlight API: The Future of Highlighting Text Ranges on the Web](https://css-tricks.com/css-custom-highlight-api-early-look/)