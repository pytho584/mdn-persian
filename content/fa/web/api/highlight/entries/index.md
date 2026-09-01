---
title: "Highlight: entries() method"
short-title: entries()
slug: Web/API/Highlight/entries
page-type: web-api-instance-method
browser-compat: api.Highlight.entries
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-set.prototype.entries
---

{{APIRef("CSS Custom Highlight API")}}

متد **`entries()`** از واسط {{domxref("Highlight")}} یک شیء [Iterator](/en-US/docs/Web/JavaScript/Guide/Iterators_and_generators) جدید برمی‌گرداند که شامل یک آرایه از `[range, range]` برای هر شیء {{domxref("AbstractRange")}} در شیء `Highlight` به ترتیب درج است.

`Highlight` یک شیء شبیه به {{jsxref("Set")}} است، بنابراین این متد مشابه استفاده از {{jsxref("Set.entries()")}} می‌باشد.

## نحو

```js-nolint
entries()
```

### پارامترها

هیچکدام.

### مقدار برگشتی

یک شیء مکرر (iterator) جدید که شامل آرایه‌ای از `[range, range]` برای هر شیء `AbstractRange` در `Highlight` داده شده، به ترتیب درج است.

## مثال‌ها

قطعه کد زیر نحوه ایجاد یک هایلایت جدید با دو محدوده (range) و سپس لاگ کردن محدوده‌ها با استفاده از مکرر (iterator) برگردانده شده توسط متد `entries()` را نشان می‌دهد:

```js
const text = new Text("Time is an illusion. Lunchtime doubly so.");

const range1 = document.createRange();
range1.setStart(text, 0);
range1.setEnd(text, 4);

const range2 = document.createRange();
range2.setStart(text, 21);
range2.setEnd(text, 30);

const myHighlight = new Highlight();
myHighlight.add(range1);
myHighlight.add(range2);

const iter = myHighlight.entries();

console.log(iter.next().value); // [Range, Range]
console.log(iter.next().value); // [Range, Range]
```

مثال کد زیر نحوه پیمایش محدوده‌ها در یک هایلایت با استفاده از حلقه [`for...of`](/en-US/docs/Web/JavaScript/Reference/Statements/for...of) را نشان می‌دهد:

```js
const text = new Text("Time is an illusion. Lunchtime doubly so.");

const range1 = document.createRange();
range1.setStart(text, 0);
range1.setEnd(text, 4);

const range2 = document.createRange();
range2.setStart(text, 21);
range2.setEnd(text, 30);

const highlight = new Highlight();
highlight.add(range1);
highlight.add(range2);

for (const [range] of highlight.entries()) {
  console.log(range.toString());
  // Time
  // Lunchtime
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- [CSS Custom Highlight API: آینده هایلایت کردن محدوده‌های متن در وب](https://css-tricks.com/css-custom-highlight-api-early-look/)