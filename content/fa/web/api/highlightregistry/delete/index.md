---
title: "HighlightRegistry: delete() method"
short-title: delete()
slug: Web/API/HighlightRegistry/delete
page-type: web-api-instance-method
browser-compat: api.HighlightRegistry.delete
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-map.prototype.delete
---

{{APIRef("CSS Custom Highlight API")}}

متد **`delete()`** از رابط {{domxref("HighlightRegistry")}} یک شیء {{domxref("Highlight")}} با نام مشخص را از `HighlightRegistry` حذف می‌کند.

`HighlightRegistry` یک شیء شبیه به {{jsxref("Map")}} است، بنابراین این متد مشابه استفاده از {{jsxref("Map.delete()")}} می‌باشد.

## نحو

```js-nolint
delete(customHighlightName)
```

### پارامترها

- `customHighlightName`
  - : نام شیء {{domxref("Highlight")}} به صورت یک {{jsxref("String")}} که باید از `HighlightRegistry` حذف شود.

### مقدار بازگشتی

اگر یک شیء `Highlight` با نام داده شده در `HighlightRegistry` وجود داشته باشد، `true` و در غیر این صورت `false` بازمی‌گرداند.

## مثال‌ها

نمونه کد زیر یک هایلایت را در ثبات ثبت می‌کند و سپس آن را حذف می‌کند:

```js
const myHighlight = new Highlight(range1, range2);

CSS.highlights.set("my-highlight", myHighlight);

CSS.highlights.delete("foo"); // false
CSS.highlights.delete("my-highlight"); // true
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- [رابط برنامه‌نویسی CSS Custom Highlight: آینده برجسته‌سازی محدوده‌های متن در وب](https://css-tricks.com/css-custom-highlight-api-early-look/)