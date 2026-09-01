---
title: "Highlight: keys() method"
short-title: keys()
slug: Web/API/Highlight/keys
page-type: web-api-instance-method
browser-compat: api.Highlight.keys
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-set.prototype.keys
---

{{APIRef("CSS Custom Highlight API")}}

متد **`keys()`** در رابط {{domxref("Highlight")}} یک نام مستعار (alias) برای متد {{domxref("Highlight.values()", "values()")}} است.

`Highlight` یک شیء شبیه به {{jsxref("Set")}} است، بنابراین این متد مشابه استفاده از {{jsxref("Set.keys()")}} عمل می‌کند.

## Syntax

```js-nolint
keys()
```

### Parameters

هیچ.

### Return value

یک شیء iterator جدید که شامل هر شیء `AbstractRange` در `Highlight` داده‌شده، به ترتیب درج، است.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- [CSS Custom Highlight API: The Future of Highlighting Text Ranges on the Web](https://css-tricks.com/css-custom-highlight-api-early-look/)