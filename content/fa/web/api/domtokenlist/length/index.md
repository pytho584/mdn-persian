---
title: "DOMTokenList: length property"
short-title: length
slug: Web/API/DOMTokenList/length
page-type: web-api-instance-property
browser-compat: api.DOMTokenList.length
---

{{APIRef("DOM")}}

خاصیت فقط خواندنی **`length`** از رابط {{domxref("DOMTokenList")}} یک عدد صحیح (`integer`) است که تعداد اشیاء ذخیره‌شده در آن شیء را نشان می‌دهد.

## مقدار

یک عدد صحیح مثبت، یا `0` اگر فهرست خالی باشد.

## مثال‌ها

در مثال زیر، فهرست کلاس‌های تنظیم‌شده روی یک عنصر {{htmlelement("span")}} را به صورت یک `DOMTokenList` با استفاده از {{domxref("Element.classList")}} بازیابی می‌کنیم، سپس طول فهرست را در {{domxref("Node.textContent")}} عنصر `<span>` می‌نویسیم.

ابتدا، HTML:

```html
<span class="a b c"></span>
```

حالا جاوااسکریپت:

```js
const span = document.querySelector("span");
const classes = span.classList;
const length = classes.length;

span.textContent = `classList length = ${length}`;
```

خروجی به این شکل است:

{{ EmbedLiveSample('Examples', '100%', 60) }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}