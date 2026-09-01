---
title: "DOMTokenList: item() method"
short-title: item()
slug: Web/API/DOMTokenList/item
page-type: web-api-instance-method
browser-compat: api.DOMTokenList.item
---

{{APIRef("DOM")}}

متد **`item()`** در رابط {{domxref("DOMTokenList")}} آیتمی از فهرست را بر اساس موقعیت آن در فهرست، یعنی اندیس آن، برمی‌گرداند.

> [!NOTE]
> این متد معادل [نشانه‌گذاری براکت](/en-US/docs/Web/JavaScript/Reference/Operators/Property_accessors#bracket_notation) است. بنابراین `list.item(i)` با `list[i]` یکسان است.

## سینتکس

```js-nolint
item(index)
```

### پارامترها

- `index`
  - : عددی است که اندیس آیتم موردنظر برای بازگرداندن را مشخص می‌کند. اگر این عدد صحیح نباشد، فقط بخش صحیحِ آن در نظر گرفته می‌شود.

### مقدار بازگشتی

یک رشته که آیتم بازگشتی را نشان می‌دهد، یا اگر عدد بزرگ‌تر یا مساوی با `length` فهرست باشد، `null` برگردانده می‌شود.

### استثناها

- {{jsxref("TypeError")}}
  - : اگر نتوان `index` را به یک عدد صحیح تبدیل کرد، این خطا پرتاب می‌شود.

## مثال‌ها

در مثال زیر، فهرست کلاس‌های یک عنصر {{htmlelement("span")}} را به‌صورت یک `DOMTokenList` با استفاده از {{domxref("Element.classList")}} دریافت می‌کنیم. سپس آخرین آیتم فهرست را با `item(tokenList.length - 1)` برمی‌گردانیم و آن را در {{domxref("Node.textContent")}} عنصر `<span>` می‌نویسیم.

ابتدا HTML:

```html
<span class="a b c"></span>
```

حالا جاوااسکریپت:

```js
const span = document.querySelector("span");
const classes = span.classList;
const item = classes.item(classes.length - 1);
span.textContent = item;
```

خروجی به این صورت است:

{{ EmbedLiveSample('Examples', '100%', 60) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
