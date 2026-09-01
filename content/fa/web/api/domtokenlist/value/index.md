---
title: "DOMTokenList: value property"
short-title: value
slug: Web/API/DOMTokenList/value
page-type: web-api-instance-property
browser-compat: api.DOMTokenList.value
---

{{APIRef("DOM")}}

ویژگی **`value`** در واسط {{domxref("DOMTokenList")}} یک {{Glossary("stringifier")}} است که مقدار فهرست را به‌صورت رشته‌ای بازمی‌گرداند، یا فهرست را پاک کرده و آن را با مقدار داده‌شده تنظیم می‌کند.

## مقدار

یک رشته که محتوای سریالیزه‌شدهٔ فهرست را نشان می‌دهد.
هر آیتم با یک فاصله از دیگری جدا می‌شود.

## مثال‌ها

در مثال زیر، فهرست کلاس‌های تنظیم‌شده روی یک عنصر {{htmlelement("span")}} را به‌صورت یک `DOMTokenList` با استفاده از {{domxref("Element.classList")}} دریافت می‌کنیم، سپس مقدار فهرست را در {{domxref("Node.textContent")}} آن `<span>` می‌نویسیم.

ابتدا HTML:

```html
<span class="a b c"></span>
```

حالا جاوااسکریپت:

```js
const span = document.querySelector("span");
const classes = span.classList;
span.textContent = classes.value;
```

خروجی به این صورت است:

{{ EmbedLiveSample('Examples', '100%', 60) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}