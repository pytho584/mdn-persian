---
title: "HighlightRegistry: size property"
short-title: size
slug: Web/API/HighlightRegistry/size
page-type: web-api-instance-property
browser-compat: api.HighlightRegistry.size
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-get-map.prototype.size
---

{{APIRef("CSS Custom Highlight API")}}

ویژگی **`size`** تعداد اشیاء {{domxref("Highlight")}} را در {{domxref("HighlightRegistry")}} برمی‌گرداند.

## مقدار

یک عدد صحیح فقط‌خواندنی که نشان می‌دهد چند شیء `Highlight` در این رجیستری وجود دارد.

## مثال‌ها

### استفاده از size

```js
const highlight1 = new Highlight();
const highlight2 = new Highlight();

CSS.highlights.set("highlight-1", highlight1);
CSS.highlights.set("highlight-2", highlight2);

console.log(CSS.highlights.size); // 2
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- [CSS Custom Highlight API: آینده هایلایت کردن بازه‌های متن در وب](https://css-tricks.com/css-custom-highlight-api-early-look/)