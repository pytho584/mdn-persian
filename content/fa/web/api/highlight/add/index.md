---
title: "Highlight: add() method"
short-title: add()
slug: Web/API/Highlight/add
page-type: web-api-instance-method
browser-compat: api.Highlight.add
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-set.prototype.add
---

{{APIRef("CSS Custom Highlight API")}}

متد **`add()`** در رابط {{domxref("Highlight")}} یک شیء {{domxref("AbstractRange")}} تازه به یک هایلایت اضافه می‌کند تا با استفاده از {{domxref("css_custom_highlight_api", "CSS Custom Highlight API", "", "nocode")}} استایل‌دهی شود.

`Highlight` یک شیء شبیه به {{jsxref("Set")}} است، بنابراین این کار مشابه استفاده از {{jsxref("Set.add()")}} است.

## Syntax

```js-nolint
add(range)
```

### Parameters

- `range`
  - : یک شیء {{domxref("AbstractRange")}} که باید به `Highlight` اضافه شود.

### Return value

شیء `Highlight` به همراه محدوده‌ی اضافه‌شده.

## Examples

قطعه‌کد زیر نشان می‌دهد که چگونه دو range به یک شیء highlight جدید اضافه کنیم:

```js
const highlight = new Highlight();

const range1 = new Range();
const range2 = new Range();

highlight.add(range1).add(range2);

console.log(highlight.size); // 2
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- [CSS Custom Highlight API: The Future of Highlighting Text Ranges on the Web](https://css-tricks.com/css-custom-highlight-api-early-look/)