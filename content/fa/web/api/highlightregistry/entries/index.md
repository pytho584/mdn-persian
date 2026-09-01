---
title: "HighlightRegistry: entries() method"
short-title: entries()
slug: Web/API/HighlightRegistry/entries
page-type: web-api-instance-method
browser-compat: api.HighlightRegistry.entries
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-map.prototype.entries
---

{{APIRef("CSS Custom Highlight API")}}

متد **`entries()`** در رابط {{domxref("HighlightRegistry")}} یک شیء [Iterator](/en-US/docs/Web/JavaScript/Guide/Iterators_and_generators) جدید برمی‌گرداند که شامل جفت‌های `[name, highlight]` برای هر عنصر در شیء `HighlightRegistry` به ترتیب درج است.

`HighlightRegistry` یک شیء شبیه به {{jsxref("Map")}} است، بنابراین این کار مشابه استفاده از {{jsxref("Map.entries()")}} است.

## نحو (Syntax)

```js-nolint
entries()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء iterator جدید که شامل آرایه‌ای از `[name, highlight]` برای هر شیء `Highlight` در `HighlightRegistry` به ترتیب درج است.

## مثال‌ها

قطعه کد زیر دو هایلایت جدید ایجاد و ثبت می‌کند و سپس با استفاده از iterator بازگشتی از متد `entries()`، هایلایت‌ها و نام‌های آن‌ها را ثبت (log) می‌کند:

```js
const myHighlight1 = new Highlight();
const myHighlight2 = new Highlight();

CSS.highlights.set("first-highlight", myHighlight1);
CSS.highlights.set("second-highlight", myHighlight2);

const iter = CSS.highlights.entries();

console.log(iter.next().value); // ['first-highlight', Highlight]
console.log(iter.next().value); // ['second-highlight', Highlight]
```

مثال کد زیر نحوه پیمایش هایلایت‌ها در رجیستری را با استفاده از حلقه [`for...of`](/en-US/docs/Web/JavaScript/Reference/Statements/for...of) نشان می‌دهد:

```js
const myHighlight1 = new Highlight();
const myHighlight2 = new Highlight();

CSS.highlights.set("first-highlight", myHighlight1);
CSS.highlights.set("second-highlight", myHighlight2);

for (const [name, highlight] of CSS.highlights.entries()) {
  console.log(`Highlight ${name}`, highlight);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- [CSS Custom Highlight API: The Future of Highlighting Text Ranges on the Web](https://css-tricks.com/css-custom-highlight-api-early-look/)