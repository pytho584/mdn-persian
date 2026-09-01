---
title: "Highlight: size property"
short-title: size
slug: Web/API/Highlight/size
page-type: web-api-instance-property
browser-compat: api.Highlight.size
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-get-set.prototype.size
---

{{APIRef("CSS Custom Highlight API")}}

ویژگی **`size`** تعداد اشیاء {{domxref("AbstractRange")}} موجود در یک شیء {{domxref("Highlight")}} را برمیگرداند.

## مقدار

مقدار `size` یک عدد صحیح فقط‌خواندنی است که تعداد ورودی‌های شیء highlight را نشان می‌دهد.

## مثال‌ها

### استفاده از size

```js
const highlight = new Highlight();
highlight.add(range1);
highlight.add(range2);
highlight.add(range3);

console.log(highlight.size); // 3
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- [CSS Custom Highlight API: The Future of Highlighting Text Ranges on the Web](https://css-tricks.com/css-custom-highlight-api-early-look/)