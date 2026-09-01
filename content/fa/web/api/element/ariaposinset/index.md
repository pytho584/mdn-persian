---
title: "Element: ariaPosInSet property"
short-title: ariaPosInSet
slug: Web/API/Element/ariaPosInSet
page-type: web-api-instance-property
browser-compat: api.Element.ariaPosInSet
---

{{APIRef("DOM")}}

ویژگی **`ariaPosInSet`** در رابط {{domxref("Element")}} مقدار ویژگی [`aria-posinset`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-posinset) را منعکس می‌کند که شماره یا موقعیت یک عنصر را در مجموعه فعلی از listitemها یا treeitemها تعریف می‌کند.

## مقدار

یک رشته شامل یک عدد صحیح.

## مثال‌ها

در این مثال، ویژگی `aria-posinset` روی عنصری با شناسه `article2` برابر با «2» تنظیم شده است. با استفاده از `ariaPosInSet` مقدار را به «3» تغییر می‌دهیم.

```html
<article id="article1" aria-posinset="1">…</article>
<article id="article2" aria-posinset="2">…</article>
```

```js
let el = document.getElementById("article2");
console.log(el.ariaPosInSet); // "2"
el.ariaPosInSet = "3";
console.log(el.ariaPosInSet); // "3"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}