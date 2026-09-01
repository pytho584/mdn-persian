---
title: "HighlightRegistry: clear() method"
short-title: clear()
slug: Web/API/HighlightRegistry/clear
page-type: web-api-instance-method
browser-compat: api.HighlightRegistry.clear
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-map.prototype.clear
---

{{APIRef("CSS Custom Highlight API")}}

متد **`clear()`** از رابط {{domxref("HighlightRegistry")}} همه‌ی اشیاء {{domxref("Highlight")}} ثبت‌شده در `HighlightRegistry` را حذف می‌کند.

`HighlightRegistry` یک شیء شبیه به {{jsxref("Map")}} است، بنابراین این متد مشابه استفاده از {{jsxref("Map.clear()")}} می‌باشد.

## Syntax

```js-nolint
clear()
```

### Parameters

هیچکدام.

### Return value

هیچکدام ({{jsxref("undefined")}}).

## Examples

قطعه کد زیر دو شیء highlight را در ثبّات (registry) ثبت می‌کند و سپس ثبّات را پاک می‌کند:

```js
const customHighlight1 = new Highlight(range1, range2);
const customHighlight2 = new Highlight(range3, range4, range5);

CSS.highlights.set("custom-highlight-1", customHighlight1);
CSS.highlights.set("custom-highlight-2", customHighlight2);

console.log(CSS.highlights.size); // 2

CSS.highlights.clear();
console.log(CSS.highlights.size); // 0
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- [CSS Custom Highlight API: The Future of Highlighting Text Ranges on the Web](https://css-tricks.com/css-custom-highlight-api-early-look/)