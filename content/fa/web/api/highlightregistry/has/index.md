---
title: "HighlightRegistry: has() method"
short-title: has()
slug: Web/API/HighlightRegistry/has
page-type: web-api-instance-method
browser-compat: api.HighlightRegistry.has
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-map.prototype.has
---

{{APIRef("CSS Custom Highlight API")}}

متد **`has()`** در رابط {{domxref("HighlightRegistry")}} یک مقدار بولین برمی‌گرداند که نشان می‌دهد آیا یک شیء {{domxref("Highlight")}} با نام مشخص‌شده در رجیستری وجود دارد یا خیر.

`HighlightRegistry` یک شیء شبیه به {{jsxref("Map")}} است، بنابراین این متد مشابه استفاده از {{jsxref("Map.has()")}} عمل می‌کند.

## نحو (Syntax)

```js-nolint
has(name)
```

### پارامترها

- `name`
  - : نام شیء `Highlight` که باید برای بررسی وجود آن در رجیستری آزموده شود.

### مقدار بازگشتی

اگر هایلایتی با نام مشخص‌شده در رجیستری وجود داشته باشد، `true` و در غیر این صورت `false` برمی‌گرداند.

## مثال‌ها

```js
const fooHighlight = new Highlight();
CSS.highlights.set("foo", fooHighlight);

myHighlight.has("foo"); // true
myHighlight.has("bar"); // false
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- [CSS Custom Highlight API: The Future of Highlighting Text Ranges on the Web](https://css-tricks.com/css-custom-highlight-api-early-look/)