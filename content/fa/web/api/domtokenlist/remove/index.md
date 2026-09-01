---
title: "DOMTokenList: remove() method"
short-title: remove()
slug: Web/API/DOMTokenList/remove
page-type: web-api-instance-method
browser-compat: api.DOMTokenList.remove
---

{{APIRef("DOM")}}

متد **`remove()``** در رابط {{domxref("DOMTokenList")}} توکن‌های مشخص‌شده را از فهرست حذف می‌کند.

## نحو (Syntax)

```js-nolint
remove(token1)
remove(token1, token2)
remove(token1, token2, /* …, */ tokenN)
```

### پارامترها

- `token1`, …, `tokenN`
  - : رشته‌ای که نشان‌دهنده توکنی است که می‌خواهید از فهرست حذف کنید. اگر رشته در فهرست وجود نداشته باشد، خطایی رخ نمی‌دهد و هیچ اتفاقی نمی‌افتد.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

در مثال زیر، فهرست کلاس‌های یک عنصر {{htmlelement("span")}} را به صورت `DOMTokenList` با استفاده از {{domxref("Element.classList")}} دریافت می‌کنیم. سپس یک توکن را از فهرست حذف کرده و فهرست را درون خاصیت {{domxref("Node.textContent")}} آن `<span>` می‌نویسیم.

ابتدا، HTML:

```html
<span id="ab" class="a b c"></span> <span id="a" class="a b c"></span>
```

حالا JavaScript:

```js
const span = document.getElementById("ab");
const classes = span.classList;
classes.remove("c");
span.textContent = classes;
```

برای حذف چند کلاس به‌طور همزمان، می‌توانید چند توکن را ارائه دهید. ترتیب ارائه توکن‌ها نیازی به تطابق با ترتیب ظاهر شدن آن‌ها در فهرست ندارد:

```js
const span2 = document.getElementById("a");
const classes2 = span2.classList;

classes2.remove("c", "b");
span2.textContent = classes2;
```

خروجی به این شکل است:

{{ EmbedLiveSample('Examples', '100%', 60) }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}