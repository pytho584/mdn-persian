---
title: "Highlight: delete() method"
---

---
title: "Highlight: delete() method"
short-title: delete()
slug: Web/API/Highlight/delete
page-type: web-api-instance-method
browser-compat: api.Highlight.delete
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-set.prototype.delete
---

{{APIRef("CSS Custom Highlight API")}}

متد **`delete()`** از رابط {{domxref("Highlight")}} یک شیء {{domxref("AbstractRange")}} مشخص را از یک شیء `Highlight` حذف می‌کند.

`Highlight` یک شیء شبیه به {{jsxref("Set")}} است، بنابراین این متد مشابه استفاده از {{jsxref("Set.delete()")}} است.

## Syntax

```js-nolint
delete(range)
```

### Parameters

- `range`
  - : شیء {{domxref("AbstractRange")}} که باید از `Highlight` حذف شود.

### Return value

اگر `range` قبلاً در `Highlight` وجود داشته باشد `true` و در غیر این صورت `false` بازمی‌گرداند.

## Examples

قطعه کد زیر نحوه ایجاد یک هایلایت جدید با دو ناحیه و سپس حذف یکی از آنها را نشان می‌دهد:

```js
const range1 = new Range();
const range2 = new Range();

const highlight = new Highlight(range1, range2);
console.log(highlight.size); // 2

highlight.delete(range1);
console.log(highlight.size); // 1
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- [CSS Custom Highlight API: The Future of Highlighting Text Ranges on the Web](https://css-tricks.com/css-custom-highlight-api-early-look/)