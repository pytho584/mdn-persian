---
title: "HighlightRegistry: values() method"
---

---
title: "HighlightRegistry: values() method"
short-title: values()
slug: Web/API/HighlightRegistry/values
page-type: web-api-instance-method
browser-compat: api.HighlightRegistry.values
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-map.prototype.values
---

{{APIRef("CSS Custom Highlight API")}}

متد **`values()`** از رابط {{domxref("HighlightRegistry")}} یک شیء [Iterator](/en-US/docs/Web/JavaScript/Guide/Iterators_and_generators) جدید برمی‌گرداند که شامل مقادیر هر شیء `Highlight` در شیء `HighlightRegistry` به ترتیب درج است.

`HighlightRegistry` یک شیء شبیه به {{jsxref("Map")}} است، بنابراین این متد مشابه استفاده از {{jsxref("Map.values()")}} است.

## Syntax

```js-nolint
values()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک شیء iterator جدید که شامل هر شیء `Highlight` در ثبات، به ترتیب درج است.

## مثال‌ها

قطعه کد زیر نحوه ایجاد و ثبت سه شیء `Highlight` و استفاده از iterator بازگشتی توسط متد `values()` برای لاگ کردن highlightها را نشان می‌دهد:

```js
const fooHighlight = new Highlight();
const barHighlight = new Highlight();
const bazHighlight = new Highlight();

CSS.highlights.set("foo", fooHighlight);
CSS.highlights.set("bar", barHighlight);
CSS.highlights.set("baz", bazHighlight);

const iter = CSS.highlights.values();

console.log(iter.next().value); // Highlight
console.log(iter.next().value); // Highlight
console.log(iter.next().value); // Highlight
```

مثال کد زیر نحوه پیمایش highlightها در ثبات با استفاده از حلقه [`for...of`](/en-US/docs/Web/JavaScript/Reference/Statements/for...of) را نشان می‌دهد:

```js
const fooHighlight = new Highlight();
const barHighlight = new Highlight();
const bazHighlight = new Highlight();

CSS.highlights.set("foo", fooHighlight);
CSS.highlights.set("bar", barHighlight);
CSS.highlights.set("baz", bazHighlight);

for (const highlight of CSS.highlights.values()) {
  console.log(highlight); // Highlight
}
```

## Specifications

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- [CSS Custom Highlight API: The Future of Highlighting Text Ranges on the Web](https://css-tricks.com/css-custom-highlight-api-early-look/)