---
title: "Highlight: has() method"
short-title: has()
slug: Web/API/Highlight/has
page-type: web-api-instance-method
browser-compat: api.Highlight.has
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-set.prototype.has
---

{{APIRef("CSS Custom Highlight API")}}

متد **`has()`** از رابط {{domxref("Highlight")}} یک مقدار بولی (boolean) برمی‌گرداند که نشان می‌دهد آیا یک شیء {{domxref("AbstractRange")}} در یک شیء `Highlight` وجود دارد یا خیر.

`Highlight` یک شیء شبیه به {{jsxref("Set")}} است، بنابراین این متد مشابه استفاده از {{jsxref("Set.has()")}} است.

## نحو (Syntax)

```js-nolint
has(range)
```

### پارامترها

- `range`
  - : شیء `AbstractRange` که باید حضور آن در شیء `Highlight` بررسی شود.

### مقدار بازگشتی

اگر بازه (range) مشخص‌شده در شیء `Highlight` وجود داشته باشد، `true` و در غیر این صورت `false` برمی‌گرداند.

## مثال‌ها

قطعه کد زیر دو بازه و یک شیء هایلایت که شامل یکی از آنهاست ایجاد می‌کند. سپس کد از متد `has()` برای بررسی وجود هر بازه در هایلایت استفاده می‌کند:

```js
const range1 = new Range();
const range2 = new Range();
const myHighlight = new Highlight(range1);

myHighlight.has(range1); // true
myHighlight.has(range2); // false
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- [CSS Custom Highlight API: The Future of Highlighting Text Ranges on the Web](https://css-tricks.com/css-custom-highlight-api-early-look/)