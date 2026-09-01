---
title: "HighlightRegistry: keys() method"
short-title: keys()
slug: Web/API/HighlightRegistry/keys
page-type: web-api-instance-method
browser-compat: api.HighlightRegistry.keys
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-map.prototype.keys
---

{{APIRef("CSS Custom Highlight API")}}

متد **`keys()`** در رابط {{domxref("HighlightRegistry")}} یک شیء [Iterator](/en-US/docs/Web/JavaScript/Guide/Iterators_and_generators) جدید برمی‌گرداند که شامل کلیدهای هر شیء `Highlight` در شیء `HighlightRegistry`، به ترتیب درج، می‌باشد.

`HighlightRegistry` یک شیء شبیه به {{jsxref("Map")}} است، بنابراین این متد مشابه استفاده از {{jsxref("Map.keys()")}} می‌باشد.

## Syntax

```js-nolint
keys()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء iterator جدید که نام هر شیء `Highlight` را در registry، به ترتیب درج، دربردارد.

## مثال‌ها

قطعه کد زیر نحوه ایجاد و ثبت سه شیء `Highlight` و استفاده از iterator برگردانده‌شده توسط متد `keys()` برای ثبت نام آن‌ها را نشان می‌دهد:

```js
const fooHighlight = new Highlight();
const barHighlight = new Highlight();
const bazHighlight = new Highlight();

CSS.highlights.set("foo", fooHighlight);
CSS.highlights.set("bar", barHighlight);
CSS.highlights.set("baz", bazHighlight);

const iter = CSS.highlights.keys();

console.log(iter.next().value); // "foo"
console.log(iter.next().value); // "bar"
console.log(iter.next().value); // "baz"
```

مثال کد زیر نحوه پیمایش روی هایلایت‌های موجود در registry را با استفاده از حلقه [`for...of`](/en-US/docs/Web/JavaScript/Reference/Statements/for...of) نشان می‌دهد:

```js
const fooHighlight = new Highlight();
const barHighlight = new Highlight();
const bazHighlight = new Highlight();

CSS.highlights.set("foo", fooHighlight);
CSS.highlights.set("bar", barHighlight);
CSS.highlights.set("baz", bazHighlight);

for (const name of CSS.highlights.keys()) {
  console.log(name);
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- [CSS Custom Highlight API: The Future of Highlighting Text Ranges on the Web](https://css-tricks.com/css-custom-highlight-api-early-look/)